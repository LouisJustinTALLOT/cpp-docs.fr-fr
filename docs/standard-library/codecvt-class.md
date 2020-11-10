---
title: La classe `codecvt`
description: décrit l’API de la classe Microsoft C Runtime `codecvt`
ms.date: 11/09/2020
f1_keywords:
- xlocale/std::codecvt
- xlocale/std::codecvt::extern_type
- xlocale/std::codecvt::intern_type
- xlocale/std::codecvt::state_type
- xlocale/std::codecvt::always_noconv
- xlocale/std::codecvt::do_always_noconv
- xlocale/std::codecvt::do_encoding
- xlocale/std::codecvt::do_in
- xlocale/std::codecvt::do_length
- xlocale/std::codecvt::do_max_length
- xlocale/std::codecvt::do_out
- xlocale/std::codecvt::do_unshift
- xlocale/std::codecvt::encoding
- xlocale/std::codecvt::in
- xlocale/std::codecvt::length
- xlocale/std::codecvt::max_length
- xlocale/std::codecvt::out
- xlocale/std::codecvt::unshift
helpviewer_keywords:
- std::codecvt [C++]
- std::codecvt [C++], extern_type
- std::codecvt [C++], intern_type
- std::codecvt [C++], state_type
- std::codecvt [C++], always_noconv
- std::codecvt [C++], do_always_noconv
- std::codecvt [C++], do_encoding
- std::codecvt [C++], do_in
- std::codecvt [C++], do_length
- std::codecvt [C++], do_max_length
- std::codecvt [C++], do_out
- std::codecvt [C++], do_unshift
- std::codecvt [C++], encoding
- std::codecvt [C++], in
- std::codecvt [C++], length
- std::codecvt [C++], max_length
- std::codecvt [C++], out
- std::codecvt [C++], unshift
ms.assetid: 37d3efa1-2b7f-42b6-b04f-7a972c8c2c86
ms.openlocfilehash: 8d2970297cca199c70c101dca93f453c512317c4
ms.sourcegitcommit: b38485bb3a9d479e0c5d64ffc3d841fa2c2b366f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94441279"
---
# <a name="codecvt-class"></a>La classe `codecvt`

