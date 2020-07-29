---
title: Avertissement du compilateur (niveau 4) C4800
ms.date: 03/14/2019
f1_keywords:
- C4800
helpviewer_keywords:
- C4800
ms.assetid: 4f409799-a250-45ed-bb5f-657691b0d9f7
ms.openlocfilehash: a516be2e6e1966c3249ed21cc6d480ddea8b5ec1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220013"
---
# <a name="compiler-warning-level-4-c4800"></a>Avertissement du compilateur (niveau 4) C4800

::: moniker range=">= vs-2019"
Visual Studio 2019 et ultérieur :
> Conversion implicite de'*type*'en bool. Perte d’informations possible
::: moniker-end

C4800 est un avertissement de niveau 3 dans Visual Studio 2015 et versions antérieures :
> '*type*' : valeur forcée à bool’true’ou’false' (avertissement de performance)

Cet avertissement est généré lorsqu’une valeur est implicitement convertie en type **`bool`** . En règle générale, ce message est provoqué par **`int`** l’affectation de variables aux **`bool`** variables où la **`int`** variable contient uniquement **`true`** des valeurs et **`false`** , et qui peut être redéclarée en tant que type **`bool`** . Si vous ne pouvez pas réécrire l’expression pour utiliser le type **`bool`** , vous pouvez ajouter « `!=0` » à l’expression, qui donne le type d’expression **`bool`** . Le cast de l’expression en type **`bool`** ne désactive pas l’avertissement, ce qui est lié à la conception.

::: moniker range=">= vs-2017"
Cet avertissement n’est pas émis dans Visual Studio 2017.
::: moniker-end

::: moniker range=">= vs-2019"
Cet avertissement est désactivé par défaut à partir de Visual Studio 2019. Utilisez __/w__*n*__4800__ pour activer C4800 comme un avertissement de niveau *n* ou [/Wall](../../build/reference/compiler-option-warning-level.md) pour activer tous les avertissements qui sont désactivés par défaut. Pour plus d’informations, consultez [avertissements du compilateur désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md).
::: moniker-end

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4800 et montre comment la corriger :

```cpp
// C4800.cpp
// compile with: /W4 /w44800
int main() {
   int i = 0;

   // To fix, instead try:
   // bool i = 0;

   bool j = i;   // C4800
   j++;
}
```
