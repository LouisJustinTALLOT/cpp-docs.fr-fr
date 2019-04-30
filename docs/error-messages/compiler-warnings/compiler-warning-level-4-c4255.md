---
title: Avertissement du compilateur (niveau 4) C4255
ms.date: 11/04/2016
f1_keywords:
- C4255
helpviewer_keywords:
- C4255
ms.assetid: 2087b635-4b4c-4182-8a01-c26770d2bb88
ms.openlocfilehash: 1796e28e88bbe52c4c21ffdf0a8a96a278a44388
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400960"
---
# <a name="compiler-warning-level-4-c4255"></a>Avertissement du compilateur (niveau 4) C4255

'function' : no function prototype given: converting '()' to '(void)'

Le compilateur ne trouve pas une liste explicite des arguments d’une fonction. Cet avertissement concerne uniquement le compilateur C.

Cet avertissement est désactivé par défaut. Consultez [Avertissements du compilateur désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md) pour plus d'informations.

L’exemple suivant génère l’erreur C4255 :

```
// C4255.c
// compile with: /W4 /WX
#pragma warning (default : 4255)

void f()  { // C4255
// try the following line instead
//void f(void) {
}

int main(int argc, char *argv[]) {
   f();
}
```