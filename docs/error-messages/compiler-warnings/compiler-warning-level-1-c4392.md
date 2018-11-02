---
title: Avertissement du compilateur (niveau 1) C4392
ms.date: 11/04/2016
f1_keywords:
- C4392
helpviewer_keywords:
- C4392
ms.assetid: 817806ad-06a6-4b9e-8355-e25687c782dc
ms.openlocfilehash: 1dc0c546509b17132358f432f6a781035a314a72
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50472200"
---
# <a name="compiler-warning-level-1-c4392"></a>Avertissement du compilateur (niveau 1) C4392

'signature' : nombre incorrect d’arguments de fonction intrinsèque, attendu 'nombre' arguments

Une déclaration de fonction pour intrinsèque du compilateur avait un nombre incorrect d’arguments. L’image résultante peut ne pas fonctionne correctement.

Pour résoudre cet avertissement, corrigez la déclaration ou supprimez la déclaration et simplement #include du fichier d’en-tête approprié.

L’exemple suivant génère l’erreur C4392 :

```
// C4392.cpp
// compile with: /W1
// processor: x86
// uncomment the following line and delete the line that
// generated the warning to resolve
// #include "xmmintrin.h"

#ifdef  __cplusplus
extern "C" {
#endif

extern void _mm_stream_pd(double *dp);   // C4392

#ifdef  __cplusplus
}
#endif

int main()
{
}
```