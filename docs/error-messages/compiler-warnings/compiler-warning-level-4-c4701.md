---
title: Compilateur avertissement (niveau 4) C4701 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4701
dev_langs:
- C++
helpviewer_keywords:
- C4701
ms.assetid: d7c76c66-1f3f-4d3c-abe4-5d94c84a5a1f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c48df2f4ac3d5aad4ae82abf76dab4d96e8af89a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33293947"
---
# <a name="compiler-warning-level-4-c4701"></a>Avertissement du compilateur (niveau 4) C4701
variable locale potentiellement non initialisée 'name' utilisé  
  
 La variable locale *nom* a peut-être été utilisé sans assignée une valeur. Cela peut entraîner des résultats imprévisibles.  
  
## <a name="example"></a>Exemple  
 Le code suivant génère C4701 et C4703.  
  
```cpp  
#include <malloc.h>  
  
void func(int size)  
{  
    void* p;  
    if (size < 256) {  
        p = malloc(size);  
    }  
  
    if (p != nullptr) // C4701 and C4703  
        free(p);  
}  
  
void main()  
{  
    func(9);  
}  
```  
  
```Output  
c:\src\test.cpp(10) : warning C4701: potentially uninitialized local variable 'p' used  
c:\src\test.cpp(10) : warning C4703: potentially uninitialized local pointer variable 'p' used  
  
```  
  
 Pour corriger cet avertissement, initialisez la variable comme indiqué dans cet exemple :  
  
```cpp  
#include <malloc.h>  
  
void func(int size)  
{  
    void* p = nullptr;  
    if (size < 256) {  
        p = malloc(size);  
    }  
  
    if (p != nullptr)  
        free(p);  
}  
  
void main()  
{  
    func(9);  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Compilateur avertissement (niveau 4) C4703](../../error-messages/compiler-warnings/compiler-warning-level-4-c4703.md)   
 [Avertissements, /sdl et amélioration de la détection des variable non initialisées](http://blogs.msdn.com/b/sdl/archive/2012/06/06/warnings-sdl-and-improving-uninitialized-variable-detection.aspx)