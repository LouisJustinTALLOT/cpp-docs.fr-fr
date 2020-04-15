---
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
ms.openlocfilehash: 955b26137ce976514d84f95f4d819779b93bd78a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368673"
---
# <a name="recordset-more-about-updates-odbc"></a>Recordset : informations complémentaires sur les mises à jour (ODBC)

Cette rubrique s’applique aux classes ODBC MFC.

Cette rubrique répond aux questions suivantes :

- [Comment d’autres opérations, telles que les transactions, affectent les mises à jour](#_core_how_transactions_affect_updates).

- [Vos mises à jour et celles d’autres utilisateurs](#_core_your_updates_and_the_updates_of_other_users).

- [En savoir plus sur les fonctions des membres De mise à jour et de suppression](#_core_more_about_update_and_delete).

> [!NOTE]
> Cette rubrique s’applique aux objets dérivés de `CRecordset` où l’extraction de lignes en bloc n’a pas été implémentée. Si vous avez mis en œuvre la mise en place de la ligne en vrac, certaines des informations ne s’appliquent pas. Par exemple, vous `AddNew`ne `Edit` `Delete`pouvez `Update` pas appeler les fonctions , , et membres; cependant, vous pouvez effectuer des transactions. Pour plus d’informations sur la ligne en vrac aller chercher, voir [Recordset: Fetching Records in Bulk (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

## <a name="how-other-operations-affect-updates"></a><a name="_core_how_other_operations_affect_updates"></a>Comment les autres opérations affectent les mises à jour

Vos mises à jour sont affectées par les transactions en vigueur au moment de la mise à jour, en fermant le dossier avant de conclure une transaction, et en faisant défiler avant de conclure une transaction.

### <a name="how-transactions-affect-updates"></a><a name="_core_how_transactions_affect_updates"></a>Comment les transactions affectent les mises à jour

Au-delà `AddNew` `Edit`de `Delete` la compréhension de la façon `BeginTrans` `CommitTrans`dont `Rollback` , , et le travail, il est important de comprendre comment le , , et les fonctions des membres de [CDatabase](../../mfc/reference/cdatabase-class.md) travailler avec les fonctions de mise à jour de [CRecordset](../../mfc/reference/crecordset-class.md).

Par défaut, `AddNew` les `Edit` appels vers et affectent `Update`la source de données immédiatement lorsque vous appelez . `Delete`les appels prennent effet immédiatement. Mais vous pouvez établir une transaction et exécuter un lot de ces appels. Les mises à jour ne sont pas permanentes tant que vous ne les avez pas commises. Si vous changez d’avis, vous pouvez annuler la transaction au lieu de l’engager.

Pour plus d’informations sur les transactions, voir [Transaction (ODBC)](../../data/odbc/transaction-odbc.md).

### <a name="how-closing-the-recordset-affects-updates"></a><a name="_core_how_closing_the_recordset_affects_updates"></a>Comment la fermeture du recordet affecte les mises à jour

Si vous fermez un ensemble `CDatabase` d’enregistrements, ou son objet associé, avec une transaction en cours (vous n’avez pas appelé [CDatabase::CommitTrans](../../mfc/reference/cdatabase-class.md#committrans) ou [CDatabase::Rollback](../../mfc/reference/cdatabase-class.md#rollback)), la transaction est annulée automatiquement (sauf si votre backend de base de données est le moteur de base de données Microsoft Jet).

> [!CAUTION]
> Si vous utilisez le moteur de base de données Microsoft Jet, la fermeture d’un ensemble d’enregistrements à l’intérieur d’une transaction explicite n’entraîne pas la libération de l’une des lignes qui ont été modifiées ou des verrous qui ont été placés jusqu’à ce que la transaction explicite soit engagée ou annulée. Il est recommandé que vous soyez toujours à la fois ouvert et fermez des enregistrements à l’intérieur ou à l’extérieur d’une transaction Jet explicite.

### <a name="how-scrolling-affects-updates"></a><a name="_core_how_scrolling_affects_updates"></a>Comment le défilement affecte les mises à jour

Lorsque vous [enregistrez : Faire défiler (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) dans un ensemble d’enregistrements, le tampon d’édition est rempli de chaque nouvel enregistrement actuel (l’enregistrement précédent n’est pas stocké en premier). Le défilement saute sur les enregistrements précédemment supprimés. Si vous faites `AddNew` `Edit` défiler `Update`après `CommitTrans`un `Rollback` ou appelez sans appeler, , ou d’abord, toutes les modifications sont perdues (sans avertissement pour vous) comme un nouvel enregistrement est introduit dans le tampon de modification. Le tampon de modification est rempli avec l’enregistrement défilé, l’enregistrement stocké est libéré, et aucun changement ne se produit sur la source de données. Cela s’applique à `AddNew` et à `Edit`.

## <a name="your-updates-and-the-updates-of-other-users"></a><a name="_core_your_updates_and_the_updates_of_other_users"></a>Vos mises à jour et les mises à jour d’autres utilisateurs

Lorsque vous utilisez un jeu d’enregistrement pour mettre à jour les données, vos mises à jour affectent les autres utilisateurs. De même, les mises à jour d’autres utilisateurs au cours de la durée de vie de votre dossier vous affectent.

Dans un environnement multi-utilisateurs, d’autres utilisateurs peuvent ouvrir des enregistrements contenant certains des mêmes enregistrements que vous avez sélectionnés dans votre jeu d’enregistrement. Les modifications apportées à un enregistrement avant de le récupérer sont reflétées dans votre dossier. Étant donné que les dynasets récupèrent un enregistrement chaque fois que vous faites défiler vers elle, les dynasets reflètent les changements chaque fois que vous faites défiler vers un enregistrement. Les instantanés récupèrent un enregistrement la première fois que vous faites défiler vers elle, de sorte que les instantanés reflètent uniquement les modifications qui se produisent avant de faire défiler à l’enregistrement au départ.

Les enregistrements ajoutés par d’autres utilisateurs après l’ouverture du recordet ne s’affichent pas dans votre dossier à moins que vous ne requiy. Si votre jeu d’enregistrement est un dynaset, les modifications aux enregistrements existants par d’autres utilisateurs apparaissent dans votre dynaset lorsque vous faites défiler vers l’enregistrement affecté. Si votre historique est un instantané, les modifications ne s’affichent pas tant que vous n’avez pas requié l’instantané. Si vous souhaitez voir les enregistrements ajoutés ou supprimés par d’autres utilisateurs dans votre instantané, ou les enregistrements ajoutés par d’autres utilisateurs dans votre dynaset, appelez [CRecordset::Requery](../../mfc/reference/crecordset-class.md#requery) pour reconstruire le jeu d’enregistrements. (Notez que les suppressions d’autres utilisateurs apparaissent dans votre dynaset.) Vous pouvez `Requery` également appeler pour voir les enregistrements que vous ajoutez, mais pas pour voir vos suppressions.

> [!TIP]
> Pour forcer la mise en cache `MoveLast` d’un instantané entier à la fois, appelez immédiatement après avoir ouvert l’instantané. Appelez `MoveFirst` ensuite pour commencer à travailler avec les dossiers. `MoveLast`est équivalent à défiler sur tous les enregistrements, mais il les récupère tous à la fois. Notez toutefois que cela peut réduire les performances et pourrait ne pas être nécessaire pour certains conducteurs.

Les effets de vos mises à jour sur d’autres utilisateurs sont similaires à leurs effets sur vous.

## <a name="more-about-update-and-delete"></a><a name="_core_more_about_update_and_delete"></a>Plus d’actualités sur les mises à jour et les suppressions

Cette section fournit des informations `Update` supplémentaires `Delete`pour vous aider à travailler avec et .

### <a name="update-success-and-failure"></a>Mettre à jour le succès et l’échec

En `Update` cas de `AddNew` `Edit` succès, le mode ou se termine. Pour recommencer `AddNew` `Edit` un ou `AddNew` un `Edit`mode, appelez ou .

En `Update` cas d’échec (retourne FALSE ou `AddNew` `Edit` lance une exception), vous restez en mode ou en mode, selon la fonction que vous avez appelée en dernier. Vous pouvez alors effectuer l’une des opérations suivantes :

- Modifier un membre des `Update` données sur le terrain et essayer à nouveau.

- Appelez `AddNew` pour réinitialiser les membres des données sur le `Update` terrain à Null, définir les valeurs des membres des données sur le terrain, puis appeler à nouveau.

- Appelez `Edit` pour recharger les valeurs qui étaient dans `AddNew` le `Edit`dossier avant le premier appel à `Update` ou, définir les valeurs des membres des données de terrain, puis appeler à nouveau. Après un `Update` appel réussi `AddNew` (sauf après un appel), les membres des données sur le terrain conservent leurs nouvelles valeurs.

- Appelez `Move` (y compris `Move` avec un paramètre de AFX_MOVE_REFRESH, ou 0), `AddNew` `Edit` qui rince tout changement et se termine tout ou mode en vigueur.

### <a name="update-and-delete"></a>Mise à jour et suppression

Cette section s’applique aux deux `Update` et `Delete`.

Sur `Update` un `Delete` ou une opération, un seul et unique enregistrement doit être mis à jour. Ce dossier est le record actuel, qui correspond aux valeurs de données dans les domaines de l’enregistrement. Si, pour une raison ou une autre, aucun enregistrement n’est affecté ou si plus d’un enregistrement est affecté, une exception est projetée contenant l’une des valeurs **RETCODE** suivantes :

- AFX_SQL_ERROR_NO_ROWS_AFFECTED

- AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED

Lorsque ces exceptions sont jetées, `Edit` vous restez dans `Update` l’état `AddNew` ou vous étiez dans quand vous avez appelé ou `Delete`. Voici les scénarios les plus courants dans lesquels vous verriez ces exceptions. Vous êtes le plus susceptible de voir:

- AFX_SQL_ERROR_NO_ROWS_AFFECTED lorsque vous utilisez un mode de verrouillage optimiste et qu’un autre utilisateur a modifié l’enregistrement d’une manière qui empêche le cadre d’identifier l’enregistrement correct pour mettre à jour ou supprimer.

- AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED lorsque la table que vous mise à jour n’a pas de clé primaire ou d’index unique et vous n’avez pas assez de colonnes dans le jeu d’enregistrement pour identifier de façon unique une ligne de table.

## <a name="see-also"></a>Voir aussi

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Recordset : sélection d'enregistrements par les recordsets (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)<br/>
[Échange de terrain record (RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[SQL](../../data/odbc/sql.md)<br/>
[Exceptions : exceptions de base de données](../../mfc/exceptions-database-exceptions.md)
