---
description: 'En savoir plus sur : avertissement du compilateur (niveau 4) C4201'
title: Avertissement du compilateur (niveau 4) C4201
ms.date: 11/04/2016
f1_keywords:
- C4201
helpviewer_keywords:
- C4201
ms.assetid: 6156f508-9393-4d77-9e73-1ec3e1c32d0d
ms.openlocfilehash: 739e09750f8f051ee0fd380fbb25858e620c70a4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97206719"
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
