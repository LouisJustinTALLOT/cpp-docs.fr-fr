---
title: Avertissement du compilateur (niveau 4) C4220
ms.date: 11/04/2016
f1_keywords:
- C4220
helpviewer_keywords:
- C4220
ms.assetid: aba18868-825f-4763-9af6-3296406a80e4
ms.openlocfilehash: 177fb01ba4181f72740724d107fe08e6680ed492
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50542439"
---
# <a name="compiler-warning-level-4-c4220"></a>Avertissement du compilateur (niveau 4) C4220

varargs correspond aux paramètres restants

Sous les extensions Microsoft par défaut (/Ze), un pointeur vers une fonction correspond à un pointeur vers une fonction avec des arguments similaires mais variables.

## <a name="example"></a>Exemple

```
// C4220.c
// compile with: /W4

int ( *pFunc1) ( int a, ... );
int ( *pFunc2) ( int a, int b);

int main()
{
   if ( pFunc1 != pFunc2 ) {};  // C4220
}
```

Ces pointeurs ne correspondent pas sous compatibilité ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).