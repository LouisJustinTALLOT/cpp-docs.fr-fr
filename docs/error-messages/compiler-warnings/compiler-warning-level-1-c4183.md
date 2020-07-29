---
title: Avertissement du compilateur (niveau 1) C4183
ms.date: 11/04/2016
f1_keywords:
- C4183
helpviewer_keywords:
- C4183
ms.assetid: dc48312c-4b34-44dd-80ff-eb5f11d5ca47
ms.openlocfilehash: cff62c18442cd6d55a9444bb86944b691145b9fe
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231921"
---
# <a name="compiler-warning-level-1-c4183"></a>Avertissement du compilateur (niveau 1) C4183

'identificateur' : type de retour manquant ; supposé être une fonction membre qui retourne’int'

La définition Inline d’une fonction membre dans une classe ou une structure n’a pas de type de retour. Cette fonction membre est supposée avoir un type de retour par défaut **`int`** .

L’exemple suivant génère l’C4183 :

```cpp
// C4183.cpp
// compile with: /W1 /c
#pragma warning(disable : 4430)
class MyClass1;
class MyClass2 {
   MyClass1() {};   // C4183
};
```
