---
title: '&lt;string&gt;, fonctions'
ms.date: 11/04/2016
f1_keywords:
- string/std::getline
- string/std::stod
- string/std::stof
- string/std::stoi
- string/std::stol
- string/std::stold
- string/std::stoll
- string/std::stoul
- string/std::stoull
- string/std::swap
- string/std::to_string
- string/std::to_wstring
ms.assetid: 1a4ffd11-dce5-4cc6-a043-b95de034c7c4
helpviewer_keywords:
- std::getline [C++]
- std::stod [C++]
- std::stof [C++]
- std::stoi [C++]
- std::stol [C++]
- std::stold [C++]
- std::stoll [C++]
- std::stoul [C++]
- std::stoull [C++]
- std::swap [C++]
- std::to_string [C++]
- std::to_wstring [C++]
ms.openlocfilehash: 3f1dca71a6bb9d5461150378191b9373f907ecd1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376661"
---
# <a name="ltstringgt-functions"></a>&lt;string&gt;, fonctions

||||
|-|-|-|
|[getline](#getline)|[stod](#stod)|[stof](#stof)|
|[stoi stoi](#stoi)|[stol](#stol)|[stold](#stold)|
|[stoll](#stoll)|[stoul](#stoul)|[stoull stoull](#stoull)|
|[swap](#swap)|[to_string](#to_string)|[to_wstring](#to_wstring)|

## <a name="getline"></a><a name="getline"></a>Getline

Extrait des chaînes du flux d'entrée, ligne par ligne.

```cpp
// (1) delimiter as parameter
template <class CharType, class Traits, class Allocator>
basic_istream<CharType, Traits>& getline(
    basic_istream<CharType, Traits>& in_stream,
    basic_string<CharType, Traits, Allocator>& str,
    CharType delimiter);

template <class CharType, class Traits, class Allocator>
basic_istream<CharType, Traits>& getline(
    basic_istream<CharType, Traits>&& in_stream,
    basic_string<CharType, Traits, Allocator>& str,
    const CharType delimiter);

// (2) default delimiter used
template <class CharType, class Traits, class Allocator>
basic_istream<CharType, Traits>& getline(
    basic_istream<CharType, Traits>& in_stream,
    basic_string<CharType, Traits, Allocator>& str);

template <class Allocator, class Traits, class Allocator>
basic_istream<Allocator, Traits>& getline(
    basic_istream<Allocator, Traits>&& in_stream,
    basic_string<Allocator, Traits, Allocator>& str);
```

### <a name="parameters"></a>Paramètres

*in_stream*\
Flux d'entrée à partir duquel une chaîne doit être extraite.

*Str*\
Chaîne dans laquelle les caractères sont lus à partir du flux d'entrée.

*Délimiteur*\
Délimiteur de ligne.

### <a name="return-value"></a>Valeur de retour

Le flux *d’entrée in_stream*.

### <a name="remarks"></a>Notes

La `(1)` paire de signatures de fonction a marqué des caractères extrait de *in_stream* jusqu’à ce que *delimiter* est trouvé, les stocker dans *str*.

La paire de signatures de fonction marquées `(2)` utiliser newline `getline(in_stream, str, in_stream. widen('\n'))`comme délimitant ligne par défaut et se comporter comme .

La seconde fonction de chaque paire est analogue à la première pour la prise en charge des [références rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md).

L'extraction s'arrête dans les situations suivantes :

- À la fin du dossier, auquel *in_stream* cas le drapeau interne `ios_base::eofbit`de l’État de in_stream est fixé à .

- Après la fonction extrait un élément qui se compare égal à *delimiter*. L’élément ne se remet pas ou n’est pas annexé à la séquence contrôlée.

- Après la fonction `str.`extrait [max_size](../standard-library/basic-string-class.md#max_size) éléments. Le drapeau interne *in_stream* de l’État `ios_base::failbit`de in_stream est fixé à .

- Une autre erreur autre que celle précédemment énumérée; le drapeau interne *in_stream* de l’État `ios_base::badbit`de in_stream est fixé à .

Pour plus d’informations sur les indicateurs d’état interne, consultez [ios_base::iostate](../standard-library/ios-base-class.md#iostate).

Si la fonction n’extrait aucun élément, le drapeau interne `ios_base::failbit`de l’état de *in_stream* est réglé à . En tout `getline` cas, les retours *in_stream*.

Si une exception est lancée, *in_stream* et *str* sont laissés dans un état valide.

### <a name="example"></a>Exemple

Le code suivant illustre `getline()` dans deux modes : d'abord avec le délimiteur par défaut (nouvelle ligne) et ensuite avec un espace blanc comme délimiteur. Le caractère de fin de fichier (Ctrl-Z sur le clavier) est utilisé pour contrôler la fin des boucles while. Cette valeur définit le `cin` drapeau `eofbit`de l’état interne de , qui doit être effacé avec [basic_ios::clair()](../standard-library/basic-ios-class.md#clear) avant la seconde tandis que la boucle fonctionnera correctement.

```cpp
// compile with: /EHsc /W4
#include <string>
#include <iostream>
#include <vector>

using namespace std;

int main()
{
    string str;
    vector<string> v1;
    cout << "Enter a sentence, press ENTER between sentences. (Ctrl-Z to stop): " << endl;
    // Loop until end-of-file (Ctrl-Z) is input, store each sentence in a vector.
    // Default delimiter is the newline character.
    while (getline(cin, str)) {
        v1.push_back(str);
    }

    cout << "The following input was stored with newline delimiter:" << endl;
    for (const auto& p : v1) {
        cout << p << endl;
    }

    cin.clear();

    vector<string> v2;
    // Now try it with a whitespace delimiter
    while (getline(cin, str, ' ')) {
        v2.push_back(str);
    }

    cout << "The following input was stored with whitespace as delimiter:" << endl;
    for (const auto& p : v2) {
        cout << p << endl;
    }
}
```

## <a name="stod"></a><a name="stod"></a>stod

Convertit une séquence **`double`** de caractères en un .

```cpp
double stod(
    const string& str,
    size_t* idx = 0);

double stod(
    const wstring& str,
    size_t* idx = 0
;
```

### <a name="parameters"></a>Paramètres

*Str*\
Séquence de caractères à convertir.

*Idx*\
Valeur d'index du premier caractère non converti.

### <a name="return-value"></a>Valeur de retour

La **`double`** valeur.

### <a name="remarks"></a>Notes

La fonction convertit la *str* séquence d’éléments **`double`** en str `strtod( str.c_str(), _Eptr)`à une valeur de type comme si en appelant , où `_Eptr` est un objet interne à la fonction. Si `str.c_str() == *_Eptr`, il jette un `invalid_argument`objet de type . Si cet appel définit `errno`, elle lève un objet de type `out_of_range`. Sinon, si *idx* n’est pas un `*_Eptr -  str.c_str()` `*idx` pointeur nul, la fonction se conserve et retourne la valeur.

## <a name="stof"></a><a name="stof"></a>stof

Convertit une séquence de caractères en type flottant.

```cpp
float stof(
    const string& str,
    size_t* idx = 0);

float stof(
    const wstring& str,
    size_t* idx = 0);
```

### <a name="parameters"></a>Paramètres

*Str*\
Séquence de caractères à convertir.

*Idx*\
Valeur d'index du premier caractère non converti.

### <a name="return-value"></a>Valeur de retour

La **`float`** valeur.

### <a name="remarks"></a>Notes

La fonction convertit la *str* séquence d’éléments **`float`** en str `strtof( str.c_str(), _Eptr)`à une valeur de type comme si en appelant , où `_Eptr` est un objet interne à la fonction. Si `str.c_str() == *_Eptr`, il jette un `invalid_argument`objet de type . Si cet appel définit `errno`, elle lève un objet de type `out_of_range`. Sinon, si *idx* n’est pas un `*_Eptr -  str.c_str()` `*idx` pointeur nul, la fonction se conserve et retourne la valeur.

## <a name="stoi"></a><a name="stoi"></a>stoi stoi

Convertit une séquence de caractères en entier.

```cpp
int stoi(
    const string& str,
    size_t* idx = 0,
    int base = 10);

int stoi(
    const wstring& str,
    size_t* idx = 0,
    int base = 10);
```

### <a name="return-value"></a>Valeur de retour

Valeur entière.

### <a name="parameters"></a>Paramètres

*Str*\
Séquence de caractères à convertir.

*Idx*\
Valeur d'index du premier caractère non converti.

*Base*\
Base numérique à utiliser.

### <a name="remarks"></a>Notes

La `stoi` fonction convertit la séquence des caractères **`int`** en *str* à une valeur de type et retourne la valeur. Par exemple, quand la séquence de caractères « 10 » est passée, la valeur retournée par `stoi` est l'entier 10.

`stoi`se comporte de `strtol` la même manière que la fonction pour `strtol( str.c_str(), _Eptr, idx)`les `_Eptr` caractères undés lorsqu’il est appelé de la manière, où est un objet interne à la fonction; ou `wcstol` pour les personnages larges, quand `wcstol(Str.c_str(), _Eptr, idx)`il est appelé de la même manière, . Pour plus d’informations, consultez [strtol, wcstol, _strtol_l, _wcstol_l](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md).

Si `str.c_str() == *_Eptr` `stoi` , jette un `invalid_argument`objet de type . Si un tel `errno`appel serait réglé, ou si la valeur retournée **`int`** ne peut pas être `out_of_range`représenté comme un objet de type , il jette un objet de type . Sinon, si *idx* n’est pas un `*_Eptr - str.c_str()` `*idx`pointeur nul, la fonction se conserve dans .

## <a name="stol"></a><a name="stol"></a>Stol

Convertit une séquence **`long`** de caractères en un .

```cpp
long stol(
    const string& str,
    size_t* idx = 0,
    int base = 10);

long stol(
    const wstring& str,
    size_t* idx = 0,
    int base = 10);
```

### <a name="parameters"></a>Paramètres

*Str*\
Séquence de caractères à convertir.

*Idx*\
Valeur d'index du premier caractère non converti.

*Base*\
Base numérique à utiliser.

### <a name="return-value"></a>Valeur de retour

Valeur entière de type long.

### <a name="remarks"></a>Notes

La fonction convertit la *str* séquence d’éléments **`long`** en str `strtol( str.c_str(), _Eptr, idx)`à une valeur de type comme si en appelant , où `_Eptr` est un objet interne à la fonction. Si `str.c_str() == *_Eptr`, il jette un `invalid_argument`objet de type . Si cet appel définit `errno`, elle lève un objet de type `out_of_range`. Sinon, si *idx* n’est pas un `*_Eptr -  str.c_str()` `*idx` pointeur nul, la fonction se conserve et retourne la valeur.

## <a name="stold"></a><a name="stold"></a>stold

Convertit une séquence **`long double`** de caractères en un .

```cpp
double stold(
    const string& str,
    size_t* idx = 0);

double stold(
    const wstring& str,
    size_t* idx = 0);
```

### <a name="parameters"></a>Paramètres

*Str*\
Séquence de caractères à convertir.

*Idx*\
Valeur d'index du premier caractère non converti.

### <a name="return-value"></a>Valeur de retour

La **`long double`** valeur.

### <a name="remarks"></a>Notes

La fonction convertit la *str* séquence d’éléments **`long double`** en str `strtold( str.c_str(), _Eptr)`à une valeur de type comme si en appelant , où `_Eptr` est un objet interne à la fonction. Si `str.c_str() == *_Eptr`, il jette un `invalid_argument`objet de type . Si cet appel définit `errno`, elle lève un objet de type `out_of_range`. Sinon, si *idx* n’est pas un `*_Eptr -  str.c_str()` `*idx` pointeur nul, la fonction se conserve et retourne la valeur.

## <a name="stoll"></a><a name="stoll"></a>Stoll

Convertit une séquence **`long long`** de caractères en un .

```cpp
long long stoll(
    const string& str,
    size_t* idx = 0,
    int base = 10);

long long stoll(
    const wstring& str,
    size_t* idx = 0,
    int base = 10);
```

### <a name="parameters"></a>Paramètres

*Str*\
Séquence de caractères à convertir.

*Idx*\
Valeur d'index du premier caractère non converti.

*Base*\
Base numérique à utiliser.

### <a name="return-value"></a>Valeur de retour

La **`long long`** valeur.

### <a name="remarks"></a>Notes

La fonction convertit la *str* séquence d’éléments **`long long`** en str `strtoll( str.c_str(), _Eptr, idx)`à une valeur de type comme si en appelant , où `_Eptr` est un objet interne à la fonction. Si `str.c_str() == *_Eptr`, il jette un `invalid_argument`objet de type . Si cet appel définit `errno`, elle lève un objet de type `out_of_range`. Sinon, si *idx* n’est pas un `*_Eptr -  str.c_str()` `*idx` pointeur nul, la fonction se conserve et retourne la valeur.

## <a name="stoul"></a><a name="stoul"></a>stoul

Convertit une séquence de caractères en type long non signé.

```cpp
unsigned long stoul(
    const string& str,
    size_t* idx = 0,
    int base = 10);

unsigned long stoul(
    const wstring& str,
    size_t* idx = 0,
    int base = 10);
```

### <a name="parameters"></a>Paramètres

*Str*\
Séquence de caractères à convertir.

*Idx*\
Valeur d'index du premier caractère non converti.

*Base*\
Base numérique à utiliser.

### <a name="return-value"></a>Valeur de retour

Valeur entière de type long non signé.

### <a name="remarks"></a>Notes

La fonction convertit la *str* séquence d’éléments **`unsigned long`** en str `strtoul( str.c_str(), _Eptr, idx)`à une valeur de type comme si en appelant , où `_Eptr` est un objet interne à la fonction. Si `str.c_str() == *_Eptr`, il jette un `invalid_argument`objet de type . Si cet appel définit `errno`, elle lève un objet de type `out_of_range`. Sinon, si *idx* n’est pas un `*_Eptr -  str.c_str()` `*idx` pointeur nul, la fonction se conserve et retourne la valeur.

## <a name="stoull"></a><a name="stoull"></a>stoull stoull

Convertit une séquence **`unsigned long long`** de caractères en un .

```cpp
unsigned long long stoull(
    const string& str,
    size_t* idx = 0,
    int base = 10);

unsigned long long stoull(
    const wstring& str,
    size_t* idx = 0,
    int base = 10);
```

### <a name="parameters"></a>Paramètres

*Str*\
Séquence de caractères à convertir.

*Idx*\
Valeur d'index du premier caractère non converti.

*Base*\
Base numérique à utiliser.

### <a name="return-value"></a>Valeur de retour

La **`unsigned long long`** valeur.

### <a name="remarks"></a>Notes

La fonction convertit la *str* séquence d’éléments **`unsigned long long`** en str `strtoull( str.c_str(), _Eptr, idx)`à une valeur de type comme si en appelant , où `_Eptr` est un objet interne à la fonction. Si `str.c_str() == *_Eptr`, il jette un `invalid_argument`objet de type . Si cet appel définit `errno`, elle lève un objet de type `out_of_range`. Sinon, si *idx* n’est pas un `*_Eptr -  str.c_str()` `*idx` pointeur nul, la fonction se conserve et retourne la valeur.

## <a name="swap"></a><a name="swap"></a>Swap

Échange les tableaux de caractères de deux chaînes.

```cpp
template <class Traits, class Allocator>
void swap(basic_string<CharType, Traits, Allocator>& left, basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*Gauche*\
Une chaîne dont les éléments doivent être échangés avec les éléments d’une autre chaîne.

*Oui*\
Autre chaîne dont les éléments doivent être échangés avec la première chaîne.

### <a name="remarks"></a>Notes

La fonction de modèle exécute la fonction de membre spécialisé *gauche*. [swap](../standard-library/basic-string-class.md#swap)*(à droite)* pour les cordes, ce qui garantit une complexité constante.

### <a name="example"></a>Exemple

```cpp
// string_swap.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   // Declaring an object of type basic_string<char>
   string s1 ( "Tweedledee" );
   string s2 ( "Tweedledum" );
   cout << "Before swapping string s1 and s2:" << endl;
   cout << "The basic_string s1 = " << s1 << "." << endl;
   cout << "The basic_string s2 = " << s2 << "." << endl;

   swap ( s1 , s2 );
   cout << "\nAfter swapping string s1 and s2:" << endl;
   cout << "The basic_string s1 = " << s1 << "." << endl;
   cout << "The basic_string s2 = " << s2 << "." << endl;
}
```

```Output
Before swapping string s1 and s2:
The basic_string s1 = Tweedledee.
The basic_string s2 = Tweedledum.

After swapping string s1 and s2:
The basic_string s1 = Tweedledum.
The basic_string s2 = Tweedledee.
```

## <a name="to_string"></a><a name="to_string"></a>to_string

Convertit une valeur en `string`.

```cpp
string to_string(int value);
string to_string(unsigned int value);
string to_string(long value);
string to_string(unsigned long value);
string to_string(long long value);
string to_string(unsigned long long value);
string to_string(float value);
string to_string(double value);
string to_string(long double value);
```

### <a name="parameters"></a>Paramètres

*Valeur*\
Valeur à convertir.

### <a name="return-value"></a>Valeur de retour

Objet `string` qui représente la valeur.

### <a name="remarks"></a>Notes

La fonction convertit la *valeur* en une `Buf` séquence d’éléments stockés `sprintf(Buf, Fmt, value)`dans `Fmt` un objet de tableau interne à la fonction comme si en appelant, où est

- `"%d"`si la *valeur* est de type**`int`**

- `"%u"`si la *valeur* est de type**`unsigned int`**

- `"%ld"`si la *valeur* est de type**`long`**

- `"%lu"`si la *valeur* est de type**`unsigned long`**

- `"%lld"`si la *valeur* est de type**`long long`**

- `"%llu"`si la *valeur* est de type**`unsigned long long`**

- `"%f"`si *value* la valeur **`float`** est de type ou**`double`**

- `"%Lf"`si la *valeur* est de type**`long double`**

La fonction retourne `string(Buf)`.

## <a name="to_wstring"></a><a name="to_wstring"></a>to_wstring

Convertit une valeur en une chaîne étendue.

```cpp
wstring to_wstring(int value);
wstring to_wstring(unsigned int value);
wstring to_wstring(long value);
wstring to_wstring(unsigned long value);
wstring to_wstring(long long value);
wstring to_wstring(unsigned long long value);
wstring to_wstring(float value);
wstring to_wstring(double value);
wstring to_wstring(long double value);
```

### <a name="parameters"></a>Paramètres

*Valeur*\
Valeur à convertir.

### <a name="return-value"></a>Valeur de retour

Chaîne étendue qui représente la valeur.

### <a name="remarks"></a>Notes

La fonction convertit la *valeur* en une `Buf` séquence d’éléments stockés `swprintf(Buf, Len, Fmt, value)`dans `Fmt` un objet de tableau interne à la fonction comme si en appelant, où est

- `L"%d"`si la *valeur* est de type**`int`**

- `L"%u"`si la *valeur* est de type**`unsigned int`**

- `L"%ld"`si la *valeur* est de type**`long`**

- `L"%lu"`si la *valeur* est de type**`unsigned long`**

- `L"%lld"`si la *valeur* est de type**`long long`**

- `L"%llu"`si la *valeur* est de type**`unsigned long long`**

- `L"%f"`si *value* la valeur **`float`** est de type ou**`double`**

- `L"%Lf"`si la *valeur* est de type**`long double`**

La fonction retourne `wstring(Buf)`.

## <a name="see-also"></a>Voir aussi

[\<>de cordes](../standard-library/string.md)
