---
description: 'En savoir plus sur : avertissement du compilateur (niveau 4) C4289'
title: Avertissement du compilateur (niveau 4) C4289
ms.date: 11/04/2016
f1_keywords:
- C4289
helpviewer_keywords:
- C4289
ms.assetid: 0dbd2863-4cde-4e16-894b-104a2d5fa724
ms.openlocfilehash: c0b82702195aa7f5dcd88cd4e9bffbc1bbd1769f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97294611"
---
# <a name="compiler-warning-level-4-c4289"></a>Avertissement du compilateur (niveau 4) C4289

extension non standard utilisée : ’var’ : variable de contrôle de boucle déclarée dans la boucle for utilisée à l’extérieur de la portée de la boucle

Lors de la compilation avec [/Ze](../../build/reference/za-ze-disable-language-extensions.md) et **/Zc : forScope-**, une variable déclarée dans une boucle [for](../../cpp/for-statement-cpp.md) a été utilisée après la **`for`** portée de la boucle.

Consultez [/Zc : forScope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) pour plus d’informations sur la façon de spécifier le comportement standard dans **`for`** les boucles avec **/Ze**.

Cet avertissement est désactivé par défaut. Consultez [Avertissements du compilateur désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md) pour plus d'informations.

L’exemple suivant génère l’C4289 :

```cpp
// C4289.cpp
// compile with: /W4 /Zc:forScope-
#pragma warning(default:4289)
int main() {
   for (int i = 0 ; ; )   // C4289
      break;
   i++;
}
```
