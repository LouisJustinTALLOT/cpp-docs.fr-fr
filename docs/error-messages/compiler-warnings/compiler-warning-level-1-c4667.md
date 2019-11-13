---
title: Avertissement du compilateur (niveau 1) C4667
ms.date: 11/04/2016
f1_keywords:
- C4667
helpviewer_keywords:
- C4667
ms.assetid: 5d2b7fe0-4f0e-4cd6-b432-ca02c3d194ab
ms.openlocfilehash: 9ae0d5cdcc1f6cca25f55cd1d7c03cc345c39e5e
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051394"
---
# <a name="compiler-warning-level-1-c4667"></a>Avertissement du compilateur (niveau 1) C4667

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