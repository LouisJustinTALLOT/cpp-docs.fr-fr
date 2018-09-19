---
title: Compilateur avertissement (niveau 1) C4391 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4391
dev_langs:
- C++
helpviewer_keywords:
- C4391
ms.assetid: 95c6182c-fae9-4174-8f7b-98aa352e68ca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d0b3873beb635afe81cee3030a78d2b1223197a7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46047083"
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