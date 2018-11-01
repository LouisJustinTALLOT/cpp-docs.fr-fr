---
title: Avertissement du compilateur (niveau 4) C4221
ms.date: 11/04/2016
f1_keywords:
- C4221
helpviewer_keywords:
- C4221
ms.assetid: 8532bd68-54dc-4526-8597-f61dcb0a0129
ms.openlocfilehash: f552a5d76d1a778cdf72cbe079138f609350ffb1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50511239"
---
# <a name="compiler-warning-level-4-c4221"></a>Avertissement du compilateur (niveau 4) C4221

extension non standard utilisée : 'identificateur' : ne peut pas être initialisée à l’aide de l’adresse de la variable automatique

Avec les extensions Microsoft (/Ze), vous pouvez initialiser un type d’agrégat (**tableau**, `struct`, ou **union**) avec l’adresse d’une variable locale (automatique).

## <a name="example"></a>Exemple

```
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

Ces initialisations ne sont pas valides sous compatibilité ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).