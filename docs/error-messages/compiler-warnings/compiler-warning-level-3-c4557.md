---
title: Avertissement du compilateur (niveau 3) C4557
ms.date: 11/04/2016
f1_keywords:
- C4557
helpviewer_keywords:
- C4557
ms.assetid: 7d9db716-03b2-4ee5-9b09-ba8aa5aa7e4c
ms.openlocfilehash: 22ee456c5f79434c5e3b8a79b4c174aa3cdb3c7a
ms.sourcegitcommit: 217fac22604639ebd62d366a69e6071ad5b724ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2019
ms.locfileid: "74188940"
---
# <a name="compiler-warning-level-3-c4557"></a>Avertissement du compilateur (niveau 3) C4557

'__assume' contient l'effet 'effet'

La valeur passée à une [__assume](../../intrinsics/assume.md) instruction2 a été modifiée.

Cet avertissement est désactivé par défaut. Consultez [Avertissements du compilateur désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md) pour plus d'informations.

L’exemple suivant génère l’C4557 :

```cpp
// C4557.cpp
// compile with: /W3
#pragma warning(default : 4557)
int main()
{
   int i;
   __assume(i++);   // C4557
}
```