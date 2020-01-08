---
title: Littéraux numériques, booléens et deC++pointeur ()
ms.date: 11/04/2016
helpviewer_keywords:
- literals, C++
- constants, literals
- literals [C++]
ms.assetid: 17c09fc3-3ad7-47e2-8b48-ba8ae994edc8
ms.openlocfilehash: 467300501ffbbf8063e203d4c7395af34a954ed0
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301364"
---
# <a name="numeric-boolean-and-pointer-literals"></a>Littéraux numériques, booléens et de pointeur

Un littéral est un élément de programme qui représente directement une valeur. Cet article traite des littéraux de type entier, virgule flottante, booléen et de pointeur. Pour plus d’informations sur les littéraux de chaîne et de caractère, consultez [littéraux de chaîne et deC++caractère ()](../cpp/string-and-character-literals-cpp.md). Vous pouvez également définir vos propres littéraux en fonction de l’une de ces catégories. Pour plus d’informations [, consultez littéraux définis parC++l’utilisateur ()](../cpp/user-defined-literals-cpp.md) .

. Vous pouvez utiliser des littéraux dans de nombreux contextes, mais le plus souvent pour initialiser des variables nommées et passer des arguments à des fonctions :

```cpp
const int answer = 42; // integer literal
double d = sin(108.87);     //floating point literal passed to sin function
bool b = true;              // boolean literal
MyClass* mc = nullptr;      // pointer literal
```

Parfois, il est important indiquer au compilateur comment interpréter un littéral ou le type spécifique à lui affecter. Pour cela, ajoutez des préfixes ou suffixes au littéral. Par exemple, le préfixe 0x indique au compilateur d'interpréter le nombre qui le suit en tant que valeur hexadécimale, par exemple 0x35. Le suffixe d’extension indique au compilateur de traiter la valeur comme un type long long **non signé** , comme dans 5894345ULL. Consultez les sections suivantes pour obtenir la liste complète des préfixes et suffixes pour chaque type de littéral.

## <a name="integer-literals"></a>Littéraux d'entier

Les littéraux d'entier commencent par un chiffre et n'ont aucune partie fractionnaire ni exposant. Vous pouvez spécifier les littéraux d'entier sous forme décimale, octale ou hexadécimale. Ils peuvent spécifier des types signés ou non signés, longs ou courts.

Quand aucun préfixe ou suffixe n’est présent, le compilateur donne un littéral intégral de type valeur **int** (32 bits), si la valeur est ajustée. sinon, il lui donne le type **long** long (64 bits).

Pour spécifier un littéral intégral décimal, commencez la spécification par un chiffre différent de zéro. Par exemple :

```cpp
int i = 157;   // Decimal literal
int j = 0198;       // Not a decimal number; erroneous octal literal
int k = 0365;       // Leading zero specifies octal literal, not decimal
int m = 36'000'000  // digit separators make large values more readable
int
```

Pour spécifier un littéral intégral octal, commencez la spécification par 0, suivi d'une séquence de chiffres dans la plage 0 à 7. Les chiffres 8 et 9 sont des erreurs lors de la spécification d'un littéral octal. Par exemple :

```cpp
int i = 0377;   // Octal literal
int j = 0397;        // Error: 9 is not an octal digit
```

Pour spécifier un littéral intégral hexadécimal, commencez la spécification par `0x` ou `0X` (la casse de « x » n'a pas d'importance) suivi d'une séquence de chiffres dans la plage `0` à `9` et `a` (ou `A`) à `f` (ou `F`). Les chiffres hexadécimaux `a` (ou `A`) à `f` (ou `F`) représentent des valeurs dans la plage 10 à 15. Par exemple :

```cpp
int i = 0x3fff;   // Hexadecimal literal
int j = 0X3FFF;        // Equal to i
```

Pour spécifier un type non signé, utilisez le suffixe `u` ou `U`. Pour spécifier un type long, utilisez le suffixe `l` ou `L`. Pour spécifier un type intégral 64 bits, utilisez le suffixe LL ou ll. Le suffixe i64 est toujours pris en charge mais doit être évité, car il est spécifique à Microsoft et n'est pas portable. Par exemple :

