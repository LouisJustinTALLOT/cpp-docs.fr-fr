---
title: 'Recordset : Modification des jeux d’enregistrements enregistrements (ODBC) | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- records, updating
- ODBC recordsets, updating
- recordsets, editing records
- updating recordsets
- recordsets, updating
ms.assetid: 5ceecc06-7a86-43b1-93db-a54fb1e717c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b16faf4c5ef0208c946cff123ecbe62b513e65ca
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33092455"
---
# <a name="recordset-how-recordsets-update-records-odbc"></a>Recordset : modification des enregistrements par les recordsets (ODBC)
Cette rubrique s’applique aux classes ODBC MFC.  
  
 En dehors de leur capacité à sélectionner des enregistrements à partir d’une source de données, les jeux d’enregistrements permettre (facultatif) mettre à jour ou supprimer les enregistrements sélectionnés ou ajouter de nouveaux enregistrements. Trois facteurs déterminent la mise à jour un jeu d’enregistrements : indique si la source de données connectée est modifiable, les options que vous spécifiez lorsque vous créez un objet recordset et l’instruction SQL qui est créé.  
  
> [!NOTE]
>  Le code SQL sur lequel votre `CRecordset` objet repose peut affecter la mise à jour du jeu d’enregistrements. Par exemple, si votre SQL contient une jointure ou une **GROUP BY** clause, MFC définit la mise à jour **FALSE**.  
  
> [!NOTE]
>  Cette rubrique s’applique aux objets dérivés de `CRecordset` dans les lignes en bloc l’extraction n’a pas été implémentée. Si vous utilisez l’extraction de lignes en bloc, consultez [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Cette rubrique explique :  
  
-   [Votre rôle dans la mise à jour du jeu d’enregistrements](#_core_your_role_in_recordset_updating) et ce que le framework fait pour vous.  
  
-   [Le jeu d’enregistrements en tant que tampon d’édition](#_core_the_edit_buffer) et [les différences entre les feuilles de réponse dynamiques et les instantanés](#_core_dynasets_and_snapshots).  
  
 [Recordset : Comment AddNew, Edit et Delete (ODBC)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md) décrit les actions de ces fonctions à partir du point de vue de l’objet recordset.  
  
 [Recordset : Informations complémentaires sur mises à jour (ODBC)](../../data/odbc/recordset-more-about-updates-odbc.md) conclut la mise à jour des recordsets en expliquant comment les transactions affectent les mises à jour, comment la fermeture d’un recordset influe sur les mises à jour en cours et comment vos mises à jour interagissent avec les mises à jour des autres utilisateurs.  
  
##  <a name="_core_your_role_in_recordset_updating"></a> Votre rôle dans la mise à jour du jeu d’enregistrements  
 Le tableau suivant indique le rôle à l’aide de jeux d’enregistrements à ajouter, modifier ou supprimer des enregistrements, ainsi que ce que le framework fait pour vous.  
  
### <a name="recordset-updating-you-and-the-framework"></a>Mise à jour du jeu d’enregistrements : L’infrastructure et vous  
  
|Vous|L'infrastructure|  
|---------|-------------------|  
|Déterminez si la source de données est mise à jour (ou modifiable).|Blocs [CDatabase](../../mfc/reference/cdatabase-class.md) fonctions membres pour tester la mise à jour ou extensible de la source de données.|  
|Ouvrez un jeu d’enregistrements actualisable (de n’importe quel type).||  
|Déterminer si le jeu d’enregistrements est modifiable en appelant `CRecordset` mettre à jour des fonctions telles que `CanUpdate` ou `CanAppend`.||  
|Appeler des fonctions membres pour ajouter, modifier et supprimer des enregistrements recordset.|Gère les mécanismes d’échange de données entre votre objet recordset et la source de données.|  
|Si vous le souhaitez, utilisez des transactions pour contrôler le processus de mise à jour.|Blocs `CDatabase` fonctions membres pour prendre en charge des transactions.|  
  
 Pour plus d’informations sur les transactions, consultez [Transaction (ODBC)](../../data/odbc/transaction-odbc.md).  
  
##  <a name="_core_the_edit_buffer"></a> Le tampon d’édition  
 Pris collectivement, les membres de données de champ d’un recordset font Office de tampon d’édition qui contient un enregistrement, l’enregistrement actif. Les opérations de mise à jour permet de cette mémoire tampon ne fonctionne pas sur l’enregistrement actif.  
  
-   Lorsque vous ajoutez un enregistrement, le tampon d’édition est utilisé pour générer un nouvel enregistrement. Lorsque vous avez terminé l’ajout de l’enregistrement, l’enregistrement qui était précédemment redevient actif.  
  
-   Lorsque vous mettez à jour (modifier) un enregistrement, la modification de tampon est utilisé pour définir les membres de données de champ de l’objet recordset à nouvelles valeurs. Lorsque vous avez terminé la mise à jour, l’enregistrement mis à jour est toujours en cours.  
  
 Lorsque vous appelez [AddNew](../../mfc/reference/crecordset-class.md#addnew) ou [modifier](../../mfc/reference/crecordset-class.md#edit), l’enregistrement actif est stockée afin de pouvoir être restauré en fonction des besoins. Lorsque vous appelez [supprimer](../../mfc/reference/crecordset-class.md#delete), l’enregistrement courant n’est pas stocké, mais est marqué comme supprimé et vous devez accéder à un autre enregistrement.  
  
> [!NOTE]
>  Le tampon d’édition ne joue aucun rôle dans la suppression de l’enregistrement. Lorsque vous supprimez l’enregistrement en cours, l’enregistrement est marqué comme supprimé, et le jeu d’enregistrements est « pas d’un enregistrement de » jusqu'à ce que vous faites défiler vers un autre enregistrement.  
  
##  <a name="_core_dynasets_and_snapshots"></a> Les instantanés et les feuilles de réponse dynamiques  
 [Feuilles de réponse dynamiques](../../data/odbc/dynaset.md) actualiser le contenu d’un enregistrement que vous accédez à l’enregistrement. [Instantanés](../../data/odbc/snapshot.md) sont des représentations statiques des enregistrements, pour le contenu d’un enregistrement n’est pas actualisés, sauf si vous appelez [Requery](../../mfc/reference/crecordset-class.md#requery). Pour utiliser toutes les fonctionnalités des feuilles de réponse dynamiques, vous devez travailler avec un pilote ODBC conforme au niveau correct de prise en charge de l’API ODBC. Pour plus d’informations, consultez [ODBC](../../data/odbc/odbc-basics.md) et [Dynaset](../../data/odbc/dynaset.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Jeu d’enregistrements (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Recordset : fonctionnement d’AddNew, Edit et Delete (ODBC)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md)