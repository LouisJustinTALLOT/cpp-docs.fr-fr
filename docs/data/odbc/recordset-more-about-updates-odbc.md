---
description: 'En savoir plus sur : Recordset : en savoir plus sur les mises à jour (ODBC)'
title: 'Recordset : informations complémentaires sur les mises à jour (ODBC)'
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
ms.openlocfilehash: 9d125456189828d50f1fbfd4aece00a16790424f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97304439"
---
# <a name="recordset-more-about-updates-odbc"></a>Recordset : informations complémentaires sur les mises à jour (ODBC)

Cette rubrique s’applique aux classes ODBC MFC.

Cette rubrique répond aux questions suivantes :

- [Comment d’autres opérations, telles que les transactions, affectent les mises à jour](#_core_how_transactions_affect_updates).

- [Vos mises à jour et celles d’autres utilisateurs](#_core_your_updates_and_the_updates_of_other_users).

- En [savoir plus sur les fonctions membres Update et Delete](#_core_more_about_update_and_delete).

> [!NOTE]
> Cette rubrique s’applique aux objets dérivés de `CRecordset` où l’extraction de lignes en bloc n’a pas été implémentée. Si vous avez implémenté l’extraction de lignes en bloc, certaines des informations ne s’appliquent pas. Par exemple, vous ne pouvez pas appeler les `AddNew` `Edit` fonctions membres,, `Delete` et `Update` ; Toutefois, vous pouvez effectuer des transactions. Pour plus d’informations sur l’extraction de lignes en bloc, consultez [Recordset : extraction globale d’enregistrements (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

## <a name="how-other-operations-affect-updates"></a><a name="_core_how_other_operations_affect_updates"></a> Impact des autres opérations sur les mises à jour

Vos mises à jour sont affectées par les transactions en vigueur au moment de la mise à jour, en fermant le Recordset avant d’effectuer une transaction et en faisant défiler avant d’effectuer une transaction.

### <a name="how-transactions-affect-updates"></a><a name="_core_how_transactions_affect_updates"></a> Répercussions des transactions sur les mises à jour

Au-delà de la compréhension de la façon dont `AddNew` , `Edit` et `Delete` fonctionnent, il est important de comprendre comment les `BeginTrans` `CommitTrans` `Rollback` fonctions membres, et de [CDatabase](../../mfc/reference/cdatabase-class.md) fonctionnent avec les fonctions de mise à jour de [CRecordset](../../mfc/reference/crecordset-class.md).

Par défaut, les appels à `AddNew` et `Edit` affectent la source de données immédiatement lorsque vous appelez `Update` . `Delete` les appels prennent effet immédiatement. Toutefois, vous pouvez établir une transaction et exécuter un lot de tels appels. Les mises à jour ne sont pas définitives tant que vous ne les avez pas validées. Si vous changez d’avis, vous pouvez restaurer la transaction au lieu de la valider.

Pour plus d’informations sur les transactions, consultez [transaction (ODBC)](../../data/odbc/transaction-odbc.md).

### <a name="how-closing-the-recordset-affects-updates"></a><a name="_core_how_closing_the_recordset_affects_updates"></a> Impact de la fermeture du Recordset sur les mises à jour

Si vous fermez un Recordset, ou son `CDatabase` objet associé, avec une transaction en cours (vous n’avez pas appelé [CDatabase :: CommitTrans](../../mfc/reference/cdatabase-class.md#committrans) ou [CDatabase :: Rollback](../../mfc/reference/cdatabase-class.md#rollback)), la transaction est restaurée automatiquement (à moins que le serveur principal de votre base de données ne soit le moteur de base de données Microsoft Jet).

> [!CAUTION]
> Si vous utilisez le moteur de base de données Microsoft Jet, la fermeture d’un jeu d’enregistrements à l’intérieur d’une transaction explicite n’entraîne pas la libération des lignes qui ont été modifiées ou les verrous placés jusqu’à ce que la transaction explicite soit validée ou restaurée. Il est recommandé de toujours ouvrir et fermer des jeux d’enregistrements à l’intérieur ou à l’extérieur d’une transaction jet explicite.

### <a name="how-scrolling-affects-updates"></a><a name="_core_how_scrolling_affects_updates"></a> Impact du défilement sur les mises à jour

Lorsque vous [faites un Recordset : défilement (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) dans un Recordset, le tampon d’édition est rempli avec chaque nouvel enregistrement actif (l’enregistrement précédent n’est pas stocké en premier). Le défilement ignore les enregistrements précédemment supprimés. Si vous faites défiler la liste après un `AddNew` `Edit` appel ou sans appeler `Update` , `CommitTrans` ou en `Rollback` premier lieu, toutes les modifications sont perdues (sans avertissement) lorsqu’un nouvel enregistrement est placé dans le tampon d’édition. Le tampon d’édition est rempli avec l’enregistrement défilant, l’enregistrement stocké est libéré et aucune modification n’est apportée à la source de données. Cela s’applique à `AddNew` et à `Edit`.

## <a name="your-updates-and-the-updates-of-other-users"></a><a name="_core_your_updates_and_the_updates_of_other_users"></a> Vos mises à jour et les mises à jour d’autres utilisateurs

Lorsque vous utilisez un jeu d’enregistrements pour mettre à jour des données, vos mises à jour affectent les autres utilisateurs. De même, les mises à jour d’autres utilisateurs au cours de la durée de vie de votre jeu d’enregistrements vous affectent.

Dans un environnement multi-utilisateur, d’autres utilisateurs peuvent ouvrir des jeux d’enregistrements qui contiennent certains des enregistrements que vous avez sélectionnés dans votre jeu d’enregistrements. Les modifications apportées à un enregistrement avant sa récupération sont reflétées dans votre jeu d’enregistrements. Étant donné que les feuilles de réponse dynamiques récupèrent un enregistrement chaque fois que vous y accédez, les feuilles de réponse dynamiques reflètent les modifications chaque fois que vous faites défiler un enregistrement. Les instantanés récupèrent un enregistrement la première fois que vous y faites défiler. ainsi, les instantanés reflètent uniquement les modifications qui se produisent avant de pouvoir accéder initialement à l’enregistrement.

Les enregistrements ajoutés par d’autres utilisateurs après l’ouverture de l’ensemble d’enregistrements n’apparaissent pas dans votre Recordset, sauf si vous reinterrogez. Si votre jeu d’enregistrements est une feuille de réponse dynamique, les modifications apportées aux enregistrements existants par d’autres utilisateurs s’affichent dans votre feuille de réponse dynamique lorsque vous faites défiler jusqu’à l’enregistrement affecté. Si votre recordset est un instantané, les modifications ne s’affichent pas tant que vous n’avez pas reinterrogé l’instantané. Si vous souhaitez voir les enregistrements ajoutés ou supprimés par d’autres utilisateurs dans votre instantané, ou des enregistrements ajoutés par d’autres utilisateurs dans votre feuille de réponse dynamique, appelez [CRecordset :: Requery](../../mfc/reference/crecordset-class.md#requery) pour reconstruire le Recordset. (Notez que les suppressions d’autres utilisateurs s’affichent dans votre feuille de réponse dynamique.) Vous pouvez également appeler `Requery` pour voir les enregistrements que vous ajoutez, mais pas pour voir vos suppressions.

> [!TIP]
> Pour forcer la mise en cache d’un instantané entier en même temps, appelez `MoveLast` immédiatement après l’ouverture de l’instantané. Appelez ensuite `MoveFirst` pour commencer à travailler avec les enregistrements. `MoveLast` équivaut à faire défiler tous les enregistrements, mais les récupère tous en même temps. Notez, cependant, que cela peut réduire les performances et ne pas être nécessaire pour certains pilotes.

Les effets de vos mises à jour sur d’autres utilisateurs sont similaires à leurs effets sur vous.

## <a name="more-about-update-and-delete"></a><a name="_core_more_about_update_and_delete"></a> En savoir plus sur les mises à jour et les suppressions

Cette section fournit des informations supplémentaires pour vous aider à utiliser `Update` et `Delete` .

### <a name="update-success-and-failure"></a>Réussite et échec de la mise à jour

Si `Update` aboutit, le `AddNew` `Edit` mode ou se termine. Pour recommencer un `AddNew` ou le `Edit` mode, `AddNew` appelez ou `Edit` .

Si `Update` échoue (retourne la valeur false ou lève une exception), vous restez en `AddNew` mode ou en `Edit` mode, selon la fonction que vous avez appelée en dernier. Vous pouvez alors effectuer l’une des opérations suivantes :

- Modifiez un membre de données de champ et réessayez `Update` .

- Appelez `AddNew` pour réinitialiser les membres de données de champ sur null, définissez les valeurs des membres de données de champ, puis rappelez `Update` .

- Appelez `Edit` pour recharger les valeurs qui se trouvaient dans le Recordset avant le premier appel à `AddNew` ou `Edit` , définissez les valeurs des membres de données de champ, puis rappelez `Update` . Après un `Update` appel réussi (sauf après un `AddNew` appel), les membres de données de champ conservent leurs nouvelles valeurs.

- Appelez `Move` (y compris `Move` avec un paramètre de AFX_MOVE_REFRESH, ou 0), qui vide les modifications et met fin à l’un ou l’autre des `AddNew` `Edit` modes en vigueur.

### <a name="update-and-delete"></a>Mettre à jour et supprimer

Cette section s’applique à `Update` et à `Delete` .

Sur une `Update` `Delete` opération ou, un seul enregistrement doit être mis à jour. Cet enregistrement est l’enregistrement actif, qui correspond aux valeurs des données dans les champs de l’ensemble d’enregistrements. Si, pour une raison quelconque, aucun enregistrement n’est affecté ou si plusieurs enregistrements sont affectés, une exception est levée, contenant l’une des valeurs **RETCODE** suivantes :

- AFX_SQL_ERROR_NO_ROWS_AFFECTED

- AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED

Lorsque ces exceptions sont levées, vous restez dans `AddNew` l' `Edit` État ou dans lequel vous étiez lorsque vous avez appelé `Update` ou `Delete` . Voici les scénarios les plus courants dans lesquels vous pouvez voir ces exceptions. Vous pouvez voir les éléments suivants :

- AFX_SQL_ERROR_NO_ROWS_AFFECTED lorsque vous utilisez le mode de verrouillage optimiste et qu’un autre utilisateur a modifié l’enregistrement d’une manière qui empêche l’infrastructure d’identifier l’enregistrement correct à mettre à jour ou à supprimer.

- AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED lorsque la table que vous mettez à jour n’a pas de clé primaire ou d’index unique et que vous n’avez pas assez de colonnes dans le jeu d’enregistrements pour identifier de manière unique une ligne de table.

## <a name="see-also"></a>Voir aussi

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Recordset : sélection d’enregistrements par les recordsets (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)<br/>
[RFX (Record Field Exchange)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[SQL](../../data/odbc/sql.md)<br/>
[Exceptions : exceptions de base de données](../../mfc/exceptions-database-exceptions.md)
