---
description: 'En savoir plus sur : erreur du compilateur C2594'
title: Erreur du compilateur C2594
ms.date: 11/04/2016
f1_keywords:
- C2594
helpviewer_keywords:
- C2594
ms.assetid: 68cd708f-266e-44b0-a211-3e3ab63b11bf
ms.openlocfilehash: 972fb58624a7f2ba185c34f2e58fd9f2dc15217d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97120150"
---
# <a name="compiler-error-c2594"></a>Erreur du compilateur C2594

'opérateur' : conversions ambiguës de’type1 'en’type2 '

Aucune conversion de *type1* en *type2* n’était plus directe que les autres. Nous vous suggérons deux solutions possibles pour convertir de *type1* en *type2*. La première option consiste à définir une conversion directe de *type1* en *type2*, et la deuxième option est de spécifier une séquence de conversions de *type1* en *type2*.

L’exemple suivant génère l’C2594. La résolution suggérée à l’erreur est une séquence de conversions :

```cpp
// C2594.cpp
// compile with: /c
struct A{};
struct I1 : A {};
struct I2 : A {};
struct D : I1, I2 {};

A *f (D *p) {
   return (A*) (p);    // C2594

// try the following line instead
// return static_cast<A *>(static_cast<I1 *>(p));
}
```
