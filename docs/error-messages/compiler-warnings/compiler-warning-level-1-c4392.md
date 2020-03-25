---
title: Avertissement du compilateur (niveau 1) C4392
ms.date: 11/04/2016
f1_keywords:
- C4392
helpviewer_keywords:
- C4392
ms.assetid: 817806ad-06a6-4b9e-8355-e25687c782dc
ms.openlocfilehash: a62bfdb6b9b29abf047e7690179978cb9516d477
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186879"
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
