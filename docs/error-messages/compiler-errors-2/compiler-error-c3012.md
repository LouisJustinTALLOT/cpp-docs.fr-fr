---
title: Erreur du compilateur C3012
ms.date: 11/04/2016
f1_keywords:
- C3012
helpviewer_keywords:
- C3012
ms.assetid: cc7040b1-b3fb-4da6-a474-877914d30332
ms.openlocfilehash: 69f0544815804e9827631be81bf9735a95bd1a22
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80176700"
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
