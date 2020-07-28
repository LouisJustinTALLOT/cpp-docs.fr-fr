---
title: Avertissement du compilateur (niveau 1) C4288
ms.date: 11/04/2016
f1_keywords:
- C4288
helpviewer_keywords:
- C4288
ms.assetid: 6aaeb139-90cd-457a-9d37-65687042736f
ms.openlocfilehash: a732614ac5d71168ece8ada8e468afa5ba54c1f9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220078"
---
# <a name="compiler-warning-level-1-c4288"></a>Avertissement du compilateur (niveau 1) C4288

> extension non standard utilisée : 'var' : la variable de contrôle de boucle déclarée dans la boucle for est utilisée à l’extérieur de la portée de la boucle. Il est en conflit avec la déclaration dans la portée externe

Lors de la compilation avec [`/Ze`](../../build/reference/za-ze-disable-language-extensions.md) et **/Zc : forScope-**, une variable déclarée dans une **`for`** boucle a été utilisée après l’étendue de la boucle [for](../../cpp/for-statement-cpp.md). Une extension Microsoft du langage C++ permet à cette variable de rester dans la portée, et C4288 vous rappelle que la première déclaration de la variable n’est pas utilisée.

Consultez [`/Zc:forScope`](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) pour plus d’informations sur la façon de spécifier l’extension Microsoft dans en **`for`** boucle avec/Ze.

L’exemple suivant génère l’C4288 :

```cpp
// C4288.cpp
// compile with: /W1 /c /Zc:forScope-
int main() {
   int i = 0;    // not used in this program
   for (int i = 0 ; ; ) ;
   i++;   // C4288 using for-loop declaration of i
}
```
