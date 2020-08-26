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
ms.openlocfilehash: 350a66481c7061322f08a768ec1628598f4af68e
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88843181"
---
# <a name="ltstringgt-functions"></a>&lt;string&gt;, fonctions

[getline](#getline)\
[stod](#stod)\
[stof](#stof)\
[stoi](#stoi)\
[stol](#stol)\
[stold](#stold)\
[stoll](#stoll)\
[stoul](#stoul)\
[stoull](#stoull)\
[échange](#swap)\
[to_string](#to_string)\
[to_wstring](#to_wstring)

## <a name="getline"></a><a name="getline"></a> getline

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

*limite*\
Délimiteur de ligne.

### <a name="return-value"></a>Valeur renvoyée

*In_stream*de flux d’entrée.

### <a name="remarks"></a>Notes

La paire de signatures de fonction marquée `(1)` extrait des caractères de *in_stream* jusqu’à ce que le *délimiteur* soit trouvé, en les stockant dans *Str*.

La paire de signatures de fonction marquée `(2)` use NewLine comme délimiteur de ligne par défaut et se comporte comme `getline(in_stream, str, in_stream. widen('\n'))` .

La seconde fonction de chaque paire est analogue à la première pour la prise en charge des [références rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md).

L'extraction s'arrête dans les situations suivantes :

- À la fin du fichier, auquel cas l’indicateur d’état interne de *in_stream* a la valeur `ios_base::eofbit` .

- Une fois que la fonction a extrait un élément qui compare égal au *délimiteur*. L’élément n’est pas remis en arrière ou n’est pas ajouté à la séquence contrôlée.

- Une fois que la fonction a extrait `str.` [max_size](../standard-library/basic-string-class.md#max_size) éléments. L’indicateur d’état interne de *in_stream* a la valeur `ios_base::failbit` .

- Autre erreur différente de celles précédemment listées ; l’indicateur d’état interne de *in_stream* a la valeur `ios_base::badbit` .

Pour plus d’informations sur les indicateurs d’état interne, consultez [ios_base::iostate](../standard-library/ios-base-class.md#iostate).

Si la fonction n’extrait aucun élément, l’indicateur d’état interne de *in_stream* a la valeur `ios_base::failbit` . Dans tous les cas, `getline` retourne *in_stream*.

Si une exception est levée, *in_stream* et *Str* sont laissés dans un état valide.

### <a name="example"></a>Exemple

Le code suivant illustre `getline()` dans deux modes : d'abord avec le délimiteur par défaut (nouvelle ligne) et ensuite avec un espace blanc comme délimiteur. Le caractère de fin de fichier (Ctrl-Z sur le clavier) est utilisé pour contrôler la fin des boucles while. Cette valeur définit l’indicateur d’état interne de `cin` sur `eofbit` , qui doit être effacé avec [basic_ios :: Clear ()](../standard-library/basic-ios-class.md#clear) avant que la seconde boucle while fonctionne correctement.

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

## <a name="stod"></a><a name="stod"></a> stod

Convertit une séquence de caractères en **`double`** .

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

*mét*\
Valeur d'index du premier caractère non converti.

### <a name="return-value"></a>Valeur renvoyée

**`double`** Valeur.

### <a name="remarks"></a>Notes

La fonction convertit la séquence d’éléments de *Str* en une valeur de type **`double`** comme si en appelant `strtod( str.c_str(), _Eptr)` , où `_Eptr` est un objet interne à la fonction. Si `str.c_str() == *_Eptr` , elle lève un objet de type `invalid_argument` . Si cet appel définit `errno`, elle lève un objet de type `out_of_range`. Dans le cas contraire, si *idx* n’est pas un pointeur null, la fonction stocke `*_Eptr -  str.c_str()` dans `*idx` et retourne la valeur.

## <a name="stof"></a><a name="stof"></a> stof

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

*mét*\
Valeur d'index du premier caractère non converti.

### <a name="return-value"></a>Valeur renvoyée

**`float`** Valeur.

### <a name="remarks"></a>Notes

La fonction convertit la séquence d’éléments de *Str* en une valeur de type **`float`** comme si en appelant `strtof( str.c_str(), _Eptr)` , où `_Eptr` est un objet interne à la fonction. Si `str.c_str() == *_Eptr` , elle lève un objet de type `invalid_argument` . Si cet appel définit `errno`, elle lève un objet de type `out_of_range`. Dans le cas contraire, si *idx* n’est pas un pointeur null, la fonction stocke `*_Eptr -  str.c_str()` dans `*idx` et retourne la valeur.

## <a name="stoi"></a><a name="stoi"></a> stoi

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

### <a name="return-value"></a>Valeur renvoyée

Valeur entière.

### <a name="parameters"></a>Paramètres

*Str*\
Séquence de caractères à convertir.

*mét*\
Valeur d'index du premier caractère non converti.

*base*\
Base numérique à utiliser.

### <a name="remarks"></a>Notes

La fonction `stoi` convertit la séquence de caractères de *Str* en une valeur de type **`int`** et retourne la valeur. Par exemple, quand la séquence de caractères « 10 » est passée, la valeur retournée par `stoi` est l'entier 10.

`stoi` se comporte de la même façon que la fonction pour les caractères codés sur un `strtol` octet quand elle est appelée de la manière `strtol( str.c_str(), _Eptr, idx)` , où `_Eptr` est un objet interne à la fonction, ou `wcstol` pour les caractères larges, quand elle est appelée de manière similaire, `wcstol(Str.c_str(), _Eptr, idx)` . Pour plus d’informations, consultez [strtol, wcstol, _strtol_l, _wcstol_l](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md).

Si `str.c_str() == *_Eptr` , `stoi` lève un objet de type `invalid_argument` . Si un tel appel est défini `errno` , ou si la valeur retournée ne peut pas être représentée en tant qu’objet de type **`int`** , elle lève un objet de type `out_of_range` . Sinon, si *idx* n’est pas un pointeur null, la fonction stocke `*_Eptr - str.c_str()` dans `*idx` .

## <a name="stol"></a><a name="stol"></a> stol

Convertit une séquence de caractères en **`long`** .

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

*mét*\
Valeur d'index du premier caractère non converti.

*base*\
Base numérique à utiliser.

### <a name="return-value"></a>Valeur renvoyée

Valeur entière de type long.

### <a name="remarks"></a>Notes

La fonction convertit la séquence d’éléments de *Str* en une valeur de type **`long`** comme si en appelant `strtol( str.c_str(), _Eptr, idx)` , où `_Eptr` est un objet interne à la fonction. Si `str.c_str() == *_Eptr` , elle lève un objet de type `invalid_argument` . Si cet appel définit `errno`, elle lève un objet de type `out_of_range`. Dans le cas contraire, si *idx* n’est pas un pointeur null, la fonction stocke `*_Eptr -  str.c_str()` dans `*idx` et retourne la valeur.

## <a name="stold"></a><a name="stold"></a> stold

Convertit une séquence de caractères en **`long double`** .

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

*mét*\
Valeur d'index du premier caractère non converti.

### <a name="return-value"></a>Valeur renvoyée

**`long double`** Valeur.

### <a name="remarks"></a>Notes

La fonction convertit la séquence d’éléments de *Str* en une valeur de type **`long double`** comme si en appelant `strtold( str.c_str(), _Eptr)` , où `_Eptr` est un objet interne à la fonction. Si `str.c_str() == *_Eptr` , elle lève un objet de type `invalid_argument` . Si cet appel définit `errno`, elle lève un objet de type `out_of_range`. Dans le cas contraire, si *idx* n’est pas un pointeur null, la fonction stocke `*_Eptr -  str.c_str()` dans `*idx` et retourne la valeur.

## <a name="stoll"></a><a name="stoll"></a> stoll

Convertit une séquence de caractères en **`long long`** .

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

*mét*\
Valeur d'index du premier caractère non converti.

*base*\
Base numérique à utiliser.

### <a name="return-value"></a>Valeur renvoyée

**`long long`** Valeur.

### <a name="remarks"></a>Notes

La fonction convertit la séquence d’éléments de *Str* en une valeur de type **`long long`** comme si en appelant `strtoll( str.c_str(), _Eptr, idx)` , où `_Eptr` est un objet interne à la fonction. Si `str.c_str() == *_Eptr` , elle lève un objet de type `invalid_argument` . Si cet appel définit `errno`, elle lève un objet de type `out_of_range`. Dans le cas contraire, si *idx* n’est pas un pointeur null, la fonction stocke `*_Eptr -  str.c_str()` dans `*idx` et retourne la valeur.

## <a name="stoul"></a><a name="stoul"></a> stoul

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

*mét*\
Valeur d'index du premier caractère non converti.

*base*\
Base numérique à utiliser.

### <a name="return-value"></a>Valeur renvoyée

Valeur entière de type long non signé.

### <a name="remarks"></a>Notes

La fonction convertit la séquence d’éléments de *Str* en une valeur de type **`unsigned long`** comme si en appelant `strtoul( str.c_str(), _Eptr, idx)` , où `_Eptr` est un objet interne à la fonction. Si `str.c_str() == *_Eptr` , elle lève un objet de type `invalid_argument` . Si cet appel définit `errno`, elle lève un objet de type `out_of_range`. Dans le cas contraire, si *idx* n’est pas un pointeur null, la fonction stocke `*_Eptr -  str.c_str()` dans `*idx` et retourne la valeur.

## <a name="stoull"></a><a name="stoull"></a> stoull

Convertit une séquence de caractères en **`unsigned long long`** .

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

*mét*\
Valeur d'index du premier caractère non converti.

*base*\
Base numérique à utiliser.

### <a name="return-value"></a>Valeur renvoyée

**`unsigned long long`** Valeur.

### <a name="remarks"></a>Notes

La fonction convertit la séquence d’éléments de *Str* en une valeur de type **`unsigned long long`** comme si en appelant `strtoull( str.c_str(), _Eptr, idx)` , où `_Eptr` est un objet interne à la fonction. Si `str.c_str() == *_Eptr` , elle lève un objet de type `invalid_argument` . Si cet appel définit `errno`, elle lève un objet de type `out_of_range`. Dans le cas contraire, si *idx* n’est pas un pointeur null, la fonction stocke `*_Eptr -  str.c_str()` dans `*idx` et retourne la valeur.

## <a name="swap"></a><a name="swap"></a> échange

Échange les tableaux de caractères de deux chaînes.

```cpp
template <class Traits, class Allocator>
void swap(basic_string<CharType, Traits, Allocator>& left, basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Une chaîne dont les éléments doivent être échangés avec les éléments d’une autre chaîne.

*Oui*\
Autre chaîne dont les éléments doivent être échangés avec la première chaîne.

### <a name="remarks"></a>Notes

La fonction de modèle exécute la fonction membre spécialisée *Left*. [échange](../standard-library/basic-string-class.md#swap)(*Right*) pour les chaînes, ce qui garantit une complexité constante.

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

## <a name="to_string"></a><a name="to_string"></a> to_string

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

*ajoutée*\
Valeur à convertir.

### <a name="return-value"></a>Valeur renvoyée

Objet `string` qui représente la valeur.

### <a name="remarks"></a>Notes

La fonction convertit la *valeur* en une séquence d’éléments stockés dans un objet tableau `Buf` interne à la fonction comme si vous appeliez `sprintf(Buf, Fmt, value)` , où `Fmt` est

- `"%d"` Si la *valeur* est de type **`int`**

- `"%u"` Si la *valeur* est de type **`unsigned int`**

- `"%ld"` Si la *valeur* est de type **`long`**

- `"%lu"` Si la *valeur* est de type **`unsigned long`**

- `"%lld"` Si la *valeur* est de type **`long long`**

- `"%llu"` Si la *valeur* est de type **`unsigned long long`**

- `"%f"` Si la *valeur* est de type **`float`** ou **`double`**

- `"%Lf"` Si la *valeur* est de type **`long double`**

La fonction retourne `string(Buf)`.

## <a name="to_wstring"></a><a name="to_wstring"></a> to_wstring

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

*ajoutée*\
Valeur à convertir.

### <a name="return-value"></a>Valeur renvoyée

Chaîne étendue qui représente la valeur.

### <a name="remarks"></a>Notes

La fonction convertit la *valeur* en une séquence d’éléments stockés dans un objet tableau `Buf` interne à la fonction comme si vous appeliez `swprintf(Buf, Len, Fmt, value)` , où `Fmt` est

- `L"%d"` Si la *valeur* est de type **`int`**

- `L"%u"` Si la *valeur* est de type **`unsigned int`**

- `L"%ld"` Si la *valeur* est de type **`long`**

- `L"%lu"` Si la *valeur* est de type **`unsigned long`**

- `L"%lld"` Si la *valeur* est de type **`long long`**

- `L"%llu"` Si la *valeur* est de type **`unsigned long long`**

- `L"%f"` Si la *valeur* est de type **`float`** ou **`double`**

- `L"%Lf"` Si la *valeur* est de type **`long double`**

La fonction retourne `wstring(Buf)`.

## <a name="see-also"></a>Voir aussi

[\<string>](../standard-library/string.md)
