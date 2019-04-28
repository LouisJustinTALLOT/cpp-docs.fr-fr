---
title: Erreur du compilateur C2770
ms.date: 11/04/2016
f1_keywords:
- C2770
helpviewer_keywords:
- C2770
ms.assetid: 100001b5-80b0-4971-8ff6-9023f443c926
ms.openlocfilehash: 9397b52838f61449f0475a31d5bb4077dad7f587
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62257399"
---
# <a name="compiler-error-c2770"></a>Erreur du compilateur C2770

argument (s) template_ou_génériques explicite non valide pour 'template'

Candidats de modèle de fonction avec modèle explicit ou arguments génériques a entraîné des types de fonction non autorisés.

L’exemple suivant génère l’erreur C2770 :

```
// C2770.cpp
#include <stdio.h>
template <class T>
int f(typename T::B*);   // expects type with member B

struct Err {};

int main() {
   f<int>(0);   // C2770 int has no B
   // try the following line instead
   f<OK>(0);
}
```