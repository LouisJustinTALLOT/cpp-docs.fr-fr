---
title: Compilateur avertissement (niveau 4) C4718 | Documents Microsoft
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
ms.openlocfilehash: a92ab7a32babd181f282c799568e3a9dea436c49
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33294032"
---
# <a name="compiler-warning-level-4-c4718"></a>Avertissement du compilateur (niveau 4) C4718
'function call' : un appel récurrent n’a pas d’effets secondaires, suppression  
  
 Une fonction contient un appel récurrent, mais n’a pas d’effets secondaires. Un appel à cette fonction est en cours de suppression. L’exactitude du programme n’est pas affectée ; par contre, son comportement l’est. Si le fait de laisser l’appel peut provoquer une exception de dépassement de capacité de la pile d’exécution, la suppression de l’appel élimine ce risque.