---
title: LNK4219 d’avertissement des outils Éditeur de liens | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4219
dev_langs:
- C++
helpviewer_keywords:
- LNK4219
ms.assetid: 363fedf4-b10c-4985-811a-55a9fba688d6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 59cb7376957b7985b7ae2335ea472171d490ff42
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33301133"
---
# <a name="linker-tools-warning-lnk4219"></a>Avertissement des outils Éditeur de liens LNK4219
dépassement de la correction nom correction. Cible 'nom de symbole cible' est hors limites, insertion du thunk  
  
 L’éditeur de liens a inséré un thunk dans une situation où l’adresse ou le décalage n’a pas pu être contenue dans l’instruction donnée parce que le symbole cible est trop loin à partir de l’emplacement de l’instruction.  
  
 Vous pouvez souhaiter réorganiser l’image (à l’aide de la [/Order](../../build/reference/order-put-functions-in-order.md) option, par exemple) pour éviter le niveau supplémentaire d’indirection.