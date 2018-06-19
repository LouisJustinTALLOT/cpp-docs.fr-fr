---
title: 'Record Field Exchange : Fonctionnement de RFX | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- record editing [C++], using RFX
- RFX (ODBC) [C++], updating data in recordsets
- scrolling [C++]
- ODBC [C++], RFX
- data binding [C++], DFX
- scrolling [C++], RFX
- RFX (ODBC) [C++], binding fields and parameters
ms.assetid: e647cacd-62b0-4b80-9e20-b392deca5a88
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 48cece77101a14efb827e48b53be2f5852df83ee
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33094297"
---
# <a name="record-field-exchange-how-rfx-works"></a>Record Field Exchange : fonctionnement de RFX
Cette rubrique explique le processus RFX. Il s’agit d’une avancée couverture de la rubrique :  
  
-   [RFX et le jeu d’enregistrements](#_core_rfx_and_the_recordset)  
  
-   [Le processus RFX](#_core_the_record_field_exchange_process)  
  
> [!NOTE]
>  Cette rubrique s’applique aux classes dérivées de `CRecordset` dans les lignes en bloc l’extraction n’a pas été implémentée. Si vous utilisez l’extraction de lignes en bloc, RFX en bloc (RFX en bloc) est implémentée. RFX en bloc est similaire à RFX. Pour comprendre les différences, consultez [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="_core_rfx_and_the_recordset"></a> RFX et le jeu d’enregistrements  
 Membres de données de champ de l’objet recordset, ensemble, constituent un mémoire tampon de modification qui conserve les colonnes sélectionnées d’un enregistrement. Lorsque le jeu d’enregistrements est tout d’abord ouvert et est à lire le premier enregistrement, RFX lie (associe chaque) colonne sélectionnée à l’adresse du membre de données de champ approprié. Lorsque le jeu d’enregistrements met à jour un enregistrement, RFX appelle les fonctions API ODBC pour envoyer une SQL **mise à jour** ou **insérer** instruction au pilote. RFX utilise sa connaissance des données membres de champ pour spécifier les colonnes à écrire.  
  
 L’infrastructure de sauvegarde le tampon d’édition à certaines étapes, il peut restaurer son contenu si nécessaire. RFX sauvegarde le tampon d’édition avant d’ajouter un nouvel enregistrement et avant de modifier un enregistrement existant. Il restaure le tampon d’édition dans certains cas, par exemple, après un **mise à jour** appel suivant `AddNew`. Le tampon d’édition n’est pas restauré si vous quittez un tampon d’édition qui vient d’être modifié par, par exemple, un autre enregistrement avant d’appeler **mise à jour**.  
  
 En dehors de l’échange de données entre la source de données et les membres de données de champ du jeu d’enregistrements, RFX gère les paramètres de liaison. Lorsque le jeu d’enregistrements est ouvert, tous les membres de données de paramètre sont liés dans l’ordre de la « ? » des espaces réservés dans l’instruction SQL qui `CRecordset::Open` construit. Pour plus d’informations, consultez [Recordset : paramétrage d’un Recordset (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).  
  
 La substitution de la classe de recordset `DoFieldExchange` effectue le travail, déplacement de données dans les deux sens. Comme l’échange de données de boîtes de dialogue (DDX), RFX a besoin d’informations sur les membres de données de votre classe. L’Assistant fournit les informations nécessaires en écrivant une implémentation spécifique au jeu d’enregistrements de `DoFieldExchange` pour vous, selon les données du champ membre les noms et types de données vous spécifiez avec l’Assistant.  
  
##  <a name="_core_the_record_field_exchange_process"></a> Processus d’échange de champs enregistrement  
 Cette section décrit la séquence des événements RFX lorsqu’un objet de jeu d’enregistrements est ouvert et que vous ajoutez, mettez à jour et supprimer des enregistrements. La table [séquence d’opérations RFX lors de l’ouverture d’un Recordset](#_core_sequence_of_rfx_operations_during_recordset_open) et la table [ordre des opérations RFX lors du défilement](#_core_sequence_of_rfx_operations_during_scrolling) dans cette rubrique montrent le processus en tant que processus RFX un **déplacer**dans le jeu d’enregistrements et gère une mise à jour. Lors de ces processus, [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) est appelée pour effectuer diverses opérations. Le **m_nOperation** membre de données de la [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) objet détermine l’opération demandée. Il peut s’avérer utile de lire [Recordset : sélection d’enregistrements (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md) et [Recordset : modification des enregistrements de jeux d’enregistrements (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md) avant de lire ce document.  
  
###  <a name="_mfc_rfx.3a_.initial_binding_of_columns_and_parameters"></a> RFX : La liaison initiale des colonnes et paramètres  
 Les activités RFX suivantes se produisent dans l’ordre indiqué, lorsque vous appelez l’objet recordset [ouvrir](../../mfc/reference/crecordset-class.md#open) fonction membre :  
  
-   Si le jeu d’enregistrements possède des membres de données de paramètre, l’infrastructure appelle `DoFieldExchange` pour lier les paramètres aux espaces réservés de paramètre dans la chaîne de l’instruction SQL du jeu d’enregistrements. Une représentation sous forme de type dépendant de la valeur du paramètre est utilisé pour chaque espace réservé des données trouvées dans le **sélectionnez** instruction. Cela se produit une fois l’instruction SQL est préparée mais avant son exécution. Pour plus d’informations sur la préparation de l’instruction, consultez la **:: SQLPrepare** fonction dans ODBC *de référence du programmeur*.  
  
-   Le framework appelle `DoFieldExchange` une seconde fois pour lier les valeurs des colonnes sélectionnées aux membres de données de champ correspondant dans le jeu d’enregistrements. Ceci établit l’objet recordset en tant que tampon d’édition contenant les colonnes du premier enregistrement.  
  
-   Le jeu d’enregistrements exécute l’instruction SQL et la source de données sélectionne le premier enregistrement. Les colonnes de l’enregistrement sont chargées dans les membres de données de champ du jeu d’enregistrements.  
  
 Le tableau suivant indique l’ordre des opérations RFX lorsque vous ouvrez un jeu d’enregistrements.  
  
### <a name="_core_sequence_of_rfx_operations_during_recordset_open"></a> Ordre des opérations RFX lors de l’ouverture du jeu d’enregistrements  
  
|L’opération|Opération DoFieldExchange|Opération de base de données/SQL|  
|--------------------|-------------------------------|-----------------------------|  
|1. Ouvrez le jeu d’enregistrements.|||  
||2. Générer une instruction SQL.||  
|||3. Envoyer l’instruction SQL.|  
||4. Lier les membres de données de paramètre.||  
||5. Lier des données membres de champ aux colonnes.||  
|||6. ODBC effectue le transfert et insère les données.|  
||7. Corriger les données pour C++.||  
  
 Jeux d’enregistrements utilisent l’exécution préparée d’ODBC pour permettre lancement rapide d’une nouvelle requête avec la même instruction SQL. Pour plus d’informations sur l’exécution préparée, consultez le SDK ODBC *de référence du programmeur* dans MSDN Library.  
  
###  <a name="_mfc_rfx.3a_.scrolling"></a> RFX : le défilement  
 Lorsque vous passez d’un enregistrement à un autre, l’infrastructure appelle `DoFieldExchange` pour remplacer les valeurs précédemment stockées dans les membres de données de champ avec des valeurs pour le nouvel enregistrement.  
  
 Le tableau suivant indique l’ordre des opérations RFX lorsque l’utilisateur déplace d’un enregistrement à l’autre.  
  
### <a name="_core_sequence_of_rfx_operations_during_scrolling"></a> Ordre des opérations RFX lors du défilement  
  
|L’opération|Opération DoFieldExchange|Opération de base de données/SQL|  
|--------------------|-------------------------------|-----------------------------|  
|1. Appelez `MoveNext` ou l’une des autres fonctions de déplacement.|||  
|||2. ODBC effectue le transfert et insère les données.|  
||3. Corriger les données pour C++.||  
  
###  <a name="_mfc_rfx.3a_.adding_new_records_and_editing_existing_records"></a> RFX : Ajout de nouveaux enregistrements et modification des enregistrements existants  
 Si vous ajoutez un nouvel enregistrement, le jeu d’enregistrements fonctionne comme un mémoire tampon de modification pour constituer le contenu du nouvel enregistrement. Comme avec l’ajout d’enregistrements, modifier les enregistrements implique la modification des valeurs des membres de données de champ du jeu d’enregistrements. À partir de la perspective RFX, la séquence est comme suit :  
  
1.  Votre appel à l’ensemble d’enregistrements [AddNew](../../mfc/reference/crecordset-class.md#addnew) ou [modifier](../../mfc/reference/crecordset-class.md#edit) provoque la fonction membre RFX stocker le tampon d’édition actuel afin qu’il puisse être restaurée plus tard.  
  
2.  `AddNew` ou **modifier** prépare les champs dans le tampon d’édition afin que RFX puisse identifier les membres de données de champ modifié.  
  
     Car un nouvel enregistrement n’a pas de valeurs à comparer les nouvelles, `AddNew` définit la valeur de chaque membre de données de champ à un **PSEUDO_NULL** valeur. Ensuite, lorsque vous appelez **mise à jour**, RFX compare la valeur de chaque membre de données avec le **PSEUDO_NULL** valeur. S’il existe une différence, le membre de données a été défini. (**PSEUDO_NULL** n’est pas identique à une colonne d’enregistrement ayant la valeur Null et n’est pas une de ces identique C++ **NULL**.)  
  
     Contrairement à la **mise à jour** appeler pour `AddNew`, le **mise à jour** appeler pour **modifier** compare les valeurs mises à jour avec les valeurs précédemment stockées plutôt qu’à l’aide de **PSEUDO_NULL**. La différence est que `AddNew` n’a aucuns valeurs précédemment stockées pour la comparaison.  
  
3.  Vous définissez directement les valeurs des membres de données de champ dont vous souhaitez modifier les valeurs ou que vous renseigner pour un nouvel enregistrement. Cela peut inclure l’appel `SetFieldNull`.  
  
4.  Votre appel à [mise à jour](../../mfc/reference/crecordset-class.md#update) vérifie pour les membres de données de champ modifié, comme décrit à l’étape 2 (consultez le tableau [ordre des opérations RFX lors du défilement](#_core_sequence_of_rfx_operations_during_scrolling)). Si aucune n’a changé, **mise à jour** retourne 0. Si certains membres ont été modifiés, **mise à jour** prépare et exécute une SQL **insérer** instruction qui contient des valeurs pour tous les champs mis à jour dans l’enregistrement.  
  
5.  Pour `AddNew`, **mise à jour** se termine en restaurant les valeurs précédemment stockées de l’enregistrement qui était active avant la `AddNew` appeler. Pour **modifier**, les nouvelles valeurs modifiées demeurent en place.  
  
 Le tableau suivant indique l’ordre des opérations RFX lorsque vous ajoutez un nouvel enregistrement ou modifiez un enregistrement existant.  
  
### <a name="sequence-of-rfx-operations-during-addnew-and-edit"></a>Ordre des opérations RFX pendant AddNew et Edit  
  
|L’opération|Opération DoFieldExchange|Opération de base de données/SQL|  
|--------------------|-------------------------------|-----------------------------|  
|1. Appelez `AddNew` ou **modifier**.|||  
||2. Sauvegarder le tampon d’édition.||  
||3. Pour `AddNew`, marquer les membres de données de champ comme « clean » et Null.||  
|4. Assigner des valeurs aux membres de données de champ de recordset.|||  
|5. Appelez **mise à jour**.|||  
||6. Vérifier les champs modifiés.||  
||7. Génération SQL **insérer** instruction pour `AddNew` ou **mise à jour** instruction pour **modifier**.||  
|||8. Envoyer l’instruction SQL.|  
||9. Pour `AddNew`, restaurer le tampon d’édition avec son contenu sauvegardé. Pour **modifier**, supprimer la sauvegarde.||  
  
### <a name="rfx-deleting-existing-records"></a>RFX : Suppression d’enregistrements existants  
 Lorsque vous supprimez un enregistrement, RFX définit tous les champs **NULL** rappeler que l’enregistrement est supprimé et vous devez l’enlever. Vous n’avez pas besoin de toutes les autres informations de séquence RFX.  
  
## <a name="see-also"></a>Voir aussi  
 [Record Field Exchange (RFX)](../../data/odbc/record-field-exchange-rfx.md)   
 [MFC ODBC, consommation](../../mfc/reference/adding-an-mfc-odbc-consumer.md)   
 [Macros, fonctions globales et Variables globales](../../mfc/reference/mfc-macros-and-globals.md)  
 [Classe de CFieldExchange](../../mfc/reference/cfieldexchange-class.md)   
 [CRecordset::DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)