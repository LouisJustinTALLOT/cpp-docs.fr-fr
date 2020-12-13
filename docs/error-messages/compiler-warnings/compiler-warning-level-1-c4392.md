---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4392'
title: Avertissement du compilateur (niveau 1) C4392
ms.date: 11/04/2016
f1_keywords:
- C4392
helpviewer_keywords:
- C4392
ms.assetid: 817806ad-06a6-4b9e-8355-e25687c782dc
ms.openlocfilehash: d10b966f6727ec3461255d3789a6e9a7aed78c22
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339889"
---
# <a name="compiler-warning-level-1-c4392"></a>Avertissement du compilateur (niveau 1) C4392

'signature' : nombre d’arguments incorrect pour la fonction intrinsèque, 'nombre’arguments attendus

Une déclaration de fonction pour un intrinsèque du compilateur a un nombre incorrect d’arguments. L’image résultante peut ne pas s’exécuter correctement.

Pour résoudre cet avertissement, corrigez la déclaration ou supprimez la déclaration et #include simplement le fichier d’en-tête approprié.

L’exemple suivant génère l’C4392 :

```cpp
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
