---
title: 'TN053 : Personnaliser les Routines DFX pour DAO base Classes de données | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.mfc.dfx
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c7bbbcc4e9fbf71713a55cd58538dbd69ef33b9f
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50064093"
---
# <a name="tn053-custom-dfx-routines-for-dao-database-classes"></a>TN053 : personnaliser les routines DFX pour les classes de base de données DAO

> [!NOTE]
>  Les Assistants et l’environnement Visual C++ ne prennent pas en charge les DAO (bien que les classes DAO sont incluses et vous pouvez toujours les utiliser). Microsoft recommande d’utiliser [modèles OLE DB](../data/oledb/ole-db-templates.md) ou [ODBC et MFC](../data/odbc/odbc-and-mfc.md) pour les nouveaux projets. Vous devez uniquement utiliser DAO à la gestion des applications existantes.

Cette note technique décrit le mécanisme DAO record field exchange (DFX). Pour aider à comprendre ce qui se passe dans les routines DFX, le `DFX_Text` fonction sera expliquée en détail par exemple. Comme une source supplémentaire d’informations à cette note technique, vous pouvez examiner le code pour les autres fonctions DFX individuelles. Vous aurez probablement pas besoin une routine DFX personnalisée aussi souvent que vous devrez peut-être une routine personnalisée de RFX (utilisée avec les classes de base de données ODBC).

Cette note technique contient :

- Vue d’ensemble DFX

