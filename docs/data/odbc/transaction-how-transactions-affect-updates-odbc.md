---
title: 'Transaction : Répercussions des Transactions sur les mises à jour (ODBC) | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- transactions, updating recordsets
- ODBC recordsets, transactions
- transactions, rolling back
- CommitTrans method
- Rollback method, ODBC transactions
ms.assetid: 9e00bbf4-e9fb-4332-87fc-ec8ac61b3f68
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 549f8495ca3a088ec4314cd26318d19f9a5a3176
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33098002"
---
# <a name="transaction-how-transactions-affect-updates-odbc"></a>Transaction : répercussions des transactions sur les mises à jour (ODBC)
Met à jour vers la [source de données](../../data/odbc/data-source-odbc.md) sont managées pendant les transactions grâce à l’utilisation d’une mémoire tampon de modification (la même méthode utilisée en dehors des transactions). Données membres de champ d’un recordset jouent collectivement le rôle en tant que tampon d’édition qui contient l’enregistrement en cours, ce qui le jeu d’enregistrements sauvegardé temporairement pendant une `AddNew` ou **modifier**. Pendant un **supprimer** opération, l’enregistrement actif n’est pas sauvegardée dans une transaction. Pour plus d’informations sur la mémoire tampon de modification et comment les mises à jour de stocker l’enregistrement actif, consultez [Recordset : modification des enregistrements de jeux d’enregistrements (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).  
  
> [!NOTE]
>  Si vous avez implémenté l’extraction de lignes en bloc, vous ne pouvez pas appeler `AddNew`, **modifier**, ou **supprimer**. Vous devez à la place écrire vos propres fonctions pour effectuer des mises à jour de la source de données. Pour plus d’informations sur l’extraction de lignes en bloc, consultez [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Pendant les transactions, `AddNew`, **modifier**, et **supprimer** opérations peuvent être validées ou restaurées. Les effets de **CommitTrans** et **restauration** peut entraîner l’enregistrement en cours de restauration pour le tampon d’édition. Pour vous assurer que l’enregistrement actif est correctement restaurée, il est important de comprendre comment les **CommitTrans** et **restauration** les fonctions membres de `CDatabase` fonctionnent avec les fonctions de mise à jour de `CRecordset`.  
  
##  <a name="_core_how_committrans_affects_updates"></a> Impact de CommitTrans sur les mises à jour  
 Le tableau suivant explique les effets de **CommitTrans** sur des transactions.  
  
### <a name="how-committrans-affects-updates"></a>Impact de CommitTrans sur les mises à jour  
  
|Opération|État de la source de données|  
|---------------|---------------------------|  
|`AddNew` et **mise à jour**, puis **CommitTrans**|Nouvel enregistrement sont ajoutés à la source de données.|  
|`AddNew` (sans **mise à jour**), puis **CommitTrans**|Nouvel enregistrement est perdue. Enregistrement ne pas ajouté à la source de données.|  
|**Modifier** et **mise à jour**, puis **CommitTrans**|Modifications validées dans la source de données.|  
|**Modifier** (sans **mise à jour**), puis **CommitTrans**|Modifications de l’enregistrement sont perdues. Enregistrement reste identique dans la source de données.|  
|**Supprimer** puis **CommitTrans**|Enregistrements supprimés de la source de données.|  
  
##  <a name="_core_how_rollback_affects_updates"></a> Impact de la restauration des Transactions  
 Le tableau suivant explique les effets de **restauration** sur des transactions.  
  
### <a name="how-rollback-affects-transactions"></a>Impact de la restauration des Transactions  
  
|Opération|État de l’enregistrement actif|Vous devez également|État de la source de données|  
|---------------|------------------------------|-------------------|---------------------------|  
|`AddNew` et **mise à jour**, puis **Rollback**|Contenu de l’enregistrement actif est stocké temporairement pour libérer de l’espace pour le nouvel enregistrement. Nouvel enregistrement est entré dans la mémoire tampon de modification. Après avoir **mise à jour** est appelée, actuel enregistrement est rétabli dans la mémoire tampon de modification.||Ajout à la source de données effectuée par **mise à jour** est inversée.|  
|`AddNew` (sans **mise à jour**), puis **Rollback**|Contenu de l’enregistrement actif est stocké temporairement pour libérer de l’espace pour le nouvel enregistrement. Modifier mémoire tampon contient le nouvel enregistrement.|Appelez `AddNew` pour rétablir la mémoire tampon de modification pour un nouvel enregistrement vide. Ou appelez **déplacer**(0) pour rétablir les anciennes valeurs dans la mémoire tampon de modification.|Étant donné que **mise à jour** n’est pas appelée, aucune modification apportée à la source de données.|  
|**Modifier** et **mise à jour**, puis **Rollback**|Une version non modifiée de l’enregistrement actif est stockée temporairement. Des modifications sont apportées au contenu de la mémoire tampon de modification. Après avoir **mise à jour** est appelée, la version non modifiée version de l’enregistrement est toujours temporairement stockée.|*Feuille de réponse dynamique*: l’enregistrement en cours, puis y revenir pour rétablir la version non modifiée de l’enregistrement pour le tampon d’édition.<br /><br /> *Instantané*: appelez **Requery** pour actualiser le jeu d’enregistrements à partir de la source de données.|Modifications apportées à la source de données effectuée par **mise à jour** sont inversées.|  
|**Modifier** (sans **mise à jour**), puis **Rollback**|Une version non modifiée de l’enregistrement actif est stockée temporairement. Des modifications sont apportées au contenu de la mémoire tampon de modification.|Appelez **modifier** afin de rétablir la version non modifiée de l’enregistrement pour le tampon d’édition.|Étant donné que **mise à jour** n’est pas appelée, aucune modification apportée à la source de données.|  
|**Supprimer** puis **Rollback**|Contenu de l’enregistrement actif est supprimé.|Appelez **Requery** pour restaurer le contenu de l’enregistrement en cours à partir de la source de données.|Suppression de données à partir de la source de données est inversée.|  
  
## <a name="see-also"></a>Voir aussi  
 [Transactions (ODBC)](../../data/odbc/transaction-odbc.md)   
 [Transactions (ODBC)](../../data/odbc/transaction-odbc.md)   
 [Transaction : Exécution d’une Transaction dans un Recordset (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)   
 [CDatabase (classe)](../../mfc/reference/cdatabase-class.md)   
 [CRecordset, classe](../../mfc/reference/crecordset-class.md)