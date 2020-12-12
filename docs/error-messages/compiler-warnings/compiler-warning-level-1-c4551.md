---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4551'
title: Avertissement du compilateur (niveau 1) C4551
ms.date: 11/04/2016
f1_keywords:
- C4551
helpviewer_keywords:
- C4551
ms.assetid: 458b59bd-e2d7-425f-9ba6-268ff200424f
ms.openlocfilehash: 74a0f773f304c4ed4ce2da53a393a858f316c80b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97265946"
---
# <a name="compiler-warning-level-1-c4551"></a>Avertissement du compilateur (niveau 1) C4551

liste d’arguments manquante dans l’appel de fonction

Un appel de fonction doit inclure les parenthèses ouvrantes et fermantes après le nom de la fonction, même si la fonction n’accepte aucun paramètre.

L’exemple suivant génère l’C4551 :

```cpp
// C4551.cpp
// compile with: /W1
void function1() {
}

int main() {
   function1;   // C4551
   function1();   // OK
}
```
