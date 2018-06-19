---
title: Compilateur avertissement (niveaux 2 et 3) C4008 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4008
dev_langs:
- C++
helpviewer_keywords:
- C4008
ms.assetid: fb45e535-cb68-4743-80e9-a6e34cfffeca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4cdc88f222f9e5ce3829a63c131c955ce2abdd7d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33294256"
---
# <a name="compiler-warning-levels-2-and-3-c4008"></a>Avertissement du compilateur (niveaux 2 et 3) C4008
'identifier' : 'attribute' attribut ignoré  
  
 Le compilateur a ignoré l’attribut `__fastcall`, **static**ou **inline** pour une fonction (avertissement de niveau 3) ou des données (avertissement de niveau 2).  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes  
  
1.  Attribut`__fastcall` avec des données.  
  
2.  Attribut**static** ou **inline** avec la fonction **main** .