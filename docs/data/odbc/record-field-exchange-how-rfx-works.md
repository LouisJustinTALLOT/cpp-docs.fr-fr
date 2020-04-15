---
title: 'Record Field Exchange : fonctionnement de RFX'
ms.date: 11/04/2016
helpviewer_keywords:
- record editing [C++], using RFX
- RFX (ODBC) [C++], updating data in recordsets
- scrolling [C++]
- ODBC [C++], RFX
- data binding [C++], DFX
- scrolling [C++], RFX
- RFX (ODBC) [C++], binding fields and parameters
ms.assetid: e647cacd-62b0-4b80-9e20-b392deca5a88
ms.openlocfilehash: 903acf4f55fb2708f4998a2babf3f143c895429b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367174"
---
# <a name="record-field-exchange-how-rfx-works"></a>Record Field Exchange : fonctionnement de RFX

Ce sujet explique le processus RFX. Il s’agit d’un sujet avancé couvrant:

- [RFX et le recordet](#_core_rfx_and_the_recordset)

- [Le processus RFX](#_core_the_record_field_exchange_process)

> [!NOTE]
> Cette rubrique s’applique aux classes dérivées de `CRecordset` où l’extraction de lignes en bloc n’a pas été implémentée. Si vous utilisez l’extraction de lignes en bloc, l’échange de champs d’enregistrements en bloc (Bulk RFX) est implémenté. Bulk RFX est similaire à RFX. Pour comprendre les différences, voir [Recordset: Fetching Records in Bulk (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

## <a name="rfx-and-the-recordset"></a><a name="_core_rfx_and_the_recordset"></a>RFX et le Recordet

Les membres des données de terrain de l’objet de l’enregistrement, pris ensemble, constituent un tampon de modification qui contient les colonnes sélectionnées d’un enregistrement. Lorsque le jeu d’enregistrement est ouvert pour la première fois et est sur le point de lire le premier enregistrement, RFX lie (associés) chaque colonne sélectionnée à l’adresse du membre de données de terrain approprié. Lorsque le recordet met à jour un enregistrement, RFX appelle les fonctions API D’ODBC pour envoyer une déclaration SQL **UPDATE** ou **INSERT** au conducteur. RFX utilise sa connaissance des membres des données sur le terrain pour spécifier les colonnes à écrire.

Le cadre soutient le tampon de modification à certaines étapes afin qu’il puisse restaurer son contenu si nécessaire. RFX soutient le tampon de modification avant d’ajouter un nouvel enregistrement et avant d’éditer un enregistrement existant. Il restaure le tampon de modification dans `Update` certains `AddNew`cas, par exemple, après un appel suivant . Le tampon de modification n’est pas restauré si vous abandonnez un `Update`tampon de modification nouvellement modifié en passant, par exemple, à un autre enregistrement avant d’appeler .

En plus d’échanger des données entre la source de données et les membres des données de terrain du recordet, RFX gère des paramètres contraignants. Lorsque le dossier est ouvert, les membres des données de paramètres sont liés dans `CRecordset::Open` l’ordre des « ? » les détenteurs de places dans la déclaration SQL qui construit. Pour plus d’informations, voir [Recordset: Parameterizing a Recordset (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

Votre classe de documents remplace `DoFieldExchange` tout le travail, en déplaçant les données dans les deux sens. Comme l’échange de données de dialogue (DDX), RFX a besoin d’informations sur les données des membres de votre classe. L’assistant fournit les informations nécessaires en écrivant une mise en œuvre spécifique à l’enregistrement pour vous, en fonction des noms des membres de données sur le terrain et des types de `DoFieldExchange` données que vous spécifiez avec l’assistant.

## <a name="record-field-exchange-process"></a><a name="_core_the_record_field_exchange_process"></a>Processus d’échange de terrain record

Cette section décrit la séquence des événements RFX comme un objet de recordet est ouvert et que vous ajoutez, mettez à jour et supprimez des enregistrements. La séquence de tableau [des opérations RFX pendant l’ouverture de records](#_core_sequence_of_rfx_operations_during_recordset_open) et la séquence de table des opérations [RFX Pendant le défilement](#_core_sequence_of_rfx_operations_during_scrolling) dans ce sujet montrent le processus pendant que RFX traite une `Move` commande dans le jeu d’enregistrement et que RFX gère une mise à jour. Au cours de ces processus, [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) est appelé à effectuer de nombreuses opérations différentes. Le `m_nOperation` membre des données de l’objet [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) détermine l’opération demandée. Vous trouverez peut-être utile de lire [Recordset: How Recordsets Select Records (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md) et [Recordset: How Recordsets Update Records (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md) avant de lire ce matériel.

### <a name="rfx-initial-binding-of-columns-and-parameters"></a><a name="_mfc_rfx.3a_.initial_binding_of_columns_and_parameters"></a>RFX : Liaison initiale des colonnes et des paramètres

Les activités RFX suivantes se produisent, dans l’ordre indiqué, lorsque vous appelez la fonction de membre [Open](../../mfc/reference/crecordset-class.md#open) d’un objet d’enregistrement :

- Si le jeu d’enregistrement a `DoFieldExchange` des membres de données de paramètres, le cadre appelle à lier les paramètres aux paramètres des participants dans la chaîne de relevé SQL du dossier. Une représentation dépendante du type de données de la valeur du paramètre est utilisée pour chaque place que l’on trouve dans l’énoncé **SELECT.** Cela se produit après la déclaration SQL est préparé, mais avant qu’il ne soit exécuté. Pour plus d’informations `::SQLPrepare` sur la préparation des déclarations, consultez la fonction dans la référence du programmeur de *l’ODBC*.

- Le cadre `DoFieldExchange` appelle une deuxième fois à lier les valeurs des colonnes sélectionnées aux membres de données de terrain correspondants dans le jeu d’enregistrement. Cela établit l’objet de l’enregistrement comme tampon de modification contenant les colonnes du premier enregistrement.

- Le dossier exécute l’instruction SQL et la source de données sélectionne le premier enregistrement. Les colonnes de l’enregistrement sont chargées dans les membres des données de terrain du recordet.

Le tableau suivant montre la séquence des opérations RFX lorsque vous ouvrez un jeu d’enregistrements.

### <a name="sequence-of-rfx-operations-during-recordset-open"></a><a name="_core_sequence_of_rfx_operations_during_recordset_open"></a>Séquence des opérations RFX pendant l’open De Recordset

|Votre opération|Opération DoFieldExchange|Base de données/opération SQL|
|--------------------|-------------------------------|-----------------------------|
|1. Open recordset.|||
||2. Construire une déclaration SQL.||
|||3. Envoyer le SQL.|
||4. Lier les membres des données de paramètres.||
||5. Lier les membres des données sur le terrain aux colonnes.||
|||6. ODBC effectue le déménagement et remplit les données.|
||7. Réparez les données pour le C.||

Les records utilisent l’exécution préparée par ODBC pour permettre un requerying rapide avec la même déclaration SQL. Pour plus d’informations sur l’exécution préparée, consultez la *référence du programmeur* SDK de l’ODBC dans la bibliothèque MSDN.

### <a name="rfx-scrolling"></a><a name="_mfc_rfx.3a_.scrolling"></a>RFX: Défilement

Lorsque vous faites défiler d’un `DoFieldExchange` enregistrement à l’autre, le cadre appelle pour remplacer les valeurs précédemment stockées dans les membres de données de terrain par des valeurs pour le nouvel enregistrement.

Le tableau suivant montre la séquence des opérations RFX lorsque l’utilisateur passe de l’enregistrement à l’enregistrement.

### <a name="sequence-of-rfx-operations-during-scrolling"></a><a name="_core_sequence_of_rfx_operations_during_scrolling"></a>Séquence des opérations RFX pendant le défilement

|Votre opération|Opération DoFieldExchange|Base de données/opération SQL|
|--------------------|-------------------------------|-----------------------------|
|1. `MoveNext` Appelez ou l’une des autres fonctions Move.|||
|||2. ODBC fait le mouvement et remplit les données.|
||3. Réparez les données pour le C.||

### <a name="rfx-adding-new-records-and-editing-existing-records"></a><a name="_mfc_rfx.3a_.adding_new_records_and_editing_existing_records"></a>RFX: Ajout de nouveaux enregistrements et l’édition des enregistrements existants

Si vous ajoutez un nouvel enregistrement, le recordet fonctionne comme tampon de modification pour construire le contenu du nouvel enregistrement. Comme pour l’ajout d’enregistrements, l’édition des enregistrements implique de modifier les valeurs des membres des données sur le terrain du groupe d’enregistrement. Du point de vue RFX, la séquence est la suivante :

1. Votre appel à la fonction [AddNew](../../mfc/reference/crecordset-class.md#addnew) ou [Edit](../../mfc/reference/crecordset-class.md#edit) membre du recordet fait en sorte que RFX stocke le tampon de modification actuel afin qu’il puisse être restauré plus tard.

1. `AddNew`ou `Edit` prépare les champs dans le tampon de modification afin que RFX puisse détecter les membres modifiés des données sur le terrain.

   Parce qu’un nouvel enregistrement n’a pas `AddNew` de valeurs antérieures pour comparer de nouvelles avec, définit la valeur de chaque membre des données de champ à une valeur PSEUDO_NULL. Plus tard, `Update`lorsque vous appelez, RFX compare la valeur de chaque membre de données avec la valeur PSEUDO_NULL. S’il y a une différence, le membre des données a été défini. (PSEUDO_NULL n’est pas la même chose qu’une colonne d’enregistrement avec une vraie valeur Null ni l’un ou l’autre de ces n’est le même que C 'NULL.)

   Contrairement `Update` à `AddNew`l’appel pour , l’appel `Update` pour `Edit` compare les valeurs mises à jour avec des valeurs précédemment stockées plutôt que d’utiliser PSEUDO_NULL. La différence `AddNew` est qu’il n’y a pas de valeurs précédemment stockées à comparer.

1. Vous définissez directement les valeurs des membres de données sur le terrain dont vous souhaitez modifier les valeurs ou que vous souhaitez remplir pour un nouvel enregistrement. Cela peut `SetFieldNull`inclure l’appel .

1. Votre appel pour mettre à [jour](../../mfc/reference/crecordset-class.md#update) les contrôles pour les membres modifiés des données sur le terrain, tel que décrit à l’étape 2 (voir la séquence de tableau [des opérations RFX pendant le défilement](#_core_sequence_of_rfx_operations_during_scrolling)). Si aucun n’a changé, `Update` les retours 0. Si certains membres des `Update` données sur le terrain ont changé, prépare et exécute une déclaration SQL **INSERT** qui contient des valeurs pour tous les champs mis à jour dans le dossier.

1. Pour `AddNew` `Update` , conclut en rétablissant les valeurs précédemment stockées `AddNew` de l’enregistrement qui était à jour avant l’appel. Pour `Edit`, les nouvelles valeurs éditées restent en place.

Le tableau suivant affiche la séquence des opérations RFX lorsque vous ajoutez un nouvel enregistrement ou modifiez un enregistrement existant.

### <a name="sequence-of-rfx-operations-during-addnew-and-edit"></a>Séquence des opérations RFX pendant AddNew et Edit

|Votre opération|Opération DoFieldExchange|Base de données/opération SQL|
|--------------------|-------------------------------|-----------------------------|
|1. `AddNew` Appelez `Edit`ou .|||
||2. Sauvegarder le tampon de modification.||
||3. `AddNew`Pour , marquer les membres des données sur le terrain comme «propre» et Null.||
|4. Attribuer des valeurs aux membres des données sur le terrain de l’enregistrement.|||
|5. `Update`Appelez .|||
||6. Vérifiez s’il y a des champs changés.||
||7. Construire **INSERT** SQL `AddNew` INSERT déclaration `Edit`pour ou MISE à **JOUR** déclaration pour .||
|||8. Envoyer le SQL.|
||9. `AddNew`Pour, restaurer le tampon de modification à son contenu de sauvegarde. Pour `Edit`, supprimer la sauvegarde.||

### <a name="rfx-deleting-existing-records"></a>RFX: Suppression des dossiers existants

Lorsque vous supprimez un enregistrement, RFX définit tous les champs vers NULL pour rappeler que l’enregistrement est supprimé et que vous devez vous en éloigner. Vous n’avez pas besoin d’autres informations de séquence RFX.

## <a name="see-also"></a>Voir aussi

[Échange de terrain record (RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[Consommation ODBC MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[Macros, fonctions globales et variables globales](../../mfc/reference/mfc-macros-and-globals.md)<br/>
[Classe CFieldExchange](../../mfc/reference/cfieldexchange-class.md)<br/>
[CRecordset::DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)
