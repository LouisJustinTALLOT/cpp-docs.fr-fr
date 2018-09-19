---
title: Erreur du compilateur C2439 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2439
dev_langs:
- C++
helpviewer_keywords:
- C2439
ms.assetid: 3c5dbe5c-b7d3-4bb0-8619-92f6e280461e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 419bf7be45a1383135d0231cd059837e1fe62729
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46058410"
---
# <a name="compiler-error-c2439"></a>Erreur du compilateur C2439

'identificateur' : membre n’a pas pu être initialisé.

Une classe, une structure ou un membre d’union ne peut pas être initialisé.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes

1. Tente d’initialiser une classe de base indirecte ou une structure.

1. Tentative d’initialiser un membre hérité d’une classe ou structure. Un membre hérité doit être initialisé par le constructeur de la classe ou structure.