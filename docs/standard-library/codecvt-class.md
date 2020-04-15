---
title: codecvt, classe
ms.date: 11/04/2016
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
ms.openlocfilehash: 3dba971b112c23325e0529e53746cbee827df5e9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371954"
---
# <a name="codecvt-class"></a>codecvt, classe

Un modèle de classe qui décrit un objet qui peut servir de facette locale. Elle peut contrôler les conversions d'une séquence de valeurs utilisées pour encoder des caractères au sein du programme en une séquence de valeurs utilisées pour encoder des caractères en dehors du programme.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType, class Byte, class StateType>
class codecvt : public locale::facet, codecvt_base;
```

### <a name="parameters"></a>Paramètres

*CharType CharType*\
Type utilisé dans le cadre d'un programme pour encoder des caractères.

*Octet*\
Type utilisé pour encoder des caractères en dehors d'un programme.

*StateType (StateType)*\
Type qui peut être utilisé pour représenter les états intermédiaires d'une conversion entre types internes et types externes de représentations de caractères.

## <a name="remarks"></a>Notes

Le modèle de classe décrit un objet qui peut servir de [facette locale,](../standard-library/locale-class.md#facet_class)pour contrôler les conversions entre une séquence de valeurs de type *CharType* et une séquence de valeurs de type *Byte*. La classe *StateType* caractérise la transformation - et un objet de classe *StateType stocke* toutes les informations d’état nécessaires lors d’une conversion.

L’encodage interne utilise une représentation avec un nombre fixe d’octets par personnage, généralement soit type **d’omble** ou de type **wchar_t**.

Comme avec n'importe quelle facette de paramètres régionaux, l'objet statique `id` possède une valeur stockée initiale de zéro. La première tentative d’accès à sa valeur stockée entraîne le stockage d’une valeur positive unique dans `id`.

Les versions de modèle de [do_in](#do_in) et [do_out](#do_out) retournent toujours `codecvt_base::noconv`.

La bibliothèque C++ Standard définit plusieurs spécialisations explicites :

```cpp
template<>
codecvt<wchar_t, char, mbstate_t>
```

se convertit entre les séquences **wchar_t** et les séquences **d’omble chevalier.**

```cpp
template<>
codecvt<char16_t, char, mbstate_t>
```

convertit `char16_t` entre les séquences codées sous forme UTF-16 et les séquences **d’ombles** codées sous forme UTF-8.

```cpp
template<>
codecvt<char32_t, char, mbstate_t>
```

convertit `char32_t` entre les séquences codées sous forme UTF-32 (UCS-4) et les séquences **d’ombles** codées sous forme UTF-8.

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[codecvt](#codecvt)|Constructeur d'objets de la classe `codecvt` qui sert de facette de paramètres régionaux pour la gestion des conversions.|

### <a name="typedefs"></a>Typedefs

|Nom de type|Description|
|-|-|
|[extern_type](#extern_type)|Type de caractère utilisé pour les représentations externes.|
|[intern_type](#intern_type)|Type de caractère utilisé pour les représentations internes.|
|[state_type](#state_type)|Type de caractère utilisé pour représenter les états intermédiaires lors de conversions entre des représentations internes et externes.|

### <a name="member-functions"></a>Fonctions Membre

|Fonction membre|Description|
|-|-|
|[always_noconv](#always_noconv)|Vérifie si une conversion doit être effectuée.|
|[do_always_noconv](#do_always_noconv)|Fonction virtuelle appelée pour vérifier si une conversion doit être effectuée.|
|[do_encoding](#do_encoding)|Une fonction virtuelle qui teste `Byte` si l’encodage du `Byte` flux dépend `CharType` de l’état, si le rapport entre les valeurs utilisées et les valeurs produites est constant, et, dans l’affirmative, détermine la valeur de ce ratio.|
|[do_in](#do_in)|Une fonction virtuelle appelée à `Byte` convertir une séquence `CharType` de valeurs internes en une séquence de valeurs externes.|
|[do_length](#do_length)|Une fonction virtuelle qui `Byte` détermine le nombre de `Byte` valeurs d’une séquence donnée `CharType` de valeurs externes `Byte` ne produit pas plus d’un nombre donné de valeurs internes et retourne ce nombre de valeurs.|
|[do_max_length](#do_max_length)|Fonction virtuelle qui retourne le nombre maximal d'octets externes nécessaires pour produire un `CharType` interne.|
|[do_out](#do_out)|Une fonction virtuelle appelée à `CharType` convertir une séquence de valeurs internes en une séquence de Octets externes.|
|[do_unshift](#do_unshift)|Une fonction virtuelle appelée `Byte` à fournir les valeurs nécessaires dans une conversion `Byte` dépendante de l’État pour compléter le dernier personnage dans une séquence de valeurs.|
|[Encodage](#encoding)|Tests si l’encodage du flux dépend de l’état, `Byte` si le rapport entre les `Byte` valeurs utilisées et les `CharType` valeurs produites est constante, et, dans l’affirmative, détermine la valeur de ce ratio.|
|[in](#in)|Convertit une représentation externe `Byte` d’une séquence de valeurs `CharType` en une représentation interne d’une séquence de valeurs.|
|[length](#length)|Détermine le `Byte` nombre de valeurs d’une séquence donnée de valeurs externes `Byte` ne produisent pas plus d’un nombre donné de valeurs internes `CharType` et retourne ce nombre de `Byte` valeurs.|
|[max_length](#max_length)|Retourne le nombre `Byte` maximum de valeurs `CharType`externes nécessaires pour produire un interne .|
|[out](#out)|Convertit une séquence `CharType` de valeurs internes `Byte` en une séquence de valeurs externes.|
|[unshift](#unshift)|Fournit les `Byte` valeurs externes nécessaires à une conversion dépendante de `Byte` l’État pour compléter le dernier caractère dans la séquence des valeurs.|

## <a name="requirements"></a>Spécifications

**En-tête :** \<locale>

**Espace de noms :** std

## <a name="codecvtalways_noconv"></a><a name="always_noconv"></a>codecvt::always_noconv

Testez si aucune conversion n’a besoin d’être effectuée.

```cpp
bool always_noconv() const throw();
```

### <a name="return-value"></a>Valeur de retour

Une valeur Boolean qui est **vraie** si aucune conversion n’a besoin d’être faite; **faux** si au moins il faut le faire.

### <a name="remarks"></a>Notes

La fonction membre retourne [do_always_noconv](#do_always_noconv).

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
   bool result1 = use_facet<codecvt<char, char, mbstate_t> >
      ( loc ).always_noconv( );

   if ( result1 )
      cout << "No conversion is needed." << endl;
   else
      cout << "At least one conversion is required." << endl;

   bool result2 = use_facet<codecvt<wchar_t, char, mbstate_t> >
      ( loc ).always_noconv( );

   if ( result2 )
      cout << "No conversion is needed." << endl;
   else
      cout << "At least one conversion is required." << endl;
}
```

