---
description: 'En savoir plus sur : erreur du compilateur C3058'
title: Erreur du compilateur C3058
ms.date: 11/04/2016
f1_keywords:
- C3058
helpviewer_keywords:
- C3058
ms.assetid: 669d08c8-0b58-4351-88aa-c6e6e1af481c
ms.openlocfilehash: 9a7c4c3fa4fd8186055985ff66caa3ffd0c4f081
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97269456"
---
# <a name="compiler-error-c3058"></a>Erreur du compilateur C3058

'symbol' : symbole non déclaré en tant que 'threadprivate' avant d’être utilisé dans la clause 'copyin'

Un symbole doit d’abord être déclaré en tant que [threadprivate](../../parallel/openmp/reference/openmp-directives.md#threadprivate) avant de pouvoir être utilisé dans une clause [copyin](../../parallel/openmp/reference/openmp-clauses.md#copyin) .

L’exemple suivant génère l’erreur C3058 :

```cpp
// C3058.cpp
// compile with: /openmp
int x, y, z;
#pragma omp threadprivate(x, z)

void test() {
   #pragma omp parallel copyin(x, y)   // C3058
   {
   }
}
```

Solution possible :

```cpp
// C3058b.cpp
// compile with: /openmp /LD
int x, y, z;
#pragma omp threadprivate(x, y)

void test() {
   #pragma omp parallel copyin(x, y)
   {
   }
}
```
