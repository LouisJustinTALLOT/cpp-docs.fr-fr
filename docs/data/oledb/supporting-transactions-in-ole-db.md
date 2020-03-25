---
title: Prise en charge des transactions dans OLE DB
ms.date: 10/24/2018
helpviewer_keywords:
- OLE DB consumer templates [C++], transaction support
- transactions [C++], OLE DB support for
- nested transactions [C++]
- OLE DB [C++], transaction support
- databases [C++], transactions
- distributed transactions [C++]
ms.assetid: 3d72e583-ad38-42ff-8f11-e2166d60a5a7
ms.openlocfilehash: e7ec4f69b4bba497446c94afb94cb5a1d648f7c7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209540"
---
# <a name="supporting-transactions-in-ole-db"></a>Prise en charge des transactions dans OLE DB

Une [transaction](../../data/transactions-mfc-data-access.md) est un moyen de regrouper ou de traiter par lot une série de mises à jour d’une source de données de sorte que toutes les opérations réussissent et soient validées simultanément ou (si l’une d’entre elles échoue), aucune n’est validée et la totalité de la transaction est restaurée. Ce processus garantit l’intégrité du résultat sur la source de données.

OLE DB prend en charge les transactions avec les trois méthodes suivantes :

- [ITransactionLocal :: StartTransaction](/previous-versions/windows/desktop/ms709786(v=vs.85))

- [ITransaction :: Commit](/previous-versions/windows/desktop/ms713008(v=vs.85))

- [ITransaction :: Abort](/previous-versions/windows/desktop/ms709833(v=vs.85))

## <a name="relationship-of-sessions-and-transactions"></a>Relation entre les sessions et les transactions

Un objet de source de données unique peut créer un ou plusieurs objets de session, chacun pouvant être à l’intérieur ou à l’extérieur de l’étendue d’une transaction à un moment donné.

Lorsqu’une session n’entre pas dans une transaction, tout le travail effectué dans cette session sur le magasin de données est immédiatement validé pour chaque appel de méthode. (Parfois appelé mode de validation automatique ou mode implicite).

Lorsqu’une session entre dans une transaction, tout le travail effectué dans cette session sur le magasin de données fait partie de cette transaction et est validé ou abandonné en tant qu’unité unique. (Cette opération est parfois appelée mode de validation manuelle).

La prise en charge des transactions est spécifique au fournisseur. Si le fournisseur que vous utilisez prend en charge les transactions, un objet de session qui prend en charge `ITransaction` et `ITransactionLocal` peut entrer une transaction (non imbriquée). La classe de modèles OLE DB [CSession](../../data/oledb/csession-class.md) prend en charge ces interfaces et constitue la méthode recommandée pour implémenter C++la prise en charge des transactions dans Visual.

## <a name="starting-and-ending-the-transaction"></a>Démarrage et fin de la transaction

Vous appelez les méthodes `StartTransaction`, `Commit`et `Abort` dans l’objet rowset dans le consommateur.

L’appel de `ITransactionLocal::StartTransaction` démarre une nouvelle transaction locale. Lorsque vous démarrez la transaction, toutes les modifications imposées par les opérations ultérieures ne sont pas appliquées au magasin de données tant que vous n’avez pas validé la transaction.

L’appel de `ITransaction::Commit` ou `ITransaction::Abort` met fin à la transaction. `Commit` entraîne l’application de toutes les modifications dans l’étendue de la transaction à la Banque de données. `Abort` entraîne l’annulation de toutes les modifications dans l’étendue de la transaction et la Banque de données reste dans l’État où elle se trouvait avant le démarrage de la transaction.

## <a name="nested-transactions"></a>Transactions imbriquées

Une [transaction imbriquée](/previous-versions/windows/desktop/ms716985(v=vs.85)) se produit lorsque vous démarrez une nouvelle transaction locale alors qu’une transaction active existe déjà dans la session. La nouvelle transaction est lancée sous la forme d’une transaction imbriquée sous la transaction en cours. Si le fournisseur ne prend pas en charge les transactions imbriquées, l’appel de `StartTransaction` lorsqu’une transaction est déjà active sur la session retourne XACT_E_XTIONEXISTS.

## <a name="distributed-transactions"></a>Transactions distribuées

Une transaction distribuée est une transaction qui met à jour des données distribuées ; autrement dit, les données de plusieurs systèmes informatiques en réseau. Si vous souhaitez prendre en charge les transactions sur un système distribué, vous devez utiliser le .NET Framework plutôt que la prise en charge des transactions OLE DB.

## <a name="see-also"></a>Voir aussi

[Utilisation des accesseurs](../../data/oledb/using-accessors.md)