Modèle de classe qui décrit un objet pouvant servir de facette de paramètres régionaux. Il peut contrôler les conversions entre une séquence de valeurs utilisées pour encoder des caractères dans le programme et une séquence de valeurs utilisées pour encoder des caractères en dehors du programme.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType, class Byte, class StateType>
class codecvt : public locale::facet, codecvt_base;
```

### <a name="parameters"></a>Paramètres

*`CharType`*\
Type utilisé dans le cadre d'un programme pour encoder des caractères.

*`Byte`*\
Type utilisé pour encoder des caractères en dehors d'un programme.

*`StateType`*\
Type qui peut être utilisé pour représenter les états intermédiaires d'une conversion entre types internes et types externes de représentations de caractères.

## <a name="remarks"></a>Notes

Le modèle de classe décrit un objet pouvant servir de [facette de paramètres régionaux](../standard-library/locale-class.md#facet_class)pour contrôler les conversions entre une séquence de valeurs de type *`CharType`* et une séquence de valeurs de type *`Byte`* . La classe *`StateType`* caractérise la transformation--et un objet de la classe *`StateType`* stocke toutes les informations d’État nécessaires pendant une conversion.

L’encodage interne utilise une représentation avec un nombre fixe d’octets par caractère, généralement de type **`char`** ou de type **`wchar_t`** .

Comme avec n'importe quelle facette de paramètres régionaux, l'objet statique `id` possède une valeur stockée initiale de zéro. La première tentative d’accès à sa valeur stockée entraîne le stockage d’une valeur positive unique dans `id`.

Les versions de modèle de [`do_in`](#do_in) et [`do_out`](#do_out) retournent toujours `codecvt_base::noconv` .

La bibliothèque C++ Standard définit plusieurs spécialisations explicites :

```cpp
template<>
codecvt<wchar_t, char, mbstate_t>
```

effectue la conversion entre **`wchar_t`** les **`char`** séquences et.

```cpp
template<>
codecvt<char16_t, char, mbstate_t>
```

effectue une conversion entre des **`char16_t`** séquences encodées au format UTF-16 et des **`char`** séquences encodées au format UTF-8.

```cpp
template<>
codecvt<char32_t, char, mbstate_t>
```

effectue une conversion entre **`char32_t`** des séquences encodées au format UTF-32 (UCS-4) et des **`char`** séquences encodées au format UTF-8.

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[`codecvt`](#codecvt)|Constructeur d'objets de la classe `codecvt` qui sert de facette de paramètres régionaux pour la gestion des conversions.|

### <a name="typedefs"></a>Typedefs

|Nom de type|Description|
|-|-|
|[`extern_type`](#extern_type)|Type de caractère utilisé pour les représentations externes.|
|[`intern_type`](#intern_type)|Type de caractère utilisé pour les représentations internes.|
|[`state_type`](#state_type)|Type de caractère utilisé pour représenter les états intermédiaires lors de conversions entre des représentations internes et externes.|

### <a name="member-functions"></a>Fonctions Membre

|Fonction membre|Description|
|-|-|
|[`always_noconv`](#always_noconv)|Vérifie si une conversion doit être effectuée.|
|[`do_always_noconv`](#do_always_noconv)|Fonction virtuelle appelée pour vérifier si une conversion doit être effectuée.|
|[`do_encoding`](#do_encoding)|Fonction virtuelle qui vérifie si l’encodage du `Byte` flux est dépendant de l’État, si le rapport entre les `Byte` valeurs utilisées et les `CharType` valeurs produites est constant et, le cas échéant, détermine la valeur de ce ratio.|
|[`do_in`](#do_in)|Fonction virtuelle appelée pour convertir une séquence de valeurs internes `Byte` en une séquence de valeurs externes `CharType` .|
|[`do_length`](#do_length)|Fonction virtuelle qui détermine le nombre de `Byte` valeurs d’une séquence donnée de valeurs externes qui `Byte` ne produisent pas plus d’un nombre donné de `CharType` valeurs internes et retourne ce nombre de `Byte` valeurs.|
|[`do_max_length`](#do_max_length)|Fonction virtuelle qui retourne le nombre maximal d'octets externes nécessaires pour produire un `CharType` interne.|
|[`do_out`](#do_out)|Fonction virtuelle appelée pour convertir une séquence de valeurs internes `CharType` en une séquence d’octets externes.|
|[`do_unshift`](#do_unshift)|Fonction virtuelle appelée pour fournir les `Byte` valeurs nécessaires dans une conversion dépendante de l’État pour terminer le dernier caractère d’une séquence de `Byte` valeurs.|
|[`encoding`](#encoding)|Teste si l’encodage du `Byte` flux dépend de l’État, si le rapport entre les `Byte` valeurs utilisées et les `CharType` valeurs produites est constant et, le cas échéant, détermine la valeur de ce ratio.|
|[`in`](#in)|Convertit une représentation externe d’une séquence de `Byte` valeurs en représentation interne d’une séquence de `CharType` valeurs.|
|[`length`](#length)|Détermine le nombre de `Byte` valeurs d’une séquence donnée de `Byte` valeurs externes qui ne produisent pas plus d’un nombre donné de `CharType` valeurs internes et retourne ce nombre de `Byte` valeurs.|
|[`max_length`](#max_length)|Retourne le nombre maximal de `Byte` valeurs externes nécessaires pour produire un interne `CharType` .|
|[`out`](#out)|Convertit une séquence de `CharType` valeurs internes en une séquence de `Byte` valeurs externes.|
|[`unshift`](#unshift)|Fournit les `Byte` valeurs externes nécessaires dans une conversion dépendante de l’État pour terminer le dernier caractère de la séquence de `Byte` valeurs.|

## <a name="requirements"></a>Configuration requise

**En-tête :**`<locale>`

**Espace de noms :** `std`

## <a name="codecvtalways_noconv"></a><a name="always_noconv"></a> `codecvt::always_noconv`

Teste si aucune conversion n’est nécessaire.

```cpp
bool always_noconv() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Valeur booléenne qui est **`true`** si aucune conversion n’est nécessaire ; **`false`** si au moins un doit être effectué.

