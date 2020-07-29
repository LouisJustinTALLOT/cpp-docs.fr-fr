---
title: Littéraux définis par l’utilisateur (C++)
description: Décrit l’objectif et l’utilisation de littéraux définis par l’utilisateur en C++ standard.
ms.date: 02/10/2020
ms.assetid: ff4a5bec-f795-4705-a2c0-53788fd57609
ms.openlocfilehash: 21ed3db84f057131b0404d5f950a4419cb753070
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227047"
---
# <a name="user-defined-literals"></a>Littéraux définis par l’utilisateur

Il existe six catégories principales de littéraux en C++ : entier, caractère, virgule flottante, chaîne, booléen et pointeur. À partir de C++ 11, vous pouvez définir vos propres littéraux en fonction de ces catégories, afin de fournir des raccourcis syntaxiques pour les idiomes courants et accroître la sécurité des types. Par exemple, imaginons que vous avez une `Distance` classe. Vous pouvez définir un littéral pour les kilomètres et un autre pour les miles, et encourager l’utilisateur à être explicite sur les unités de mesure en écrivant : `auto d = 42.0_km` ou `auto d = 42.0_mi` . Les littéraux définis par l’utilisateur n’ont pas d’avantage en termes de performances ou d’inconvénient. ils sont principalement utilisés pour des raisons pratiques ou pour la déduction de type au moment de la compilation. La bibliothèque standard a des littéraux définis par l’utilisateur pour `std::string` , pour `std::complex` et pour les unités dans les opérations de temps et de durée dans l' \<chrono> en-tête :

```cpp
Distance d = 36.0_mi + 42.0_km;         // Custom UDL (see below)
std::string str = "hello"s + "World"s;  // Standard Library <string> UDL
complex<double> num =
   (2.0 + 3.01i) * (5.0 + 4.3i);        // Standard Library <complex> UDL
auto duration = 15ms + 42h;             // Standard Library <chrono> UDLs
```

## <a name="user-defined-literal-operator-signatures"></a>Signatures d'opérateur littéral défini par l'utilisateur

Vous implémentez un littéral défini par l’utilisateur en définissant un **opérateur «»** au niveau de la portée de l’espace de noms avec l’une des formes suivantes :

```cpp
ReturnType operator "" _a(unsigned long long int);   // Literal operator for user-defined INTEGRAL literal
ReturnType operator "" _b(long double);              // Literal operator for user-defined FLOATING literal
ReturnType operator "" _c(char);                     // Literal operator for user-defined CHARACTER literal
ReturnType operator "" _d(wchar_t);                  // Literal operator for user-defined CHARACTER literal
ReturnType operator "" _e(char16_t);                 // Literal operator for user-defined CHARACTER literal
ReturnType operator "" _f(char32_t);                 // Literal operator for user-defined CHARACTER literal
ReturnType operator "" _g(const char*, size_t);      // Literal operator for user-defined STRING literal
ReturnType operator "" _h(const wchar_t*, size_t);   // Literal operator for user-defined STRING literal
ReturnType operator "" _i(const char16_t*, size_t);  // Literal operator for user-defined STRING literal
ReturnType operator "" _g(const char32_t*, size_t);  // Literal operator for user-defined STRING literal
ReturnType operator "" _r(const char*);              // Raw literal operator
template<char...> ReturnType operator "" _t();       // Literal operator template
```

Les noms d'opérateur dans l'exemple précédent sont des espaces réservés pour le nom que vous fournissez ; toutefois, le caractère de soulignement de début est requis. (Seule la bibliothèque standard est autorisée à définir des littéraux sans le trait de soulignement.) Le type de retour est l’endroit où vous personnalisez la conversion ou d’autres opérations effectuées par le littéral. En outre, chacun de ces opérateurs peut être défini comme **`constexpr`** .

## <a name="cooked-literals"></a>Littéraux traités

