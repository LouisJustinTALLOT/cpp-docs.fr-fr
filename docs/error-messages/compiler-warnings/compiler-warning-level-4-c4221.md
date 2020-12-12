---
description: 'En savoir plus sur : avertissement du compilateur (niveau 4) C4221'
title: Avertissement du compilateur (niveau 4) C4221
ms.date: 11/04/2016
f1_keywords:
- C4221
helpviewer_keywords:
- C4221
ms.assetid: 8532bd68-54dc-4526-8597-f61dcb0a0129
ms.openlocfilehash: 4632b075dfb6a7c1895415a253c70f5b4fd4f278
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97164274"
---
# <a name="compiler-warning-level-4-c4221"></a>Avertissement du compilateur (niveau 4) C4221

extension non standard utilisée : 'identifier' : ne peut pas être initialisé à l’aide de l’adresse de la variable automatique

Avec les extensions Microsoft par défaut (/Ze), vous pouvez initialiser un type d’agrégat (**Array**, **`struct`** ou **`union`** ) avec l’adresse d’une variable locale (automatique).

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
