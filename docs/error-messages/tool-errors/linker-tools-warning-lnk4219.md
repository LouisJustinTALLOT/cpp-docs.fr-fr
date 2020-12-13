---
description: 'En savoir plus sur les éléments suivants : avertissement des outils Éditeur de liens LNK4219'
title: Avertissement des outils Éditeur de liens LNK4219
ms.date: 11/04/2016
f1_keywords:
- LNK4219
helpviewer_keywords:
- LNK4219
ms.assetid: 363fedf4-b10c-4985-811a-55a9fba688d6
ms.openlocfilehash: 2d9e720ba358b109aca1ade634009985e83974be
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97150577"
---
# <a name="linker-tools-warning-lnk4219"></a>Avertissement des outils Éditeur de liens LNK4219

dépassement de la correction du nom de la correction. La cible’target Symbol Name’est hors limites, insertion du thunk

L’éditeur de liens a inséré un thunk dans une situation où l’adresse ou le décalage n’a pas pu tenir dans l’instruction donnée, car le symbole cible est trop éloigné de l’emplacement de l’instruction.

Vous pouvez réorganiser l’image (à l’aide de l’option [/Order](../../build/reference/order-put-functions-in-order.md) , par exemple) pour éviter le niveau supplémentaire d’indirection.
