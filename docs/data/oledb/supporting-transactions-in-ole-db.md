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
ms.openlocfilehash: 3c71200e39641a69443599e0445f89f469aceeda
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59038746"
---
# <a name="supporting-transactions-in-ole-db"></a>Prise en charge des transactions dans OLE DB

Un [transaction](../../data/transactions-mfc-data-access.md) consiste à regrouper ou du lot, une série de mises à jour à une source de données afin que toutes réussissent et sont validées en même temps ou (si l’une d’elles échoue), aucun n’est validée et toute la transaction est restaurée. Ce processus garantit l’intégrité du résultat sur la source de données.

OLE DB prend en charge les transactions avec les trois méthodes suivantes :

- [ITransactionLocal::StartTransaction](/previous-versions/windows/desktop/ms709786(v=vs.85))

- [ITransaction::Commit](/previous-versions/windows/desktop/ms713008(v=vs.85))

- [ITransaction::Abort](/previous-versions/windows/desktop/ms709833(v=vs.85))

## <a name="relationship-of-sessions-and-transactions"></a>Relations des Sessions et Transactions

Un objet de source de données unique peut créer un ou plusieurs objets de session, chacun d’eux peut être à l’intérieur ou en dehors de l’étendue d’une transaction à un moment donné.

Quand une session n’entre pas une transaction, tout le travail effectué au sein de cette session sur le magasin de données est immédiatement validé sur chaque appel de méthode. (Cela est parfois appelé mode de validation automatique ou implicite.)

Lorsqu’une session entre une transaction, les tout le travail effectué au sein de cette session sur le magasin de données fait partie de cette transaction et soit validé ou abandonné comme une seule unité. (Cela est parfois appelé mode de validation manuelle.)

Prise en charge de la transaction est spécifique au fournisseur. Si le fournisseur que vous utilisez prend en charge les transactions, un objet de session qui prend en charge `ITransaction` et `ITransactionLocal` pouvez entrer une transaction (non imbriqué). La classe de modèles OLE DB [CSession](../../data/oledb/csession-class.md) prend en charge ces interfaces et est la méthode recommandée pour implémenter la prise en charge des transactions dans Visual C++.

## <a name="starting-and-ending-the-transaction"></a>Début et fin de la Transaction

Vous appelez le `StartTransaction`, `Commit`, et `Abort` méthodes dans l’objet d’ensemble de lignes dans le consommateur.

Appel `ITransactionLocal::StartTransaction` démarre une nouvelle transaction locale. Lorsque vous démarrez la transaction, toutes les modifications mandatées par les opérations ultérieures ne sont pas appliquées au magasin de données jusqu'à ce que vous validez la transaction.

Appel `ITransaction::Commit` ou `ITransaction::Abort` met fin à la transaction. `Commit` toutes les modifications dans l’étendue de la transaction à appliquer au magasin de données. `Abort` causes de toutes les modifications dans l’étendue de la transaction doit être annulée et le magasin de données est laissé dans un état, il avaient avant le démarrage de la transaction.

## <a name="nested-transactions"></a>Transactions imbriquées

Un [imbriqués transaction](/previous-versions/windows/desktop/ms716985(v=vs.85)) se produit lorsque vous démarrez une nouvelle transaction locale lorsqu’une transaction active existe déjà sur la session. La nouvelle transaction est démarrée en tant que transaction imbriquée sous la transaction en cours. Si le fournisseur ne prend pas en charge les transactions imbriquées, l’appel `StartTransaction` lorsqu’il existe déjà une transaction active dans la session renvoie XACT_E_XTIONEXISTS.

## <a name="distributed-transactions"></a>Transactions distribuées

Une transaction distribuée est une transaction qui met à jour des données distribuées ; Autrement dit, les données sur plusieurs systèmes informatiques en réseau. Si vous souhaitez prendre en charge des transactions sur un système distribué, vous devez utiliser le .NET Framework plutôt que la prise en charge des transactions OLE DB.

## <a name="see-also"></a>Voir aussi

[Utilisation des accesseurs](../../data/oledb/using-accessors.md)