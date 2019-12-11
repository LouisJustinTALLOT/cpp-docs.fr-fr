---
title: Avertissement du compilateur (niveau 3) C4534
ms.date: 11/04/2016
f1_keywords:
- c4534
helpviewer_keywords:
- C4534
ms.assetid: ec2adf3b-d7a1-4005-bb0c-5d219df78dc8
ms.openlocfilehash: 7d8ff442e84aa7563b1787e5a030297c034e1871
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74992057"
---
# <a name="compiler-warning-level-3-c4534"></a>Avertissement du compilateur (niveau 3) C4534

'Constructor’ne sera pas un constructeur par défaut pour la classe’class’en raison de l’argument par défaut

Une classe non managée peut avoir un constructeur avec des paramètres qui ont des valeurs par défaut et le compilateur l’utilise comme constructeur par défaut. Une classe marquée avec le mot clé `value` n’utilise pas un constructeur avec des valeurs par défaut pour ses paramètres comme constructeur par défaut.

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