Dans le code source, tout littéral, qu’il soit ou non défini par l’utilisateur, est essentiellement une séquence de caractères alphanumériques, tels que `101` , ou `54.7` `"hello"` **`true`** . Le compilateur interprète la séquence comme une chaîne entière, flottante, const char \* , et ainsi de suite. Un littéral défini par l’utilisateur qui accepte comme entrée quel que soit le type que le compilateur assigne à la valeur littérale est informellement connu sous le nom de *littéral cuit*. Tous les opérateurs ci-dessus, à l'exception de `_r` et `_t`, sont des littéraux traités. Par exemple, un littéral `42.0_km` établit une liaison avec un opérateur nommé _km ayant une signature similaire à _b et le littéral `42_km` établit une liaison avec un opérateur ayant une signature similaire à _a.

L'exemple suivant montre comment des littéraux définis par l'utilisateur peuvent encourager les appelants à être explicites sur leur entrée. Pour créer une `Distance`, l'utilisateur doit spécifier explicitement des kilomètres ou des miles à l'aide du littéral défini par l'utilisateur approprié. Vous pouvez obtenir le même résultat d’une manière ou d’une autre, mais les littéraux définis par l’utilisateur sont moins détaillés que les alternatives.

```cpp
// UDL_Distance.cpp

#include <iostream>
#include <string>

struct Distance
{
private:
    explicit Distance(long double val) : kilometers(val)
    {}

    friend Distance operator"" _km(long double val);
    friend Distance operator"" _mi(long double val);

    long double kilometers{ 0 };
public:
    const static long double km_per_mile;
    long double get_kilometers() { return kilometers; }

    Distance operator+(Distance other)
    {
        return Distance(get_kilometers() + other.get_kilometers());
    }
};

const long double Distance::km_per_mile = 1.609344L;

Distance operator"" _km(long double val)
{
    return Distance(val);
}

Distance operator"" _mi(long double val)
{
    return Distance(val * Distance::km_per_mile);
}

int main()
{
    // Must have a decimal point to bind to the operator we defined!
    Distance d{ 402.0_km }; // construct using kilometers
    std::cout << "Kilometers in d: " << d.get_kilometers() << std::endl; // 402

    Distance d2{ 402.0_mi }; // construct using miles
    std::cout << "Kilometers in d2: " << d2.get_kilometers() << std::endl;  //646.956

    // add distances constructed with different units
    Distance d3 = 36.0_mi + 42.0_km;
    std::cout << "d3 value = " << d3.get_kilometers() << std::endl; // 99.9364

    // Distance d4(90.0); // error constructor not accessible

    std::string s;
    std::getline(std::cin, s);
    return 0;
}
```

Le nombre littéral doit utiliser une valeur décimale. Dans le cas contraire, le nombre est interprété comme un entier et le type ne sera pas compatible avec l’opérateur. Pour une entrée à virgule flottante, le type doit être **`long double`** , et pour les types intégraux, il doit être **`long long`** .

## <a name="raw-literals"></a>Littéraux bruts

Dans un littéral défini par l’utilisateur brut, l’opérateur que vous définissez accepte le littéral sous la forme d’une séquence de valeurs char. C’est à vous d’interpréter cette séquence comme un nombre ou une chaîne ou un autre type. Dans la liste des opérateurs présentée plus haut dans cette page, `_r` et `_t` peuvent être utilisés pour définir des littéraux bruts :

```cpp
ReturnType operator "" _r(const char*);              // Raw literal operator
template<char...> ReturnType operator "" _t();       // Literal operator template
```

Vous pouvez utiliser des littéraux bruts pour fournir une interprétation personnalisée d’une séquence d’entrée différente du comportement normal du compilateur. Par exemple, vous pouvez définir un littéral qui convertit la séquence `4.75987` en un type Decimal personnalisé au lieu d'un type à virgule flottante IEEE 754. Les littéraux bruts, comme les littéraux cuits, peuvent également être utilisés pour la validation au moment de la compilation des séquences d’entrée.

### <a name="example-limitations-of-raw-literals"></a>Exemple : limitations des littéraux bruts

