---
title: Avertissement du compilateur (niveau 4) C4289
ms.date: 11/04/2016
f1_keywords:
- C4289
helpviewer_keywords:
- C4289
ms.assetid: 0dbd2863-4cde-4e16-894b-104a2d5fa724
ms.openlocfilehash: b9083670465d68493d90a8e96ff7ee5db34c1978
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991323"
---
# <a name="compiler-warning-level-4-c4289"></a>Avertissement du compilateur (niveau 4) C4289

extension non standard utilisée : ’var’ : variable de contrôle de boucle déclarée dans la boucle for utilisée à l’extérieur de la portée de la boucle

Lors de la compilation avec [/Ze](../../build/reference/za-ze-disable-language-extensions.md) et **/Zc : forScope-** , une variable déclarée dans une boucle [for](../../cpp/for-statement-cpp.md) a été utilisée après l’étendue de la boucle **for**.

Consultez [/Zc : forScope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) pour plus d’informations sur la spécification du comportement standard dans **les boucles for** avec **/Ze**.

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
