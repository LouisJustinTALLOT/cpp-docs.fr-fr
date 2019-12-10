---
title: Avertissement du compilateur (niveau 4) C4937
ms.date: 11/04/2016
f1_keywords:
- C4937
helpviewer_keywords:
- C4937
ms.assetid: 2bb9f0e7-bbd6-4697-84de-95955e32ae29
ms.openlocfilehash: dd7a7f9ac3d0ce0798a88f753cb0ccb4addbd5bc
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988758"
---
# <a name="compiler-warning-level-4-c4937"></a>Avertissement du compilateur (niveau 4) C4937

impossible de distinguer 'text1' et 'text2' comme arguments de 'directive'

Compte tenu de la méthode utilisée par le compilateur pour traiter les arguments aux directives, il est impossible de différencier les noms qui ont une signification pour le compilateur, notamment les mots clés avec plusieurs représentations textuelles (formes à un ou deux traits de soulignement).

__Cdecl et \__forceinline sont des exemples de ces chaînes.  Sous /Za, notez que seules les formes à deux traits de soulignement sont activées.

L’exemple suivant génère l’avertissement C4937 :

```cpp
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
