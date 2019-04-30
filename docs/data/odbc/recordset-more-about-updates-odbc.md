---
title: 'Recordset : Plus d’informations sur les mises à jour (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- records, updating
- transactions, updating recordsets
- ODBC recordsets, updating
- multiuser environments, updates to recordsets
- scrolling, updates to recordsets
- updating recordsets
- recordsets, updating
ms.assetid: 0353a742-d226-4fe2-8881-a7daeffe86cd
ms.openlocfilehash: c29ff110fc507c4e449b2f3d082d98c159a35107
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397768"
---
# <a name="recordset-more-about-updates-odbc"></a>Recordset : Plus d’informations sur les mises à jour (ODBC)

Cette rubrique s’applique aux classes ODBC MFC.

Cette rubrique explique :

- [Répercussions des autres opérations, telles que les transactions, sur les mises à jour](#_core_how_transactions_affect_updates).

- [Vos mises à jour et celles des autres utilisateurs](#_core_your_updates_and_the_updates_of_other_users).

- [Plus d’informations sur les fonctions membres Update et Delete](#_core_more_about_update_and_delete).

> [!NOTE]
>  Cette rubrique s’applique aux objets dérivés de `CRecordset` dans les lignes en bloc l’extraction n’a pas été implémentée. Si vous avez implémenté l’extraction de lignes en bloc, certaines informations ne s’applique pas. Par exemple, vous ne pouvez pas appeler le `AddNew`, `Edit`, `Delete`, et `Update` fonctions membres ; Toutefois, vous pouvez effectuer des transactions. Pour plus d’informations sur l’extraction de lignes en bloc, consultez [jeu d’enregistrements : Extraction globale d’enregistrements en bloc (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

##  <a name="_core_how_other_operations_affect_updates"></a> Répercussions des autres opérations sur les mises à jour

Vos mises à jour sont affectées par les transactions en vigueur au moment de la mise à jour, en fermant le jeu d’enregistrements avant la fin d’une transaction et en faisant défiler avant d’effectuer une transaction.

###  <a name="_core_how_transactions_affect_updates"></a> Répercussions des Transactions sur les mises à jour

Au-delà de comprendre comment `AddNew`, `Edit`, et `Delete` travail, il est important de comprendre comment la `BeginTrans`, `CommitTrans`, et `Rollback` fonctions membres de [CDatabase](../../mfc/reference/cdatabase-class.md) fonctionnent avec les fonctions de mise à jour de [CRecordset](../../mfc/reference/crecordset-class.md).

Par défaut, les appels aux `AddNew` et `Edit` affectent la source de données immédiatement lorsque vous appelez `Update`. `Delete` appels immédiatement en vigueur. Mais vous pouvez établir une transaction et exécuter un traitement de ces appels. Les mises à jour ne sont pas permanentes jusqu'à ce que vous les validiez. Si vous changez d’avis, vous pouvez restaurer la transaction au lieu de la valider.

Pour plus d’informations sur les transactions, consultez [Transaction (ODBC)](../../data/odbc/transaction-odbc.md).

###  <a name="_core_how_closing_the_recordset_affects_updates"></a> Impact de la fermeture de l’ensemble d’enregistrements sur les mises à jour

Si vous fermez un jeu d’enregistrements, ou qui lui sont associés `CDatabase` objet, avec une transaction en cours (vous n’avez pas appelé [CDatabase::CommitTrans](../../mfc/reference/cdatabase-class.md#committrans) ou [CDatabase::Rollback](../../mfc/reference/cdatabase-class.md#rollback)), la transaction est restaurée. sauvegarder automatiquement (à moins que votre base de données principale est le moteur de base de données Microsoft Jet).

> [!CAUTION]
>  Si vous utilisez le moteur de base de données Microsoft Jet, la fermeture d’un jeu d’enregistrements à l’intérieur d’une transaction explicite n’entraîne pas la libération des lignes qui ont été modifiées ou des verrous qui ont été placés jusqu'à ce que la transaction explicite est validée ou restaurée. Il est recommandé que vous ouvrez et fermez les jeux d’enregistrements à l’intérieur ou en dehors d’une transaction Jet explicite.

###  <a name="_core_how_scrolling_affects_updates"></a> Influence du défilement mises à jour

Lorsque vous [jeu d’enregistrements : Défilement (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) dans un jeu d’enregistrements, la mémoire tampon d’édition est rempli avec chaque nouvel enregistrement courant (l’enregistrement précédent n’est pas stocké d’abord). Défilement ignore les enregistrements supprimés précédemment. Si vous faites défiler après un `AddNew` ou `Edit` appel sans appeler `Update`, `CommitTrans`, ou `Rollback` tout d’abord, toutes les modifications sont perdues (aucun avertissement pour vous) lorsqu’un nouvel enregistrement est placé dans la mémoire tampon d’édition. La mémoire tampon d’édition est rempli avec l’enregistrement défilent jusqu’au, l’enregistrement stocké est libéré, et aucune modification n’intervient sur la source de données. Cela s’applique aux deux `AddNew` et `Edit`.

##  <a name="_core_your_updates_and_the_updates_of_other_users"></a> Vos mises à jour et les mises à jour d’autres utilisateurs

Lorsque vous utilisez un jeu d’enregistrements à mettre à jour des données, vos mises à jour affectant d’autres utilisateurs. De même, les mises à jour des autres utilisateurs pendant la durée de vie de votre recordset vous affectent.

Dans un environnement multi-utilisateur, les autres utilisateurs peuvent ouvrir des jeux d’enregistrements qui contiennent certains enregistrements identiques à ceux que vous avez sélectionné dans votre jeu d’enregistrements. Modifications apportées à un enregistrement avant que vous récupériez sont répercutées dans votre jeu d’enregistrements. Étant donné que les dynasets extraire un enregistrement chaque fois que vous accédez par défilement, répercutent les modifications chaque fois que vous accédez à un enregistrement. Captures instantanées de récupérer un enregistrement de la première fois que vous accédez par défilement, instantanés reflètent uniquement les modifications qui se produisent avant que vous accédiez à l’enregistrement.

Les enregistrements ajoutés par d’autres utilisateurs après avoir ouvert le jeu d’enregistrements ne s’affichent pas dans le jeu d’enregistrements, sauf si vous réexécutez la requête. Si le recordset est une feuille de réponse dynamique, modifications d’enregistrements existants par d’autres utilisateurs s’affichent dans votre feuille de réponse dynamique lorsque vous faites défiler à l’enregistrement concerné. Si votre jeu d’enregistrements est un instantané, les modifications n’apparaissent pas jusqu'à ce que vous actualisez l’instantané. Si vous souhaitez voir les enregistrements ajoutés ou supprimés par d’autres utilisateurs dans l’instantané, ou les enregistrements ajoutés par d’autres utilisateurs dans votre feuille de réponse dynamique, appelez [CRecordset::Requery](../../mfc/reference/crecordset-class.md#requery) pour reconstruire le jeu d’enregistrements. (Notez que les suppressions d’autres utilisateurs s’affichent dans votre feuille de réponse dynamique.) Vous pouvez également appeler `Requery` pour afficher les enregistrements vous ajoutez, mais ne pas pour voir vos propres suppressions.

> [!TIP]
>  Pour forcer la mise en cache de l’intégralité d’un instantané à la fois, appelez `MoveLast` immédiatement après l’ouverture de l’instantané. Appelez ensuite `MoveFirst` pour commencer à travailler avec les enregistrements. `MoveLast` est équivalent au défilement sur tous les enregistrements, mais ceux-ci sont tous en même temps. Toutefois, notez que cela peut réduire les performances et ne peut pas être nécessaire pour certains pilotes.

Les effets de vos mises à jour sur les autres utilisateurs sont semblables à leurs effets sur vous.

##  <a name="_core_more_about_update_and_delete"></a> Plus d’informations sur Update et Delete

Cette section fournit des informations supplémentaires pour vous aider à travailler avec `Update` et `Delete`.

### <a name="update-success-and-failure"></a>Réussite de la mise à jour et d’échec

Si `Update` réussit, le `AddNew` ou `Edit` fin en mode. Pour commencer un `AddNew` ou `Edit` mode à nouveau, appelez `AddNew` ou `Edit`.

Si `Update` échoue (lève une exception ou retourne la valeur FALSE), vous restez dans `AddNew` ou `Edit` mode, selon la fonction qui a été appelée en dernier. Vous pouvez ensuite effectuer une des opérations suivantes :

- Modifier un membre de données de champ et essayer la `Update` à nouveau.

- Appelez `AddNew` pour réinitialiser les données membres de champ sur Null, définissez les valeurs des données membres de champ, puis appelez `Update` à nouveau.

- Appelez `Edit` pour recharger les valeurs qui étaient dans le jeu d’enregistrements avant le premier appel à `AddNew` ou `Edit`, définissez les valeurs des données membres de champ, puis appelez `Update` à nouveau. Après une réussite `Update` appeler (sauf après un `AddNew` appeler), les membres de données de champ conservent leurs nouvelles valeurs.

- Appelez `Move` (y compris `Move` avec un paramètre de AFX_MOVE_REFRESH, ou 0), qui vide les modifications et met fin `AddNew` ou `Edit` mode en vigueur.

### <a name="update-and-delete"></a>Update et Delete

Cette section s’applique aux deux `Update` et `Delete`.

Sur un `Update` ou `Delete` opération, un seul enregistrement et doit être mis à jour. Cet enregistrement est l’enregistrement actif, ce qui correspond aux valeurs de données dans les champs du recordset. Si pour une raison quelconque, aucun enregistrements ne sont concernés ou de plusieurs enregistrements est affectée, une exception est levée contenant l’une des opérations suivantes **et RETCODE contient** valeurs :

- AFX_SQL_ERROR_NO_ROWS_AFFECTED

- AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED

Lorsque ces exceptions sont levées, vous restez dans le `AddNew` ou `Edit` état vous étiez lorsque vous avez appelé `Update` ou `Delete`. Voici les scénarios les plus courants dans lesquels vous devriez voir ces exceptions. Vous êtes probablement voir :

- AFX_SQL_ERROR_NO_ROWS_AFFECTED lorsque vous utilisez le mode de verrouillage optimiste et un autre utilisateur a modifié l’enregistrement d’une manière qui empêche le framework identifiant l’enregistrement à mettre à jour ou supprimer.

- AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED apparaît lorsque la table que vous mettez à jour ne possède aucune clé primaire ou index unique et que vous n’avez pas de suffisamment de colonnes dans le jeu d’enregistrements pour identifier de manière unique une ligne de table.

## <a name="see-also"></a>Voir aussi

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Recordset : Sélection d’enregistrements par les recordsets (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)<br/>
[Record Field Exchange (RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[SQL](../../data/odbc/sql.md)<br/>
[Exceptions : Exceptions de base de données](../../mfc/exceptions-database-exceptions.md)