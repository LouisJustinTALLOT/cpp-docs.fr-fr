---
description: 'En savoir plus sur : erreur du compilateur C2572'
title: Erreur du compilateur C2572
ms.date: 11/04/2016
f1_keywords:
- C2572
helpviewer_keywords:
- C2572
ms.assetid: f1a42d69-727d-4ce5-88c8-d5f55dea66ac
ms.openlocfilehash: ff0549309df0567e2d1d7f26f98f95c3c3b629d5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97208955"
---
# <a name="compiler-error-c2572"></a>Erreur du compilateur C2572

'Class :: Member' : redéfinition du paramètre par défaut : paramètre param

Les paramètres par défaut ne peuvent pas être redéfinis. Si vous avez besoin d’une autre valeur pour le paramètre, le paramètre par défaut doit rester non défini.

L’exemple suivant génère l’C2572 :

```cpp
// C2572.cpp
// compile with: /c
void f(int i = 1);   // function declaration

// function definition
void f(int i = 1) {}   // C2572

// try the following line instead
// void f(int i) {}
```
