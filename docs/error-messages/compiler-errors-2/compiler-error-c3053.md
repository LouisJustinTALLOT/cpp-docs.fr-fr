---
description: 'En savoir plus sur : erreur du compilateur C3053'
title: Erreur du compilateur C3053
ms.date: 11/04/2016
f1_keywords:
- C3053
helpviewer_keywords:
- C3053
ms.assetid: ab9a25f3-e341-4f6e-8e69-069b4a963a64
ms.openlocfilehash: 8f42d3301ae5980942d33cefc90c74a5a0d39b16
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97269625"
---
# <a name="compiler-error-c3053"></a>Erreur du compilateur C3053

'symbole' : 'threadprivate' n’est valide que pour les éléments de données global ou static

Les symboles passés à [threadprivate](../../parallel/openmp/reference/openmp-directives.md#threadprivate) doivent être de type global ou static.

L’exemple suivant génère l’erreur C3053 :

```cpp
// C3053.cpp
// compile with: /openmp
void Test() {
   int x, y;
   #pragma omp threadprivate(x, y)   // C3053
   #pragma omp parallel copyin(x, y)
   {
      x = y;
   }
}
```

Solution possible :

```cpp
// C3053b.cpp
// compile with: /openmp /LD
int x, y;
#pragma omp threadprivate(x, y)

void Test() {
   #pragma omp parallel copyin(x, y)
   {
      x = y;
   }
}
```
