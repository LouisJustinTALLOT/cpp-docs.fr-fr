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
ms.openlocfilehash: 6dde96520d9472726da86f8da295770cccc5d42c
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303434"
---
# <a name="tn053-custom-dfx-routines-for-dao-database-classes"></a>TN053 : personnaliser les routines DFX pour les classes de base de données DAO

> [!NOTE]
>  DAO est utilisé avec les bases de données Access et est pris en charge via Office 2013. DAO 3,6 est la version finale et est considéré comme obsolète. L’environnement C++ visuel et les assistants ne prennent pas en charge DAO (bien que les classes DAO soient incluses et vous puissiez toujours les utiliser). Microsoft vous recommande d'utiliser les [modèles OLE DB](../data/oledb/ole-db-templates.md) ou [ODBC et MFC](../data/odbc/odbc-and-mfc.md) pour vos nouveaux projets. Vous ne devez utiliser que DAO pour gérer les applications existantes.

Cette note technique décrit le mécanisme d’échange de champs d’enregistrements DAO (DFX). Pour mieux comprendre ce qui se passe dans les routines DFX, la fonction `DFX_Text` est expliquée en détail comme exemple. En tant que source supplémentaire d’informations pour cette note technique, vous pouvez examiner le code pour les autres fonctions DFX individuelles. Vous n’aurez probablement pas besoin d’une routine DFX personnalisée aussi souvent que vous aurez besoin d’une routine RFX personnalisée (utilisée avec les classes de base de données ODBC).

Cette note technique contient les éléments suivants :

- Présentation de DFX

