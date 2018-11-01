---
title: Erreur du compilateur C2970
ms.date: 11/04/2016
f1_keywords:
- C2970
helpviewer_keywords:
- C2970
ms.assetid: 21d90348-20d3-438c-b278-efdbfb93a7d2
ms.openlocfilehash: 425d1bf50d56c4455ccd9292b300e744625d34c7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50638410"
---
# <a name="compiler-error-c2970"></a>Erreur du compilateur C2970

'classe' : paramètre de modèle 'param' : 'arg' : une expression impliquant des objets avec une liaison interne ne peut pas être utilisée comme argument sans type

Vous ne pouvez pas utiliser le nom ou l’adresse d’une variable statique comme argument de modèle. La classe de modèle attend une valeur const pouvant être évaluée au moment de la compilation.

L’exemple suivant génère C2970 :

```
// C2970.cpp
// compile with: /c
static int si;
// could declare nonstatic to resolve all errors
// int si;

template <int i>
class X {};

template <int *pi>
class Y {};

X<si> anX;   // C2970 cannot use static variable in templates

// this would also work
const int i = 10;
X<i> anX2;
```