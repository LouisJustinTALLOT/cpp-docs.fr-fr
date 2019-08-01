---
title: Opérateur d'enchaînement (#)
ms.date: 11/04/2016
f1_keywords:
- '#'
helpviewer_keywords:
- preprocessor, operators
- arguments [C++], converting to strings
- stringizing operator
- preprocessor
- string literals, converting macro parameters to
- macros [C++], converting parameters to strings
- '# preprocessor operator'
ms.assetid: 1175dd19-4538-43b3-ad97-a008ab80e7b1
ms.openlocfilehash: d90d07c8f3cce6c443be0eb994db494746c00fcc
ms.sourcegitcommit: 40ffe764244784c715b086c79626ac390b855d47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68711139"
---
# <a name="stringizing-operator-"></a>Opérateur d'enchaînement (#)

Le signe dièse () ou l’opérateur «Stringing **#** » () convertit les paramètres de macro en littéraux de chaîne sans développer la définition de paramètre. Il est utilisé uniquement avec les macros qui acceptent des arguments. S’il précède un paramètre formel dans la définition de la macro, l’argument réel passé par l’appel de macro est entre guillemets et traité en tant que littéral de chaîne. Le littéral de chaîne remplace alors chaque occurrence d'une combinaison de l'opérateur de chaîne et du paramètre formel dans la définition de macro.

> [!NOTE]
> L’extension Microsoft C (versions 6.0 et antérieures) de la norme C ANSI, qui développait auparavant les arguments formels de macro apparaissant dans les littéraux de chaîne et les constantes caractère, n’est plus prise en charge. Le code qui reposait sur cette extension doit être réécrit à l’aide de **#** l’opérateur de chaîne ().

L'espace blanc qui précède le premier jeton de l'argument réel ou qui suit le dernier jeton de l'argument réel est ignoré. Tout espace blanc situé entre les jetons dans l’argument réel est réduit à un espace blanc unique dans le littéral de chaîne résultant. Ainsi, si un commentaire figure entre deux jetons de l’argument réel, il est réduit à un espace blanc unique. Le littéral de chaîne résultant est automatiquement concaténé avec tous les littéraux de chaîne adjacents dont il est séparé uniquement par un espace blanc.

En outre, si un caractère contenu dans l’argument requiert généralement une séquence d’échappement lorsqu’il est utilisé dans un littéral de chaîne (par exemple, un guillemet (" **\\** ) ou une barre oblique inverse ()), la barre oblique inverse d’échappement requise est automatiquement insérée avant le caractère.

L’opérateur C++ de chaîne visuelle ne se comporte pas correctement lorsqu’il est utilisé avec des chaînes qui incluent des séquences d’échappement. Dans ce cas, le compilateur génère une [Erreur du compilateur C2017](../error-messages/compiler-errors-1/compiler-error-c2017.md).

## <a name="examples"></a>Exemples

L'exemple ci-dessous illustre une définition de macro incluant l'opérateur de chaîne et une fonction principale qui appelle la macro :

```cpp
// stringizer.cpp
#include <stdio.h>
#define stringer( x ) printf_s( #x "\n" )
int main() {
   stringer( In quotes in the printf function call );
   stringer( "In quotes when printed to the screen" );
   stringer( "This: \"  prints an escaped double quote" );
}
```

Les `stringer` macros sont développées pendant le prétraitement, ce qui génère le code suivant:

```cpp
int main() {
   printf_s( "In quotes in the printf function call" "\n" );
   printf_s( "\"In quotes when printed to the screen\"" "\n" );
   printf_s( "\"This: \\\" prints an escaped double quote\"" "\n" );
}
```

```Output
In quotes in the printf function call
"In quotes when printed to the screen"
"This: \"  prints an escaped double quote"
```

L'exemple suivant montre comment développer un paramètre de macro :

```cpp
// stringizer_2.cpp
// compile with: /E
#define F abc
#define B def
#define FB(arg) #arg
#define FB1(arg) FB(arg)
FB(F B)
FB1(F B)
```

## <a name="see-also"></a>Voir aussi

[Opérateurs de préprocesseur](../preprocessor/preprocessor-operators.md)
