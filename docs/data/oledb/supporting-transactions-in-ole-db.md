---
title: Prise en charge des Transactions dans OLE DB | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB consumer templates [C++], transaction support
- transactions [C++], OLE DB support for
- nested transactions [C++]
- OLE DB [C++], transaction support
- databases [C++], transactions
- distributed transactions [C++]
ms.assetid: 3d72e583-ad38-42ff-8f11-e2166d60a5a7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ecd5b7274e62508289a83d6c0420d5f76e239e4d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33110339"
---
# <a name="supporting-transactions-in-ole-db"></a>Prise en charge des transactions dans OLE DB
A [transaction](../../data/transactions-mfc-data-access.md) est un moyen pour le groupe ou le lot, une série de mises à jour à une source de données, tous les réussissent et sont validées en même temps ou (si l’une d’elles échoue), aucune n’est validée et toute la transaction est restaurée. Ce processus garantit l’intégrité du résultat sur la source de données.  
  
 OLE DB prend en charge les transactions avec les trois méthodes suivantes :  
  
-   [ITransactionLocal::StartTransaction](https://msdn.microsoft.com/en-us/library/ms709786.aspx)  
  
-   [ITransaction::Commit](https://msdn.microsoft.com/en-us/library/ms713008.aspx)  
  
-   [ITransaction::Abort](https://msdn.microsoft.com/en-us/library/ms709833.aspx)  
  
## <a name="relationship-of-sessions-and-transactions"></a>Relation des Sessions et des Transactions  
 Un objet de source de données unique peut créer un ou plusieurs objets de session, chacun d’eux peut être à l’intérieur ou à l’extérieur de l’étendue d’une transaction à un moment donné.  
  
 Lorsqu’une session n’entre pas une transaction, tout le travail effectué au cours de cette session sur le magasin de données est immédiatement validé sur chaque appel de méthode. (Cela est parfois en tant que le mode de validation automatique ou mode implicite.)  
  
 Lorsqu’une session entre une transaction, tout le travail effectué au cours de cette session sur le magasin de données fait partie de cette transaction est validé et abandonné comme une unité unique. (Cela est parfois appelé mode de validation manuelle.)  
  
 Prise en charge de la transaction est spécifique au fournisseur. Si le fournisseur que vous utilisez prend en charge les transactions, un objet de session qui prend en charge **ITransaction** et **ITransactionLocal** pouvez entrer un simple (c'est-à-dire, non imbriquée) transaction. La classe de modèles OLE DB [CSession](../../data/oledb/csession-class.md) prend en charge ces interfaces et est la méthode recommandée pour implémenter la prise en charge des transactions dans Visual C++.  
  
## <a name="starting-and-ending-the-transaction"></a>Début et fin de la Transaction  
 Vous appelez le `StartTransaction`, **valider**, et **abandonner** méthodes dans l’objet d’ensemble de lignes dans le consommateur.  
  
 Appel de **ITransactionLocal::StartTransaction** démarre une nouvelle transaction locale. Lorsque vous démarrez la transaction, les modifications éventuellement mandatées par les opérations suivantes ne sont pas effectivement appliquées au magasin de données jusqu'à ce que vous validez la transaction.  
  
 Appel de **ITransaction::Commit** ou **ITransaction::Abort** met fin à la transaction. **Valider** entraîne toutes les modifications dans la portée de la transaction à appliquer au magasin de données. **Abandonner** causes toutes les modifications dans la portée de la transaction doit être annulée et le magasin de données est laissé dans un état, il avaient avant le démarrage de la transaction.  
  
## <a name="nested-transactions"></a>Transactions imbriquées  
 A [imbriqués transaction](https://msdn.microsoft.com/en-us/library/ms716985.aspx) se produit lorsque vous démarrez une nouvelle transaction locale lors d’une transaction active existe déjà dans la session. La nouvelle transaction est démarrée en tant que transaction imbriquée sous la transaction en cours. Si le fournisseur ne prend pas en charge les transactions imbriquées, l’appel `StartTransaction` lorsqu’il existe déjà une transaction active sur la session retourne **XACT_E_XTIONEXISTS**.  
  
## <a name="distributed-transactions"></a>Transactions distribuées  
 Une transaction distribuée est une transaction qui met à jour des données distribuées ; Autrement dit, les données sur plusieurs systèmes informatiques. Si vous souhaitez prendre en charge des transactions sur un système distribué, vous devez utiliser le .NET Framework plutôt que la prise en charge des transactions OLE DB.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des accesseurs](../../data/oledb/using-accessors.md)