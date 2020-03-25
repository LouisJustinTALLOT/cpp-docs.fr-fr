---
title: Avertissement du compilateur (niveau 4) C4205
ms.date: 11/04/2016
f1_keywords:
- C4205
helpviewer_keywords:
- C4205
ms.assetid: 39b5108c-7230-41b4-b2fe-2293eb6aae28
ms.openlocfilehash: 7b6e273de196f6708b92774ce5b436dc810ad3a5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161437"
---
# <a name="compiler-warning-level-4-c4205"></a>Avertissement du compilateur (niveau 4) C4205

extension non standard utilisée : déclaration de fonction statique dans la portée de la fonction

Avec les extensions Microsoft (/Ze), les fonctions **statiques** peuvent être déclarées dans une autre fonction. La portée globale est donnée à la fonction.

## <a name="example"></a>Exemple

```c
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

Ces initialisations ne sont pas valides sous compatibilité ANSI ([/za](../../build/reference/za-ze-disable-language-extensions.md)).
