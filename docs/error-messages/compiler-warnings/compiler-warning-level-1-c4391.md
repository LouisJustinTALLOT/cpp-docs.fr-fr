---
title: Avertissement du compilateur (niveau 1) C4391
ms.date: 11/04/2016
f1_keywords:
- C4391
helpviewer_keywords:
- C4391
ms.assetid: 95c6182c-fae9-4174-8f7b-98aa352e68ca
ms.openlocfilehash: d9d1cebe08a6a163d76271ab001ec91b7cee82a2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50567126"
---
# <a name="compiler-warning-level-1-c4391"></a>Avertissement du compilateur (niveau 1) C4391

'signature' : type de retour incorrect pour la fonction intrinsèque, le 'type' attendu

Une déclaration de fonction pour intrinsèque du compilateur a le type de retour incorrect. L’image résultante peut ne pas fonctionne correctement.

Pour résoudre cet avertissement, corrigez la déclaration ou supprimez la déclaration et simplement #include du fichier d’en-tête approprié.

L’exemple suivant génère l’erreur C4391 :

```
// C4391.cpp
// compile with: /W1
// processor: x86
// uncomment the following line and delete the line that
// generated the warning to resolve
// #include "xmmintrin.h"

#ifdef  __cplusplus
extern "C" {
#endif

extern void _mm_load_ss(float *p);   // C4391

#ifdef  __cplusplus
}
#endif

int main()
{
}
```