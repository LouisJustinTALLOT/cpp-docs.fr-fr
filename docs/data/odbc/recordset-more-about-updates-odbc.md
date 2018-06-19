---
title: 'Recordset : en savoir plus sur les mises à jour (ODBC) | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- records, updating
- transactions, updating recordsets
- ODBC recordsets, updating
- multiuser environments, updates to recordsets
- scrolling, updates to recordsets
- updating recordsets
- recordsets, updating
ms.assetid: 0353a742-d226-4fe2-8881-a7daeffe86cd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ea46e0462f3763e04ec18ad9bff2b0d3ded1deee
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33098665"
---
# <a name="recordset-more-about-updates-odbc"></a>Recordset : informations complémentaires sur les mises à jour (ODBC)
Cette rubrique s’applique aux classes ODBC MFC.  
  
 Cette rubrique explique :  
  
-   [Répercussions des autres opérations, telles que les transactions, sur les mises à jour](#_core_how_transactions_affect_updates).  
  
-   [Les mises à jour et celles des autres utilisateurs](#_core_your_updates_and_the_updates_of_other_users).  
  
-   [Plus d’informations sur les fonctions membres Update et Delete](#_core_more_about_update_and_delete).  
  
> [!NOTE]
>  Cette rubrique s’applique aux objets dérivés de `CRecordset` dans les lignes en bloc l’extraction n’a pas été implémentée. Si vous avez implémenté l’extraction de lignes en bloc, certaines informations ne s’applique pas. Par exemple, vous ne pouvez pas appeler la `AddNew`, **modifier**, **supprimer**, et **mise à jour** les fonctions membres ; Toutefois, vous pouvez effectuer des transactions. Pour plus d’informations sur l’extraction de lignes en bloc, consultez [Recordset : extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="_core_how_other_operations_affect_updates"></a> Répercussions des autres opérations sur les mises à jour  
 Les mises à jour sont affectées par les transactions au moment de la mise à jour, en fermant le jeu d’enregistrements avant d’effectuer une transaction et en faisant défiler avant la fin d’une transaction.  
  
###  <a name="_core_how_transactions_affect_updates"></a> Répercussions des Transactions sur les mises à jour  
 Au-delà de comprendre comment `AddNew`, **modifier**, et **supprimer** travail, il est important de comprendre comment les **BeginTrans**, **CommitTrans**, et **restauration** les fonctions membres de [CDatabase](../../mfc/reference/cdatabase-class.md) fonctionnent avec les fonctions de mise à jour de [CRecordset](../../mfc/reference/crecordset-class.md).  
  
 Par défaut, les appels à `AddNew` et **modifier** affectent la source de données immédiatement lorsque vous appelez **mise à jour**. **Supprimer** appels prennent effet immédiatement. Mais vous pouvez établir une transaction et exécuter un traitement de ces appels. Les mises à jour ne sont pas permanentes jusqu'à ce que vous les validez. Si vous changez d’avis, vous pouvez restaurer la transaction au lieu de sa validation.  
  
 Pour plus d’informations sur les transactions, consultez [Transaction (ODBC)](../../data/odbc/transaction-odbc.md).  
  
###  <a name="_core_how_closing_the_recordset_affects_updates"></a> Impact de la fermeture de l’ensemble d’enregistrements sur les mises à jour  
 Si vous fermez un jeu d’enregistrements, ou qui lui est associée `CDatabase` objet, avec une transaction en cours (vous n’avez pas appelé [CDatabase::CommitTrans](../../mfc/reference/cdatabase-class.md#committrans) ou [CDatabase::Rollback](../../mfc/reference/cdatabase-class.md#rollback)), la transaction est restaurée. sauvegarder automatiquement (à moins que votre base de données principale est le moteur de base de données Microsoft Jet).  
  
> [!CAUTION]
>  Si vous utilisez le moteur de base de données Microsoft Jet, la fermeture d’un jeu d’enregistrements à l’intérieur d’une transaction explicite n’entraîne pas la libération des lignes qui ont été modifiées ou des verrous qui ont été placés jusqu'à ce que la transaction explicite est validée ou restaurée. Il est recommandé que vous ouvrez et fermez les jeux d’enregistrements à l’intérieur ou en dehors d’une transaction Jet explicite.  
  
###  <a name="_core_how_scrolling_affects_updates"></a> Influence du défilement mises à jour  
 Lorsque vous [Recordset : défilement (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) dans un jeu d’enregistrements, le tampon d’édition est rempli avec chaque nouvel enregistrement courant (l’enregistrement précédent n’est pas stocké d’abord). Défilement ignore les enregistrements supprimés précédemment. Si vous faites défiler après une `AddNew` ou **modifier** appel sans appeler **mise à jour**, **CommitTrans**, ou **restauration** première, toutes les modifications sont perdues (aucun avertissement vous) lorsqu’un nouvel enregistrement est placé dans le tampon d’édition. Le tampon d’édition est rempli avec l’enregistrement de défilement à l’enregistrement stocké est libéré et aucune modification se produit sur la source de données. Cela s’applique aux deux `AddNew` et **modifier**.  
  
##  <a name="_core_your_updates_and_the_updates_of_other_users"></a> Les mises à jour et les mises à jour d’autres utilisateurs  
 Lorsque vous utilisez un jeu d’enregistrements à mettre à jour des données, vos mises à jour affectent les autres utilisateurs. De même, les mises à jour des autres utilisateurs pendant la durée de vie de votre recordset vous affectent.  
  
 Dans un environnement multi-utilisateur, les autres utilisateurs peuvent ouvrir des jeux d’enregistrements qui contiennent certains enregistrements identiques à ceux que vous avez sélectionné dans le jeu d’enregistrements. Modifications apportées à un enregistrement avant que vous récupériez sont répercutées dans le jeu d’enregistrements. Étant donné que les feuilles de réponse dynamiques récupèrent un enregistrement chaque fois que vous accédez par défilement, répercutent les modifications chaque fois que vous accédez à un enregistrement. Instantanés de récupérer un enregistrement de la première fois que vous accédez par défilement, instantanés reflètent uniquement les modifications qui se produisent avant que vous accédiez à l’enregistrement.  
  
 Les enregistrements ajoutés par d’autres utilisateurs après avoir ouvert le jeu d’enregistrements ne s’affichent pas dans le jeu d’enregistrements, sauf si vous actualisez. Si le recordset est une feuille de réponse dynamique, modifications d’enregistrements existants par d’autres utilisateurs s’affichent dans votre feuille de réponse dynamique lorsque vous faites défiler à l’enregistrement concerné. Si votre jeu d’enregistrements est un instantané, les modifications n’apparaissent pas jusqu'à ce que vous actualisez l’instantané. Si vous souhaitez voir les enregistrements ajoutés ou supprimés par d’autres utilisateurs dans l’instantané, ou les enregistrements ajoutés par d’autres utilisateurs dans votre feuille de réponse dynamique, appelez [CRecordset::Requery](../../mfc/reference/crecordset-class.md#requery) pour reconstruire le recordset. (Notez que les suppressions des autres utilisateurs apparaissent dans votre feuille de réponse dynamique). Vous pouvez aussi appeler **Requery** pour afficher les enregistrements vous ajoutez, mais ne pas pour voir vos propres suppressions.  
  
> [!TIP]
>  Pour forcer la mise en cache de l’intégralité d’un instantané, appelez `MoveLast` immédiatement après l’ouverture de l’instantané. Appelez ensuite **MoveFirst** pour commencer à travailler avec les enregistrements. `MoveLast` est équivalent au défilement sur tous les enregistrements, mais ceux-ci sont tous en même temps. Toutefois, notez que cela peut réduire les performances et ne peut pas être nécessaire pour certains pilotes.  
  
 Les effets de vos mises à jour sur les autres utilisateurs sont semblables aux effets sur vous.  
  
##  <a name="_core_more_about_update_and_delete"></a> Plus d’informations sur la mise à jour et de suppression  
 Cette section fournit des informations supplémentaires pour vous aider à utiliser avec **mise à jour** et **supprimer**.  
  
### <a name="update-success-and-failure"></a>Réussite de la mise à jour et d’échec  
 Si **mise à jour** réussit, le `AddNew` ou **modifier** fin en mode. Pour commencer un `AddNew` ou **modifier** à nouveau le mode, appelez `AddNew` ou **modifier**.  
  
 Si **mise à jour** échoue (retourne **FALSE** ou lève une exception), vous gardez le `AddNew` ou **modifier** mode, selon que la fonction a été appelée en dernier. Vous pouvez ensuite effectuer une des opérations suivantes :  
  
-   Modifier un membre de données de champ et essayez du **mise à jour** à nouveau.  
  
-   Appelez `AddNew` pour réinitialiser les données membres de champ null, définissez les valeurs des membres de données du champ, puis appelez **mise à jour** à nouveau.  
  
-   Appelez **modifier** pour recharger les valeurs qui se trouvaient dans le jeu d’enregistrements avant le premier appel à `AddNew` ou **modifier**, définissez les valeurs des membres de données du champ, puis appelez **mettre à jour**à nouveau. Après la réussite **mise à jour** appeler (sauf après un `AddNew` appeler), les membres de données de champ conservent leurs nouvelles valeurs.  
  
-   Appelez **déplacer** (y compris **déplacer** avec un paramètre de **AFX_MOVE_REFRESH**, ou 0), qui vide les modifications et met fin `AddNew` ou **modifier** mode en vigueur.  
  
### <a name="update-and-delete"></a>Mise à jour et suppression  
 Cette section s’applique aux deux **mise à jour** et **supprimer**.  
  
 Sur un **mise à jour** ou **supprimer** opération, un seul enregistrement et doit être mis à jour. Cet enregistrement est l’enregistrement actif, ce qui correspond aux valeurs de données dans les champs de l’objet recordset. Si pour une raison quelconque aucun enregistrement n’est affectées ou de plusieurs enregistrements est affectée, une exception est levée contenant l’une des opérations suivantes **et RETCODE contient** valeurs :  
  
-   **AFX_SQL_ERROR_NO_ROWS_AFFECTED**  
  
-   **AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED APPARAÎT**  
  
 Lorsque ces exceptions sont levées, vous gardez le `AddNew` ou **modifier** état vous étiez lorsque vous avez appelé **mise à jour** ou **supprimer**. Voici les scénarios les plus courants dans lesquels vous visualiserez ces exceptions. Vous êtes probablement voir :  
  
-   **AFX_SQL_ERROR_NO_ROWS_AFFECTED** lorsque vous utilisez le mode de verrouillage optimisé et un autre utilisateur a modifié l’enregistrement d’une manière qui empêche l’infrastructure d’identifier l’enregistrement à mettre à jour ou supprimer.  
  
-   **AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED apparaît** lorsque la table que vous mettez à jour ne possède aucune clé primaire ou index unique et que vous n’avez pas suffisamment de colonnes dans le jeu d’enregistrements pour identifier de façon unique une ligne de table.  
  
## <a name="see-also"></a>Voir aussi  
 [Jeu d’enregistrements (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Recordset : Comment Recordsets sélection d’enregistrements (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)   
 [Record Field Exchange (RFX)](../../data/odbc/record-field-exchange-rfx.md)   
 [SQL](../../data/odbc/sql.md)   
 [Exceptions : exceptions de base de données](../../mfc/exceptions-database-exceptions.md)