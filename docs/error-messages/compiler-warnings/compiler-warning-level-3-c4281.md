---
title: Avertissement du compilateur (niveau 3) C4281
ms.date: 11/04/2016
f1_keywords:
- C4281
helpviewer_keywords:
- C4281
ms.assetid: a9771261-5725-4fc6-87b6-16cf92113a25
ms.openlocfilehash: 31c389f4bc0546270240c9c701be7f1e9e620db1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174139"
---
# <a name="compiler-warning-level-3-c4281"></a>Avertissement du compilateur (niveau 3) C4281

la récursivité’operator-> 's’est produite via le type’type'

Votre code permet à **operator->** de s’appeler lui-même.

L’exemple suivant génère l’C4281 :

```cpp
// C4281.cpp
// compile with: /W3 /WX
struct A;
struct B;
struct C;

struct A
{
   int z;
   B& operator->();
};

struct B
{
   C& operator->();
};

struct C
{
   A& operator->();
};

void f(A p)
{
   int i = p->z; // C4281
}
```
