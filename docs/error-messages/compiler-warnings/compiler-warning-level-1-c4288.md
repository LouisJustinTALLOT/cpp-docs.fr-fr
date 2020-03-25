---
title: Avertissement du compilateur (niveau 1) C4288
ms.date: 11/04/2016
f1_keywords:
- C4288
helpviewer_keywords:
- C4288
ms.assetid: 6aaeb139-90cd-457a-9d37-65687042736f
ms.openlocfilehash: e706a448f4264eceedbb4fa8932c0fc30e88d532
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175738"
---
# <a name="compiler-warning-level-1-c4288"></a>Avertissement du compilateur (niveau 1) C4288

extension non standard utilisée : 'var' : la variable de contrôle de boucle déclarée dans la boucle for est utilisée à l’extérieur de la portée de la boucle. Il est en conflit avec la déclaration dans la portée externe

Lors de la compilation avec [/Ze](../../build/reference/za-ze-disable-language-extensions.md) et **/Zc : forScope-** , une variable déclarée dans une boucle **for** a été utilisée après l’étendue de la boucle [for](../../cpp/for-statement-cpp.md). Une extension Microsoft du langage C++ permet à cette variable de rester dans la portée, et C4288 vous rappelle que la première déclaration de la variable n’est pas utilisée.

Pour plus d’informations sur la spécification de l’extension Microsoft dans les boucles **for** avec/Ze., consultez [/Zc : forScope.](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md)

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
