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
ms.openlocfilehash: 0661e61bceeedc0dd049ef47f5a0a0b71a8d82ed
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213068"
---
# <a name="record-field-exchange-how-rfx-works"></a>Record Field Exchange : fonctionnement de RFX

Cette rubrique décrit le processus RFX. Il s’agit d’une rubrique avancée qui couvre les sujets suivants :

- [RFX et le Recordset](#_core_rfx_and_the_recordset)

- [Processus RFX](#_core_the_record_field_exchange_process)

> [!NOTE]
>  Cette rubrique s’applique aux classes dérivées de `CRecordset` où l’extraction de lignes en bloc n’a pas été implémentée. Si vous utilisez l’extraction de lignes en bloc, l’échange de champs d’enregistrements en bloc (Bulk RFX) est implémenté. Bulk RFX est similaire à RFX. Pour comprendre les différences, consultez [Recordset : extraction globale d’enregistrements (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

##  <a name="rfx-and-the-recordset"></a><a name="_core_rfx_and_the_recordset"></a>RFX et le Recordset

Les membres de données de champ de l’objet Recordset, pris ensemble, constituent un tampon de modification qui contient les colonnes sélectionnées d’un enregistrement. Lorsque le Recordset est ouvert pour la première fois et qu’il est sur le point de lire le premier enregistrement, RFX lie (associe) chaque colonne sélectionnée à l’adresse du membre de données de champ approprié. Lorsque le recordset met à jour un enregistrement, RFX appelle les fonctions API ODBC pour envoyer une instruction SQL **Update** ou **Insert** au pilote. RFX utilise sa connaissance des membres de données de champ pour spécifier les colonnes à écrire.

L’infrastructure sauvegarde le tampon d’édition à certaines étapes afin de pouvoir restaurer son contenu si nécessaire. RFX sauvegarde le tampon d’édition avant d’ajouter un nouvel enregistrement et avant de modifier un enregistrement existant. Il restaure le tampon d’édition dans certains cas, par exemple, après un appel de `Update` suivant `AddNew`. Le tampon d’édition n’est pas restauré si vous abandonnez un tampon d’édition récemment modifié par, par exemple, en le déplaçant vers un autre enregistrement avant d’appeler `Update`.

Outre l’échange de données entre la source de données et les membres de données de champ du Recordset, RFX gère les paramètres de liaison. Lorsque le jeu d’enregistrements est ouvert, tous les membres de données de paramètre sont liés dans l’ordre des espaces réservés «  ? » de l’instruction SQL que `CRecordset::Open` construit. Pour plus d’informations, consultez [Recordset : paramétrage d’un Recordset (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

La substitution de la classe Recordset de `DoFieldExchange` effectue tout le travail, en déplaçant les données dans les deux directions. Comme l’échange de données de boîtes de dialogue (DDX), RFX a besoin d’informations sur les données membres de votre classe. L’Assistant fournit les informations nécessaires en écrivant une implémentation de `DoFieldExchange` spécifique à un Recordset, en fonction des noms de membres de données de champ et des types de données que vous spécifiez avec l’Assistant.

##  <a name="record-field-exchange-process"></a><a name="_core_the_record_field_exchange_process"></a>Processus d’échange de champs d’enregistrement

Cette section décrit la séquence d’événements RFX lorsqu’un objet Recordset est ouvert et que vous ajoutez, mettez à jour et supprimez des enregistrements. La [séquence de table des opérations RFX au cours](#_core_sequence_of_rfx_operations_during_recordset_open) de l’ouverture de l’ensemble d’enregistrements et la [séquence de table des opérations RFX pendant le défilement](#_core_sequence_of_rfx_operations_during_scrolling) dans cette rubrique montrent le processus comme rfx traite une commande `Move` dans le Recordset et comme RFX gère une mise à jour. Au cours de ces processus, [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) est appelé pour effectuer de nombreuses opérations différentes. Le `m_nOperation` membre de données de l’objet [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) détermine l’opération demandée. Il peut s’avérer utile de lire [Recordset : comment les recordsets sélectionnent les enregistrements (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md) et [Recordset : comment les recordsets mettent à jour les enregistrements (ODBC) avant de](../../data/odbc/recordset-how-recordsets-update-records-odbc.md) lire ce document.

###  <a name="rfx-initial-binding-of-columns-and-parameters"></a><a name="_mfc_rfx.3a_.initial_binding_of_columns_and_parameters"></a>RFX : liaison initiale des colonnes et des paramètres

Les activités RFX suivantes se produisent, dans l’ordre indiqué, lorsque vous appelez la fonction membre [Open](../../mfc/reference/crecordset-class.md#open) d’un objet Recordset :

- Si le Recordset possède des membres de données de paramètre, le Framework appelle `DoFieldExchange` pour lier les paramètres aux espaces réservés de paramètre dans la chaîne de l’instruction SQL du Recordset. Une représentation dépendante du type de données de la valeur du paramètre est utilisée pour chaque espace réservé trouvé dans l’instruction **Select** . Cela se produit après la préparation de l’instruction SQL, mais avant son exécution. Pour plus d’informations sur la préparation des instructions, consultez la fonction `::SQLPrepare` dans le *Guide de référence du programmeur*ODBC.

- Le Framework appelle `DoFieldExchange` une deuxième fois pour lier les valeurs des colonnes sélectionnées aux membres de données de champ correspondants dans le Recordset. L’objet Recordset est ainsi établi sous la forme d’une mémoire tampon de modification contenant les colonnes du premier enregistrement.

- Le Recordset exécute l’instruction SQL et la source de données sélectionne le premier enregistrement. Les colonnes de l’enregistrement sont chargées dans les membres de données de champ du Recordset.

Le tableau suivant montre la séquence des opérations RFX lorsque vous ouvrez un jeu d’enregistrements.

### <a name="sequence-of-rfx-operations-during-recordset-open"></a><a name="_core_sequence_of_rfx_operations_during_recordset_open"></a>Séquence des opérations RFX lors de l’ouverture de l’ensemble d’enregistrements

|Votre opération|Opération DoFieldExchange|Base de données/opération SQL|
|--------------------|-------------------------------|-----------------------------|
|1. Ouvrez le Recordset.|||
||2. Créez une instruction SQL.||
|||3. envoyez le SQL.|
||4. liez les membres de données de paramètre.||
||5. liez les membres de données de champ aux colonnes.||
|||6. ODBC effectue le déplacement et remplit les données.|
||7. corrigez les données pour C++.||

Les jeux d’enregistrements utilisent l’exécution préparée d’ODBC pour permettre une rerequête rapide avec la même instruction SQL. Pour plus d’informations sur l’exécution préparée, consultez le *Guide de référence du programmeur* ODBC SDK dans MSDN Library.

###  <a name="rfx-scrolling"></a><a name="_mfc_rfx.3a_.scrolling"></a>RFX : défilement

Lorsque vous faites défiler d’un enregistrement à un autre, le Framework appelle `DoFieldExchange` pour remplacer les valeurs précédemment stockées dans les membres de données de champ avec les valeurs du nouvel enregistrement.

Le tableau suivant montre la séquence des opérations RFX lorsque l’utilisateur passe d’un enregistrement à un autre.

### <a name="sequence-of-rfx-operations-during-scrolling"></a><a name="_core_sequence_of_rfx_operations_during_scrolling"></a>Séquence d’opérations RFX pendant le défilement

|Votre opération|Opération DoFieldExchange|Base de données/opération SQL|
|--------------------|-------------------------------|-----------------------------|
|1. appelez `MoveNext` ou l’une des autres fonctions Move.|||
|||2. ODBC effectue le déplacement et remplit les données.|
||3. corrigez les données pour C++.||

###  <a name="rfx-adding-new-records-and-editing-existing-records"></a><a name="_mfc_rfx.3a_.adding_new_records_and_editing_existing_records"></a>RFX : ajout de nouveaux enregistrements et modification d’enregistrements existants

Si vous ajoutez un nouvel enregistrement, le jeu d’enregistrements fonctionne comme un tampon d’édition pour générer le contenu du nouvel enregistrement. Comme pour l’ajout d’enregistrements, la modification d’enregistrements implique la modification des valeurs des membres de données de champ du Recordset. Du point de vue de RFX, la séquence est la suivante :

1. Votre appel à la fonction membre [AddNew](../../mfc/reference/crecordset-class.md#addnew) ou [Edit](../../mfc/reference/crecordset-class.md#edit) du Recordset fait que RFX stocke la mémoire tampon d’édition actuelle pour pouvoir être restaurée ultérieurement.

1. `AddNew` ou `Edit` prépare les champs dans la mémoire tampon d’édition afin que RFX puisse détecter les membres de données de champ modifiés.

   Comme un nouvel enregistrement n’a pas de valeurs précédentes pour en comparer de nouvelles avec, `AddNew` définit la valeur de chaque membre de données de champ sur une valeur de PSEUDO_NULL. Plus tard, quand vous appelez `Update`, RFX compare la valeur de chaque membre de données à la valeur de PSEUDO_NULL. En cas de différence, le membre de données a été défini. (PSEUDO_NULL n’est pas la même chose qu’une colonne d’enregistrement avec une valeur null vraie, et n’est pas C++ de la même façon que NULL.)

   Contrairement à l’appel de `Update` pour `AddNew`, l’appel de `Update` pour `Edit` compare les valeurs mises à jour aux valeurs précédemment stockées au lieu d’utiliser PSEUDO_NULL. La différence est que `AddNew` n’a pas de valeurs précédemment stockées pour la comparaison.

1. Vous définissez directement les valeurs des membres de données de champ dont vous souhaitez modifier les valeurs ou que vous souhaitez remplir pour un nouvel enregistrement. Cela peut inclure l’appel de `SetFieldNull`.

1. Votre appel à [Update](../../mfc/reference/crecordset-class.md#update) vérifie les membres de données de champ modifiés, comme décrit à l’étape 2 (voir la [séquence de tableau des opérations RFX lors du défilement](#_core_sequence_of_rfx_operations_during_scrolling)). Si aucune modification n’a été apportée, `Update` retourne 0. Si certains membres de données de champ ont changé, `Update` prépare et exécute une instruction SQL **Insert** qui contient des valeurs pour tous les champs mis à jour dans l’enregistrement.

1. Par `AddNew`, `Update` conclut en restaurant les valeurs précédemment stockées de l’enregistrement qui était en cours avant l’appel de `AddNew`. Pour `Edit`, les nouvelles valeurs modifiées restent en place.

Le tableau suivant montre la séquence des opérations RFX lorsque vous ajoutez un nouvel enregistrement ou modifiez un enregistrement existant.

### <a name="sequence-of-rfx-operations-during-addnew-and-edit"></a>Séquence d’opérations RFX pendant AddNew et Edit

|Votre opération|Opération DoFieldExchange|Base de données/opération SQL|
|--------------------|-------------------------------|-----------------------------|
|1. appelez `AddNew` ou `Edit`.|||
||2. Sauvegardez la mémoire tampon d’édition.||
||3. pour `AddNew`, marquez les membres de données de champ comme « Clean » et null.||
|4. assignez des valeurs aux membres de données de champ du Recordset.|||
|5. appelez `Update`.|||
||6. Recherchez les champs modifiés.||
||7. générer une instruction SQL **Insert** pour `AddNew` ou **Update** pour `Edit`.||
|||8. envoyez le SQL.|
||9. pour `AddNew`, restaurez la mémoire tampon d’édition sur son contenu sauvegardé. Pour `Edit`, supprimez la sauvegarde.||

### <a name="rfx-deleting-existing-records"></a>RFX : suppression des enregistrements existants

Lorsque vous supprimez un enregistrement, RFX affecte à tous les champs la valeur NULL pour rappeler que l’enregistrement est supprimé et que vous devez le déplacer. Vous n’avez pas besoin d’autres informations de séquence RFX.

## <a name="see-also"></a>Voir aussi

[Record Field Exchange (RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[Consommation ODBC MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[Macros, fonctions globales et variables globales](../../mfc/reference/mfc-macros-and-globals.md)<br/>
[CFieldExchange, classe](../../mfc/reference/cfieldexchange-class.md)<br/>
[CRecordset ::D oFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)
