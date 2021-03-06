---
description: 'En savoir plus sur : avertissement du compilateur (niveau 4) C4937'
title: Avertissement du compilateur (niveau 4) C4937
ms.date: 11/04/2016
f1_keywords:
- C4937
helpviewer_keywords:
- C4937
ms.assetid: 2bb9f0e7-bbd6-4697-84de-95955e32ae29
ms.openlocfilehash: fa614e9f93cf83afbe3ff46e624f13b5199a28d4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97251243"
---
# <a name="compiler-warning-level-4-c4937"></a>Avertissement du compilateur (niveau 4) C4937

impossible de distinguer 'text1' et 'text2' comme arguments de 'directive'

Compte tenu de la méthode utilisée par le compilateur pour traiter les arguments aux directives, il est impossible de différencier les noms qui ont une signification pour le compilateur, notamment les mots clés avec plusieurs représentations textuelles (formes à un ou deux traits de soulignement).

__Cdecl et _forceinline sont des exemples de ces chaînes \_ .  Sous /Za, notez que seules les formes à deux traits de soulignement sont activées.

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
