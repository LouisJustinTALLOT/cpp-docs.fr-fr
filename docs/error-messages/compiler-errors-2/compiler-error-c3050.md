---
title: Erreur du compilateur C3050
ms.date: 11/04/2016
f1_keywords:
- C3050
helpviewer_keywords:
- C3050
ms.assetid: ee090a0b-29cc-4215-a2f9-d82af79b8e82
ms.openlocfilehash: f8ab53974ac59de235a36e56991d2ef89f06be59
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761271"
---
# <a name="compiler-error-c3050"></a>Erreur du compilateur C3050

'type1' : une classe ref ne peut pas hériter de 'type1'

`System::ValueType` ne peut pas être une classe de base pour un type référence.

L’exemple suivant génère l’erreur C3050 :

```cpp
// C3050.cpp
// compile with: /clr /LD
ref struct X : System::ValueType {};   // C3050
ref struct Y {};   // OK
```
