---
description: 'En savoir plus sur : avertissement du compilateur (niveau 3) C4534'
title: Avertissement du compilateur (niveau 3) C4534
ms.date: 11/04/2016
f1_keywords:
- c4534
helpviewer_keywords:
- C4534
ms.assetid: ec2adf3b-d7a1-4005-bb0c-5d219df78dc8
ms.openlocfilehash: 6a13b27716488fa04f6342da76fdcd32c5635f2d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97257886"
---
# <a name="compiler-warning-level-3-c4534"></a>Avertissement du compilateur (niveau 3) C4534

'Constructor’ne sera pas un constructeur par défaut pour la classe’class’en raison de l’argument par défaut

Une classe non managée peut avoir un constructeur avec des paramètres qui ont des valeurs par défaut et le compilateur l’utilise comme constructeur par défaut. Une classe marquée avec le `value` mot clé n’utilise pas un constructeur avec des valeurs par défaut pour ses paramètres comme constructeur par défaut.

Pour plus d’informations, consultez [Classes et structs](../../extensions/classes-and-structs-cpp-component-extensions.md).

L’exemple suivant génère l’C4534 :

```cpp
// C4534.cpp
// compile with: /W3 /clr /WX
value class MyClass {
public:
   int ii;
   MyClass(int i = 9) {   // C4534, will not be the default constructor
      i++;
   }
};

int main() {
   MyClass ^ xx = gcnew MyClass;
   xx->ii = 0;
}
```
