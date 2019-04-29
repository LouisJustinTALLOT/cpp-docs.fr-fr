---
title: Erreur du compilateur C2808
ms.date: 11/04/2016
f1_keywords:
- C2808
helpviewer_keywords:
- C2808
ms.assetid: 3d745102-d3b3-4735-a7d2-ad42d5bf3cfa
ms.openlocfilehash: 84135288255c806e644e153a4d8f678fc13d2787
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62281883"
---
# <a name="compiler-error-c2808"></a>Erreur du compilateur C2808

l’opérateur unaire 'operator opérateur' a trop de paramètres formels

L’opérateur unaire possède une liste de paramètres non ' void '.

L’exemple suivant génère l’erreur C2808 :

```
// C2808.cpp
// compile with: /c
class X {
public:
   X operator! ( X );   // C2808 nonvoid parameter list
   X operator! ( void );   // OK
};
```