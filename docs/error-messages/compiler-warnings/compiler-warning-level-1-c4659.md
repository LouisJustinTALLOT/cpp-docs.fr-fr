---
title: Compilateur avertissement (niveau 1) C4659 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4659
dev_langs:
- C++
helpviewer_keywords:
- C4659
ms.assetid: e29ba8db-7917-43f6-8e34-868b752279ae
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 643b599cd11d0935f1769ad37dca4e764f0418e6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33285614"
---
# <a name="compiler-warning-level-1-c4659"></a>Avertissement du compilateur (niveau 1) C4659
\#pragma 'pragma' : utilisation du segment réservé 'segment' a un comportement indéfini, utilisez #pragma comment (linker,...)  
  
 L’option .drectve a été utilisée pour passer d’une option à l’éditeur de liens. Utilisez à la place de pragma [commentaire](../../preprocessor/comment-c-cpp.md) pour passer une option de l’éditeur de liens.  
  
```  
// C4659.cpp  
// compile with: /W1 /LD  
#pragma code_seg(".drectve")   // C4659  
```