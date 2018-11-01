---
title: Avertissement du compilateur (niveau 3) C4534
ms.date: 11/04/2016
f1_keywords:
- c4534
helpviewer_keywords:
- C4534
ms.assetid: ec2adf3b-d7a1-4005-bb0c-5d219df78dc8
ms.openlocfilehash: a2af04502082f7fb30d59af5e6434161227c6d30
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50437266"
---
# <a name="compiler-warning-level-3-c4534"></a>Avertissement du compilateur (niveau 3) C4534

'constructeur' ne sera pas un constructeur par défaut pour la classe 'class' en raison de l’argument par défaut

Une classe non managée peut avoir un constructeur avec les paramètres qui ont des valeurs par défaut et le compilateur utilisera en tant que le constructeur par défaut. Une classe marquée avec le `value` mot clé n’utilise pas un constructeur avec valeurs par défaut pour ses paramètres en tant qu’un constructeur par défaut.

Pour plus d’informations, consultez [les Classes et Structs](../../windows/classes-and-structs-cpp-component-extensions.md).

L’exemple suivant génère l’erreur C4534 :

```
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