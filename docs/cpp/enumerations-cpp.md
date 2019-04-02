---
title: Énumérations (C++)
ms.date: 06/01/2018
f1_keywords:
- enum_cpp
helpviewer_keywords:
- declarations, enumerations
- enumerators, declaring
- enum keyword [C++]
- named constants, enumeration declarations
- declaring enumerations
ms.assetid: 081829db-5dca-411e-a53c-bffef315bcb3
ms.openlocfilehash: caec9ea7ac5482ff23b73676a3fd7b3d25ad293f
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58772563"
---
# <a name="enumerations-c"></a>Énumérations (C++)

Une énumération est un type défini par l'utilisateur qui se compose d'un jeu de constantes intégrales nommées, appelées énumérateurs.

> [!NOTE]
>  Cet article couvre le langage C++ de la norme ISO **enum** type et l’étendue (ou fortement typé) **classe enum** type qui a été introduit dans C ++ 11. Pour plus d’informations sur la **classe enum publique** ou **privé enum, classe** types en C / c++ / CLI et c++ / CX, consultez [enum, classe](../extensions/enum-class-cpp-component-extensions.md).

## <a name="syntax"></a>Syntaxe

```
// unscoped enum:
enum [identifier] [: type]
{enum-list};

// scoped enum:
enum [class|struct]
[identifier] [: type]
{enum-list};
```

```cpp
// Forward declaration of enumerations  (C++11):
enum A : int; // non-scoped enum must have type specified
enum class B; // scoped enum defaults to int but ...
enum class C : short;  // ... may have any integral underlying type
```

## <a name="parameters"></a>Paramètres

*identifier*<br/>
Nom de type donné à l'énumération.

*type*<br/>
Type sous-jacent des énumérateurs ; tous les énumérateurs ont le même type sous-jacent. Peut être tout type intégral.

*enum-list*<br/>
Liste délimitée par des virgules des énumérateurs dans l'énumération. Chaque nom d'énumérateur ou de variable dans la portée doit être unique. Toutefois, les valeurs peuvent être dupliquées. Dans un enum non délimité, la portée est la portée environnante ; dans un enum délimité, la portée est la *liste d’énumération* lui-même.  Dans un enum délimité, la liste peut être vide qui définit ce qui entraîne un nouveau type intégral.

*class*<br/>
À l’aide de ce mot clé dans la déclaration, vous spécifiez l’enum est délimité et un *identificateur* doit être fourni. Vous pouvez également utiliser le **struct** mot clé à la place de **classe**, car ils sont sémantiquement équivalentes dans ce contexte.

## <a name="enumerator-scope"></a>Étendue de l’énumérateur

Une énumération fournit un contexte pour décrire une plage de valeurs qui sont représentées en tant que constantes nommées, également appelées « énumérateurs ». Dans les types d'enum C et C++ d'origine, les énumérateurs non qualifiés sont visibles dans toute la portée dans laquelle l'enum est déclaré. Dans les enums délimités, le nom de l'énumérateur doit être qualifié par le nom du type d'enum. L'exemple suivant illustre cette différence fondamentale entre les deux genres d'enums :

```cpp
namespace CardGame_Scoped
{
    enum class Suit { Diamonds, Hearts, Clubs, Spades };

    void PlayCard(Suit suit)
    {
        if (suit == Suit::Clubs) // Enumerator must be qualified by enum type
        { /*...*/}
    }
}

namespace CardGame_NonScoped
{
    enum Suit { Diamonds, Hearts, Clubs, Spades };

    void PlayCard(Suit suit)
    {
        if (suit == Clubs) // Enumerator is visible without qualification
        { /*...*/
        }
    }
}
```

À chaque nom d'une énumération est assignée une valeur entière qui correspond à sa place dans l'ordre des valeurs de l'énumération. Par défaut, la première valeur est 0, la suivante 1, et ainsi de suite, mais vous pouvez définir explicitement la valeur d'un énumérateur, comme indiqué ci-dessous :

```cpp
enum Suit { Diamonds = 1, Hearts, Clubs, Spades };
```

L'énumérateur `Diamonds` reçoit la valeur `1`. Les énumérateurs suivants, si aucune valeur explicite ne leur est assignée, reçoivent la valeur de l'énumérateur précédent incrémentée d'une unité. Dans l'exemple précédent, `Hearts` aurait la valeur 2, `Clubs` aurait la valeur 3, et ainsi de suite.

