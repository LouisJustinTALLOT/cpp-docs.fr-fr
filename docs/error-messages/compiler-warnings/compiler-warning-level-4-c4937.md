---
title: Compilateur avertissement (niveau 4) C4937 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4937
dev_langs:
- C++
helpviewer_keywords:
- C4937
ms.assetid: 2bb9f0e7-bbd6-4697-84de-95955e32ae29
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e7bc6232458b357f41e859c58d4b6b77f78ef2a7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118295"
---
# <a name="compiler-warning-level-4-c4937"></a>Avertissement du compilateur (niveau 4) C4937

impossible de distinguer 'text1' et 'text2' comme arguments de 'directive'

Compte tenu de la méthode utilisée par le compilateur pour traiter les arguments aux directives, il est impossible de différencier les noms qui ont une signification pour le compilateur, notamment les mots clés avec plusieurs représentations textuelles (formes à un ou deux traits de soulignement).

Exemples de ces chaînes sont __cdecl et \__forceinline.  Sous /Za, notez que seules les formes à deux traits de soulignement sont activées.

L’exemple suivant génère l’avertissement C4937 :

```
// C4937.cpp
// compile with: /openmp /W4
#include "omp.h"
int main() {
   #pragma omp critical ( __leave )   // C4937
   ;

   // OK
   #pragma omp critical ( leave )
   ;
}
```