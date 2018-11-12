---
title: Littéraux de chaîne et caractère (C++)
ms.date: 11/04/2016
f1_keywords:
- R
helpviewer_keywords:
- L constant
- escape sequences
- Null strings, null-terminated strings
- literal strings, C++
- Null strings
- string literals, syntax
- string literals
- literal strings
- strings [C++], string literals
- NULL, character constant
- wide characters, strings
ms.assetid: 61de8f6f-2714-4e7b-86b6-a3f885d3b9df
ms.openlocfilehash: 787756dd3e886afb6afa87ed3871158bddcbf3ae
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50614589"
---
# <a name="string-and-character-literals--c"></a>Littéraux de chaîne et caractère (C++)

C++ prend en charge divers types de chaîne et de caractère, et fournit les moyens d'exprimer les valeurs littérales de chacun de ces types. Dans votre code source, vous exprimez le contenu de vos littéraux de caractère et de chaîne à l’aide d’un jeu de caractères. Les noms de caractères universels et les caractères d’échappement vous permettent d’exprimer une chaîne en utilisant uniquement le jeu de caractères sources de base. Un littéral de chaîne brut vous permet d'éviter d'utiliser des caractères d'échappement et peut servir à exprimer tous les types de littéral de chaîne. Vous pouvez également créer des littéraux std::string sans avoir à effectuer d’étapes de conversion ou de construction supplémentaires.

```cpp
#include <string>
using namespace std::string_literals; // enables s-suffix for std::string literals

int main()
{
    // Character literals
    auto c0 =   'A'; // char
    auto c1 = u8'A'; // char
    auto c2 =  L'A'; // wchar_t
    auto c3 =  u'A'; // char16_t
    auto c4 =  U'A'; // char32_t

    // String literals
    auto s0 =   "hello"; // const char*
    auto s1 = u8"hello"; // const char*, encoded as UTF-8
    auto s2 =  L"hello"; // const wchar_t*
    auto s3 =  u"hello"; // const char16_t*, encoded as UTF-16
    auto s4 =  U"hello"; // const char32_t*, encoded as UTF-32

    // Raw string literals containing unescaped \ and "
    auto R0 =   R"("Hello \ world")"; // const char*
    auto R1 = u8R"("Hello \ world")"; // const char*, encoded as UTF-8
    auto R2 =  LR"("Hello \ world")"; // const wchar_t*
    auto R3 =  uR"("Hello \ world")"; // const char16_t*, encoded as UTF-16
    auto R4 =  UR"("Hello \ world")"; // const char32_t*, encoded as UTF-32

    // Combining string literals with standard s-suffix
    auto S0 =   "hello"s; // std::string
    auto S1 = u8"hello"s; // std::string
    auto S2 =  L"hello"s; // std::wstring
    auto S3 =  u"hello"s; // std::u16string
    auto S4 =  U"hello"s; // std::u32string

    // Combining raw string literals with standard s-suffix
    auto S5 =   R"("Hello \ world")"s; // std::string from a raw const char*
    auto S6 = u8R"("Hello \ world")"s; // std::string from a raw const char*, encoded as UTF-8
    auto S7 =  LR"("Hello \ world")"s; // std::wstring from a raw const wchar_t*
    auto S8 =  uR"("Hello \ world")"s; // std::u16string from a raw const char16_t*, encoded as UTF-16
    auto S9 =  UR"("Hello \ world")"s; // std::u32string from a raw const char32_t*, encoded as UTF-32
}
```

Il est possible que les littéraux de chaîne n’aient aucun préfixe, ou qu’ils aient les préfixes `u8`, `L`, `u`et  `U` pour désigner un caractère étroit (codé sur un ou plusieurs octets), UTF-8, un caractère large (UCS-2 ou UTF-16), ainsi que les encodages UTF-16 et UTF-32, respectivement. Un littéral de chaîne brut peut avoir les préfixes `R`, `u8R`, `LR`, `uR` et `UR` pour les équivalents en version brute de ces encodages.  Pour créer des valeurs std::string temporaires ou statiques, vous pouvez utiliser des littéraux de chaîne ou des littéraux de chaîne bruts avec un suffixe `s` . Pour plus d’informations, consultez la section Littéraux de chaîne ci-dessous. Pour plus d’informations sur le jeu de caractères sources de base, les noms de caractères universels et l’utilisation de caractères de pages de codes étendues dans votre code source, consultez [Character Sets](../cpp/character-sets.md).

