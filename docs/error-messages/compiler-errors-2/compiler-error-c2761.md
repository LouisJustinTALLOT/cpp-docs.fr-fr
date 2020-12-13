---
description: 'En savoir plus sur : erreur du compilateur C2761'
title: Erreur du compilateur C2761
ms.date: 11/04/2016
f1_keywords:
- C2761
helpviewer_keywords:
- C2761
ms.assetid: 38c79a05-b56d-485b-820f-95e8c0cb926f
ms.openlocfilehash: 624a375aedc78b6d63f3a6c5a1185edfade28c7d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336151"
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
