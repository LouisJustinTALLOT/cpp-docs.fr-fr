---
title: 'TN053 : personnaliser les routines DFX pour les classes de base de données DAO'
ms.date: 09/17/2019
helpviewer_keywords:
- MFC, DAO and
- database classes [MFC], DAO
- DAO [MFC], MFC
- DFX (DAO record field exchange) [MFC], custom routines
- TN053
- DAO [MFC], classes
- DFX (DAO record field exchange) [MFC]
- custom DFX routines [MFC]
ms.assetid: fdcf3c51-4fa8-4517-9222-58aaa4f25cac
ms.openlocfilehash: f7ad854f4dbb4e90c09e886c69260e4e2eea3be2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365262"
---
# <a name="tn053-custom-dfx-routines-for-dao-database-classes"></a>TN053 : personnaliser les routines DFX pour les classes de base de données DAO

> [!NOTE]
> DAO est utilisé avec les bases de données Access et est pris en charge par Office 2013. DAO 3.6 est la version finale, et il est considéré comme obsolète. L’environnement visuel et les assistants ne prennent pas en charge DAO (bien que les classes DAO soient incluses et que vous puissiez toujours les utiliser). Microsoft vous recommande d’utiliser [OLE DB Templates](../data/oledb/ole-db-templates.md) ou [ODBC et MFC](../data/odbc/odbc-and-mfc.md) pour de nouveaux projets. Vous ne devez utiliser DAO que pour maintenir les applications existantes.

Cette note technique décrit le mécanisme d’échange de terrain record DAO (DFX). Pour aider à comprendre ce qui se passe `DFX_Text` dans les routines DFX, la fonction sera expliquée en détail à titre d’exemple. En tant que source d’information supplémentaire à cette note technique, vous pouvez examiner le code pour l’autre des fonctions DFX individuelles. Vous n’aurez probablement pas besoin d’une routine DFX personnalisée aussi souvent que vous pourriez avoir besoin d’une routine RFX personnalisée (utilisée avec les classes de base de données ODBC).

Cette note technique contient :

- Aperçu DFX

