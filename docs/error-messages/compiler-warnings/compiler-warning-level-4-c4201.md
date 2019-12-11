---
title: Avertissement du compilateur (niveau 4) C4201
ms.date: 11/04/2016
f1_keywords:
- C4201
helpviewer_keywords:
- C4201
ms.assetid: 6156f508-9393-4d77-9e73-1ec3e1c32d0d
ms.openlocfilehash: 4bbbc8987c3ae4157d5f8133978a46a004988bce
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991624"
---
# <a name="compiler-warning-level-4-c4201"></a>Avertissement du compilateur (niveau 4) C4201

extension non standard utilisée : struct/union sans type

Sous extensions Microsoft (/Ze), vous pouvez spécifier une structure sans déclarateur en tant que membre d’une autre structure ou Union. Ces structures génèrent une erreur sous compatibilité ANSI ([/za](../../build/reference/za-ze-disable-language-extensions.md)).

## <a name="example"></a>Exemple

```cpp
// C4201.cpp
// compile with: /W4
struct S
{
   float y;
   struct
   {
      int a, b, c;  // C4201
   };
} *p_s;

int main()
{
}
```
