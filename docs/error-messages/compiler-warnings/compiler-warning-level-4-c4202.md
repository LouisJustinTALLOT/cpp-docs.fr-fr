---
title: Avertissement du compilateur (niveau 4) C4202
ms.date: 11/04/2016
f1_keywords:
- C4202
helpviewer_keywords:
- C4202
ms.assetid: 253293aa-97a3-4878-a2e8-c6cc9e20b1cb
ms.openlocfilehash: c66e2243ee5eca55105de27c9824ee8ced338500
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50536151"
---
# <a name="compiler-warning-level-4-c4202"></a>Avertissement du compilateur (niveau 4) C4202

extension non standard utilisée : '...' : paramètre de prototype non conforme de liste de nom dans

Une définition de fonction de style ancien contient des arguments variables. Ces définitions génèrent une erreur sous compatibilité ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).

## <a name="example"></a>Exemple

```
// C4202.c
// compile with: /W4
void func( a, b, ...)   // C4202
int a, b;
{}

int main()
{
}
```