- [Exemples](#_mfcnotes_tn053_examples) utilisant DAO Record Field Exchange et Dynamic Binding

- [Fonctionnement de DFX](#_mfcnotes_tn053_how_dfx_works)

- [Ce que votre routine DFX personnalisée fait](#_mfcnotes_tn053_what_your_custom_dfx_routine_does)

- [Détails de DFX_Text](#_mfcnotes_tn053_details_of_dfx_text)

**Aperçu DFX**

Le mécanisme d’échange de terrain d’enregistrement DAO (DFX) est utilisé `CDaoRecordset` pour simplifier la procédure de récupération et de mise à jour des données lors de l’utilisation de la classe. Le processus est simplifié à `CDaoRecordset` l’aide des membres des données de la classe. En tirant de `CDaoRecordset`, vous pouvez ajouter des membres de données à la classe dérivée représentant chaque champ dans une table ou une requête. Ce mécanisme de « liaison statique » est simple, mais il se peut qu’il ne s’agisse pas de la méthode de collecte de données/mise à jour de choix pour toutes les applications. DFX récupère chaque champ lié chaque fois que l’enregistrement actuel est modifié. Si vous développez une application sensible aux performances qui ne nécessite pas d’aller chercher tous les champs lorsque la monnaie est modifiée, la « liaison dynamique » via `CDaoRecordset::GetFieldValue` et `CDaoRecordset::SetFieldValue` peut être la méthode d’accès aux données de choix.

> [!NOTE]
> DFX et liaison dynamique ne sont pas mutuellement exclusives, de sorte qu’une utilisation hybride de liaison statique et dynamique peut être utilisée.

## <a name="example-1--use-of-dao-record-field-exchange-only"></a><a name="_mfcnotes_tn053_examples"></a>Exemple 1 — Utilisation de DAO Record Field Exchange seulement

(suppose `CDaoRecordset` — classe `CMySet` dérivée déjà ouverte)

```
// Add a new record to the customers table
myset.AddNew();

myset.m_strCustID = _T("MSFT");

myset.m_strCustName = _T("Microsoft");

myset.Update();
```

**Exemple 2 — Utilisation de la liaison dynamique seulement**

(assume l’utilisation de `CDaoRecordset` la classe, `rs`, et il est déjà ouvert)

```
// Add a new record to the customers table
COleVariant  varFieldValue1 (_T("MSFT"),
    VT_BSTRT);

//Note: VT_BSTRT flags string type as ANSI,
    instead of UNICODE default
COleVariant  varFieldValue2  (_T("Microsoft"),
    VT_BSTRT);

rs.AddNew();

rs.SetFieldValue(_T("Customer_ID"),
    varFieldValue1);

rs.SetFieldValue(_T("Customer_Name"),
    varFieldValue2);

rs.Update();
```

**Exemple 3 — Utilisation de DAO Record Field Exchange et liaison dynamique**

(assume la navigation des `CDaoRecordset`données `emp`des employés avec la classe dérivée )

```
// Get the employee's data so that it can be displayed
emp.MoveNext();

// If user wants to see employee's photograph,
// fetch it
COleVariant varPhoto;
if (bSeePicture)
    emp.GetFieldValue(_T("photo"),
    varPhoto);

// Display the data
PopUpEmployeeData(emp.m_strFirstName,
    emp.m_strLastName,
    varPhoto);
```

## <a name="how-dfx-works"></a><a name="_mfcnotes_tn053_how_dfx_works"></a>Fonctionnement de DFX

Le mécanisme DFX fonctionne de la même manière que le mécanisme d’échange de champs de disques (RFX) utilisé par les classes MFC ODBC. Les principes de DFX et RFX sont les mêmes, mais il existe de nombreuses différences internes. La conception des fonctions DFX était telle que pratiquement tout le code est partagé par les routines DFX individuelles. Au plus haut niveau DFX ne fait que quelques choses.

- DFX construit la clause **SQL SELECT** et la clause **PARAMÈTRES SQL** si nécessaire.

- DFX construit la structure de liaison `GetRows` utilisée par la fonction de DAO (plus sur ce plus tard).

- DFX gère le tampon de données utilisé pour détecter les champs sales (si le double tampon est utilisé)

- DFX gère les tableaux de statut **NULL** et **DIRTY** et définit les valeurs si nécessaire sur les mises à jour.

Au cœur du mécanisme DFX se `DoFieldExchange` trouve la fonction de la `CDaoRecordset` classe dérivée. Cette fonction envoie des appels aux fonctions DFX individuelles d’un type d’opération approprié. Avant `DoFieldExchange` d’appeler les fonctions internes MFC définir le type de fonctionnement. La liste suivante montre les différents types d’opérations et une brève description.

|Opération|Description|
|---------------|-----------------|
|`AddToParameterList`|Construit la clause PARAMETERS|
|`AddToSelectList`|Construit la clause SELECT|
|`BindField`|Établit une structure de liaison|
|`BindParam`|Définit les valeurs de paramètres|
|`Fixup`|Définit l’état NULL|
|`AllocCache`|Alloue cache pour le chèque sale|
|`StoreField`|Enregistre le record actuel à cache|
|`LoadField`|Restaure le cache aux valeurs des membres|
|`FreeCache`|Frees cache|
|`SetFieldNull`|Définit l’état du terrain & valeur à NULL|
|`MarkForAddNew`|Marques champs sales si ce n’est PSEUDO NULL|
|`MarkForEdit`|Marques champs sales si ne correspondent pas cache|
|`SetDirtyField`|Définit les valeurs de champ marquées comme sales|

Dans la section suivante, chaque opération sera `DFX_Text`expliquée plus en détail pour .

La caractéristique la plus importante à comprendre au sujet du `GetRows` processus `CDaoRecordset` d’échange de terrain d’enregistrement DAO est qu’il utilise la fonction de l’objet. La fonction `GetRows` DAO peut fonctionner de plusieurs façons. Cette note technique ne `GetRows` sera que brièvement décrit car elle est en dehors du champ d’application de cette note technique.
DAO `GetRows` peut fonctionner de plusieurs façons.

- Il peut aller chercher plusieurs enregistrements et plusieurs champs de données en même temps. Cela permet un accès plus rapide aux données avec la complication de traiter avec une grande structure de données et les décalages appropriés pour chaque domaine et pour chaque enregistrement des données dans la structure. MFC ne profite pas de ce mécanisme d’aller chercher des dossiers multiples.

- Une `GetRows` autre façon peut fonctionner est de permettre aux programmeurs de spécifier des adresses contraignantes pour les données récupérées de chaque champ pour un enregistrement de données.

- DAO va également "rappeler" dans l’appelant pour les colonnes de longueur variable afin de permettre à l’appelant d’allouer la mémoire. Cette deuxième fonctionnalité a l’avantage de minimiser le nombre de copies de données ainsi que `CDaoRecordset` de permettre le stockage direct des données dans les membres d’une classe (la classe dérivée). Ce deuxième mécanisme est la méthode que MFC utilise pour se lier aux membres de données dans `CDaoRecordset` les classes dérivées.

## <a name="what-your-custom-dfx-routine-does"></a><a name="_mfcnotes_tn053_what_your_custom_dfx_routine_does"></a>Ce que votre routine DFX personnalisée fait

Il ressort de cette discussion que l’opération la plus importante mise en œuvre dans `GetRows`toute fonction DFX doit être la capacité de mettre en place les structures de données requises pour appeler avec succès . Il existe un certain nombre d’autres opérations qu’une fonction DFX doit également `GetRows` prendre en charge, mais aucune aussi importante ou complexe que la préparation correcte pour l’appel.

L’utilisation de DFX est décrite dans la documentation en ligne. Essentiellement, il y a deux exigences. Tout d’abord, les `CDaoRecordset` membres doivent être ajoutés à la classe dérivée pour chaque champ et paramètre lié. La `CDaoRecordset::DoFieldExchange` suite devrait être annulée. Notez que le type de données du membre est important. Il doit correspondre aux données du champ dans la base de données ou au moins être convertible à ce type. Par exemple, un champ numérique dans la base de données, tel qu’un `CString` long integer, peut toujours être converti en texte et lié à un membre, mais un champ de texte dans une base de données ne peut pas nécessairement être converti en une représentation numérique, comme un long integer et lié à un membre integer long. DAO et le moteur de base de données Microsoft Jet sont responsables de la conversion (plutôt que MFC).

## <a name="details-of-dfx_text"></a><a name="_mfcnotes_tn053_details_of_dfx_text"></a>Détails de DFX_Text

Comme mentionné précédemment, la meilleure façon d’expliquer comment DFX fonctionne est de travailler à travers un exemple. À cette fin, passer `DFX_Text` par les internes de devrait fonctionner très bien pour aider à fournir au moins une compréhension de base de DFX.

- `AddToParameterList`

   Cette opération construit la clause SQL`Parameters <param name>, <param type> ... ;` **PARAMETERS** («) exigée par Jet. Chaque paramètre est nommé et tapé (comme indiqué dans l’appel RFX). Consultez la `CDaoFieldExchange::AppendParamType` fonction pour voir les noms des types individuels. Dans le `DFX_Text`cas de , le type utilisé est **le texte**.

- `AddToSelectList`

   Construit la clause **SQL SELECT.** C’est assez simple que le nom de colonne spécifié par l’appel DFX est tout simplement annexé (").`SELECT <column name>, ...`

- `BindField`

   La plus complexe des opérations. Comme mentionné précédemment, c’est là `GetRows` que la structure de liaison DAO utilisée par est mis en place. Comme vous pouvez le `DFX_Text` voir à partir du code dans les types d’informations dans la structure `DFX_Text`comprennent le type DAO utilisé **(DAO_CHAR** ou **DAO_WCHAR** dans le cas de ). En outre, le type de liaison utilisée est également mis en place. Dans une `GetRows` section antérieure n’a été décrite que brièvement, mais il suffisait d’expliquer que le type de liaison utilisée par MFC est toujours contraignante directe **(DAOBINDING_DIRECT**). En outre, pour la liaison `DFX_Text`de colonne variable (comme ) la liaison de rappel est utilisée de sorte que MFC peut contrôler l’allocation de mémoire et spécifier une adresse de la longueur correcte. Ce que cela signifie, c’est que MFC peut toujours dire À DAO "où" mettre les données, permettant ainsi de se lier directement aux variables des membres. Le reste de la structure de liaison est rempli de choses comme l’adresse de la fonction de rappel d’allocation de mémoire et le type de liaison de colonne (liaison par nom de colonne).

- `BindParam`

   Il s’agit d’une opération simple qui appelle `SetParamValue` avec la valeur de paramètre spécifiée dans votre membre paramètre.

- `Fixup`

   Remplit le statut **NULL** pour chaque champ.

- `SetFieldNull`

   Cette opération ne marque que chaque statut de champ comme **NULL** et définit la valeur de la variable du membre à **PSEUDO_NULL**.

- `SetDirtyField`

   Appels `SetFieldValue` pour chaque champ marqué sale.

Toutes les opérations restantes ne traitent que de l’utilisation du cache de données. Le cache de données est un tampon supplémentaire des données dans l’enregistrement actuel qui est utilisé pour rendre certaines choses plus simples. Par exemple, les champs « sales » peuvent être automatiquement détectés. Tel que décrit dans la documentation en ligne, il peut être désactivé complètement ou au niveau du terrain. La mise en œuvre du tampon utilise une carte. Cette carte est utilisée pour faire correspondre les copies dynamiquement allouées des `CDaoRecordset` données avec l’adresse du champ « lié » (ou membre des données dérivées).

- `AllocCache`

   Alloue dynamiquement la valeur du champ mise en cache et l’ajoute à la carte.

- `FreeCache`

   Supprime la valeur du champ mise en cache et la supprime de la carte.

- `StoreField`

   Copie la valeur actuelle du champ dans le cache de données.

- `LoadField`

   Copie la valeur mise en cache dans le membre de champ.

- `MarkForAddNew`

   Vérifie si la valeur actuelle du champ n’est pas**NULL** et la marque sale si nécessaire.

- `MarkForEdit`

   Compare la valeur actuelle du champ avec le cache de données et les marques sales si nécessaire.

> [!TIP]
> Modéchez vos routines DFX personnalisées sur les routines DFX existantes pour les types de données standard.

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)
