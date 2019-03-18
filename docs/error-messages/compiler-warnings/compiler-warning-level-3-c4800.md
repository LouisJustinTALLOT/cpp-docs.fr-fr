---
title: Avertissement (niveau 4) du compilateur C4800
ms.date: 03/14/2019
f1_keywords:
- C4800
helpviewer_keywords:
- C4800
ms.assetid: 4f409799-a250-45ed-bb5f-657691b0d9f7
ms.openlocfilehash: 46418063625e16385497740a4f7e3d837e923156
ms.sourcegitcommit: a901c4acbfc80ca10663d37c09921f04c5b6dd17
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2019
ms.locfileid: "58142579"
---
# <a name="compiler-warning-level-4-c4800"></a>Avertissement (niveau 4) du compilateur C4800

::: moniker range=">= vs-2019"
Visual Studio 2019 et versions ultérieur :
> Conversion implicite de '*type*» en valeur booléenne. Perte d’informations possible
::: moniker-end

C4800 est un avertissement de niveau 3 dans Visual Studio 2015 et versions antérieures :
> «*type*' : valeur forcée à bool 'true' ou 'false' (avertissement de performance)

Cet avertissement est généré lorsqu’une valeur est implicitement convertie en type `bool`. En règle générale, ce message est provoqué par l’assignation `int` variables à `bool` variables où le `int` variable contient uniquement des valeurs **true** et **false**et peut être redéclaration comme type `bool`. Si vous ne pouvez pas réécrire l’expression pour utiliser le type `bool`, vous pouvez alors ajouter «`!=0`» à l’expression, qui lui donne le type d’expression `bool`. Un cast de l’expression en type `bool` ne désactive pas l’avertissement, de par sa conception.

::: moniker range=">= vs-2017"
Cet avertissement n’est pas émis dans Visual Studio 2017.
::: moniker-end

::: moniker range=">= vs-2019"
Cet avertissement est désactivé par défaut à partir de Visual Studio 2019. Utilisez __/w__*n*__4800__ pour activer C4800 en tant que niveau *n* avertissement, ou [/Wall](../../build/reference/compiler-option-warning-level.md) pour activer tous les avertissements qui sont désactivés par défaut. Pour plus d’informations, consultez [du compilateur avertissements que sont désactivé par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md).
::: moniker-end

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C4800 et montre comment la corriger :

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