## <a name="character-literals"></a>Littéraux de caractère

Un *littéral de caractère* est composé d'une constante caractère. Elle est représentée par le caractère entouré de guillemets-apostrophes. Il existe cinq types de littéraux de caractère :

- Littéraux de caractère ordinaire de type **char**, par exemple `'a'`

- Littéraux de caractères UTF-8 de type **char**, par exemple `u8'a'`

- Littéraux de caractères étendus de type `wchar_t`, par exemple `L'a'`

- Littéraux de caractère UTF-16 de type `char16_t`, par exemple `u'a'`

- Littéraux de caractère UTF-32 de type `char32_t`, par exemple `U'a'`

Le caractère utilisé pour un littéral de caractère peut être n’importe quel caractère, à l’exception de la barre oblique inverse les caractères réservés ('\\'), guillemet-apostrophe ('), ou nouvelle ligne. Les caractères réservés peuvent être spécifiés à l’aide d’une séquence d’échappement. Vous pouvez spécifier des caractères à l’aide des noms de caractères universels, tant que le type est suffisamment grand pour contenir le caractère.

### <a name="encoding"></a>Encodage

Littéraux de caractère sont codés différemment en fonction de leur préfixe.

- Un caractère littéral sans préfixe est un littéral de caractère ordinaire. La valeur d’un littéral de caractère ordinaire contenant un seul caractère, séquence d’échappement, ou nom de caractère universel qui peut être représenté dans le jeu de caractères d’exécution a une valeur égale à la valeur numérique de son encodage dans le jeu de caractères d’exécution. Un littéral de caractère ordinaire qui contient plusieurs caractères, séquence d’échappement ou nom de caractère universel est un *à multiples caractères littérale*. Un littéral à multiples caractères ou un littéral de caractère ordinaire qui ne peut pas être représenté dans le jeu de caractères d’exécution est conditionnelle pris en charge, est de type int, et sa valeur est définie par l’implémentation.

- Un littéral de caractère qui commence par le préfixe L est un littéral de caractère large. La valeur d’un littéral de caractère large qui contient un caractère unique, la séquence d’échappement ou le nom de caractère universel a une valeur égale à la valeur numérique de son encodage dans l’exécution à l’échelle-jeu de caractères, sauf si le littéral de caractère n’a aucune représentation le l’exécution à l’échelle-jeu de caractères, auquel cas la valeur est définie par l’implémentation. La valeur d’un littéral de caractère large contenant plusieurs caractères, des séquences d’échappement ou des noms de caractères universels est défini par l’implémentation.

- Un littéral de caractère qui commence par le préfixe u8 est un littéral de caractère UTF-8. Séquence d’échappement contenant un seul caractère, la valeur d’un littéral de caractère UTF-8, ou nom de caractère universel a une valeur égale à sa valeur de point de code ISO 10646 si elle peut être représentée par une seule unité de code UTF-8 (correspondant aux contrôles de C0 et Latin de base Bloc Unicode). Si la valeur ne peut pas être représentée par une seule unité de code UTF-8, le programme est incorrect. Un littéral contenant plusieurs caractères, séquence d’échappement ou nom de caractère universel de caractères UTF-8 est incorrect.

- Un littéral de caractère qui commence par le préfixe u est un littéral de caractère UTF-16. Séquence d’échappement contenant un seul caractère, la valeur d’un littéral de caractère UTF-16 ou nom de caractère universel a une valeur égale à sa valeur de point de code ISO 10646 si elle peut être représentée par une seule unité de code UTF-16 (correspondant au plan multilingue de base ). Si la valeur ne peut pas être représentée par une seule unité de code UTF-16, le programme est incorrect. Un caractère UTF-16 littéral contenant plusieurs caractères, séquence d’échappement ou nom de caractère universel est incorrect.

- Un littéral de caractère qui commence par le préfixe U est un littéral de caractère UTF-32. Séquence d’échappement contenant un seul caractère, la valeur d’un littéral de caractère UTF-32, ou nom de caractère universel a une valeur égale à sa valeur de point de code ISO 10646. Un littéral contenant plusieurs caractères, séquence d’échappement ou nom de caractère universel de caractères UTF-8 est incorrect.

###  <a name="bkmk_Escape"></a> Séquences d'échappement

Il existe trois types de séquence d’échappement : simple, octal et hexadécimal. Les séquences d'échappement peuvent être de l'une des formes suivantes :

|Valeur|Séquence d'échappement|Value|Séquence d'échappement|
|-----------|---------------------|-----------|---------------------|
|saut de ligne|\n|barre oblique inverse|\\\|
|tabulation horizontale|\t|point d'interrogation|? ou \\?|
|tabulation verticale|\v|guillemet simple|\\'|
|retour arrière|\b|guillemet double|\\"|
|retour chariot|\r|caractère Null|\0|
|saut de page|\f|octal|\ooo|
|alerte (clochette)|\a|hexadécimal|\xhhh|

Le code suivant présente quelques exemples de caractères d’échappement à l’aide de littéraux de caractère ordinaire. La même syntaxe de séquence d’échappement est valide pour les autres types de littéral caractères.

```cpp
#include <iostream>
using namespace std;

int main() {
    char newline = '\n';
    char tab = '\t';
    char backspace = '\b';
    char backslash = '\\';
    char nullChar = '\0';

    cout << "Newline character: " << newline << "ending" << endl; // Newline character:
                                                                  //  ending
    cout << "Tab character: " << tab << "ending" << endl; // Tab character : ending
    cout << "Backspace character: " << backspace << "ending" << endl; // Backspace character : ending
    cout << "Backslash character: " << backslash << "ending" << endl; // Backslash character : \ending
    cout << "Null character: " << nullChar << "ending" << endl; //Null character:  ending
}
```

**Section spécifique à Microsoft**

Pour créer une valeur à partir d’un littéral de caractère ordinaire (celles sans préfixe), le compilateur convertit le caractère ou une séquence de caractères entre guillemets simples en valeurs 8 bits au sein d’un entier 32 bits. Plusieurs caractères dans le littéral remplissent les octets correspondants selon les besoins, des octets de poids fort aux octets poids faible. Pour créer un **char** valeur, le compilateur prend l’octet de poids faible. Pour créer un **wchar_t** ou `char16_t` valeur, le compilateur prend le mot de poids faible. Le compilateur avertit que le résultat est tronqué si tous les bits sont définis au-dessus de l’octet ou du mot assigné.

```cpp
char c0    = 'abcd';    // C4305, C4309, truncates to 'd'
wchar_t w0 = 'abcd';    // C4305, C4309, truncates to '\x6364'
```

Une séquence d'échappement octale est une barre oblique inverse suivie de trois chiffres octaux maximum. Une séquence d’échappement octale qui contient plus de trois chiffres est considérée comme une séquence octale à 3 chiffres suivie de caractères. Cela peut entraîner des résultats inattendus. Exemple :

```cpp
char c1 = '\100';   // '@'
char c2 = '\1000';  // C4305, C4309, truncates to '0'
```

Les séquences d’échappement qui contiennent des caractères non octaux sont évaluées sous forme de séquences octales jusqu’au dernier caractère octal, suivi des caractères restants. Exemple :

```cpp
char c3 = '\009';   // '9'
char c4 = '\089';   // C4305, C4309, truncates to '9'
char c5 = '\qrs';   // C4129, C4305, C4309, truncates to 's'
```

Une séquence d'échappement hexadécimale est une barre oblique inverse suivie du caractère `x`, suivi d'une séquence de chiffres hexadécimaux. Une séquence d'échappement qui ne contient aucun chiffre hexadécimal provoque l'erreur du compilateur C2153 : « Les littéraux hexadécimaux doivent comporter au moins un chiffre hexadécimal ». Les zéros non significatifs sont ignorés. Une séquence d’échappement qui contient des caractères hexadécimaux et non hexadécimaux est évaluée sous forme de séquence d’échappement hexadécimale jusqu’au dernier caractère hexadécimal, suivi des caractères non hexadécimaux.   Dans un caractère ordinaire ou le préfixe u8 littéral, la valeur hexadécimale la plus élevée est 0xFF. Dans un littéral de caractère large avec le préfixe L ou le préfixe u, la valeur hexadécimale la plus élevée est 0xFFFF. Dans un littéral de caractère large avec le préfixe U, la valeur hexadécimale la plus élevée est 0xFFFFFFFF.

```cpp
char c6 = '\x0050'; // 'P'
char c7 = '\x0pqr'; // C4305, C4309, truncates to 'r'
```

Si un littéral de caractère large ayant `L` pour préfixe contient plusieurs caractères, la valeur est obtenue à partir du premier caractère. Les caractères suivants sont ignorés, contrairement au comportement du caractère ordinaire équivalent littéral.

```cpp
wchar_t w1 = L'\100';   // L'@'
wchar_t w2 = L'\1000';  // C4066 L'@', 0 ignored
wchar_t w3 = L'\009';   // C4066 L'\0', 9 ignored
wchar_t w4 = L'\089';   // C4066 L'\0', 89 ignored
wchar_t w5 = L'\qrs';   // C4129, C4066 L'q' escape, rs ignored
wchar_t w6 = L'\x0050'; // L'P'
wchar_t w7 = L'\x0pqr'; // C4066 L'\0', pqr ignored
```

**FIN de la section spécifique à Microsoft**

Le caractère barre oblique inverse (\\) est un caractère de continuation de ligne lorsqu’il est placé à la fin d’une ligne. Pour qu'une barre oblique inverse apparaisse comme un littéral de caractère, vous devez taper deux barres obliques inverses sur une ligne (`\\`). Pour plus d’informations sur le caractère de continuation de ligne, consultez [Phases of Translation](../preprocessor/phases-of-translation.md).

###  <a name="bkmk_UCN"></a> Noms de caractères universels

Dans les littéraux de caractère et les littéraux de chaîne natifs (non bruts), un nom de caractère universel peut représenter n’importe quel caractère.  Les noms de caractères universels sont constitués d’un préfixe \U suivi d’un point de code Unicode à huit chiffres, ou d’un préfixe \u suivi d’un point de code Unicode à quatre chiffres. Tous les points de code Unicode à huit ou quatre chiffres, respectivement, doivent être présents pour constituer un nom de caractère universel bien formé.

```cpp
char u1 = 'A';          // 'A'
char u2 = '\101';       // octal, 'A'
char u3 = '\x41';       // hexadecimal, 'A'
char u4 = '\u0041';     // \u UCN 'A'
char u5 = '\U00000041'; // \U UCN 'A'
```

#### <a name="surrogate-pairs"></a>Paires de substitution

Les noms de caractères universels ne peuvent pas encoder les valeurs dans la plage de points de code de substitution D800-DFFF. Pour les paires de substitution Unicode, spécifiez le nom de caractère universel à l’aide de `\UNNNNNNNN`, où NNNNNNNN représente le point de code à huit chiffres du caractère. Le compilateur génère une paire de substitution, si nécessaire.

En C++03, le langage autorisait uniquement un sous-ensemble de caractères à être représentés par leurs noms de caractères universels. En outre, il autorisait certains noms de caractères universels qui ne représentaient pas en réalité des caractères Unicode valides. Ce problème a été corrigé dans la norme C++11. En C++11, les littéraux de caractère et de chaîne, ainsi que les identificateurs, peuvent utiliser des noms de caractères universels.  Pour plus d’informations sur les noms de caractères universels, consultez [Character Sets](../cpp/character-sets.md). Pour plus d’informations sur Unicode, consultez [Unicode](https://msdn.microsoft.com/library/dd374081). Pour plus d’informations sur les paires de substitution, consultez [Paires de substitution et caractères supplémentaires](/windows/desktop/Intl/surrogates-and-supplementary-characters).

## <a name="string-literals"></a>Littéraux de chaîne

Un littéral de chaîne représente une séquence de caractères qui, ensemble, forment une chaîne terminée par le caractère Null. Les caractères doivent être placés entre guillemets doubles. Il existe les genres suivants de littéraux de chaîne :

### <a name="narrow-string-literals"></a>Littéraux de chaîne étroits

Un littéral de chaîne étroit est un tableau de délimité, se terminant par null sans préfixe, le guillemet double de type `const char[n]`, où n est la longueur du tableau en octets. Un littéral de chaîne étroit peut contenir n’importe quel caractère graphique à l’exception du guillemet double (`"`), de la barre oblique inverse (`\`) ou du caractère de nouvelle ligne. Un littéral de chaîne étroit peut également contenir les séquences d’échappement répertoriées ci-dessus, ainsi que les noms de caractères universels qui tiennent dans un octet.

```cpp
const char *narrow = "abcd";

// represents the string: yes\no
const char *escaped = "yes\\no";
```

#### <a name="utf-8-encoded-strings"></a>Chaînes encodées UTF-8

Une chaîne encodée en UTF-8 est un tableau de délimité et se terminant par null, le préfixe u8, le guillemet double de type `const char[n]`, où n est la longueur du tableau encodé en octets. Un littéral de chaîne ayant le préfixe u8 peut contenir n’importe quel caractère graphique à l’exception du guillemet double (`"`), de la barre oblique inverse (`\`) ou du caractère de nouvelle ligne. Un littéral de chaîne ayant le préfixe u8 peut également contenir les séquences d’échappement répertoriées ci-dessus, ainsi que des noms de caractères universels.

```cpp
const char* str1 = u8"Hello World";
const char* str2 = u8"\U0001F607 is O:-)";
```

### <a name="wide-string-literals"></a>Littéraux de chaîne larges

Un littéral de chaîne étendu est un tableau se terminant par null de constantes **wchar_t** qui est précédé de '`L`» et contenant tout caractère graphique à l’exception du guillemet double («), barre oblique inverse (\\), ou un caractère de saut de ligne. Un littéral de chaîne large peut contenir les séquences d’échappement répertoriées ci-dessus, ainsi que des noms de caractères universels.

```cpp
const wchar_t* wide = L"zyxw";
const wchar_t* newline = L"hello\ngoodbye";
```

#### <a name="char16t-and-char32t-c11"></a>char16_t et char32_t (C++11)

C++11 présente les types de caractère portables `char16_t` (Unicode 16 bits) et `char32_t` (Unicode 32 bits) :

```cpp
auto s3 = u"hello"; // const char16_t*
auto s4 = U"hello"; // const char32_t*
```

### <a name="raw-string-literals-c11"></a>Littéraux de chaîne bruts (C++11)

Un littéral de chaîne brut est un tableau se terminant par null, de n’importe quel type de caractère, qui contient tout caractère graphique, y compris les guillemets doubles («), barre oblique inverse (\\), ou un caractère de saut de ligne. Les littéraux de chaîne bruts sont souvent utilisés dans les expressions régulières qui utilisent des classes de caractères et dans des chaînes XML et des chaînes HTML. Pour obtenir des exemples, consultez l’article du [FAQ de Bjarne Stroustrup sur C++11](http://www.stroustrup.com/C++11FAQ.html).

```cpp
// represents the string: An unescaped \ character
const char* raw_narrow = R"(An unescaped \ character)";
const wchar_t* raw_wide = LR"(An unescaped \ character)";
const char*       raw_utf8  = u8R"(An unescaped \ character)";
const char16_t* raw_utf16 = uR"(An unescaped \ character)";
const char32_t* raw_utf32 = UR"(An unescaped \ character)";
```

Un délimiteur est une séquence définie par l'utilisateur, composée au maximum de 16 caractères, qui précède immédiatement la parenthèse ouvrante d'un littéral de chaîne brut et suit immédiatement sa parenthèse fermante.  Par exemple, dans `R"abc(Hello"\()abc"` , la séquence du délimiteur est `abc` , et le contenu de la chaîne est `Hello"\(`. Vous pouvez utiliser un délimiteur pour distinguer les chaînes brutes qui contiennent à la fois des guillemets doubles et des parenthèses. Ceci provoque une erreur du compilateur :

```cpp
// meant to represent the string: )"
const char* bad_parens = R"()")";  // error C2059
```

Mais un délimiteur résout cette erreur :

```cpp
const char* good_parens = R"xyz()")xyz";
```

Vous pouvez construire un littéral de chaîne brut dans lequel il existe un saut de ligne (pas le caractère d'échappement) dans la source :

```cpp
// represents the string: hello
//goodbye
const wchar_t* newline = LR"(hello
goodbye)";
```

### <a name="stdstring-literals-c14"></a>Littéraux std::string (C++14)

Les littéraux std::string sont des implémentations de la bibliothèque standard de littéraux définis par l'utilisateur (voir ci-dessous) qui sont représentés sous la forme « xyx » s (avec un suffixe `s` ). Ce type de littéral de chaîne produit un objet temporaire de type std::string, std::wstring, std::u32string ou std::u16string selon le préfixe spécifié. Quand aucun préfixe n'est utilisé, comme ci-dessus, un littéral std::string est généré. L"xyz"s génère un littéral std::wstring. u"xyz"s génère un littéral [std::u16string](../standard-library/string-typedefs.md#u16string)et U"xyz"s génère un littéral [std::u32string](../standard-library/string-typedefs.md#u32string).

```cpp
//#include <string>
//using namespace std::string_literals;
string str{ "hello"s };
string str2{ u8"Hello World" };
wstring str3{ L"hello"s };
u16string str4{ u"hello"s };
u32string str5{ U"hello"s };
```

Le suffixe s peut également être utilisé avec des littéraux de chaîne bruts :

```cpp
u32string str6{ UR"(She said "hello.")"s };
```

les littéraux std::String sont définis dans l’espace de noms `std::literals::string_literals` dans le \<chaîne > fichier d’en-tête. Étant donné que `std::literals::string_literals`et `std::literals` sont tous deux déclarés comme [espaces de noms inline](../cpp/namespaces-cpp.md), `std::literals::string_literals` est automatiquement traité comme s'il appartenait directement à l'espace de noms `std`.

### <a name="size-of-string-literals"></a>Taille des littéraux de chaîne

Pour le caractère ANSI\* chaînes et autres encodages d’un octet (non UTF-8), la taille (en octets) d’un littéral de chaîne est le nombre de caractères plus 1 pour le caractère null de fin. Pour tous les autres types de chaîne, la taille n'est pas strictement liée au nombre de caractères. UTF-8 utilise jusqu’à quatre éléments char pour encoder certaines *unités de code*. Par ailleurs, char16_t ou wchar_t encodés au format UTF-16 peuvent utiliser deux éléments (pour un total de quatre octets) pour encoder une seule *unité de code*.   Cet exemple illustre la taille d’un littéral de chaîne large en octets :

```cpp
const wchar_t* str = L"Hello!";
const size_t byteSize = (wcslen(str) + 1) * sizeof(wchar_t);
```

Notez que `strlen()` et `wcslen()` n’incluent pas la taille du caractère null de fin, dont la taille est égale à la taille d’élément du type chaîne : un octet sur une valeur char\* de chaîne, deux octets sur wchar_t\* ou char16_t\*chaînes et quatre octets sur char32_t\* chaînes.

La longueur maximale d'un littéral de chaîne est de 65 535 octets. Cette limite s'applique à la fois aux littéraux de chaîne étroits et étendus.

### <a name="modifying-string-literals"></a>Modification des littéraux de chaîne

Étant donné que les littéraux de chaîne (sans compter les littéraux std : String) sont des constantes, toute tentative de modification, par exemple, `str[2] = 'A'`— provoque une erreur du compilateur.

**Section spécifique à Microsoft**

Dans Visual C++, vous pouvez utiliser un littéral de chaîne pour initialiser un pointeur non const **char** ou **wchar_t**. Cela est autorisé en code C99, mais est déconseillé en C++98 et supprimé en C++11. Toute tentative de modification de la chaîne provoque une violation d'accès, comme dans cet exemple :

```cpp
wchar_t* str = L"hello";
str[2] = L'a'; // run-time error: access violation
```

Vous pouvez contraindre le compilateur à émettre une erreur lorsqu’un littéral de chaîne est converti en un pointeur de caractère non_const lorsque vous définissez la [/Zc : strictstrings (désactiver la conversion de type de littéral chaîne)](../build/reference/zc-strictstrings-disable-string-literal-type-conversion.md) option du compilateur. Nous vous recommandons de procéder ainsi pour que la portabilité du code soit conforme aux normes. Il est également conseillé d’utiliser le **automatique** mot clé pour déclarer les pointeurs initialisés de littéral, chaîne car il est résolu en type (const) correct. Par exemple, cet exemple de code intercepte une tentative d’écriture dans un littéral de chaîne au moment de la compilation :

```cpp
auto str = L"hello";
str[2] = L'a'; // C3892: you cannot assign to a variable that is const.
```

Dans certains cas, des littéraux de chaîne identiques peuvent être regroupés pour économiser de l'espace dans le fichier exécutable. Dans un regroupement de littéraux de chaîne, le compilateur fait en sorte que toutes les références à un littéral de chaîne particulier pointent vers le même emplacement en mémoire, au lieu que chaque référence pointe vers une instance distincte du littéral de chaîne. Pour activer le regroupement de chaînes, utilisez l'option du compilateur [/GF](../build/reference/gf-eliminate-duplicate-strings.md) .

**End Microsoft Specific**

### <a name="concatenating-adjacent-string-literals"></a>Concaténation de littéraux de chaîne adjacents

Les littéraux de chaîne étendus ou étroits adjacents sont concaténés. Cette déclaration :

```cpp
char str[] = "12" "34";
```

est identique à la déclaration suivante :

```cpp
char atr[] = "1234";
```

et à cette déclaration :

```cpp
char atr[] =  "12\
34";
```

L'utilisation de codes d'échappement hexadécimaux incorporés pour spécifier des littéraux de chaîne peut provoquer des résultats inattendus. L'exemple suivant tente de créer un littéral de chaîne qui contient le caractère ASCII 5, suivi des caractères f, i, v et e :

```cpp
"\x05five"
```

Le résultat réel est un hexadécimal 5F, qui correspond au code ASCII pour un trait de soulignement, suivi des caractères i, v et e. Pour obtenir le résultat correct, vous pouvez utiliser l'un des éléments suivants :

```cpp
"\005five"     // Use octal literal.
"\x05" "five"  // Use string splicing.
```

Les littéraux std::string, puisqu'ils sont des types std::string, peuvent être concaténés avec l'opérateur + qui est défini pour les types [basic_string](../standard-library/basic-string-class.md) . Ils peuvent également être concaténés de la même façon que des littéraux de chaîne adjacents. Dans les deux cas, l’encodage de chaîne et le suffixe doivent correspondre :

```cpp
auto x1 = "hello" " " " world"; // OK
auto x2 = U"hello" " " L"world"; // C2308: disagree on prefix
auto x3 = u8"hello" " "s u8"world"s; // OK, agree on prefixes and suffixes
auto x4 = u8"hello" " "s u8"world"z; // C3688, disagree on suffixes
```

### <a name="string-literals-with-universal-character-names"></a>Littéraux de chaîne avec des noms de caractères universels

Les littéraux de chaîne natifs (non bruts) peuvent utiliser des noms de caractères universels pour représenter un caractère, du moment que le nom de caractère universel peut être encodé sous forme d’un ou de plusieurs caractères dans le type de chaîne.  Par exemple, un nom de caractère universel représentant un caractère étendu ne peut pas être encodé dans une chaîne étroite à l’aide de la page de codes ANSI. Toutefois, il peut être encodé dans les chaînes étroites de certaines pages de codes multioctets, dans les chaînes UTF-8 ou dans une chaîne large. Dans C ++ 11, prise en charge Unicode est étendu par le char16_t\* et char32_t\* types de chaînes :

```cpp
// ASCII smiling face
const char*     s1 = ":-)";

// UTF-16 (on Windows) encoded WINKING FACE (U+1F609)
const wchar_t*  s2 = L"😉 = \U0001F609 is ;-)";

// UTF-8  encoded SMILING FACE WITH HALO (U+1F607)
const char*     s3 = u8"😇 = \U0001F607 is O:-)";

// UTF-16 encoded SMILING FACE WITH OPEN MOUTH (U+1F603)
const char16_t* s4 = u"😃 = \U0001F603 is :-D";

// UTF-32 encoded SMILING FACE WITH SUNGLASSES (U+1F60E)
const char32_t* s5 = U"😎 = \U0001F60E is B-)";
```

## <a name="see-also"></a>Voir aussi

[Jeux de caractères](../cpp/character-sets.md)<br/>
[Littéraux numériques, booléens et de pointeur](../cpp/numeric-boolean-and-pointer-literals-cpp.md)<br/>
[Littéraux définis par l’utilisateur](../cpp/user-defined-literals-cpp.md)