- [Exemples](#_mfcnotes_tn053_examples) à l’aide de DAO Record Field Exchange et la liaison dynamique

- [Fonctionne de DFX](#_mfcnotes_tn053_how_dfx_works)

- [Ce que fait votre Routine DFX personnalisées](#_mfcnotes_tn053_what_your_custom_dfx_routine_does)

- [Détails de DFX_Text](#_mfcnotes_tn053_details_of_dfx_text)

**Vue d’ensemble DFX**

Le mécanisme d’échange champs d’enregistrements DAO (DFX) est utilisé pour simplifier la procédure de récupération et la mise à jour des données lorsque vous utilisez la `CDaoRecordset` classe. Le processus est simplifié à l’aide des membres de données de la `CDaoRecordset` classe. En dérivant de `CDaoRecordset`, vous pouvez ajouter des membres de données à la classe dérivée représentant chaque champ dans une table ou une requête. Ce mécanisme « liaison statique » est simple, mais il ne peut pas être la méthode d’extraction/mise à jour de données de choix pour toutes les applications. DFX récupère chaque champ lié à chaque modification de l’enregistrement actif. Si vous développez une application sensibles aux performances ne nécessitant pas l’extraction de chaque champ lors de la devise est modifiée, « liaison dynamique » via `CDaoRecordset::GetFieldValue` et `CDaoRecordset::SetFieldValue` peut être la méthode d’accès aux données de choix.

> [!NOTE]
>  DFX et la liaison dynamique ne sont pas mutuellement exclusives, pour une utilisation hybride de liaison statique et dynamique peut être utilisée.

## <a name="_mfcnotes_tn053_examples"></a> Exemple 1 : D’utilisation de DAO Record Field Exchange uniquement

(suppose `CDaoRecordset` — classe dérivée `CMySet` déjà ouvert)

```
// Add a new record to the customers table
myset.AddNew();

myset.m_strCustID = _T("MSFT");

myset.m_strCustName = _T("Microsoft");

myset.Update();
```

**Exemple 2 : D’utilisation de la liaison dynamique uniquement**

(suppose que le `CDaoRecordset` classe, `rs`, et elle est déjà ouverte)

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

**Exemple 3 : Utilisation de DAO Record Field Exchange et liaison dynamique**

(part du principe que les données de navigation employé avec `CDaoRecordset`-classe dérivée `emp`)

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

## <a name="_mfcnotes_tn053_how_dfx_works"></a> Fonctionne de DFX

Le mécanisme DFX fonctionne de manière similaire pour le mécanisme record field exchange (RFX) utilisée par les classes ODBC MFC. Principes de DFX et RFX sont les mêmes, mais il existe de nombreuses différences internes. La conception des fonctions DFX a été telles que pratiquement tout le code est partagé par les routines DFX individuels. Au plus haut niveau DFX uniquement effectue quelques opérations.

- DFX construit le code SQL **sélectionnez** clause et SQL **paramètres** clause si nécessaire.

- DFX construit la structure de liaison utilisée par de DAO `GetRows` (fonction) (nous y reviendrons plus tard).

- DFX gère la mémoire tampon de données utilisé pour détecter les champs modifiés (si le mécanisme de double tampon est utilisé)

- DFX gère le **NULL** et **DIRTY** état tableaux et définit les valeurs mises à jour si nécessaire.

Au cœur de la DFX mécanisme est le `CDaoRecordset` dérivée de la classe `DoFieldExchange` (fonction). Cette fonction distribue les appels aux fonctions DFX individuelles d’un type d’opération appropriée. Avant d’appeler `DoFieldExchange` les fonctions MFC internes définissent le type d’opération. La liste suivante montre les différents types d’opération et une brève description.

|Opération|Description|
|---------------|-----------------|
|`AddToParameterList`|Clause de paramètres de builds|
|`AddToSelectList`|Clause SELECT de builds|
|`BindField`|Définit la structure de liaison|
|`BindParam`|Définit les valeurs de paramètre|
|`Fixup`|Définit l’état de la valeur NULL|
|`AllocCache`|Alloue un cache pour vérification dirty|
|`StoreField`|Enregistre l’enregistrement en cours au cache|
|`LoadField`|Cache de restaurations aux valeurs de membre|
|`FreeCache`|Libère le cache|
|`SetFieldNull`|Jeux de champ État & valeur à NULL|
|`MarkForAddNew`|Marque les champs modifiés si ce n’est pas NULL PSEUDO|
|`MarkForEdit`|If incorrecte de marques champs ne correspondent pas au cache|
|`SetDirtyField`|Définit les valeurs marqués comme modifiés de champ|

Dans la section suivante, chaque opération est expliquée plus en détail pour `DFX_Text`.

La fonctionnalité la plus importante à comprendre concernant le processus d’échange de champs d’enregistrements DAO est qu’il utilise le `GetRows` fonction de la `CDaoRecordset` objet. DAO `GetRows` la fonction peut fonctionner de différentes manières. Cette note technique uniquement décris brièvement `GetRows` comme il se trouve en dehors de l’étendue de cette note technique.

DAO `GetRows` peuvent fonctionner dans plusieurs façons.

- Il peut extraire plusieurs champs de données et de plusieurs enregistrements en même temps. Ainsi, pour un accès plus rapide de données avec la complication de traiter une structure de données volumineuses et les décalages appropriés à chaque champ et pour chaque enregistrement de données de la structure. MFC ne tire pas parti de cet enregistrement plusieurs mécanisme de récupération.

- Une autre façon `GetRows` pouvez consiste à permettre aux programmeurs de spécifier les adresses de liaison pour les données récupérées de chaque champ d’un enregistrement de données.

- DAO sera également « effectuer un rappel » dans l’appelant pour les colonnes de longueur variable afin de permettre à l’appelant d’allocation de mémoire. Cette deuxième fonctionnalité présente l’avantage d’en réduisant le nombre de copies de données, ainsi que pour ce qui permet de stockage direct de données dans les membres d’une classe (la `CDaoRecordset` classe dérivée). Cet deuxième mécanisme est la méthode MFC utilise pour lier à des membres de données dans `CDaoRecordset` classes dérivées.

##  <a name="_mfcnotes_tn053_what_your_custom_dfx_routine_does"></a> Ce que fait votre Routine DFX personnalisées

Il est évident à partir de cette discussion l’opération la plus importante implémentée dans n’importe quelle fonction DFX doit être la possibilité de définir les structures de données requises pour appeler correctement `GetRows`. Il existe un nombre d’autres opérations une fonction DFX doit également prendre en charge, mais aucune comme importantes ou complexes en tant que la préparation correctement pour le `GetRows` appeler.

L’utilisation de DFX est décrite dans la documentation en ligne. En fait, il existe deux conditions. Tout d’abord, les membres doivent être ajoutés à la `CDaoRecordset` classe pour chaque champ lié et le paramètre dérivée. Suivant ce `CDaoRecordset::DoFieldExchange` doit être substituée. Notez que le type de données du membre est important. Il doit correspondre aux données à partir du champ dans la base de données ou au moins être convertible vers ce type. Par exemple, un champ numérique dans la base de données, comme un entier long, peut toujours être converti en texte et lié à un `CString` membre, mais un champ de texte dans une base de données n’est pas nécessairement peut-être être converties en une représentation numérique, tels qu’entier long et lié à une sécurité d’intégration de long er membre. DAO et le moteur de base de données Microsoft Jet sont responsables de la conversion (plutôt que MFC).

##  <a name="_mfcnotes_tn053_details_of_dfx_text"></a> Détails de DFX_Text

Comme mentionné précédemment, la meilleure façon d’expliquer le fonctionne de DFX consiste à étudier un exemple. À cet effet passer par les mécanismes internes de `DFX_Text` devrait fonctionner parfaitement bien pour fournir au moins une connaissance élémentaire de DFX.

- `AddToParameterList`

   Cette opération génère le code SQL **paramètres** clause («`Parameters <param name>, <param type> ... ;`») requis par Jet. Chaque paramètre est nommé et typé (comme spécifié dans l’appel RFX). Consultez la fonction `CDaoFieldExchange::AppendParamType` (fonction) pour afficher les noms des types individuels. Dans le cas de `DFX_Text`, le type utilisé est **texte**.

- `AddToSelectList`

   Génère le code SQL **sélectionnez** clause. Cela est assez simple comme le nom de colonne spécifié par l’appel DFX est simplement ajouté («`SELECT <column name>, ...`»).

- `BindField`

   Les plus complexes des opérations. Comme mentionné précédemment, il s’agit où la structure de liaison de DAO utilisée par `GetRows` est configuré. Comme vous pouvez le voir à partir du code dans `DFX_Text` les types d’informations dans la structure incluent le type DAO utilisé (**DAO_CHAR** ou **DAO_WCHAR** dans le cas de `DFX_Text`). En outre, le type de liaison utilisée est également configuré. Dans la section précédente `GetRows` a été décrit brièvement, mais il était suffisant expliquer que le type de liaison utilisée par MFC est toujours liaison d’adresse directe (**DAOBINDING_DIRECT**). En outre, pour la liaison de colonne de longueur variable (comme `DFX_Text`) liaison de rappel est utilisé pour que MFC peut contrôler l’allocation de mémoire et spécifiez une adresse de la longueur correcte. Cela signifie que MFC permettre toujours déterminer DAO « where » pour placer les données, permettant ainsi la liaison directement à des variables de membre. Le reste de la structure de liaison est rempli avec des éléments tels que l’adresse de la fonction de rappel d’allocation de mémoire et le type de liaison de colonne (liaison par nom de colonne).

- `BindParam`

   Il s’agit d’une opération simple qui appelle `SetParamValue` avec la valeur du paramètre spécifiée dans le membre de votre paramètre.

- `Fixup`

   Renseigne le **NULL** état pour chaque champ.

- `SetFieldNull`

   Cette opération marque seulement l’état de chaque champ en tant que **NULL** et définit le membre de la variable sur **PSEUDO_NULL**.

- `SetDirtyField`

   Appels `SetFieldValue` pour chaque champ marqué comme modifié.

Toutes les opérations restantes concernent uniquement l’utilisation du cache de données. Le cache de données est une mémoire tampon supplémentaire des données dans l’enregistrement actif est utilisé pour simplifier certaines choses. Par exemple, les champs « modifiées » peuvent être détectés automatiquement. Comme décrit dans la documentation en ligne, qu'il est possible de désactiver complètement ou au niveau du champ. L’implémentation de la mémoire tampon utilise une carte. Cette carte est utilisée pour faire correspondre les copies allouées de manière dynamique des données avec l’adresse du champ « lié » (ou `CDaoRecordset` dérivée du membre de données).

- `AllocCache`

   Dynamiquement alloue de la valeur du champ mis en cache et l’ajoute à la carte.

- `FreeCache`

   Supprime la valeur du champ mis en cache et le supprime de la carte.

- `StoreField`

   Copie la valeur du champ actuel dans le cache de données.

- `LoadField`

   Copie la valeur mise en cache dans le membre de champ.

- `MarkForAddNew`

   Vérifie si la valeur du champ actuel est non -**NULL** et marque incorrectes si nécessaire.

- `MarkForEdit`

   Compare la valeur de champ actuelle avec le cache de données et marque incorrectes si nécessaire.

> [!TIP]
> Modéliser vos routines DFX personnalisées sur les routines DFX existants pour les types de données standard.

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)

