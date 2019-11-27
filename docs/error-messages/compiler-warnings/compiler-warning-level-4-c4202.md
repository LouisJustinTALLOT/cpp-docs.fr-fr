---
title: Avertissement du compilateur (niveau 4) C4202
ms.date: 11/04/2016
f1_keywords:
- C4202
helpviewer_keywords:
- C4202
ms.assetid: 253293aa-97a3-4878-a2e8-c6cc9e20b1cb
ms.openlocfilehash: 0d5e7dd45b58f1231c39565bfd74c5895096a8b7
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541646"
---
# <a name="compiler-warning-level-4-c4202"></a>Avertissement du compilateur (niveau 4) C4202

extension non standard utilisée : '... ' : paramètre de prototype non conforme dans la liste de noms

Une définition de fonction de style ancien contient des arguments de variables. Ces définitions génèrent une erreur sous compatibilité ANSI ([/za](../../build/reference/za-ze-disable-language-extensions.md)).

## <a name="example"></a>Exemple

```c
// C4202.c
// compile with: /W4
void func( a, b, ...)   // C4202
int a, b;
{}

int main()
{
}
```