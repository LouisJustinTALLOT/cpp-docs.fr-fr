---
title: Erreur du compilateur C2761
ms.date: 11/04/2016
f1_keywords:
- C2761
helpviewer_keywords:
- C2761
ms.assetid: 38c79a05-b56d-485b-820f-95e8c0cb926f
ms.openlocfilehash: 7493934879068109c582a85592f485c1d391e2de
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90743384"
---
# <a name="compiler-error-c2761"></a>Erreur du compilateur C2761

'fonction' : la redéclaration de la fonction membre n’est pas autorisée

Vous ne pouvez pas redéclarer une fonction membre. Vous pouvez le définir, mais pas le redéclarer.

## <a name="examples"></a>Exemples

L’exemple suivant génère l’C2761.

```cpp
// C2761.cpp
class a {
   int t;
   void test();
};

void a::a;     // C2761
void a::test;  // C2761
```

Les membres non static d’une classe ou d’une structure ne peuvent pas être définis.  L’exemple suivant génère l’C2761.

```cpp
// C2761_b.cpp
// compile with: /c
struct C {
   int s;
   static int t;
};

int C::s;   // C2761
int C::t;   // OK
```
