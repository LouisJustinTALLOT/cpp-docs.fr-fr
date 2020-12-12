---
description: 'En savoir plus sur : erreur du compilateur C3012'
title: Erreur du compilateur C3012
ms.date: 11/04/2016
f1_keywords:
- C3012
helpviewer_keywords:
- C3012
ms.assetid: cc7040b1-b3fb-4da6-a474-877914d30332
ms.openlocfilehash: fff986a984acb62f770d02ff2b7b08c40e8511e3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97286005"
---
# <a name="compiler-error-c3012"></a>Erreur du compilateur C3012

> '*intrinsic*' : fonction intrinsèque non autorisée directement dans une région parallèle

Une fonction [intrinsèque du compilateur](../../intrinsics/compiler-intrinsics.md) n’est pas autorisée dans une région `omp parallel` . Pour résoudre ce problème, déplacez des intrinsèques hors de la région ou remplacez-les par des équivalents non intrinsèques.

## <a name="example"></a>Exemple

L’exemple suivant génère C3012 et montre une façon de le corriger :

```cpp
// C3012.cpp
// compile with: /openmp
#ifdef __cplusplus
extern "C" {
#endif
void* _ReturnAddress();
#ifdef __cplusplus
}
#endif

int main()
{
   #pragma omp parallel
   {
      _ReturnAddress();   // C3012
   }
   _ReturnAddress();      // OK
}
```