```cpp
unsigned val_1 = 328u;             // Unsigned value
long val_2 = 0x7FFFFFL;                 // Long value specified
                                        //  as hex literal
unsigned long val_3 = 0776745ul;        // Unsigned long value
auto val_4 = 108LL;                           // signed long long
auto val_4 = 0x8000000000000000ULL << 16;     // unsigned long long
```

**Séparateurs de chiffres**: vous pouvez utiliser le caractère guillemet simple (apostrophe) pour séparer les valeurs de placement en plus grand nombre afin de faciliter la lecture des êtres humains. Les séparateurs n'ont pas d'effet sur la compilation.

```cpp
long long i = 24'847'458'121
```

## <a name="floating-point-literals"></a>Littéraux à virgule flottante

Les littéraux à virgule flottante spécifient des valeurs qui doivent avoir une partie fractionnaire. Ces valeurs contiennent des points décimaux ( **.** ) et peuvent contenir des exposants.

Les littéraux à virgule flottante ont une « mantisse », qui spécifie la valeur du nombre, un « exposant, » qui spécifie la grandeur du nombre, et un suffixe facultatif qui spécifie le type du littéral. La mantisse est spécifiée comme une séquence de chiffres suivis d'un point, suivie d'une séquence facultative de chiffres représentant la partie fractionnaire du nombre. Par exemple :

```cpp
18.46
38.
```

L'exposant, s'il est présent, spécifie la grandeur du nombre comme puissance de 10, comme indiqué dans l'exemple suivant :

```cpp
18.46e0      // 18.46
18.46e1           // 184.6
```

L’exposant peut être spécifié à l’aide de `e` ou `E`, qui ont la même signification, suivi d’un signe facultatif (+ ou-) et d’une séquence de chiffres.  Si un exposant est présent, la virgule décimale de fin est inutile dans les nombres entiers tels que `18E0`.

Par défaut, les littéraux à virgule flottante sont de type **double**. En utilisant les suffixes `f` ou `l` (ou `F` ou `L`, le suffixe ne respecte pas la casse), le littéral peut être spécifié respectivement comme **float** ou **long double**.

Bien que **long double** et **double** aient la même représentation, ils ne sont pas du même type. Par exemple, vous pouvez avoir des fonctions surchargées comme

```cpp
void func( double );
```

et

```cpp
void func( long double );
```

## <a name="boolean-literals"></a>Littéraux booléens

Les littéraux booléens sont **true** et **false**.

## <a name="pointer-literal-c11"></a>Littéral de pointeur (C++11)

C++présente le littéral [nullptr](../cpp/nullptr.md) pour spécifier un pointeur initialisé à zéro. Dans le code portable, **nullptr** doit être utilisé à la place de zéro de type intégral ou de macros telles que NULL.

## <a name="binary-literals-c14"></a>Littéraux binaires (C++14)

Un littéral binaire peut être spécifié à l'aide du préfixe `0B` ou `0b`, suivi d'une séquence de 1 et de 0 :

```cpp
auto x = 0B001101 ; // int
auto y = 0b000001 ; // int
```

## <a name="avoid-using-literals-as-magic-constants"></a>Évitez d'utiliser des littéraux en tant que « constantes magiques »

Vous pouvez utiliser des littéraux directement dans les expressions et instructions bien qu'il ne s'agisse pas toujours d'une bonne pratique de programmation :

```cpp
if (num < 100)
    return "Success";
```

Dans l'exemple précédent, il peut être préférable d'utiliser une constante nommée avec une signification claire, par exemple « MAXIMUM_ERROR_THRESHOLD ». De plus, si la valeur de retour « Opération réussie » est visible par les utilisateurs finaux, il peut être préférable d'utiliser une constante de chaîne nommée qui peut être stockée à un emplacement unique dans un fichier d'où elle peut être localisée dans d'autres langues. L'utilisation de constantes nommées permet à d'autres utilisateurs ainsi qu'à vous-même de comprendre l'objectif du code.

## <a name="see-also"></a>Voir aussi

[Conventions lexicales](../cpp/lexical-conventions.md)<br/>
[C++Littéraux de chaîne](../cpp/string-and-character-literals-cpp.md)<br/>
[C++Littéraux définis par l’utilisateur](../cpp/user-defined-literals-cpp.md)