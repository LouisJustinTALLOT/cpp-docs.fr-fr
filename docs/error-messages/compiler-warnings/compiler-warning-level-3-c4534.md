---
title: Compilateur avertissement (niveau 3) C4534 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- c4534
dev_langs:
- C++
helpviewer_keywords:
- C4534
ms.assetid: ec2adf3b-d7a1-4005-bb0c-5d219df78dc8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ad85a6b9dff1715cbdce9738608f26c8680319d0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46099809"
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