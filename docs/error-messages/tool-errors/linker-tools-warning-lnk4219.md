---
title: Avertissement LNK4219 des outils Éditeur de liens | Microsoft Docs
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
ms.openlocfilehash: daf097cd8715a7c523e6e8a2ea46714481ca7d2a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46105206"
---
# <a name="linker-tools-warning-lnk4219"></a>Avertissement des outils Éditeur de liens LNK4219

dépassement de la correction nom correction. Cible 'nom de symbole cible' est hors limites, insertion du thunk

L’éditeur de liens a inséré un thunk dans une situation où l’adresse ou le décalage n’a pas pu être contenue dans l’instruction donnée parce que le symbole cible est trop loin à partir de l’emplacement de l’instruction.

Vous pouvez souhaiter de réorganiser l’image (à l’aide de la [/Order](../../build/reference/order-put-functions-in-order.md) option, par exemple) afin d’éviter le niveau supplémentaire d’indirection.