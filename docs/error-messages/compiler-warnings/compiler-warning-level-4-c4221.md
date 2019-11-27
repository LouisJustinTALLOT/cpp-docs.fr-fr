---
title: Avertissement du compilateur (niveau 4) C4221
ms.date: 11/04/2016
f1_keywords:
- C4221
helpviewer_keywords:
- C4221
ms.assetid: 8532bd68-54dc-4526-8597-f61dcb0a0129
ms.openlocfilehash: fa87c240472df2926753781f0f14cbd69752de00
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541923"
---
# <a name="compiler-warning-level-4-c4221"></a>Avertissement du compilateur (niveau 4) C4221

extension non standard utilisée : 'identifier' : ne peut pas être initialisé à l’aide de l’adresse de la variable automatique

Avec les extensions Microsoft par défaut (/Ze), vous pouvez initialiser un type d’agrégat (**tableau**, `struct`ou **Union**) avec l’adresse d’une variable locale (automatique).

## <a name="example"></a>Exemple

```c
// C4221.c
// compile with: /W4
struct S
{
   int *i;
};

void func()
{
   int j;
   struct S s1 = { &j };   // C4221
}

int main()
{
}
```

Ces initialisations ne sont pas valides sous compatibilité ANSI ([/za](../../build/reference/za-ze-disable-language-extensions.md)).