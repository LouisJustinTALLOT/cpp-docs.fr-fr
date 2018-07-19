---
title: '&lt;string&gt;, fonctions | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
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
author: corob-msft
ms.author: corob
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
ms.workload:
- cplusplus
ms.openlocfilehash: 6534d93b4f04826188fa13c942efd080e152aebe
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38954901"
---
# <a name="ltstringgt-functions"></a>&lt;string&gt;, fonctions

||||
|-|-|-|
|[getline](#getline)|[stod](#stod)|[stof](#stof)|
|[stoi](#stoi)|[stol](#stol)|[stold](#stold)|
|[stoll](#stoll)|[stoul](#stoul)|[stoull](#stoull)|
|[swap](#swap)|[to_string](#to_string)|[to_wstring](#to_wstring)|

## <a name="getline"></a>  getline

Extrait des chaînes du flux d'entrée, ligne par ligne.

```cpp
// (1) delimiter as parameter
template <class CharType, class Traits, class Allocator>
basic_istream<CharType, Traits>& getline(
    basic_istream<CharType, Traits>& is,
    basic_string<CharType, Traits, Allocator>& str,
    CharType delim);


template <class CharType, class Traits, class Allocator>
basic_istream<CharType, Traits>& getline(
    basic_istream<CharType, Traits>&& is,
    basic_string<CharType, Traits, Allocator>& str,
    const CharType delim);


// (2) default delimiter used
template <class CharType, class Traits, class Allocator>
basic_istream<CharType, Traits>& getline(
    basic_istream<CharType, Traits>& is,
    basic_string<CharType, Traits, Allocator>& str);


template <class Allocator, class Traits, class Allocator>
basic_istream<Allocator, Traits>& getline(
    basic_istream<Allocator, Traits>&& is,
    basic_string<Allocator, Traits, Allocator>& str);
```

### <a name="parameters"></a>Paramètres

*est* le flux d’entrée à partir de laquelle une chaîne doit être extraite.

*Str* la chaîne dans laquelle les caractères sont lus à partir du flux d’entrée.

*delim* le délimiteur de ligne.

### <a name="return-value"></a>Valeur de retour

Le flux d’entrée *est*.

### <a name="remarks"></a>Notes

La paire de signatures de fonction marquée `(1)` extraire des caractères *est* jusqu'à ce que *delim* est trouvé, en les stockant dans *str*.

La paire de signatures de fonction marquée `(2)` utilise le saut de ligne comme délimiteur de ligne par défaut et se comportent comme **getline**(`is`, `str`, `is`. `widen`(' `\n`')).

La seconde fonction de chaque paire est analogue à la première pour la prise en charge des [références rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md).

L'extraction s'arrête dans les situations suivantes :

- À la fin de fichier, auquel cas l’état interne indicateur de *est* est défini sur `ios_base::eofbit`.

- Une fois que la fonction a extrait un élément dont la valeur est égale à `delim`. Dans ce cas, l’élément n’est ni remis à sa place, ni ajouté à la séquence contrôlée.

- Une fois que la fonction extrait `str.` [max_size](../standard-library/basic-string-class.md#max_size) éléments, dans lequel cas, l’indicateur d’état interne de *est* est défini sur `ios_base::failbit`.

- Une autre erreur autres que ceux répertoriés précédemment, dans ce cas, l’état interne indicateur de *est* est défini sur `ios_base::badbit`

Pour plus d’informations sur les indicateurs d’état interne, consultez [ios_base::iostate](../standard-library/ios-base-class.md#iostate).

Si la fonction n’extrait aucun élément, l’état interne indicateur de *est* est défini sur `ios_base::failbit`. Dans tous les cas, `getline` retourne *est*.

Si une exception est levée, *est* et *str* sont laissés dans un état valid.

### <a name="example"></a>Exemple

Le code suivant illustre `getline()` dans deux modes : d'abord avec le délimiteur par défaut (nouvelle ligne) et ensuite avec un espace blanc comme délimiteur. Le caractère de fin de fichier (Ctrl-Z sur le clavier) est utilisé pour contrôler la fin des boucles while. Cela permet d’affecter à l’indicateur d’état interne de `cin` la valeur `eofbit`, qui doit être effacée avec [basic_ios::clear()](../standard-library/basic-ios-class.md#clear) pour que la seconde boucle while fonctionne correctement.

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

## <a name="stod"></a>  stod

Convertit une séquence de caractères à un **double**.

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

|Paramètre|Description|
|---------------|-----------------|
|*str*|Séquence de caractères à convertir.|
|*IDX*|Valeur d'index du premier caractère non converti.|

### <a name="return-value"></a>Valeur de retour

Le **double** valeur.

### <a name="remarks"></a>Notes

La fonction convertit la séquence d’éléments dans *str* sur une valeur `val` de type **double** comme si elle appelait `strtod( str.c_str(), _Eptr)`, où `_Eptr` est un objet interne à la fonction. Si ` str.c_str() == *_Eptr`, elle lève un objet de type `invalid_argument`. Si cet appel définit `errno`, elle lève un objet de type `out_of_range`. Sinon, si *idx* n’est pas un pointeur null, la fonction stocke `*_Eptr -  str.c_str()` dans `*idx` et retourne `val`.

## <a name="stof"></a>  stof

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

|Paramètre|Description|
|---------------|-----------------|
|*str*|Séquence de caractères à convertir.|
|*IDX*|Valeur d'index du premier caractère non converti.|

### <a name="return-value"></a>Valeur de retour

Valeur flottante.

### <a name="remarks"></a>Notes

La fonction convertit la séquence d’éléments dans *str* sur une valeur `val` de type **float** comme si elle appelait `strtof( str.c_str(), _Eptr)`, où `_Eptr` est un objet interne à la fonction. Si ` str.c_str() == *_Eptr`, elle lève un objet de type `invalid_argument`. Si cet appel définit `errno`, elle lève un objet de type `out_of_range`. Sinon, si *idx* n’est pas un pointeur null, la fonction stocke `*_Eptr -  str.c_str()` dans `*idx` et retourne `val`.

## <a name="stoi"></a>  stoi

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

|Paramètre|Description|
|---------------|-----------------|
|*str*|Séquence de caractères à convertir.|
|*IDX*|Contient l'index du premier caractère non converti au retour.|
|*base*|Base numérique à utiliser.|

### <a name="remarks"></a>Notes

La fonction `stoi` convertit la séquence de caractères dans *str* à une valeur de type **int** et retourne la valeur. Par exemple, quand la séquence de caractères « 10 » est passée, la valeur retournée par `stoi` est l'entier 10.

`stoi` a un comportement semblable à celui de la fonction `strtol` pour les caractères codés sur un octet quand la fonction est appelée sous la forme `strtol( str.c_str(), _Eptr, idx)`, où `_Eptr` est un objet interne à la fonction. Sinon, son comportement est semblable à celui de la fonction `wcstol` pour les caractères larges, quand elle est appelée de manière similaire, `wcstol(Str.c_str(), _Eptr, idx)`. Pour plus d’informations, consultez [strtol, wcstol, _strtol_l, _wcstol_l](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md).

Si `str.c_str() == *_Eptr`, `stoi` lève un objet de type `invalid_argument`. Si un tel appel définit `errno`, ou si la valeur retournée ne peut pas être représentée en tant qu’objet de type **int**, elle lève un objet de type `out_of_range`. Sinon, si *idx* n’est pas un pointeur null, la fonction stocke `*_Eptr - str.c_str()` dans `*idx`.

## <a name="stol"></a>  stol

Convertit une séquence de caractères à un **long**.

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

|Paramètre|Description|
|---------------|-----------------|
|*str*|Séquence de caractères à convertir.|
|*IDX*|Valeur d'index du premier caractère non converti.|
|*base*|Base numérique à utiliser.|

### <a name="return-value"></a>Valeur de retour

Valeur entière de type long.

### <a name="remarks"></a>Notes

La fonction convertit la séquence d’éléments dans *str* sur une valeur `val` de type **long** comme si elle appelait `strtol( str.c_str(), _Eptr, idx)`, où `_Eptr` est un objet interne à la fonction. Si ` str.c_str() == *_Eptr`, elle lève un objet de type `invalid_argument`. Si cet appel définit `errno`, elle lève un objet de type `out_of_range`. Sinon, si *idx* n’est pas un pointeur null, la fonction stocke `*_Eptr -  str.c_str()` dans `*idx` et retourne `val`.

## <a name="stold"></a>  stold

Convertit une séquence de caractères à un **long double**.

```cpp
double stold(
    const string& str,
    size_t* idx = 0);

double stold(
    const wstring& str,
    size_t* idx = 0);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*str*|Séquence de caractères à convertir.|
|*IDX*|Valeur d'index du premier caractère non converti.|

### <a name="return-value"></a>Valeur de retour

Le **long double** valeur.

### <a name="remarks"></a>Notes

La fonction convertit la séquence d’éléments dans *str* sur une valeur `val` de type **long double** comme si elle appelait `strtold( str.c_str(), _Eptr)`, où `_Eptr` est un objet interne à la fonction. Si ` str.c_str() == *_Eptr`, elle lève un objet de type `invalid_argument`. Si cet appel définit `errno`, elle lève un objet de type `out_of_range`. Sinon, si *idx* n’est pas un pointeur null, la fonction stocke `*_Eptr -  str.c_str()` dans `*idx` et retourne `val`.

## <a name="stoll"></a>  stoll

Convertit une séquence de caractères à un **longue**.

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

|Paramètre|Description|
|---------------|-----------------|
|*str*|Séquence de caractères à convertir.|
|*IDX*|Valeur d'index du premier caractère non converti.|
|*base*|Base numérique à utiliser.|

### <a name="return-value"></a>Valeur de retour

Le **longue** valeur.

### <a name="remarks"></a>Notes

La fonction convertit la séquence d’éléments dans *str* sur une valeur `val` de type **longue** comme si elle appelait `strtoll( str.c_str(), _Eptr, idx)`, où `_Eptr` est un objet interne à la fonction. Si ` str.c_str() == *_Eptr`, elle lève un objet de type `invalid_argument`. Si cet appel définit `errno`, elle lève un objet de type `out_of_range`. Sinon, si *idx* n’est pas un pointeur null, la fonction stocke `*_Eptr -  str.c_str()` dans `*idx` et retourne `val`.

## <a name="stoul"></a>  stoul

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

|Paramètre|Description|
|---------------|-----------------|
|*str*|Séquence de caractères à convertir.|
|*IDX*|Valeur d'index du premier caractère non converti.|
|*base*|Base numérique à utiliser.|

### <a name="return-value"></a>Valeur de retour

Valeur entière de type long non signé.

### <a name="remarks"></a>Notes

La fonction convertit la séquence d’éléments dans *str* sur une valeur `val` de type **long non signé** comme si elle appelait `strtoul( str.c_str(), _Eptr, idx)`, où `_Eptr` est un objet interne à la fonction . Si ` str.c_str() == *_Eptr`, elle lève un objet de type `invalid_argument`. Si cet appel définit `errno`, elle lève un objet de type `out_of_range`. Sinon, si *idx* n’est pas un pointeur null, la fonction stocke `*_Eptr -  str.c_str()` dans `*idx` et retourne `val`.

## <a name="stoull"></a>  stoull

Convertit une séquence de caractères à un **unsigned long long**.

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

|Paramètre|Description|
|---------------|-----------------|
|*str*|Séquence de caractères à convertir.|
|*IDX*|Valeur d'index du premier caractère non converti.|
|*base*|Base numérique à utiliser.|

### <a name="return-value"></a>Valeur de retour

Le **unsigned long long** valeur.

### <a name="remarks"></a>Notes

La fonction convertit la séquence d’éléments dans *str* sur une valeur `val` de type **unsigned long long** comme si elle appelait `strtoull( str.c_str(), _Eptr, idx)`, où `_Eptr` est un objet interne à la fonction. Si ` str.c_str() == *_Eptr`, elle lève un objet de type `invalid_argument`. Si cet appel définit `errno`, elle lève un objet de type `out_of_range`. Sinon, si *idx* n’est pas un pointeur null, la fonction stocke `*_Eptr -  str.c_str()` dans `*idx` et retourne `val`.

## <a name="swap"></a>  swap

Échange les tableaux de caractères de deux chaînes.

```cpp
template <class Traits, class Allocator>
void swap(basic_string<CharType, Traits, Allocator>& left, basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*gauche* une chaîne dont les éléments doivent être échangés avec ceux d’une autre chaîne.

*droit* l’autre chaîne dont les éléments doivent être échangés avec la première chaîne.

### <a name="remarks"></a>Notes

La fonction de modèle exécute la fonction membre spécialisée *gauche*.[ échange](../standard-library/basic-string-class.md#swap)(*droit*) pour les chaînes, ce qui garantit une complexité constante.

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

## <a name="to_string"></a>  to_string

Convertit une valeur en `string`.

```cpp
string to_string(int Val);
string to_string(unsigned int Val);
string to_string(long Val);
string to_string(unsigned long Val);
string to_string(long long Val);
string to_string(unsigned long long Val);
string to_string(float Val);
string to_string(double Val);
string to_string(long double Val);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*Val*|Valeur à convertir.|

### <a name="return-value"></a>Valeur de retour

Objet `string` qui représente la valeur.

### <a name="remarks"></a>Notes

La fonction convertit *Val* à une séquence d’éléments stockés dans un objet tableau `Buf` interne à la fonction comme si elle appelait `sprintf(Buf, Fmt, Val)`, où `Fmt` est

- `"%d"` Si `Val` a type **int**

- `"%u"` Si `Val` a type **int non signé**

- `"%ld"` Si `Val` a type **long**

- `"%lu"` Si `Val` a type **long non signé**

- `"%lld"` Si `Val` a type **longue**

- `"%llu"` Si `Val` a type **long long non signé**

- `"%f"` Si `Val` a type **float** ou **double**

- `"%Lf"` Si `Val` a type **long double**

La fonction retourne `string(Buf)`.

## <a name="to_wstring"></a>  to_wstring

Convertit une valeur en une chaîne étendue.

```cpp
wstring to_wstring(int Val);
wstring to_wstring(unsigned int Val);
wstring to_wstring(long Val);
wstring to_wstring(unsigned long Val);
wstring to_wstring(long long Val);
wstring to_wstring(unsigned long long Val);
wstring to_wstring(float Val);
wstring to_wstring(double Val);
wstring to_wstring(long double Val);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|`Val`|Valeur à convertir.|

### <a name="return-value"></a>Valeur de retour

Chaîne étendue qui représente la valeur.

### <a name="remarks"></a>Notes

La fonction convertit `Val` en une séquence d'éléments stockés dans un objet tableau `Buf` interne à la fonction, comme dans un appel de `swprintf(Buf, Len, Fmt, Val)`, où `Fmt` est

- `L"%d"` Si `Val` a type **int**

- `L"%u"` Si `Val` a type **int non signé**

- `L"%ld"` Si `Val` a type **long**

- `L"%lu"` Si `Val` a type **long non signé**

- `L"%lld"` Si `Val` a type **longue**

- `L"%llu"` Si `Val` a type **long long non signé**

- `L"%f"` Si `Val` a type **float** ou **double**

- `L"%Lf"` Si `Val` a type **long double**

La fonction retourne `wstring(Buf)`.

## <a name="see-also"></a>Voir aussi

[\<string>](../standard-library/string.md)<br/>
