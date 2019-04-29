---
title: Avertissement du compilateur (niveau 2) C4244
ms.date: 11/04/2016
f1_keywords:
- C4244
helpviewer_keywords:
- C4244
ms.assetid: 2c19d157-21d1-42c2-a6c0-3f30f2ce3813
ms.openlocfilehash: af821d80ff8c4c7717986f2ff4d0f3392cd6fca3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62349722"
---
# <a name="compiler-warning-level-2-c4244"></a>Avertissement du compilateur (niveau 2) C4244

'argument' : conversion de 'type1' en 'type2', perte possible de données

Un type à virgule flottante a été converti en un type entier.  Une perte de données peut avoir eu lieu.

Si vous obtenez l'avertissement C4244, vous devez modifier votre programme pour utiliser des types compatibles, ou ajouter une logique à votre code pour garantir que la plage des valeurs possibles sera toujours compatible avec les types que vous utilisez.

C4244 peut également se produire au niveau 3 et 4 ; consultez [Avertissement du compilateur (niveaux 3 et 4) C4244](../../error-messages/compiler-warnings/compiler-warning-levels-3-and-4-c4244.md) pour plus d’informations.

## <a name="example"></a>Exemple

L'exemple suivant génère l'avertissement C4244 :

```
// C4244_level2.cpp
// compile with: /W2

int f(int x){ return 0; }
int main() {
   double x = 10.1;
   int i = 10;
   return (f(x));   // C4244
   // try the following line instead
   // return (f(i));
}
```