- [Exemples](#_mfcnotes_tn053_examples) utilisant l’échange de champs d’enregistrements DAO et la liaison dynamique

- [Fonctionnement de DFX](#_mfcnotes_tn053_how_dfx_works)

- [Ce que fait votre routine DFX personnalisée](#_mfcnotes_tn053_what_your_custom_dfx_routine_does)

- [Détails de DFX_Text](#_mfcnotes_tn053_details_of_dfx_text)

**Présentation de DFX**

Le mécanisme d’échange de champs d’enregistrements DAO (DFX) est utilisé pour simplifier la procédure de récupération et de mise à jour des données lors de l’utilisation de la classe `CDaoRecordset`. Le processus est simplifié à l’aide de membres de données de la classe `CDaoRecordset`. En dérivant de `CDaoRecordset`, vous pouvez ajouter des membres de données à la classe dérivée représentant chaque champ d’une table ou d’une requête. Ce mécanisme de « liaison statique » est simple, mais il peut ne pas être la méthode d’extraction/mise à jour des données de votre choix pour toutes les applications. DFX récupère chaque champ lié chaque fois que l’enregistrement actif est modifié. Si vous développez une application sensible aux performances qui ne nécessite pas l’extraction de chaque champ lorsque la devise est modifiée, la « liaison dynamique » via `CDaoRecordset::GetFieldValue` et `CDaoRecordset::SetFieldValue` peut être la méthode d’accès aux données de votre choix.

> [!NOTE]
>  DFX et la liaison dynamique ne s’excluent pas mutuellement, par conséquent, une utilisation hybride des liaisons statiques et dynamiques peut être utilisée.

## <a name="_mfcnotes_tn053_examples"></a>Exemple 1 : utilisation de l’échange de champs d’enregistrements DAO uniquement

(suppose `CDaoRecordset` : la classe dérivée `CMySet` déjà ouverte)

```
// Add a new record to the customers table
myset.AddNew();

myset.m_strCustID = _T("MSFT");

myset.m_strCustName = _T("Microsoft");

myset.Update();
```

**Exemple 2 : utilisation de la liaison dynamique uniquement**

(suppose l’utilisation de la classe `CDaoRecordset`, `rs`et elle est déjà ouverte)

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

**Exemple 3 : utilisation de l’échange de champs d’enregistrements DAO et de la liaison dynamique**

(suppose l’exploration des données de l’employé avec une classe dérivée `CDaoRecordset``emp`)

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

## <a name="_mfcnotes_tn053_how_dfx_works"></a>Fonctionnement de DFX

Le mécanisme DFX fonctionne de la même façon que le mécanisme RFX (Record Field Exchange) utilisé par les classes ODBC MFC. Les principes de DFX et de RFX sont les mêmes, mais il existe de nombreuses différences internes. La conception des fonctions DFX était telle que presque tout le code est partagé par les routines DFX individuelles. Au niveau le plus élevé, DFX ne fait que quelques choses.

- DFX construit la clause SQL **Select** et la clause SQL **Parameters** , si nécessaire.

- DFX construit la structure de liaison utilisée par la fonction `GetRows` de DAO (plus d’informations sur ce point plus tard).

- DFX gère le tampon de données utilisé pour détecter les champs de modification (si la double mise en mémoire tampon est utilisée)

- DFX gère les tableaux d’état **null** et **incorrects** et définit des valeurs si nécessaire sur les mises à jour.

Au cœur du mécanisme DFX se trouve le `CDaoRecordset` fonction `DoFieldExchange` de la classe dérivée. Cette fonction distribue les appels aux fonctions DFX individuelles d’un type d’opération approprié. Avant d’appeler `DoFieldExchange` les fonctions MFC internes définissent le type d’opération. La liste suivante présente les différents types d’opérations et une brève description.

|Opération|Description|
|---------------|-----------------|
|`AddToParameterList`|Builds, clause de paramètres|
|`AddToSelectList`|Builds SELECT (clause)|
|`BindField`|Définit la structure de liaison|
|`BindParam`|Définit les valeurs des paramètres|
|`Fixup`|Définit l’État NULL|
|`AllocCache`|Alloue le cache pour la vérification incorrecte|
|`StoreField`|Enregistre l’enregistrement en cours dans le cache|
|`LoadField`|Restaure les valeurs de cache sur les membres|
|`FreeCache`|Libère le cache|
|`SetFieldNull`|Affecte la valeur NULL à l’état du champ &|
|`MarkForAddNew`|Marque les champs modifiés s’ils ne sont pas PSEUDO-NULL|
|`MarkForEdit`|Marque les champs erronés si ne correspond pas au cache|
|`SetDirtyField`|Définit les valeurs de champ marquées comme étant modifiées|

Dans la section suivante, chaque opération sera expliquée plus en détail pour `DFX_Text`.

La fonctionnalité la plus importante à comprendre sur le processus d’échange de champs d’enregistrements DAO est qu’elle utilise la fonction `GetRows` de l’objet `CDaoRecordset`. La fonction DAO `GetRows` peut fonctionner de plusieurs façons. Cette note technique décrira brièvement `GetRows`, car elle ne se trouve pas dans le cadre de cette note technique.
Les `GetRows` DAO peuvent fonctionner de plusieurs façons.

- Il peut extraire plusieurs enregistrements et plusieurs champs de données à la fois. Cela permet d’accélérer l’accès aux données avec une plus grande difficulté en matière de gestion d’une structure de données volumineuse et des décalages appropriés pour chaque champ et pour chaque enregistrement de données dans la structure. MFC ne tire pas parti de ce mécanisme de récupération d’enregistrements multiples.

- Une autre façon de `GetRows` peut être utilisée pour permettre aux programmeurs de spécifier des adresses de liaison pour les données récupérées de chaque champ pour un enregistrement de données.

- DAO effectue également un « rappel » dans l’appelant pour les colonnes de longueur variable afin de permettre à l’appelant d’allouer de la mémoire. Cette deuxième fonctionnalité présente l’avantage de réduire le nombre de copies de données et d’autoriser le stockage direct des données dans les membres d’une classe (classe dérivée `CDaoRecordset`). Ce deuxième mécanisme est la méthode utilisée par MFC pour effectuer une liaison à des données membres dans `CDaoRecordset` classes dérivées.

##  <a name="_mfcnotes_tn053_what_your_custom_dfx_routine_does"></a>Ce que fait votre routine DFX personnalisée

Dans cette discussion, il est évident que l’opération la plus importante implémentée dans une fonction DFX doit être la possibilité de configurer les structures de données requises pour appeler correctement `GetRows`. Une fonction DFX doit également prendre en charge un certain nombre d’autres opérations, mais aucune n’est aussi importante ou complexe que de se préparer correctement pour l’appel de `GetRows`.

L’utilisation de DFX est décrite dans la documentation en ligne. Pour l’essentiel, il existe deux exigences. Tout d’abord, les membres doivent être ajoutés à la classe dérivée `CDaoRecordset` pour chaque champ et paramètre liés. Après cette `CDaoRecordset::DoFieldExchange` devez être substitué. Notez que le type de données du membre est important. Il doit correspondre aux données du champ de la base de données ou au moins être convertibles en ce type. Par exemple, un champ numérique dans une base de données, tel qu’un entier long, peut toujours être converti en texte et lié à un membre `CString`, mais un champ de texte dans une base de données ne peut pas nécessairement être converti en représentation numérique, comme un entier long et lié à un membre long Integer. DAO et le moteur de base de données Microsoft Jet sont responsables de la conversion (plutôt que de MFC).

##  <a name="_mfcnotes_tn053_details_of_dfx_text"></a>Détails de DFX_Text

Comme nous l’avons vu précédemment, la meilleure façon d’expliquer le fonctionnement de DFX consiste à utiliser un exemple. À cet effet, le fonctionnement des éléments internes de `DFX_Text` doit être très efficace pour vous aider à fournir au moins une compréhension élémentaire de DFX.

- `AddToParameterList`

   Cette opération génère la clause de **paramètres** SQL («`Parameters <param name>, <param type> ... ;`») requise par jet. Chaque paramètre est nommé et typé (comme spécifié dans l’appel RFX). Consultez la fonction `CDaoFieldExchange::AppendParamType` pour afficher les noms des types individuels. Dans le cas de `DFX_Text`, le type utilisé est **texte**.

- `AddToSelectList`

   Génère la clause SQL **Select** . C’est assez simple, car le nom de colonne spécifié par l’appel DFX est simplement ajouté («`SELECT <column name>, ...`»).

- `BindField`

   La plus complexe des opérations. Comme mentionné précédemment, c’est là que la structure de liaison DAO utilisée par `GetRows` est configurée. Comme vous pouvez le voir dans le code de `DFX_Text` les types d’informations de la structure incluent le type DAO utilisé (**DAO_CHAR** ou **DAO_WCHAR** dans le cas de `DFX_Text`). En outre, le type de liaison utilisé est également configuré. Dans une section précédente `GetRows` n’a été décrit que brièvement, mais cela suffisait à expliquer que le type de liaison utilisé par MFC est toujours la liaison d’adresse directe (**DAOBINDING_DIRECT**). En outre, la liaison de rappel de colonne de longueur variable (comme `DFX_Text`) est utilisée pour que les MFC puissent contrôler l’allocation de mémoire et spécifier une adresse de longueur correcte. Cela signifie que les MFC peuvent toujours dire à DAO « WHERE » de placer les données, ce qui permet de lier directement les variables de membre. Le reste de la structure de liaison est rempli avec des éléments tels que l’adresse de la fonction de rappel d’allocation de mémoire et le type de liaison de colonne (liaison par nom de colonne).

- `BindParam`

   Il s’agit d’une opération simple qui appelle `SetParamValue` avec la valeur de paramètre spécifiée dans votre membre de paramètre.

- `Fixup`

   Remplit l’état **null** pour chaque champ.

- `SetFieldNull`

   Cette opération marque uniquement l’état du champ comme **null** et définit la valeur de la variable membre sur **PSEUDO_NULL**.

- `SetDirtyField`

   Appelle `SetFieldValue` pour chaque champ marqué comme modifié.

Toutes les opérations restantes traitent uniquement de l’utilisation du cache de données. Le cache de données est une mémoire tampon supplémentaire des données de l’enregistrement actif qui est utilisée pour simplifier certaines choses. Par exemple, les champs « modifiés » peuvent être détectés automatiquement. Comme décrit dans la documentation en ligne, il peut être désactivé complètement ou au niveau du champ. L’implémentation de la mémoire tampon utilise un mappage. Ce mappage est utilisé pour faire correspondre des copies allouées dynamiquement des données avec l’adresse du champ « lié » (ou `CDaoRecordset` données membres dérivées).

- `AllocCache`

   Alloue dynamiquement la valeur du champ mis en cache et l’ajoute à la classe Map.

- `FreeCache`

   Supprime la valeur du champ mis en cache et la supprime de la carte.

- `StoreField`

   Copie la valeur de champ actuelle dans le cache de données.

- `LoadField`

   Copie la valeur mise en cache dans le membre de champ.

- `MarkForAddNew`

   Vérifie si la valeur de champ actuelle n’est pas**null** et la marque comme étant modifiée si nécessaire.

- `MarkForEdit`

   Compare la valeur de champ actuelle avec le cache de données et marque les modifications incorrectes si nécessaire.

> [!TIP]
> Modélisez vos routines DFX personnalisées sur les routines DFX existantes pour les types de données standard.

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)
