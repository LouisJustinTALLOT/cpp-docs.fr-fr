---
title: Avertissement du compilateur (niveau 4) C4289
ms.date: 11/04/2016
f1_keywords:
- C4289
helpviewer_keywords:
- C4289
ms.assetid: 0dbd2863-4cde-4e16-894b-104a2d5fa724
ms.openlocfilehash: 3a997af466ddfdaaf4631afeb53d917ce0338c3b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50488808"
---
# <a name="compiler-warning-level-4-c4289"></a>Avertissement du compilateur (niveau 4) C4289

extension non standard utilisée : ’var’ : variable de contrôle de boucle déclarée dans la boucle for utilisée à l’extérieur de la portée de la boucle

Lors de la compilation avec [/Ze](../../build/reference/za-ze-disable-language-extensions.md) et **/Zc**, une variable déclarée dans une [pour](../../cpp/for-statement-cpp.md) boucle a été utilisée après la **pour**-portée de la boucle.

Consultez [/Zc : forScope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) pour plus d’informations sur la façon de spécifier un comportement standard dans **pour** effectue une itération avec **/Ze**.

Cet avertissement est désactivé par défaut. Consultez [Avertissements du compilateur désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md) pour plus d'informations.

L’exemple suivant génère l’erreur C4289 :

```
// C4289.cpp
// compile with: /W4 /Zc:forScope-
#pragma warning(default:4289)
int main() {
   for (int i = 0 ; ; )   // C4289
      break;
   i++;
}
```