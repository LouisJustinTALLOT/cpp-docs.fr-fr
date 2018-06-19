---
title: Compilateur avertissement (niveau 1) C4561 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4561
dev_langs:
- C++
helpviewer_keywords:
- C4561
ms.assetid: 3a10c12c-601b-4b6c-9861-331fd022e021
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d4862d7f570faea3e362a505e67bddaf504b32de
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33280529"
---
# <a name="compiler-warning-level-1-c4561"></a>Avertissement du compilateur (niveau 1) C4561
'__fastcall' incompatible avec le ' / clr' option : conversion en '\__stdcall'  
  
 Le [__fastcall](../../cpp/fastcall.md) convention d’appel de fonction ne peut pas être utilisée avec le [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) option du compilateur. Le compilateur ignore les appels à `__fastcall`. Pour résoudre cet avertissement, supprimez les appels à **__fastcall** ou compilez sans **/CLR**.  
  
 L’exemple suivant génère C4561 :  
  
```  
// C4561.cpp  
// compile with: /clr /W1 /c  
// processor: x86  
void __fastcall Func(void *p);   // C4561, remove __fastcall to resolve  
```