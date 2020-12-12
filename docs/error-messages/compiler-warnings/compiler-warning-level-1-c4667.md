---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4667'
title: Avertissement du compilateur (niveau 1) C4667
ms.date: 11/04/2016
f1_keywords:
- C4667
helpviewer_keywords:
- C4667
ms.assetid: 5d2b7fe0-4f0e-4cd6-b432-ca02c3d194ab
ms.openlocfilehash: 3646cdd38f66ea5154ff89d96334e9848fb48678
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97318739"
---
# <a name="compiler-warning-level-1-c4667"></a>Avertissement du compilateur (niveau 1) C4667

'fonction' : aucun modèle de fonction défini correspondant à l’instanciation forcée

Vous ne pouvez pas instancier un modèle de fonction qui n’a pas été déclaré.

L’exemple suivant entraîne l’C4667 :

```cpp
// C4667a.cpp
// compile with: /LD /W1
template
void max(const int &, const int &); // C4667 expected
```

Pour éviter cet avertissement, commencez par déclarer le modèle de fonction :

```cpp
// C4667b.cpp
// compile with: /LD
// Declare the function template
template<typename T>
const T &max(const T &a, const T &b) {
   return (a > b) ? a : b;
}
// Then forcibly instantiate it with a desired type ... i.e. 'int'
//
template
const int &max(const int &, const int &);
```
