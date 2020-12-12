---
description: 'En savoir plus sur : erreur du compilateur C3003'
title: Erreur du compilateur C3003
ms.date: 11/04/2016
f1_keywords:
- C3003
helpviewer_keywords:
- C3003
ms.assetid: 22e74f99-bb7f-4518-ab0d-934d5d49bcc7
ms.openlocfilehash: 1bed98ebd9e0a383700583e1e23e0a977cb6e3fc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97326041"
---
# <a name="compiler-error-c3003"></a>Erreur du compilateur C3003

'directive' : nom de directive OpenMP non autorisé après des clauses de directive

Un nom de directive OpenMP ne peut pas suivre une clause de directive OpenMP.

L’exemple suivant génère l’erreur C3003 :

```c
// C3003.c
// compile with: /openmp
int main()
{
   int x, y, z;
   #pragma omp parallel shared(x, y, z) for   // C3003
}
```
