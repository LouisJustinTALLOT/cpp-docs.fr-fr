---
title: Compilateur avertissement (niveau 4) C4718 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4718
dev_langs:
- C++
helpviewer_keywords:
- C4718
ms.assetid: 29507f8a-b024-42c1-a3b8-f35d1f2641f3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8736902f4c3a1cfac7313806fde65d1b253716b3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46054231"
---
# <a name="compiler-warning-level-4-c4718"></a>Avertissement du compilateur (niveau 4) C4718

'function call' : un appel récurrent n’a pas d’effets secondaires, suppression

Une fonction contient un appel récurrent, mais n’a pas d’effets secondaires. Un appel à cette fonction est en cours de suppression. L’exactitude du programme n’est pas affectée ; par contre, son comportement l’est. Si le fait de laisser l’appel peut provoquer une exception de dépassement de capacité de la pile d’exécution, la suppression de l’appel élimine ce risque.