```Output
No conversion is needed.
At least one conversion is required.
```

## <a name="codecvtcodecvt"></a><a name="codecvt"></a>codecvt::codecvt

Constructeur d’objets de la classe codecvt qui sert de facette de paramètres régionaux pour la gestion des conversions.

```cpp
explicit codecvt(size_t refs = 0);
```

### <a name="parameters"></a>Paramètres

*Refs*\
Valeur entière utilisée pour spécifier le type de gestion de mémoire pour l’objet.

### <a name="remarks"></a>Notes

Les valeurs possibles pour le *paramètre des arbitres* et leur signification sont les suivante :

- 0 : la durée de vie de l’objet est gérée par les paramètres régionaux qui le contiennent.

- 1 : la durée de vie de l’objet doit être gérée manuellement.

- 2: Ces valeurs ne sont pas définies.

Le constructeur initialise `locale::facet` son objet de base avec [local:facet](../standard-library/locale-class.md#facet_class)`(refs)`.

## <a name="codecvtdo_always_noconv"></a><a name="do_always_noconv"></a>codecvt::do-always-noconv

Une fonction virtuelle appelée à tester si aucune conversion n’a besoin d’être faite.

```cpp
virtual bool do_always_noconv() const throw();
```

### <a name="return-value"></a>Valeur de retour

La fonction de membre virtuel protégée ne renvoie **vrai** que si `noconv`chaque appel à [do_in](#do_in) ou [do_out](#do_out) revient .

La version de modèle retourne toujours **true**.

### <a name="example"></a>Exemple

Consultez l’exemple relatif à [always_noconv](#always_noconv), qui appelle la méthode `do_always_noconv`.

## <a name="codecvtdo_encoding"></a><a name="do_encoding"></a>codecvt::do-encodage

Une fonction virtuelle qui teste `Byte` si l’encodage du `Byte` flux dépend `CharType` de l’état, si le rapport entre les valeurs utilisées et les valeurs produites est constant et, dans l’affirmative, détermine la valeur de ce ratio.

```cpp
virtual int do_encoding() const throw();
```

### <a name="return-value"></a>Valeur de retour

La fonction membre virtuelle protégée retourne :

- -1, si l’encodage `extern_type` des séquences de type dépend de l’état.

- 0, si le codage implique des séquences de longueur variable.

- *N*, si le codage implique uniquement des séquences de longueur *N*

### <a name="example"></a>Exemple

Consultez l’exemple relatif à [encoding](#encoding), qui appelle `do_encoding`.

## <a name="codecvtdo_in"></a><a name="do_in"></a>codecvt::do-in

Une fonction virtuelle appelée à `Byte` convertir une séquence `CharType` de valeurs externes en une séquence de valeurs internes.

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

*État*\
État de conversion conservé entre les appels à la fonction membre.

*première1*\
Pointeur vers le début de la séquence à convertir.

*last1*\
Pointeur vers la fin de la séquence à convertir.

*next1*\
Pointeur situé après la fin de la séquence convertie, vers le premier caractère non converti.

*premier2*\
Pointeur vers le début de la séquence convertie.

*last2*\
Pointeur vers la fin de la séquence convertie.

*next2*\
Pointeur `CharType` à celui qui vient `CharType`après le dernier converti , au premier personnage inchangé dans la séquence de destination.

### <a name="return-value"></a>Valeur de retour

Retour qui indique la réussite, la réussite partielle ou l’échec de l’opération. La fonction retourne :

- `codecvt_base::error`si la séquence source est mal formée.

- `codecvt_base::noconv` si la fonction n’exécute aucune conversion.

- `codecvt_base::ok`si la conversion réussit.

- `codecvt_base::partial`si la source est insuffisante ou si la destination n’est pas assez grande, pour que la conversion réussisse.

### <a name="remarks"></a>Notes

*l’état* doit représenter l’état initial de conversion au début d’une nouvelle séquence source. La fonction modifie sa valeur stockée selon les besoins pour refléter l’état actuel d’une conversion réussie. Sinon, sa valeur stockée n’est pas spécifiée.

### <a name="example"></a>Exemple

Consultez l’exemple relatif à [in](#in), qui appelle `do_in`.

## <a name="codecvtdo_length"></a><a name="do_length"></a>codecvt::do-longueur

Une fonction virtuelle qui `Byte` détermine le nombre de `Byte` valeurs d’une séquence donnée `CharType` de valeurs externes `Byte` ne produit pas plus d’un nombre donné de valeurs internes et retourne ce nombre de valeurs.

```cpp
virtual int do_length(
    const StateType& state,
    const Byte* first1,
    const Byte* last1,
    size_t len2) const;
```

### <a name="parameters"></a>Paramètres

*État*\
État de conversion conservé entre les appels à la fonction membre.

*première1*\
Pointeur vers le début de la séquence externe.

*last1*\
Pointeur vers la fin de la séquence externe.

*len2*\
Le nombre `Byte` maximum de valeurs qui peuvent être retournées par la fonction membre.

### <a name="return-value"></a>Valeur de retour

Un intégrant qui représente un nombre maximum de conversions, pas supérieure à *len2*, défini par la séquence source externe à [ `first1`, `last1`).

### <a name="remarks"></a>Notes

La fonction de membre `do_in( state, first1, last1, next1, buf, buf + len2, next2)` virtuel protégée appelle effectivement *l’état* (une copie de l’état), certains tampons `buf` `next1` , et pointeurs et `next2`.

Elle retourne ensuite `next2` - `buf`. Ainsi, il compte le nombre maximum de conversions, pas supérieure à *len2*, défini par la séquence source à [ `first1`, `last1`).

La version modèle retourne toujours le moindre de *last1 first1* - *first1* et *len2*.

### <a name="example"></a>Exemple

Voir l’exemple pour `do_length`la [longueur](#length), qui appelle .

## <a name="codecvtdo_max_length"></a><a name="do_max_length"></a>codecvt::do-max-longueur

Une fonction virtuelle qui renvoie `Byte` le nombre maximum `CharType`de valeurs externes nécessaires pour produire un interne .

```cpp
virtual int do_max_length() const throw();
```

### <a name="return-value"></a>Valeur de retour

Le nombre `Byte` maximum de valeurs `CharType`nécessaires pour en produire une .

### <a name="remarks"></a>Notes

La fonction de membre virtuel protégée retourne la plus grande valeur permise qui peut être retournée par [do_length](#do_length) `( first1, last1, 1)` pour des valeurs arbitraires valides de *first1* et *last1*.

### <a name="example"></a>Exemple

Consultez l’exemple relatif à [max_length](#max_length), qui appelle `do_max_length`.

## <a name="codecvtdo_out"></a><a name="do_out"></a>codecvt::do-out

Une fonction virtuelle appelée à `CharType` convertir une séquence `Byte` de valeurs internes en une séquence de valeurs externes.

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

*État*\
État de conversion conservé entre les appels à la fonction membre.

*première1*\
Pointeur vers le début de la séquence à convertir.

*last1*\
Pointeur vers la fin de la séquence à convertir.

*next1*\
Référence à un pointeur au `CharType`premier non `CharType` converti, après le dernier converti.

*premier2*\
Pointeur vers le début de la séquence convertie.

*last2*\
Pointeur vers la fin de la séquence convertie.

*next2*\
Référence à un pointeur au `Byte`premier non `Byte` converti, après le dernier converti.

### <a name="return-value"></a>Valeur de retour

La fonction retourne :

- `codecvt_base::error`si la séquence source est mal formée.

- `codecvt_base::noconv` si la fonction n’exécute aucune conversion.

- `codecvt_base::ok`si la conversion réussit.

- `codecvt_base::partial`si la source est insuffisante ou si la destination n’est pas assez grande pour que la conversion réussisse.

### <a name="remarks"></a>Notes

*l’état* doit représenter l’état initial de conversion au début d’une nouvelle séquence source. La fonction modifie sa valeur stockée selon les besoins pour refléter l’état actuel d’une conversion réussie. Sinon, sa valeur stockée n’est pas spécifiée.

### <a name="example"></a>Exemple

Consultez l’exemple relatif à [out](#out), qui appelle `do_out`.

## <a name="codecvtdo_unshift"></a><a name="do_unshift"></a>codecvt::do-unshift

Une fonction virtuelle appelée `Byte` à fournir les valeurs nécessaires dans une conversion `Byte` dépendante de l’État pour compléter le dernier personnage dans une séquence de valeurs.

```cpp
virtual result do_unshift(
    StateType& state,
    Byte* first2,
    Byte* last2,
    Byte*& next2) const;
```

### <a name="parameters"></a>Paramètres

*État*\
État de conversion conservé entre les appels à la fonction membre.

*premier2*\
Pointeur vers la première position dans la plage de destination.

*last2*\
Pointeur vers la dernière position dans la plage de destination.

*next2*\
Pointeur vers le premier élément non modifié dans la séquence de destination.

### <a name="return-value"></a>Valeur de retour

La fonction retourne :

- `codecvt_base::error`si *l’État* représente un État invalide

- `codecvt_base::noconv` si la fonction n’exécute aucune conversion

- `codecvt_base::ok`si la conversion réussit

- `codecvt_base::partial`si la destination n’est pas assez grande pour que la conversion réussisse

### <a name="remarks"></a>Notes

La fonction de membre virtuel protégée `CharType`tente de convertir l’élément source `first2`(0) en une séquence de destination qu’il stocke à l’intérieur [, `last2`), à l’exception de l’élément `Byte`de fin (0). Il stocke toujours dans *next2* un pointeur à l’élément premier inchangé dans la séquence de destination.

_ *State* doit représenter l’état initial de la conversion au début d’une nouvelle séquence source. La fonction modifie sa valeur stockée selon les besoins pour refléter l’état actuel d’une conversion réussie. Typiquement, la conversion `CharType`de l’élément source (0) laisse l’état actuel dans l’état initial de conversion.

### <a name="example"></a>Exemple

Consultez l’exemple relatif à [unshift](#unshift), qui appelle `do_unshift`.

## <a name="codecvtencoding"></a><a name="encoding"></a>codecvt::encodage

Tests si l’encodage du flux dépend de l’état, `Byte` si le rapport entre les `Byte` valeurs utilisées et les `CharType` valeurs produites est constante, et, dans l’affirmative, détermine la valeur de ce ratio.

```cpp
int encoding() const throw();
```

### <a name="return-value"></a>Valeur de retour

Si la valeur de retour est positive, `Byte` cette valeur `CharType` est le nombre constant de caractères requis pour produire le personnage.

La fonction membre virtuelle protégée retourne :

- -1, si l’encodage `extern_type` des séquences de type dépend de l’état.

- 0, si le codage implique des séquences de longueur variable.

- *N*, si l’encodage n’implique que des séquences de longueur *N.*

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
   int result1 = use_facet<codecvt<char, char, mbstate_t> > ( loc ).encoding ( );
   cout << result1 << endl;
   result1 = use_facet<codecvt<wchar_t, char, mbstate_t> > ( loc ).encoding( );
   cout << result1 << endl;
   result1 = use_facet<codecvt<char, wchar_t, mbstate_t> > ( loc ).encoding( );
   cout << result1 << endl;
}
```

```Output
1
1
1
```

## <a name="codecvtextern_type"></a><a name="extern_type"></a>codecvt::extern_type

Type de caractère utilisé pour les représentations externes.

```cpp
typedef Byte extern_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du paramètre de modèle `Byte`.

## <a name="codecvtin"></a><a name="in"></a>codecvt::dans

Convertit une représentation externe `Byte` d’une séquence de valeurs `CharType` en une représentation interne d’une séquence de valeurs.

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

*État*\
État de conversion conservé entre les appels à la fonction membre.

*première1*\
Pointeur vers le début de la séquence à convertir.

*last1*\
Pointeur vers la fin de la séquence à convertir.

*next1*\
Pointeur situé après la fin de la séquence convertie, vers le premier caractère non converti.

*premier2*\
Pointeur vers le début de la séquence convertie.

*last2*\
Pointeur vers la fin de la séquence convertie.

*next2*\
Pointeur `CharType` à celui qui vient `Chartype` après le dernier converti au premier personnage inchangé dans la séquence de destination.

### <a name="return-value"></a>Valeur de retour

Retour qui indique la réussite, la réussite partielle ou l’échec de l’opération. La fonction retourne :

- `codecvt_base::error`si la séquence source est mal formée.

- `codecvt_base::noconv` si la fonction n’exécute aucune conversion.

- `codecvt_base::ok`si la conversion réussit.

- `codecvt_base::partial`si la source est insuffisante ou si la destination n’est pas assez grande pour que la conversion réussisse.

### <a name="remarks"></a>Notes

*l’état* doit représenter l’état initial de conversion au début d’une nouvelle séquence source. La fonction modifie sa valeur stockée selon les besoins pour refléter l’état actuel d’une conversion réussie. Après une conversion partielle, *l’état* doit être défini de telle sorte que de permettre à la conversion de reprendre lorsque de nouveaux personnages arrivent.

La fonction membre renvoie [do_in](#do_in)`( state, first1,  last1,  next1, first2, last2,  next2)`.

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
   char* pszExt = "This is the string to be converted!";
   wchar_t pwszInt [LEN+1];
   memset(&pwszInt[0], 0, (sizeof(wchar_t))*(LEN+1));
   const char* pszNext;
   wchar_t* pwszNext;
   mbstate_t state = {0};
   locale loc("C");//English_Britain");//German_Germany
   int res = use_facet<codecvt<wchar_t, char, mbstate_t> >
     ( loc ).in( state,
          pszExt, &pszExt[strlen(pszExt)], pszNext,
          pwszInt, &pwszInt[strlen(pszExt)], pwszNext );
   pwszInt[strlen(pszExt)] = 0;
   wcout << ( (res!=codecvt_base::error)  L"It worked! " : L"It didn't work! " )
   << L"The converted string is:\n ["
   << &pwszInt[0]
   << L"]" << endl;
   exit(-1);
}
```

```Output
It worked! The converted string is:
[This is the string to be converted!]
```

## <a name="codecvtintern_type"></a><a name="intern_type"></a>codecvt::intern_type

Type de caractère utilisé pour les représentations internes.

```cpp
typedef CharType intern_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du paramètre de modèle `CharType`.

## <a name="codecvtlength"></a><a name="length"></a>codecvt::longueur

Détermine le `Byte` nombre de valeurs d’une séquence donnée de valeurs externes `Byte` ne produisent pas plus d’un nombre donné de valeurs internes `CharType` et retourne ce nombre de `Byte` valeurs.

```cpp
int length(
    const StateType& state,
    const Byte* first1,
    const Byte* last1,
    size_t len2) const;
```

### <a name="parameters"></a>Paramètres

*État*\
État de conversion conservé entre les appels à la fonction membre.

*première1*\
Pointeur vers le début de la séquence externe.

*last1*\
Pointeur vers la fin de la séquence externe.

*len2*\
Nombre maximal d’objets Byte qui peuvent être retournés par la fonction membre.

### <a name="return-value"></a>Valeur de retour

Un intégrant qui représente un nombre maximum de conversions, pas supérieure à *len2*, défini par la séquence source externe à [ `first1`, `last1`).

### <a name="remarks"></a>Notes

La fonction membre renvoie [do_length](#do_length)`( state, first1, last1, len2)`.

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
   char* pszExt = "This is the string whose length is to be measured!";
   mbstate_t state = {0};
   locale loc("C");//English_Britain");//German_Germany
   int res = use_facet<codecvt<wchar_t, char, mbstate_t> >
     ( loc ).length( state,
          pszExt, &pszExt[strlen(pszExt)], LEN );
   cout << "The length of the string is: ";
   wcout << res;
   cout << "." << endl;
   exit(-1);
}
```

```Output
The length of the string is: 50.
```

## <a name="codecvtmax_length"></a><a name="max_length"></a>codecvt::max_length

Retourne le nombre `Byte` maximum de valeurs `CharType`externes nécessaires pour produire un interne .

```cpp
int max_length() const throw();
```

### <a name="return-value"></a>Valeur de retour

Le nombre `Byte` maximum de valeurs `CharType`nécessaires pour en produire une .

### <a name="remarks"></a>Notes

La fonction membre retourne [do_max_length](#do_max_length).

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
   int res = use_facet<codecvt<char, char, mbstate_t> >
     ( loc ).max_length( );
   wcout << res << endl;
}
```

```Output
1
```

## <a name="codecvtout"></a><a name="out"></a>codecvt::out

Convertit une séquence `CharType` de valeurs internes `Byte` en une séquence de valeurs externes.

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

*État*\
État de conversion conservé entre les appels à la fonction membre.

*première1*\
Pointeur vers le début de la séquence à convertir.

*last1*\
Pointeur vers la fin de la séquence à convertir.

*next1*\
Référence à un pointeur au `CharType` premier non `CharType` converti après le dernier converti.

*premier2*\
Pointeur vers le début de la séquence convertie.

*last2*\
Pointeur vers la fin de la séquence convertie.

*next2*\
Référence à un pointeur au `Byte` premier non converti `Byte`après le dernier converti .

### <a name="return-value"></a>Valeur de retour

La fonction membre renvoie [do_out](#do_out)`( state, first1, last1, next1, first2, last2, next2)`.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [codecvt::do_out](#do_out).

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
   char pszExt[LEN+1];
   wchar_t *pwszInt = L"This is the wchar_t string to be converted.";
   memset( &pszExt[0], 0, ( sizeof( char ) )*( LEN+1 ) );
   char* pszNext;
   const wchar_t* pwszNext;
   mbstate_t state;
   locale loc("C");//English_Britain");//German_Germany
   int res = use_facet<codecvt<wchar_t, char, mbstate_t> >
      ( loc ).out( state,
      pwszInt, &pwszInt[wcslen( pwszInt )], pwszNext ,
      pszExt, &pszExt[wcslen( pwszInt )], pszNext );
   pszExt[wcslen( pwszInt )] = 0;
   cout << ( ( res!=codecvt_base::error )  "It worked: " : "It didn't work: " )
   << "The converted string is:\n ["
   << &pszExt[0]
   << "]" << endl;
}
```

```Output
It worked: The converted string is:
[This is the wchar_t string to be converted.]
```

## <a name="codecvtstate_type"></a><a name="state_type"></a>codecvt::state_type

Type de caractère utilisé pour représenter les états intermédiaires lors de conversions entre des représentations internes et externes.

```cpp
typedef StateType state_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du paramètre de modèle `StateType`.

## <a name="codecvtunshift"></a><a name="unshift"></a>codecvt::unshift

Fournit `Byte` les valeurs nécessaires dans une conversion dépendante de l’État pour compléter le dernier personnage dans une séquence de `Byte` valeurs.

```cpp
result unshift(
    StateType& state,
    Byte* first2,
    Byte* last2,
    Byte*& next2) const;
```

### <a name="parameters"></a>Paramètres

*État*\
État de conversion conservé entre les appels à la fonction membre.

*premier2*\
Pointeur vers la première position dans la plage de destination.

*last2*\
Pointeur vers la dernière position dans la plage de destination.

*next2*\
Pointeur vers le premier élément non modifié dans la séquence de destination.

### <a name="return-value"></a>Valeur de retour

La fonction retourne :

- `codecvt_base::error`si l’État représente un État invalide.

- `codecvt_base::noconv` si la fonction n’exécute aucune conversion.

- `codecvt_base::ok`si la conversion réussit.

- `codecvt_base::partial`si la destination n’est pas assez grande pour que la conversion réussisse.

### <a name="remarks"></a>Notes

La fonction de membre virtuel protégée `CharType`tente de convertir l’élément source `first2`(0) en une séquence de destination qu’il stocke à l’intérieur [, `last2`), à l’exception de l’élément `Byte`de fin (0). Il stocke toujours dans *next2* un pointeur à l’élément premier inchangé dans la séquence de destination.

*l’état* doit représenter l’état initial de conversion au début d’une nouvelle séquence source. La fonction modifie sa valeur stockée selon les besoins pour refléter l’état actuel d’une conversion réussie. Typiquement, la conversion `CharType`de l’élément source (0) laisse l’état actuel dans l’état initial de conversion.

La fonction membre renvoie [do_unshift](#do_unshift)`( state, first2, last2, next2 )`.

## <a name="see-also"></a>Voir aussi

[\<local>](../standard-library/locale.md)\
[Code Pages](../c-runtime-library/code-pages.md)\
[Noms locaux, langues et cordes pays/région](../c-runtime-library/locale-names-languages-and-country-region-strings.md)\
[Sécurité des fils dans la bibliothèque standard de CMD](../standard-library/thread-safety-in-the-cpp-standard-library.md)
