---
title: Littéraux (C++) défini par l’utilisateur | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: ff4a5bec-f795-4705-a2c0-53788fd57609
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 76eac97c6d545f37ca13c640c80200e95a1938f9
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43208381"
---
# <a name="user-defined-literals--c"></a>Littéraux définis par l’utilisateur (C++)

Il existe cinq catégories principales de littéraux : entier, caractère, virgule flottante, booléen et pointeur.  Depuis C++11, vous pouvez définir vos propres littéraux en fonction de ces catégories pour fournir des raccourcis syntaxiques aux idiomes courants et augmenter la sécurité de type. Par exemple, supposons que vous avez une classe Distance. Vous pouvez définir un littéral pour les kilomètres et un autre pour les miles, et encourager l'utilisateur à être explicite sur les unités de mesure en écrivant simplement : d auto = 42,0_km ou d auto = 42,0_mi. Les littéraux définis par l’utilisateur ne présentent aucun avantage ni inconvénient en termes de performances ; ils sont principalement utilisés pour des raisons pratiques ou pour la déduction de type au moment de la compilation. La bibliothèque Standard a des littéraux définis par l’utilisateur pour std : String, std::Complex et pour les unités et la durée des opérations dans le \<chrono > en-tête :

```cpp
Distance d = 36.0_mi + 42.0_km;         // Custom UDL (see below)
    std::string str = "hello"s + "World"s;  // Standard Library <string> UDL
    complex<double> num =
        (2.0 + 3.01i) * (5.0 + 4.3i);       // Standard Library <complex> UDL
    auto duration = 15ms + 42h;             // Standard Library <chrono> UDLs
```

## <a name="user-defined-literal-operator-signatures"></a>Signatures d'opérateur littéral défini par l'utilisateur

Vous implémentez un littéral défini par l’utilisateur en définissant un **opérateur » «** à portée de l’espace de noms avec l’une des formes suivantes :

```cpp
ReturnType operator "" _a(unsigned long long int);   // Literal operator for user-defined INTEGRAL literal
ReturnType operator "" _b(long double);              // Literal operator for user-defined FLOATING literal
ReturnType operator "" _c(char);                     // Literal operator for user-defined CHARACTER literal
ReturnType operator "" _d(wchar_t);                  // Literal operator for user-defined CHARACTER literal
ReturnType operator "" _e(char16_t);                 // Literal operator for user-defined CHARACTER literal
ReturnType operator "" _f(char32_t);                 // Literal operator for user-defined CHARACTER literal
ReturnType operator "" _g(const     char*, size_t);  // Literal operator for user-defined STRING literal
ReturnType operator "" _h(const  wchar_t*, size_t);  // Literal operator for user-defined STRING literal
ReturnType operator "" _i(const char16_t*, size_t);  // Literal operator for user-defined STRING literal
ReturnType operator "" _g(const char32_t*, size_t);  // Literal operator for user-defined STRING literal
ReturnType operator "" _r(const char*);              // Raw literal operator
template<char...> ReturnType operator "" _t();       // Literal operator template
```

Les noms d'opérateur dans l'exemple précédent sont des espaces réservés pour le nom que vous fournissez ; toutefois, le caractère de soulignement de début est requis. (Seule la bibliothèque standard est autorisée à définir des littéraux sans le caractère de soulignement.) Le type de retour correspond à l'emplacement où vous personnalisez la conversion ou toute autre opération effectuée par le littéral. En outre, chacun de ces opérateurs peut être défini en tant que `constexpr`.

## <a name="cooked-literals"></a>Littéraux traités

Dans le code source, n'importe quel littéral défini ou non par l'utilisateur est essentiellement une séquence de caractères alphanumériques, comme `101`, ou `54.7`, ou `"hello"` ou `true`. Le compilateur interprète la séquence comme un entier, float, const char\* chaîne et ainsi de suite. Un littéral défini par l’utilisateur qui accepte comme entrée le type renvoyé par le compilateur a assigné à la valeur littérale est officieusement appelé un *littéral cuit*. Tous les opérateurs ci-dessus, à l'exception de `_r` et `_t`, sont des littéraux traités. Par exemple, un littéral `42.0_km` établit une liaison avec un opérateur nommé _km ayant une signature similaire à _b et le littéral `42_km` établit une liaison avec un opérateur ayant une signature similaire à _a.

L'exemple suivant montre comment des littéraux définis par l'utilisateur peuvent encourager les appelants à être explicites sur leur entrée. Pour créer une `Distance`, l'utilisateur doit spécifier explicitement des kilomètres ou des miles à l'aide du littéral défini par l'utilisateur approprié. Bien sûr, vous pouvez également obtenir le même résultat par d'autres moyens, mais les littéraux définis par l'utilisateur sont moins détaillés que les alternatives.

```cpp
struct Distance
{
private:
    explicit Distance(long double val) : kilometers(val)
    {}

    friend Distance operator"" _km(long double  val);
    friend Distance operator"" _mi(long double val);
    long double kilometers{ 0 };
public:
    long double get_kilometers() { return kilometers; }
    Distance operator+(Distance& other)
    {
        return Distance(get_kilometers() + other.get_kilometers());
    }
};

Distance operator"" _km(long double  val)
{
    return Distance(val);
}

Distance operator"" _mi(long double val)
{
    return Distance(val * 1.6);
}
int main(int argc, char* argv[])
{
    // Must have a decimal point to bind to the operator we defined!
    Distance d{ 402.0_km }; // construct using kilometers
    cout << "Kilometers in d: " << d.get_kilometers() << endl; // 402

    Distance d2{ 402.0_mi }; // construct using miles
    cout << "Kilometers in d2: " << d2.get_kilometers() << endl;  //643.2

    // add distances constructed with different units
    Distance d3 = 36.0_mi + 42.0_km;
    cout << "d3 value = " << d3.get_kilometers() << endl; // 99.6

    // Distance d4(90.0); // error constructor not accessible

    string s;
    getline(cin, s);
    return 0;
}
```

Notez que le nombre littéral doit utiliser une valeur décimale, sinon il serait interprété en tant qu'entier et le type ne serait pas compatible avec l'opérateur. Notez également que, pour l’entrée à virgule flottante, le type doit être **long double**et pour les types intégraux, il doit être **longue**.

## <a name="raw-literals"></a>Littéraux bruts

Dans un littéral défini par l'utilisateur brut, l'opérateur que vous définissez accepte le littéral comme une séquence de valeurs char. Il vous revient d'interpréter cette séquence comme un nombre, une chaîne ou tout autre type. Dans la liste des opérateurs présentée plus haut dans cette page, `_r` et `_t` peuvent être utilisés pour définir des littéraux bruts :

```cpp
ReturnType operator "" _r(const char*);              // Raw literal operator
template<char...> ReturnType operator "" _t();       // Literal operator template
```

Vous pouvez utiliser des littéraux bruts pour fournir une interprétation personnalisée d'une séquence d'entrée différente de celle que le compilateur exécute. Par exemple, vous pouvez définir un littéral qui convertit la séquence `4.75987` en un type Decimal personnalisé au lieu d'un type à virgule flottante IEEE 754. Les littéraux bruts, comme les littéraux traités, peuvent également servir à effectuer la validation lors de la compilation des séquences d’entrée.

### <a name="example-limitations-of-raw-literals"></a>Exemple : Les Limitations des littéraux bruts

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