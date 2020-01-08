---
title: Erreur du compilateur C3005
ms.date: 11/04/2016
f1_keywords:
- C3005
helpviewer_keywords:
- C3005
ms.assetid: 30bad565-e79f-4c3f-82cb-a74bd0baab8f
ms.openlocfilehash: b260879dfafbe40ab13d14f7208f1ffbc90b9826
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302157"
---
# <a name="compiler-error-c3005"></a>Erreur du compilateur C3005

'error_text' : jeton inattendu rencontré dans la directive 'directive' OpenMP

Une directive OpenMP est incorrecte.

L’exemple suivant génère l’erreur C3005 :

```c
// C3005.c
// compile with: /openmp
int main()
{
   #pragma omp parallel + for   // C3005
}
```

L’erreur C3005 peut également se produire si vous insérez une accolade ouvrante sur la même ligne que le pragma.

```c
// C3005b.c
// compile with: /openmp
int main() {
   #pragma omp parallel {   // C3005 put open brace on next line
   lbl2:;
   }
   goto lbl2;
}
```
