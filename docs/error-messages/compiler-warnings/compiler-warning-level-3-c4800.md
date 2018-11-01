---
title: Avertissement du compilateur (niveau 3) C4800
ms.date: 11/04/2016
f1_keywords:
- C4800
helpviewer_keywords:
- C4800
ms.assetid: 4f409799-a250-45ed-bb5f-657691b0d9f7
ms.openlocfilehash: 591b706249201691c7a9743d2cad082eb61e68b5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50636135"
---
# <a name="compiler-warning-level-3-c4800"></a>Avertissement du compilateur (niveau 3) C4800

> «*type*' : valeur forcée à bool 'true' ou 'false' (avertissement de performance)

Cet avertissement est généré lorsqu’une valeur qui n’est pas `bool` est attribuée ou converti en type `bool`. En règle générale, ce message est provoqué par l’assignation `int` variables à `bool` variables où le `int` variable contient uniquement des valeurs **true** et **false**et peut être redéclaration comme type `bool`. Si vous ne pouvez pas réécrire l’expression pour utiliser le type `bool`, vous pouvez alors ajouter «`!=0`» à l’expression, qui lui donne le type d’expression `bool`. Un cast de l’expression en type `bool` ne désactive pas l’avertissement, de par sa conception.

Cet avertissement n’est plus généré dans Visual Studio 2017.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C4800 et montre comment la corriger :

```cpp
// C4800.cpp
// compile with: /W3
int main() {
   int i = 0;

   // To fix, instead try:
   // bool i = 0;

   bool j = i;   // C4800
   j++;
}
```