L'opérateur littéral brut et le modèle d'opérateur littéral ne fonctionnent que pour les littéraux définis par l'utilisateur intégraux et à virgule flottante, comme le montre l'exemple suivant :

```cpp
#include <cstddef>
#include <cstdio>

// Literal operator for user-defined INTEGRAL literal
void operator "" _dump(unsigned long long int lit)
{
    printf("operator \"\" _dump(unsigned long long int) : ===>%llu<===\n", lit);
};

// Literal operator for user-defined FLOATING literal
void operator "" _dump(long double lit)
{
    printf("operator \"\" _dump(long double)            : ===>%Lf<===\n",  lit);
};

// Literal operator for user-defined CHARACTER literal
void operator "" _dump(char lit)
{
    printf("operator \"\" _dump(char)                   : ===>%c<===\n",   lit);
};

void operator "" _dump(wchar_t lit)
{
    printf("operator \"\" _dump(wchar_t)                : ===>%d<===\n",   lit);
};

void operator "" _dump(char16_t lit)
{
    printf("operator \"\" _dump(char16_t)               : ===>%d<===\n",   lit);
};

void operator "" _dump(char32_t lit)
{
    printf("operator \"\" _dump(char32_t)               : ===>%d<===\n",   lit);
};

// Literal operator for user-defined STRING literal
void operator "" _dump(const     char* lit, size_t)
{
    printf("operator \"\" _dump(const     char*, size_t): ===>%s<===\n",   lit);
};

void operator "" _dump(const  wchar_t* lit, size_t)
{
    printf("operator \"\" _dump(const  wchar_t*, size_t): ===>%ls<===\n",  lit);
};

void operator "" _dump(const char16_t* lit, size_t)
{
    printf("operator \"\" _dump(const char16_t*, size_t):\n"                  );
};

void operator "" _dump(const char32_t* lit, size_t)
{
    printf("operator \"\" _dump(const char32_t*, size_t):\n"                  );
};

// Raw literal operator
void operator "" _dump_raw(const char* lit)
{
    printf("operator \"\" _dump_raw(const char*)        : ===>%s<===\n",   lit);
};

template<char...> void operator "" _dump_template();       // Literal operator template

int main(int argc, const char* argv[])
{
    42_dump;
    3.1415926_dump;
    3.14e+25_dump;
     'A'_dump;
    L'B'_dump;
    u'C'_dump;
    U'D'_dump;
      "Hello World"_dump;
     L"Wide String"_dump;
    u8"UTF-8 String"_dump;
     u"UTF-16 String"_dump;
     U"UTF-32 String"_dump;
    42_dump_raw;
    3.1415926_dump_raw;
    3.14e+25_dump_raw;

    // There is no raw literal operator or literal operator template support on these types:
    //  'A'_dump_raw;
    // L'B'_dump_raw;
    // u'C'_dump_raw;
    // U'D'_dump_raw;
    //   "Hello World"_dump_raw;
    //  L"Wide String"_dump_raw;
    // u8"UTF-8 String"_dump_raw;
    //  u"UTF-16 String"_dump_raw;
    //  U"UTF-32 String"_dump_raw;
}
```

```Output
operator "" _dump(unsigned long long int) : ===>42<===
operator "" _dump(long double)            : ===>3.141593<===
operator "" _dump(long double)            : ===>31399999999999998506827776.000000<===
operator "" _dump(char)                   : ===>A<===
operator "" _dump(wchar_t)                : ===>66<===
operator "" _dump(char16_t)               : ===>67<===
operator "" _dump(char32_t)               : ===>68<===
operator "" _dump(const     char*, size_t): ===>Hello World<===
operator "" _dump(const  wchar_t*, size_t): ===>Wide String<===
operator "" _dump(const     char*, size_t): ===>UTF-8 String<===
operator "" _dump(const char16_t*, size_t):
operator "" _dump(const char32_t*, size_t):
operator "" _dump_raw(const char*)        : ===>42<===
operator "" _dump_raw(const char*)        : ===>3.1415926<===
operator "" _dump_raw(const char*)        : ===>3.14e+25<===
```