### <a name="remarks"></a>Notes

La fonction membre retourne [`do_always_noconv`](#do_always_noconv) .

### <a name="example"></a>Exemple

```cpp
// codecvt_always_noconv.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = use_facet<codecvt<char, char, mbstate_t>>
      ( loc ).always_noconv( );

   if ( result1 )
      cout << "No conversion is needed." << '\n';
   else
      cout << "At least one conversion is required." << '\n';

   bool result2 = use_facet<codecvt<wchar_t, char, mbstate_t>>
      ( loc ).always_noconv( );

   if ( result2 )
      cout << "No conversion is needed." << '\n';
   else
      cout << "At least one conversion is required." << '\n';
}
```

```Output
No conversion is needed.
At least one conversion is required.
```

## <a name="codecvtcodecvt"></a><a name="codecvt"></a> `codecvt::codecvt`

Constructeur d’objets de la classe codecvt qui sert de facette de paramètres régionaux pour la gestion des conversions.

```cpp
explicit codecvt(size_t refs = 0);
```

### <a name="parameters"></a>Paramètres

*`refs`*\
Valeur entière utilisée pour spécifier le type de gestion de mémoire pour l’objet.

### <a name="remarks"></a>Notes

Les valeurs possibles pour le *`refs`* paramètre et leur signification sont les suivantes :

- 0 : la durée de vie de l’objet est gérée par les paramètres régionaux qui le contiennent.

- 1 : la durée de vie de l’objet doit être gérée manuellement.


- 2 : ces valeurs ne sont pas définies.

Le constructeur initialise son `locale::facet` objet de base avec [`locale::facet`](../standard-library/locale-class.md#facet_class) `(refs)` .

## <a name="codecvtdo_always_noconv"></a><a name="do_always_noconv"></a> `codecvt::do_always_noconv`

Fonction virtuelle appelée pour tester si aucune conversion n’est nécessaire.

```cpp
virtual bool do_always_noconv() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

La fonction membre virtuelle protégée retourne **`true`** uniquement si chaque appel à [`do_in`](#do_in) ou [`do_out`](#do_out) retourne `noconv` .

La version de modèle retourne toujours **`true`** .

### <a name="example"></a>Exemple

Consultez l’exemple pour [`always_noconv`](#always_noconv) , qui appelle `do_always_noconv` .

## <a name="codecvtdo_encoding"></a><a name="do_encoding"></a> `codecvt::do_encoding`

Fonction virtuelle qui vérifie si l’encodage du `Byte` flux est dépendant de l’État, si le rapport entre les `Byte` valeurs utilisées et les `CharType` valeurs produites est constant et, le cas échéant, détermine la valeur de ce ratio.

```cpp
virtual int do_encoding() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

La fonction membre virtuelle protégée retourne :

- -1, si l’encodage des séquences de type `extern_type` est dépendant de l’État.

- 0, si le codage implique des séquences de longueur variable.

- *`N`* Si l’encodage implique uniquement des séquences de longueur *`N`*

### <a name="example"></a>Exemple

Consultez l’exemple relatif à [encoding](#encoding), qui appelle `do_encoding`.

## <a name="codecvtdo_in"></a><a name="do_in"></a> codecvt ::d o_in

Fonction virtuelle appelée pour convertir une séquence de valeurs externes `Byte` en une séquence de valeurs internes `CharType` .

```cpp
virtual result do_in(
    StateType& state,
    const Byte* first1,
    const Byte* last1,
    const Byte*& next1,
    CharType* first2,
    CharType* last2,
    CharType*& next2,) const;
```

### <a name="parameters"></a>Paramètres

*`state`*\
État de conversion conservé entre les appels à la fonction membre.

*`first1`*\
Pointeur vers le début de la séquence à convertir.

*`last1`*\
Pointeur vers la fin de la séquence à convertir.

*`next1`*\
Pointeur situé après la fin de la séquence convertie, vers le premier caractère non converti.

*`first2`*\
Pointeur vers le début de la séquence convertie.

*`last2`*\
Pointeur vers la fin de la séquence convertie.

*`next2`*\
Pointeur vers le `CharType` qui vient après le dernier converti `CharType` , jusqu’au premier caractère non modifié dans la séquence de destination.

### <a name="return-value"></a>Valeur renvoyée

Retour qui indique la réussite, la réussite partielle ou l’échec de l’opération. La fonction retourne :

- `codecvt_base::error` Si la séquence source est incorrecte.

- `codecvt_base::noconv` si la fonction n’exécute aucune conversion.

- `codecvt_base::ok` Si la conversion a échoué.

- `codecvt_base::partial` Si la source est insuffisante ou si la destination n’est pas assez grande, pour que la conversion aboutisse.

### <a name="remarks"></a>Notes

*`state`* doit représenter l’état de conversion initial au début d’une nouvelle séquence source. La fonction modifie sa valeur stockée selon les besoins pour refléter l’état actuel d’une conversion réussie. Sinon, sa valeur stockée n’est pas spécifiée.

### <a name="example"></a>Exemple

Consultez l’exemple pour [`in`](#in) , qui appelle `do_in` .

## <a name="codecvtdo_length"></a><a name="do_length"></a> `codecvt::do_length`

Fonction virtuelle qui détermine le nombre de `Byte` valeurs d’une séquence donnée de valeurs externes qui `Byte` ne produisent pas plus d’un nombre donné de `CharType` valeurs internes et retourne ce nombre de `Byte` valeurs.

```cpp
virtual int do_length(
    const StateType& state,
    const Byte* first1,
    const Byte* last1,
    size_t len2) const;
```

### <a name="parameters"></a>Paramètres

*`state`*\
État de conversion conservé entre les appels à la fonction membre.

*`first1`*\
Pointeur vers le début de la séquence externe.

*`last1`*\
Pointeur vers la fin de la séquence externe.

*`len2`*\
Nombre maximal de `Byte` valeurs qui peuvent être retournées par la fonction membre.

### <a name="return-value"></a>Valeur renvoyée

Entier qui représente le nombre maximal de conversions, non supérieur à *len2* , défini par la séquence source externe à [ `first1` , `last1` ).

### <a name="remarks"></a>Notes

La fonction membre virtuelle protégée appelle effectivement `do_in( state, first1, last1, next1, buf, buf + len2, next2)` l' *État* (une copie de l’État), une mémoire tampon `buf` et des pointeurs `next1` et `next2` .

Elle retourne ensuite `next2` - `buf`. Elle compte le nombre maximal de conversions, non supérieur à *len2* , défini par la séquence source sur [ `first1` , `last1` ).

La version de modèle retourne toujours la valeur la plus petite de *`last1`*  -  *`first1`* et de *`len2`* .

### <a name="example"></a>Exemple

Consultez l’exemple pour [`length`](#length) , qui appelle `do_length` .

## <a name="codecvtdo_max_length"></a><a name="do_max_length"></a> `codecvt::do_max_length`

Fonction virtuelle qui retourne le nombre maximal de valeurs externes `Byte` nécessaires pour produire un interne `CharType` .

```cpp
virtual int do_max_length() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Nombre maximal de `Byte` valeurs nécessaires pour en créer un `CharType` .

### <a name="remarks"></a>Notes

La fonction membre virtuelle protégée retourne la plus grande valeur autorisée qui peut être retournée par [`do_length`](#do_length) `( first1, last1, 1)` pour les valeurs valides arbitraires de *`first1`* et *`last1`* .

### <a name="example"></a>Exemple

Consultez l’exemple pour [`max_length`](#max_length) , qui appelle `do_max_length` .

## <a name="codecvtdo_out"></a><a name="do_out"></a> `codecvt::do_out`

Fonction virtuelle appelée pour convertir une séquence de valeurs internes `CharType` en une séquence de valeurs externes `Byte` .

```cpp
virtual result do_out(
    StateType& state,
    const CharType* first1,
    const CharType* last1,
    const CharType*& next1,
    Byte* first2,
    Byte* last2,
    Byte*& next2) const;
```

### <a name="parameters"></a>Paramètres

*`state`*\
État de conversion conservé entre les appels à la fonction membre.

*`first1`*\
Pointeur vers le début de la séquence à convertir.

*`last1`*\
Pointeur vers la fin de la séquence à convertir.

*`next1`*\
Référence à un pointeur vers le premier non converti `CharType` , après le dernier `CharType` converti.

*`first2`*\
Pointeur vers le début de la séquence convertie.

*`last2`*\
Pointeur vers la fin de la séquence convertie.

*`next2`*\
Référence à un pointeur vers le premier non converti `Byte` , après le dernier `Byte` converti.

### <a name="return-value"></a>Valeur renvoyée

La fonction retourne :

- `codecvt_base::error` Si la séquence source est incorrecte.

- `codecvt_base::noconv` si la fonction n’exécute aucune conversion.

- `codecvt_base::ok` Si la conversion a échoué.

- `codecvt_base::partial` Si la source est insuffisante ou si la destination n’est pas assez grande pour que la conversion aboutisse.

### <a name="remarks"></a>Notes

*`state`* doit représenter l’état de conversion initial au début d’une nouvelle séquence source. La fonction modifie sa valeur stockée selon les besoins pour refléter l’état actuel d’une conversion réussie. Sinon, sa valeur stockée n’est pas spécifiée.

### <a name="example"></a>Exemple

Consultez l’exemple relatif à [out](#out), qui appelle `do_out`.

## <a name="codecvtdo_unshift"></a><a name="do_unshift"></a> `codecvt::do_unshift`

Fonction virtuelle appelée pour fournir les `Byte` valeurs nécessaires dans une conversion dépendante de l’État pour terminer le dernier caractère d’une séquence de `Byte` valeurs.

```cpp
virtual result do_unshift(
    StateType& state,
    Byte* first2,
    Byte* last2,
    Byte*& next2) const;
```

### <a name="parameters"></a>Paramètres

*`state`*\
État de conversion conservé entre les appels à la fonction membre.

*`first2`*\
Pointeur vers la première position dans la plage de destination.

*`last2`*\
Pointeur vers la dernière position dans la plage de destination.

*`next2`*\
Pointeur vers le premier élément non modifié dans la séquence de destination.

### <a name="return-value"></a>Valeur renvoyée

La fonction retourne :

- `codecvt_base::error` Si l' *État* représente un État non valide

- `codecvt_base::noconv` si la fonction n’exécute aucune conversion

- `codecvt_base::ok` Si la conversion a échoué

- `codecvt_base::partial` Si la destination n’est pas assez grande pour que la conversion aboutisse

### <a name="remarks"></a>Notes

La fonction membre virtuelle protégée tente de convertir l’élément source `CharType` (0) en séquence de destination qu’il stocke dans [ `first2` , `last2` ), à l’exception de l’élément de fin `Byte` (0). Elle stocke toujours dans *`next2`* un pointeur vers le premier élément non modifié dans la séquence de destination.

*`State`* doit représenter l’état de conversion initial au début d’une nouvelle séquence source. La fonction modifie sa valeur stockée selon les besoins pour refléter l’état actuel d’une conversion réussie. En règle générale, la conversion de l’élément source `CharType` (0) conserve l’état actuel dans l’état de conversion initial.

### <a name="example"></a>Exemple

Consultez l’exemple pour [`unshift`](#unshift) , qui appelle `do_unshift` .

## <a name="codecvtencoding"></a><a name="encoding"></a> `codecvt::encoding`

Teste si l’encodage du `Byte` flux dépend de l’État, si le rapport entre les `Byte` valeurs utilisées et les `CharType` valeurs produites est constant et, le cas échéant, détermine la valeur de ce ratio.

```cpp
int encoding() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Si la valeur de retour est positive, cette valeur est le nombre constant de `Byte` caractères requis pour produire le `CharType` caractère.

La fonction membre virtuelle protégée retourne :

- -1, si l’encodage des séquences de type `extern_type` est dépendant de l’État.

- 0, si le codage implique des séquences de longueur variable.

- *`N`* Si l’encodage implique uniquement des séquences de longueur *`N`* .

### <a name="remarks"></a>Notes

La fonction membre retourne [do_encoding](#do_encoding).

### <a name="example"></a>Exemple

```cpp
// codecvt_encoding.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   int result1 = use_facet<codecvt<char, char, mbstate_t>> ( loc ).encoding ( );
   cout << result1 << '\n';
   result1 = use_facet<codecvt<wchar_t, char, mbstate_t>> ( loc ).encoding( );
   cout << result1 << '\n';
   result1 = use_facet<codecvt<char, wchar_t, mbstate_t>> ( loc ).encoding( );
   cout << result1 << '\n';
}
```

```Output
1
1
1
```

## <a name="codecvtextern_type"></a><a name="extern_type"></a> `codecvt::extern_type`

Type de caractère utilisé pour les représentations externes.

```cpp
typedef Byte extern_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du paramètre de modèle `Byte`.

## <a name="codecvtin"></a><a name="in"></a> codecvt :: in

Convertit une représentation externe d’une séquence de `Byte` valeurs en représentation interne d’une séquence de `CharType` valeurs.

```cpp
result in(
    StateType& state,
    const Byte* first1,
    const Byte* last1,
    const Byte*& next1,
    CharType* first2,
    CharType* last2,
    CharType*& next2,) const;
```

### <a name="parameters"></a>Paramètres

*`state`*\
État de conversion conservé entre les appels à la fonction membre.

*`first1`*\
Pointeur vers le début de la séquence à convertir.

*`last1`*\
Pointeur vers la fin de la séquence à convertir.

*`next1`*\
Pointeur situé après la fin de la séquence convertie, vers le premier caractère non converti.

*`first2`*\
Pointeur vers le début de la séquence convertie.

*`last2`*\
Pointeur vers la fin de la séquence convertie.

*`next2`*\
Pointeur vers `CharType` qui vient après le dernier converti `Chartype` au premier caractère non modifié dans la séquence de destination.

### <a name="return-value"></a>Valeur renvoyée

Retour qui indique la réussite, la réussite partielle ou l’échec de l’opération. La fonction retourne :

- `codecvt_base::error` Si la séquence source est incorrecte.

- `codecvt_base::noconv` si la fonction n’exécute aucune conversion.

- `codecvt_base::ok` Si la conversion a échoué.

- `codecvt_base::partial` Si la source est insuffisante ou si la destination n’est pas assez grande pour que la conversion aboutisse.

### <a name="remarks"></a>Notes

*`state`* doit représenter l’état de conversion initial au début d’une nouvelle séquence source. La fonction modifie sa valeur stockée selon les besoins pour refléter l’état actuel d’une conversion réussie. Après une conversion partielle, *`state`* doit être défini pour permettre à la conversion de reprendre lorsque de nouveaux caractères arrivent.

La fonction membre retourne [`do_in`](#do_in) `( state, first1,  last1,  next1, first2, last2,  next2)` .

### <a name="example"></a>Exemple

```cpp
// codecvt_in.cpp
// compile with: /EHsc
#define _INTL
#include <locale>
#include <iostream>
using namespace std;
#define LEN 90
int main( )
{
   const char* pszExt = "This is the string to be converted!";
   wchar_t pwszInt [LEN+1];
   memset(&pwszInt[0], 0, (sizeof(wchar_t))*(LEN+1));
   const char* pszNext;
   wchar_t* pwszNext;
   mbstate_t state = {0}; // zero-initialization represents the initial conversion state for mbstate_t
   locale loc("C");//English_Britain");//German_Germany
   int res = use_facet<codecvt<wchar_t, char, mbstate_t>>
     ( loc ).in( state,
          pszExt, &pszExt[strlen(pszExt)], pszNext,
          pwszInt, &pwszInt[strlen(pszExt)], pwszNext );
   pwszInt[strlen(pszExt)] = 0;
   wcout << ( res!=codecvt_base::error ?  L"It worked! " : L"It didn't work! " )
       << L"The converted string is:\n ["
       << &pwszInt[0]
       << L"]" << '\n';
   exit(-1);
}
```

```Output
It worked! The converted string is:
[This is the string to be converted!]
```

## <a name="codecvtintern_type"></a><a name="intern_type"></a> `codecvt::intern_type`

Type de caractère utilisé pour les représentations internes.

```cpp
typedef CharType intern_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du paramètre de modèle `CharType`.

## <a name="codecvtlength"></a><a name="length"></a> codecvt :: length

Détermine le nombre de `Byte` valeurs d’une séquence donnée de `Byte` valeurs externes qui ne produisent pas plus d’un nombre donné de `CharType` valeurs internes et retourne ce nombre de `Byte` valeurs.

```cpp
int length(
    const StateType& state,
    const Byte* first1,
    const Byte* last1,
    size_t len2) const;
```

### <a name="parameters"></a>Paramètres

*`state`*\
État de conversion conservé entre les appels à la fonction membre.

*`first1`*\
Pointeur vers le début de la séquence externe.

*`last1`*\
Pointeur vers la fin de la séquence externe.

*`len2`*\
Nombre maximal d’objets Byte qui peuvent être retournés par la fonction membre.

### <a name="return-value"></a>Valeur renvoyée

Entier qui représente le nombre maximal de conversions, non supérieur à *`len2`* , défini par la séquence source externe à [ `first1` , `last1` ).

### <a name="remarks"></a>Notes

La fonction membre retourne [`do_length`](#do_length) `( state, first1, last1, len2)` .

### <a name="example"></a>Exemple

```cpp
// codecvt_length.cpp
// compile with: /EHsc
#define _INTL
#include <locale>
#include <iostream>
using namespace std;
#define LEN 90
int main( )
{
   const char* pszExt = "This is the string whose length is to be measured!";
   mbstate_t state = {0}; // zero-initialization represents the initial conversion state for mbstate_t
   locale loc("C"); // English_Britain"); //German_Germany
   int res = use_facet<codecvt<wchar_t, char, mbstate_t>>
     ( loc ).length( state,
          pszExt, &pszExt[strlen(pszExt)], LEN );
   cout << "The length of the string is: ";
   wcout << res;
   cout << "." << '\n';
   exit(-1);
}
```

```Output
The length of the string is: 50.
```

## <a name="codecvtmax_length"></a><a name="max_length"></a> `codecvt::max_length`

Retourne le nombre maximal de `Byte` valeurs externes nécessaires pour produire un interne `CharType` .

```cpp
int max_length() const throw();
```

### <a name="return-value"></a>Valeur renvoyée

Nombre maximal de `Byte` valeurs nécessaires pour en créer un `CharType` .

### <a name="remarks"></a>Notes

La fonction membre retourne [`do_max_length`](#do_max_length) .

### <a name="example"></a>Exemple

```cpp
// codecvt_max_length.cpp
// compile with: /EHsc
#define _INTL
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc( "C");//English_Britain" );//German_Germany
   int res = use_facet<codecvt<char, char, mbstate_t>>
     ( loc ).max_length( );
   wcout << res << '\n';
}
```

```Output
1
```

## <a name="codecvtout"></a><a name="out"></a> `codecvt::out`

Convertit une séquence de `CharType` valeurs internes en une séquence de `Byte` valeurs externes.

```cpp
result out(
    StateType& state,
    const CharType* first1,
    const CharType* last1,
    const CharType*& next1,
    Byte* first2,
    Byte* last2,
    Byte*& next2) const;
```

### <a name="parameters"></a>Paramètres

*`state`*\
État de conversion conservé entre les appels à la fonction membre.

*`first1`*\
Pointeur vers le début de la séquence à convertir.

*`last1`*\
Pointeur vers la fin de la séquence à convertir.

*`next1`*\
Référence à un pointeur vers le premier non converti `CharType` après le dernier `CharType` converti.

*`first2`*\
Pointeur vers le début de la séquence convertie.

*`last2`*\
Pointeur vers la fin de la séquence convertie.

*`next2`*\
Référence à un pointeur vers le premier non converti `Byte` après le dernier converti `Byte` .

### <a name="return-value"></a>Valeur renvoyée

La fonction membre retourne [`do_out`](#do_out) `( state, first1, last1, next1, first2, last2, next2)` .

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [`codecvt::do_out`](#do_out).

### <a name="example"></a>Exemple

```cpp
// codecvt_out.cpp
// compile with: /EHsc
#define _INTL
#include <locale>
#include <iostream>
#include <wchar.h>
using namespace std;
#define LEN 90
int main( )
{
    char pszExt[LEN + 1];
    const wchar_t* pwszInt = L"This is the wchar_t string to be converted.";
    memset(&pszExt[0], 0, (sizeof(char)) * (LEN + 1));
    char* pszNext;
    const wchar_t* pwszNext;
    mbstate_t state;
    locale loc("C");//English_Britain");//German_Germany
    int res = use_facet<codecvt<wchar_t, char, mbstate_t>>
        (loc).out(state,
            pwszInt, &pwszInt[wcslen(pwszInt)], pwszNext,
            pszExt, &pszExt[wcslen(pwszInt)], pszNext);
    pszExt[wcslen(pwszInt)] = 0;
    cout << (res != codecvt_base::error ? "It worked: " : "It didn't work: ")
        << "The converted string is:\n ["
        << &pszExt[0]
        << "]" << '\n';

}
```

```Output
It worked: The converted string is:
[This is the wchar_t string to be converted.]
```

## <a name="codecvtstate_type"></a><a name="state_type"></a> `codecvt::state_type`

Type de caractère utilisé pour représenter les états intermédiaires lors de conversions entre des représentations internes et externes.

```cpp
typedef StateType state_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du paramètre de modèle `StateType`.

## <a name="codecvtunshift"></a><a name="unshift"></a> codecvt :: unshift

Fournit les `Byte` valeurs nécessaires dans une conversion dépendante de l’État pour terminer le dernier caractère d’une séquence de `Byte` valeurs.

```cpp
result unshift(
    StateType& state,
    Byte* first2,
    Byte* last2,
    Byte*& next2) const;
```

### <a name="parameters"></a>Paramètres

*`state`*\
État de conversion conservé entre les appels à la fonction membre.

*`first2`*\
Pointeur vers la première position dans la plage de destination.

*`last2`*\
Pointeur vers la dernière position dans la plage de destination.

*`next2`*\
Pointeur vers le premier élément non modifié dans la séquence de destination.

### <a name="return-value"></a>Valeur renvoyée

La fonction retourne :

- `codecvt_base::error` Si l’état représente un État non valide.

- `codecvt_base::noconv` si la fonction n’exécute aucune conversion.

- `codecvt_base::ok` Si la conversion a échoué.

- `codecvt_base::partial` Si la destination n’est pas assez grande pour que la conversion aboutisse.

### <a name="remarks"></a>Notes

La fonction membre virtuelle protégée tente de convertir l’élément source `CharType` (0) en séquence de destination qu’il stocke dans [ `first2` , `last2` ), à l’exception de l’élément de fin `Byte` (0). Elle stocke toujours dans *`next2`* un pointeur vers le premier élément non modifié dans la séquence de destination.

*`state`* doit représenter l’état de conversion initial au début d’une nouvelle séquence source. La fonction modifie sa valeur stockée selon les besoins pour refléter l’état actuel d’une conversion réussie. En règle générale, la conversion de l’élément source `CharType` (0) conserve l’état actuel dans l’état de conversion initial.

La fonction membre retourne [`do_unshift`](#do_unshift) `( state, first2, last2, next2 )` .

## <a name="see-also"></a>Voir aussi

[`<locale>`](../standard-library/locale.md)\
[Pages de codes](../c-runtime-library/code-pages.md)\
[Chaînes de noms de paramètres régionaux, de langues et de pays/région](../c-runtime-library/locale-names-languages-and-country-region-strings.md)\
[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)
