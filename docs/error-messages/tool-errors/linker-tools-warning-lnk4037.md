---
title: LNK4037 d’avertissement des outils Éditeur de liens | Documents Microsoft
ms.custom: ''
ms.date: 10/04/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4037
dev_langs:
- C++
helpviewer_keywords:
- LNK4037
ms.assetid: 9ba02fd3-b04f-4679-bab9-26fa82cf09bb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6b87f0a415d6ae7d282e29c2ca67fda043c2a901
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33302433"
---
# <a name="linker-tools-warning-lnk4037"></a>Outils de l’éditeur de liens LNK4037 d’avertissement

>'*symbole*' n’existe pas ; ignoré

Le nom décoré *symbole* n’a pas pu être trié à l’aide de la [/Order](../../build/reference/order-put-functions-in-order.md) option car il n’a pas trouvé dans le programme. Vérifiez la spécification de *symbole* dans le fichier de réponse de commande. Pour plus d’informations, consultez la [/ORDER (Put des fonctions dans l’ordre)](../../build/reference/order-put-functions-in-order.md) option de l’éditeur de liens.

> [!NOTE]
> LIEN ne peut pas classer les fonctions statiques car les noms de fonctions statiques ne sont pas des noms de symboles publics. Lorsque **/Order** est spécifié, l’éditeur de liens en cet avertissement est généré pour chaque symbole dans le fichier de réponse de commande qui est soit statique ou introuvable.