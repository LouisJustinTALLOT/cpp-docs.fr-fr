---
description: 'En savoir plus sur : avertissement du compilateur (niveau 4) C4220'
title: Avertissement du compilateur (niveau 4) C4220
ms.date: 11/04/2016
f1_keywords:
- C4220
helpviewer_keywords:
- C4220
ms.assetid: aba18868-825f-4763-9af6-3296406a80e4
ms.openlocfilehash: fd5378fd1e685b2cc6e730c2cff87fcdb041aaa8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330626"
---
# <a name="compiler-warning-level-4-c4220"></a>Avertissement du compilateur (niveau 4) C4220

varargs correspond aux paramètres restants

Sous les extensions Microsoft par défaut (/Ze), un pointeur vers une fonction correspond à un pointeur vers une fonction avec des arguments similaires, mais variables.

## <a name="example"></a>Exemple

```c
// C4220.c
// compile with: /W4

int ( *pFunc1) ( int a, ... );
int ( *pFunc2) ( int a, int b);

int main()
{
   if ( pFunc1 != pFunc2 ) {};  // C4220
}
```

Ces pointeurs ne correspondent pas sous compatibilité ANSI ([/za](../../build/reference/za-ze-disable-language-extensions.md)).
