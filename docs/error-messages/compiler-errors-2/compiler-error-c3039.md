---
title: Erreur du compilateur C3039 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3039
dev_langs:
- C++
helpviewer_keywords:
- C3039
ms.assetid: 02776f16-f57a-4ffd-b7f7-9c696b633e08
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1b225103cf45331688a65d4528cadb39e730c75c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46098093"
---
# <a name="compiler-error-c3039"></a>Erreur du compilateur C3039

'var' : la variable d’index de l’instruction 'for' OpenMP ne peut pas être une variable de réduction

Une variable d’index est implicitement privée. Elle ne peut donc pas être utilisée dans une clause [reduction](../../parallel/openmp/reference/reduction.md) dans la directive [parallel](../../parallel/openmp/reference/parallel.md) englobante.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3039 :

```
// C3039.cpp
// compile with: /openmp /c
int g_i;

int main() {
   int i;

   #pragma omp parallel reduction(+: i)
   {
      #pragma omp for
      for (i = 0; i < 10; ++i)   // C3039
         g_i += i;
   }
}
```