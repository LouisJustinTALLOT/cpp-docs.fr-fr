---
title: Du compilateur (niveau 3) d’avertissement C4316 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4316
dev_langs:
- C++
helpviewer_keywords:
- C4316
ms.assetid: 10371f01-aeb8-40ac-a290-59e63efa5ad4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 609f3bbe9f338c5d53491190512ce2b9c290cdb8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33298380"
---
# <a name="compiler-warning-level-3-c4316"></a>Du compilateur (niveau 3) d’avertissement C4316
Objet alloué sur le tas ne peut pas être alignée pour ce type.  
  
 Un objet aligné de manière excessive alloué à l’aide de `operator new` ne peut pas avoir l’alignement spécifié. Substituer [new, opérateur](../../c-runtime-library/operator-new-crt.md) et [opérateur delete](../../c-runtime-library/operator-delete-crt.md) pour types alignés trop forte afin qu’ils utilisent les routines d’allocation alignée — par exemple, [_aligned_malloc](../../c-runtime-library/reference/aligned-malloc.md) et [_aligned_free](../../c-runtime-library/reference/aligned-free.md). L’exemple suivant génère C4316 :  
  
```cpp  
// C4316.cpp  
// Test: cl /W3 /c C4316.cpp  
  
__declspec(align(32)) struct S {}; // C4324  
  
int main() {  
    new S; // C4316  
}  
```