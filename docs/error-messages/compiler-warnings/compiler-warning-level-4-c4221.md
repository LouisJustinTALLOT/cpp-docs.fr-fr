---
title: Compilateur avertissement (niveau 4) C4221 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4221
dev_langs:
- C++
helpviewer_keywords:
- C4221
ms.assetid: 8532bd68-54dc-4526-8597-f61dcb0a0129
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 18b0804c8b7cb2d059e45fa504334687a796fbe1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46056415"
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