Chaque énumérateur est traité comme une constante et doit avoir un nom unique dans l’étendue où le **enum** est défini (pour les enums non délimités) ou à l’intérieur du **enum** lui-même (pour les enums délimités). Il n'est pas obligatoire que les valeurs fournies aux noms soient uniques. Par exemple, si la déclaration d'un enum non délimité `Suit` est la suivante :

```cpp
enum Suit { Diamonds = 5, Hearts, Clubs = 4, Spades };
```

Les valeurs de `Diamonds`, `Hearts`, `Clubs` et `Spades` sont respectivement 5, 6, 4 et 5. Notez que 5 est utilisé plusieurs fois ; cela est autorisé même si ce n'est peut-être pas prévu. Ces règles sont les mêmes pour les enums délimités.

## <a name="casting-rules"></a>Règles de transtypage

Les constantes enum non délimité peuvent être convertis implicitement en **int**, mais un **int** n’est jamais implicitement convertible en une valeur enum. L'exemple suivant montre ce qui se produit si vous essayez d'assigner à `hand` une valeur qui n'est pas un `Suit` :

```cpp
int account_num = 135692;
Suit hand;
hand = account_num; // error C2440: '=' : cannot convert from 'int' to 'Suit'
```

Un cast est nécessaire pour convertir un **int** à un énumérateur délimité ou. Toutefois, vous pouvez promouvoir un énumérateur non délimité en valeur entière sans transtypage.

```cpp
int account_num = Hearts; //OK if Hearts is in a unscoped enum
```

L'utilisation des conversions implicites de cette façon peut provoquer des effets secondaires inattendus. Pour aider à éliminer les erreurs de programmation associées aux enums non délimités, les valeurs d'enums délimités sont fortement typées. Les énumérateurs délimités doivent être qualifiés par le nom du type d'enum (identificateur) et ne peuvent pas être implicitement convertis, comme indiqué dans l'exemple suivant :

```cpp
namespace ScopedEnumConversions
{
    enum class Suit { Diamonds, Hearts, Clubs, Spades };

    void AttemptConversions()
    {
        Suit hand;
        hand = Clubs; // error C2065: 'Clubs' : undeclared identifier
        hand = Suit::Clubs; //Correct.
        int account_num = 135692;
        hand = account_num; // error C2440: '=' : cannot convert from 'int' to 'Suit'
        hand = static_cast<Suit>(account_num); // OK, but probably a bug!!!

        account_num = Suit::Hearts; // error C2440: '=' : cannot convert from 'Suit' to 'int'
        account_num = static_cast<int>(Suit::Hearts); // OK
    }
}
```

Notez que la ligne `hand = account_num;` provoque toujours l'erreur avec les enums non délimités, comme indiqué précédemment. Elle est autorisée avec un transtypage explicite. Toutefois, avec les enums délimités, la tentative de conversion dans l'instruction suivante, `account_num = Suit::Hearts;`, n'est plus autorisée sans transtypage explicite.

## <a name="no_enumerators"></a> Enums avec aucun énumérateurs

**Visual Studio 2017 15.3 et versions ultérieures** (disponible avec [/std : c ++ 17](../build/reference/std-specify-language-standard-version.md)) : En définissant un enum (standard ou étendu) avec un type sous-jacent explicit et aucune énumérateurs, vous pouvez en effet introduire un nouveau type intégral qui n’a aucune conversion implicite en un autre type. À l’aide de ce type au lieu de son type sous-jacent intégré, vous pouvez éliminer le potentiel des erreurs subtiles provoquées par les conversions implicites par inadvertance.

```cpp
enum class byte : unsigned char { };
```

Le nouveau type est une copie exacte du type sous-jacent et par conséquent a la même convention d’appel, ce qui signifie qu’il peut être utilisé sur ABI sans toute altération des performances. Aucune conversion n’est requise lorsque les variables de type sont initialisées à l’aide de l’initialisation de liste de direct. L’exemple suivant montre comment initialiser les enums avec aucun énumérateurs dans différents contextes :

```cpp
enum class byte : unsigned char { };

enum class E : int { };
E e1{ 0 };
E e2 = E{ 0 };

struct X
{
    E e{ 0 };
    X() : e{ 0 } { }
};

E* p = new E{ 0 };

void f(E e) {};

int main()
{
    f(E{ 0 });
    byte i{ 42 };
    byte j = byte{ 42 };

    // unsigned char c = j; // C2440: 'initializing': cannot convert from 'byte' to 'unsigned char'
    return 0;
}
```

## <a name="see-also"></a>Voir aussi

[Déclarations d’énumération C](../c-language/c-enumeration-declarations.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)