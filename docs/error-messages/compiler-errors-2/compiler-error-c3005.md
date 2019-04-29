---
title: Erreur du compilateur C3005
ms.date: 11/04/2016
f1_keywords:
- C3005
helpviewer_keywords:
- C3005
ms.assetid: 30bad565-e79f-4c3f-82cb-a74bd0baab8f
ms.openlocfilehash: 1303fd667c92af6fd8d0476da9468b4c7d090e6b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62350739"
---
# <a name="compiler-error-c3005"></a>Erreur du compilateur C3005

'error_text' : jeton inattendu rencontré dans la directive 'directive' OpenMP

Une directive OpenMP est incorrecte.

L’exemple suivant génère l’erreur C3005 :

```
// C3005.c
// compile with: /openmp
int main()
{
   #pragma omp parallel + for   // C3005
}
```

L’erreur C3005 peut également se produire si vous insérez une accolade ouvrante sur la même ligne que le pragma.

```
// C3005b.c
// compile with: /openmp
int main() {
   #pragma omp parallel {   // C3005 put open brace on next line
   lbl2:;
   }
   goto lbl2;
}
```