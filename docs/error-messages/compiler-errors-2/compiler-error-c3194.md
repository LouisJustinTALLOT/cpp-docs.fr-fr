---
title: Erreur du compilateur C3194
ms.date: 11/04/2016
f1_keywords:
- C3194
helpviewer_keywords:
- C3194
ms.assetid: 49d3ffc6-eff6-4b46-865b-18811692a8bb
ms.openlocfilehash: 83c07da5383740ca14c9b9de6224f47cf844d5fa
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757642"
---
# <a name="compiler-error-c3194"></a>Erreur du compilateur C3194

'membre' : un type valeur ne peut pas avoir d’opérateur d’assignation

Les fonctions membres spéciales qui requièrent l’appel automatique par le compilateur, comme un constructeur de copie ou un opérateur d’assignation de copie, ne sont pas prises en charge dans une classe value.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C3194.

```cpp
// C3194.cpp
// compile with: /clr /c
value struct MyStruct {
   MyStruct& operator= (const MyStruct& i) { return *this; }   // C3194
};

ref struct MyStruct2 {
   MyStruct2% operator= (const MyStruct2% i) { return *this; }   // OK
};
```
