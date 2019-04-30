---
title: Avertissement du compilateur (niveau 4) C4205
ms.date: 11/04/2016
f1_keywords:
- C4205
helpviewer_keywords:
- C4205
ms.assetid: 39b5108c-7230-41b4-b2fe-2293eb6aae28
ms.openlocfilehash: 1b165d2bdb2fb50df89fdd77c734c054a40b6e95
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401226"
---
# <a name="compiler-warning-level-4-c4205"></a>Avertissement du compilateur (niveau 4) C4205

extension non standard utilisée : déclaration de fonction statique dans la portée de fonction

Avec les extensions Microsoft (/Ze), **statique** fonctions peuvent être déclarées à l’intérieur d’une autre fonction. La fonction reçoit une portée globale.

## <a name="example"></a>Exemple

```
// C4205.c
// compile with: /W4
void func1()
{
   static int func2();  // C4205
};

int main()
{
}
```

Ces initialisations ne sont pas valides sous compatibilité ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).