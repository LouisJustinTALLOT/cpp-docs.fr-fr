---
title: Compilateur avertissement (niveau 1) C4180 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4180
dev_langs:
- C++
helpviewer_keywords:
- C4180
ms.assetid: 40c91bd4-37f1-4d59-a4f3-d5ddab68239b
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: 993bb017e92fbc26f8bf8e97dda7dbe1a8f24285
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-level-1-c4180"></a>Avertissement du compilateur (niveau 1) C4180
qualificateur appliqué au type fonction n'a pas de sens ; ignoré  
  
 Un qualificateur, tel que **const**, est appliqué à un type de fonction défini par `typedef`.  
  
## <a name="example"></a>Exemple  
  
```  
// C4180.cpp  
// compile with: /W1 /c  
typedef int FuncType(void);  
  
// the const qualifier cannot be applied to the  
// function type FuncType  
const FuncType f;   // C4180  
```
