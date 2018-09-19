---
title: Compilateur avertissement (niveau 1) C4488 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4488
dev_langs:
- C++
helpviewer_keywords:
- C4488
ms.assetid: 55625e46-ddb5-4c7c-99c7-cd4aa9f879bd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0d2cccedada47519ada55353cb44faab0e34cf03
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118269"
---
# <a name="compiler-warning-level-1-c4488"></a>Avertissement du compilateur (niveau 1) C4488

'fonction' : requiert le mot clé 'mot_clé' pour implémenter la méthode d’interface 'méthode_interface'

Une classe doit implémenter tous les membres d’une interface dont elle hérite directement. Un membre implémenté doit avoir une accessibilité publique et doit être marqué virtual.

## <a name="example"></a>Exemple

C4488 peut se produire si un membre implémenté n’est pas public. L’exemple suivant génère l’erreur C4488.

```
// C4488.cpp
// compile with: /clr /c /W1 /WX
interface struct MyI {
   void f1();
};

// implemented member not public
ref class B : MyI { virtual void f1() {} };  // C4488

// OK
ref class C : MyI {
public:
   virtual void f1() {}
};
```

## <a name="example"></a>Exemple

C4488 peut se produire si un membre implémenté n’est pas marqué comme virtual. L’exemple suivant génère l’erreur C4488.

```
// C4488_b.cpp
// compile with: /clr /c /W1 /WX
interface struct MyI {
   void f1();
};

ref struct B : MyI { void f1() {} };   // C4488
ref struct C : MyI { virtual void f1() {} };   // OK
```