---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4183'
title: Avertissement du compilateur (niveau 1) C4183
ms.date: 11/04/2016
f1_keywords:
- C4183
helpviewer_keywords:
- C4183
ms.assetid: dc48312c-4b34-44dd-80ff-eb5f11d5ca47
ms.openlocfilehash: 1e9753637d0ee52ef40ce875e4e2d66fbdaab9db
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97266674"
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
