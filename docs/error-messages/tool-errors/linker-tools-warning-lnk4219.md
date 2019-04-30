---
title: Avertissement des outils Éditeur de liens LNK4219
ms.date: 11/04/2016
f1_keywords:
- LNK4219
helpviewer_keywords:
- LNK4219
ms.assetid: 363fedf4-b10c-4985-811a-55a9fba688d6
ms.openlocfilehash: 7407537b55525bf622fc11cdbdb8e00244e51c18
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410250"
---
# <a name="linker-tools-warning-lnk4219"></a>Avertissement des outils Éditeur de liens LNK4219

dépassement de la correction nom correction. Cible 'nom de symbole cible' est hors limites, insertion du thunk

L’éditeur de liens a inséré un thunk dans une situation où l’adresse ou le décalage n’a pas pu être contenue dans l’instruction donnée parce que le symbole cible est trop loin à partir de l’emplacement de l’instruction.

Vous pouvez souhaiter de réorganiser l’image (à l’aide de la [/Order](../../build/reference/order-put-functions-in-order.md) option, par exemple) afin d’éviter le niveau supplémentaire d’indirection.