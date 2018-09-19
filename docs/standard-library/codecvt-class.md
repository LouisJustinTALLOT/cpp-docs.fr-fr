---
title: codecvt, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f02f6a2810f5ac3a51abb80245c22a7f0c2df434
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46074147"
---
# <a name="codecvt-class"></a>codecvt, classe

Classe de modèle qui décrit un objet pouvant servir de facette de paramètres régionaux. Elle peut contrôler les conversions d'une séquence de valeurs utilisées pour encoder des caractères au sein du programme en une séquence de valeurs utilisées pour encoder des caractères en dehors du programme.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType, class Byte, class StateType>
class codecvt : public locale::facet, codecvt_base;
```

### <a name="parameters"></a>Paramètres

*CharType*<br/>
Type utilisé dans le cadre d'un programme pour encoder des caractères.

*Byte*<br/>
Type utilisé pour encoder des caractères en dehors d'un programme.

*StateType*<br/>
Type qui peut être utilisé pour représenter les états intermédiaires d'une conversion entre types internes et types externes de représentations de caractères.

## <a name="remarks"></a>Notes

La classe de modèle décrit un objet pouvant servir un [facette de paramètres régionaux](../standard-library/locale-class.md#facet_class), pour contrôler les conversions entre une séquence de valeurs de type *CharType* et une séquence de valeurs de type *octets*. La classe *StateType* caractérise la transformation--et un objet de classe *StateType* stocke les informations d’état nécessaires lors de la conversion.

L’encodage interne utilise une représentation avec un nombre fixe d’octets par caractère, généralement de type **char** ou type **wchar_t**.

Comme avec n'importe quelle facette de paramètres régionaux, l'objet statique `id` possède une valeur stockée initiale de zéro. La première tentative d’accès à sa valeur stockée entraîne le stockage d’une valeur positive unique dans `id`.

Les versions de modèle de [do_in](#do_in) et [do_out](#do_out) retournent toujours `codecvt_base::noconv`.

La bibliothèque C++ Standard définit plusieurs spécialisations explicites :

```cpp
template<>
codecvt<wchar_t, char, mbstate_t>
```

effectue la conversion entre **wchar_t** et **char** séquences.

```cpp
template<>
codecvt<char16_t, char, mbstate_t>
```

effectue la conversion entre `char16_t` séquences encodés au format UTF-16 et **char** séquences codés en UTF-8.

```cpp
template<>
codecvt<char32_t, char, mbstate_t>
```

effectue la conversion entre `char32_t` séquences encodés au format UTF-32 (UCS-4) et **char** séquences codés en UTF-8.

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[codecvt](#codecvt)|Constructeur d'objets de la classe `codecvt` qui sert de facette de paramètres régionaux pour la gestion des conversions.|

### <a name="typedefs"></a>Typedef

|Nom de type|Description|
|-|-|
|[extern_type](#extern_type)|Type de caractère utilisé pour les représentations externes.|
|[intern_type](#intern_type)|Type de caractère utilisé pour les représentations internes.|
|[state_type](#state_type)|Type de caractère utilisé pour représenter les états intermédiaires lors de conversions entre des représentations internes et externes.|

### <a name="member-functions"></a>Fonctions membres

|Fonction membre|Description|
|-|-|
|[always_noconv](#always_noconv)|Vérifie si une conversion doit être effectuée.|
|[do_always_noconv](#do_always_noconv)|Fonction virtuelle appelée pour vérifier si une conversion doit être effectuée.|
|[do_encoding](#do_encoding)|Fonction virtuelle qui vérifie si l'encodage du flux `Byte` dépend d'un état. Elle vérifie également si le rapport entre les `Byte` utilisés et les `CharType` produits est constant, et, le cas échéant, détermine la valeur de ce rapport.|
|[do_in](#do_in)|Fonction virtuelle appelée pour convertir une séquence de `Byte` internes en une séquence de `CharType` externes.|
|[do_length](#do_length)|Fonction virtuelle qui détermine le nombre de `Byte` d'une séquence donnée de d'`Byte` externes n'ayant pas produit plus d'un nombre donné de d'`CharType` internes, et retourne ce nombre de `Byte`.|
|[do_max_length](#do_max_length)|Fonction virtuelle qui retourne le nombre maximal d'octets externes nécessaires pour produire un `CharType` interne.|
|[do_out](#do_out)|Fonction virtuelle appelée pour convertir une séquence de `CharType` internes en une séquence d'octets externes.|
|[do_unshift](#do_unshift)|Fonction virtuelle appelée pour fournir le `Byte` nécessaire dans une conversion avec dépendance d'état, afin d'ajouter le dernier caractère d'une séquence de `Byte`.|
|[encoding](#encoding)|Vérifie si l'encodage du flux `Byte` dépend d'un état. Elle vérifie également si le rapport entre les `Byte` utilisés et les `CharType` produits est constant, et, le cas échéant, détermine la valeur de ce rapport.|
|[in](#in)|Convertit la représentation externe d'une séquence de `Byte` en la représentation interne d'une séquence de `CharType`.|
|[length](#length)|Détermine le nombre de `Byte` d'une séquence donnée de d'`Byte` externes n'ayant pas produit plus d'un nombre donné de d'`CharType` internes, et retourne ce nombre de `Byte`.|
|[max_length](#max_length)|Retourne le nombre maximal de `Byte` externes nécessaires pour produire un `CharType` interne.|
|[out](#out)|Convertit une séquence de `CharType` internes en une séquence de `Byte` externes.|
|[unshift](#unshift)|Fournit les `Byte` externes nécessaires pour une conversion avec dépendance d'état, afin d'ajouter le dernier caractère de la séquence de `Byte`.|

## <a name="requirements"></a>Configuration requise

**En-tête :** \<locale>

**Espace de noms :** std

## <a name="always_noconv"></a>  codecvt::always_noconv

Vérifie si une conversion doit être effectuée.

```cpp
bool always_noconv() const throw();
```

### <a name="return-value"></a>Valeur de retour

Valeur booléenne qui est **true** si aucune conversion ne doit être effectuée ; **false** si au moins une doit être effectuée.

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

## <a name="codecvt"></a>  codecvt::codecvt

Constructeur d’objets de la classe codecvt qui sert de facette de paramètres régionaux pour la gestion des conversions.

```cpp
explicit codecvt(size_t _Refs = 0);
```

### <a name="parameters"></a>Paramètres

*_Refs*<br/>
Valeur entière utilisée pour spécifier le type de gestion de mémoire pour l’objet.

### <a name="remarks"></a>Notes

Les valeurs possibles pour le *_Refs* paramètre et leur signification sont :

- 0 : la durée de vie de l’objet est gérée par les paramètres régionaux qui le contiennent.

- 1 : la durée de vie de l’objet doit être gérée manuellement.

- 2 : ces valeurs ne sont pas définies.

Le constructeur initialise ses `locale::facet` objet de base avec **paramètres régionaux ::**[facette](../standard-library/locale-class.md#facet_class)(`_Refs`).

## <a name="do_always_noconv"></a>  codecvt::do_always_noconv

Fonction virtuelle appelée pour vérifier si une conversion doit être effectuée.

```cpp
virtual bool do_always_noconv() const throw();
```

### <a name="return-value"></a>Valeur de retour

La fonction membre virtuelle protégée retourne **true** uniquement si chaque appel à [do_in](#do_in) ou [do_out](#do_out) retourne `noconv`.

La version de modèle retourne toujours **true**.

### <a name="example"></a>Exemple

Consultez l’exemple relatif à [always_noconv](#always_noconv), qui appelle la méthode `do_always_noconv`.

## <a name="do_encoding"></a>  codecvt::do_encoding

Une fonction virtuelle qui teste si l’encodage de la `Byte` flux est dépend d’un état indique si le rapport entre la `Byte`s utilisé et le `CharType`produits est constant et, le cas échéant, détermine la valeur de ce rapport.

```cpp
virtual int do_encoding() const throw();
```

### <a name="return-value"></a>Valeur de retour

La fonction membre virtuelle protégée retourne :

- -1, si le codage de séquences de type `extern_type` dépend de l’état.

- 0, si le codage implique des séquences de longueur variable.

- *N*, si le codage implique uniquement des séquences de longueur *N*

### <a name="example"></a>Exemple

Consultez l’exemple relatif à [encoding](#encoding), qui appelle `do_encoding`.

## <a name="do_in"></a>  codecvt::do_in

Une fonction virtuelle appelée pour convertir une séquence d’externes `Byte`en une séquence interne `CharType`s.

```cpp
virtual result do_in(
    StateType& _State,
    const Byte* first1,
    const Byte* last1,
    const Byte*& next1,
    CharType* first2,
    CharType* last2,
    CharType*& next2,) const;
```

### <a name="parameters"></a>Paramètres

*_State*<br/>
État de conversion conservé entre les appels à la fonction membre.

*first1*<br/>
Pointeur vers le début de la séquence à convertir.

*last1*<br/>
Pointeur vers la fin de la séquence à convertir.

*next1*<br/>
Pointeur situé après la fin de la séquence convertie, vers le premier caractère non converti.

*first2*<br/>
Pointeur vers le début de la séquence convertie.

*last2*<br/>
Pointeur vers la fin de la séquence convertie.

*next2*<br/>
Pointeur vers le `CharType` qui vient après le dernier converti `CharType`, vers le premier caractère non modifié dans la séquence de destination.

### <a name="return-value"></a>Valeur de retour

Retour qui indique la réussite, la réussite partielle ou l’échec de l’opération. La fonction retourne :

- `codecvt_base::error` Si la séquence source est malade formée.

- `codecvt_base::noconv` si la fonction n’exécute aucune conversion.

- `codecvt_base::ok` Si la conversion réussit.

- `codecvt_base::partial` Si la source est insuffisante ou si la destination n’est pas assez grande pour que la conversion réussisse.

### <a name="remarks"></a>Notes

*_State* doit représenter l’état de conversion initial au début d’une nouvelle séquence source. La fonction modifie sa valeur stockée selon les besoins pour refléter l’état actuel d’une conversion réussie. Sinon, sa valeur stockée n’est pas spécifiée.

### <a name="example"></a>Exemple

Consultez l’exemple relatif à [in](#in), qui appelle `do_in`.

## <a name="do_length"></a>  codecvt::do_length

Fonction virtuelle qui détermine le nombre de `Byte` d'une séquence donnée de d'`Byte` externes n'ayant pas produit plus d'un nombre donné de d'`CharType` internes, et retourne ce nombre de `Byte`.

```cpp
virtual int do_length(
    const StateType& _State,
    const Byte* first1,
    const Byte* last1,
    size_t _Len2) const;
```

### <a name="parameters"></a>Paramètres

*_State*<br/>
État de conversion conservé entre les appels à la fonction membre.

*first1*<br/>
Pointeur vers le début de la séquence externe.

*last1*<br/>
Pointeur vers la fin de la séquence externe.

*_Len2*<br/>
Le nombre maximal de `Byte`s qui peuvent être retournées par la fonction membre.

### <a name="return-value"></a>Valeur de retour

Entier qui représente le nombre maximal de conversions, non supérieures à *_Len2*, défini par la séquence source externe sur [ `first1`, `last1`).

### <a name="remarks"></a>Notes

La fonction membre virtuelle protégée appelle `do_in`( `_State`, `first1`, `last1`, `next1`, `_Buf`, `_Buf`  +  `_Len2`, `next2`) pour *_State* (une copie de l’état), une mémoire tampon `_Buf`, ainsi que des pointeurs `next1`et `next2`.

Elle retourne ensuite `next2`  -  `buf`. Par conséquent, il compte le nombre maximal de conversions, non supérieur à *_Len2*, défini par la séquence source sur [ `first1`, `last1`).

La version de modèle retourne toujours le plus petit de *last1* - *first1* et *_Len2*.

### <a name="example"></a>Exemple

Consultez l’exemple de [longueur](#length), qui appelle `do_length`.

## <a name="do_max_length"></a>  codecvt::do_max_length

Une fonction virtuelle qui retourne le nombre maximal d’externe `Byte`s nécessaires pour produire un interne `CharType`.

```cpp
virtual int do_max_length() const throw();
```

### <a name="return-value"></a>Valeur de retour

Le nombre maximal de `Byte`s nécessaires pour produire un `CharType`.

### <a name="remarks"></a>Notes

La fonction membre virtuelle protégée retourne la plus grande valeur autorisée qui peut être retournée par [do_length](#do_length)( `first1`, `last1`, 1) pour les valeurs valides arbitraires de *first1* et *last1*.

### <a name="example"></a>Exemple

Consultez l’exemple relatif à [max_length](#max_length), qui appelle `do_max_length`.

## <a name="do_out"></a>  codecvt::do_out

Fonction virtuelle appelée pour convertir une séquence de `CharType` internes en une séquence de `Byte` externes.

```cpp
virtual result do_out(
    StateType& _State,
    const CharType* first1,
    const CharType* last1,
    const CharType*& next1,
    Byte* first2,
    Byte* last2,
    Byte*& next2) const;
```

### <a name="parameters"></a>Paramètres

*_State*<br/>
État de conversion conservé entre les appels à la fonction membre.

*first1*<br/>
Pointeur vers le début de la séquence à convertir.

*last1*<br/>
Pointeur vers la fin de la séquence à convertir.

*next1*<br/>
Référence à un pointeur vers le premier non converti `CharType`, après le dernier `CharType` converti.

*first2*<br/>
Pointeur vers le début de la séquence convertie.

*last2*<br/>
Pointeur vers la fin de la séquence convertie.

*next2*<br/>
Référence à un pointeur vers le premier non converti `Byte`, après le dernier `Byte` converti.

### <a name="return-value"></a>Valeur de retour

La fonction retourne :

- `codecvt_base::error` Si la séquence source est malade formée.

- `codecvt_base::noconv` si la fonction n’exécute aucune conversion.

- `codecvt_base::ok` Si la conversion réussit.

- `codecvt_base::partial` Si la source est insuffisante ou si la destination n’est pas assez grande pour que la conversion réussisse.

### <a name="remarks"></a>Notes

*_State* doit représenter l’état de conversion initial au début d’une nouvelle séquence source. La fonction modifie sa valeur stockée selon les besoins pour refléter l’état actuel d’une conversion réussie. Sinon, sa valeur stockée n’est pas spécifiée.

### <a name="example"></a>Exemple

Consultez l’exemple relatif à [out](#out), qui appelle `do_out`.

## <a name="do_unshift"></a>  codecvt::do_unshift

Fonction virtuelle appelée pour fournir le `Byte` nécessaire dans une conversion avec dépendance d'état, afin d'ajouter le dernier caractère d'une séquence de `Byte`.

```cpp
virtual result do_unshift(
    StateType& _State,
    Byte* first2,
    Byte* last2,
    Byte*& next2) const;
```

### <a name="parameters"></a>Paramètres

*_State*<br/>
État de conversion conservé entre les appels à la fonction membre.

*first2*<br/>
Pointeur vers la première position dans la plage de destination.

*last2*<br/>
Pointeur vers la dernière position dans la plage de destination.

*next2*<br/>
Pointeur vers le premier élément non modifié dans la séquence de destination.

### <a name="return-value"></a>Valeur de retour

La fonction retourne :

- `codecvt_base::error` Si _ *état* représente un état non valide

- `codecvt_base::noconv` si la fonction n’exécute aucune conversion

- `codecvt_base::ok` Si la conversion réussit

- `codecvt_base::partial` Si la destination n’est pas assez grande pour que la conversion réussisse

### <a name="remarks"></a>Notes

La fonction membre virtuelle protégée tente de convertir l’élément source `CharType`(0) à une séquence de destination qu’elle stocke dans [ `first2`, `last2`), à l’exception de l’élément de fin `Byte`(0). Elle stocke toujours dans *next2* un pointeur vers le premier élément non modifié dans la séquence de destination.

_ *State* doit représenter l’état initial de la conversion au début d’une nouvelle séquence source. La fonction modifie sa valeur stockée selon les besoins pour refléter l’état actuel d’une conversion réussie. En règle générale, conversion de l’élément source `CharType`(0) conserve l’état actuel dans l’état de conversion initial.

### <a name="example"></a>Exemple

Consultez l’exemple relatif à [unshift](#unshift), qui appelle `do_unshift`.

## <a name="encoding"></a>  codecvt::encoding

Vérifie si l'encodage du flux `Byte` dépend d'un état. Elle vérifie également si le rapport entre les `Byte` utilisés et les `CharType` produits est constant, et, le cas échéant, détermine la valeur de ce rapport.

```cpp
int encoding() const throw();
```

### <a name="return-value"></a>Valeur de retour

Si la valeur de retour est positive, cette valeur est le nombre constant de `Byte` caractères requis pour produire le `CharType` caractère.

La fonction membre virtuelle protégée retourne :

- -1, si le codage de séquences de type `extern_type` dépend de l’état.

- 0, si le codage implique des séquences de longueur variable.

- *N*, si le codage implique uniquement des séquences de longueur *N.*

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

## <a name="extern_type"></a>  codecvt::extern_type

Type de caractère utilisé pour les représentations externes.

```cpp
typedef Byte extern_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du paramètre de modèle `Byte`.

## <a name="in"></a>  codecvt::in

Convertit la représentation externe d'une séquence de `Byte` en la représentation interne d'une séquence de `CharType`.

```cpp
result in(
    StateType& _State,
    const Byte* first1,
    const Byte* last1,
    const Byte*& next1,
    CharType* first2,
    CharType* last2,
    CharType*& next2,) const;
```

### <a name="parameters"></a>Paramètres

*_State*<br/>
État de conversion conservé entre les appels à la fonction membre.

*first1*<br/>
Pointeur vers le début de la séquence à convertir.

*last1*<br/>
Pointeur vers la fin de la séquence à convertir.

*next1*<br/>
Pointeur situé après la fin de la séquence convertie, vers le premier caractère non converti.

*first2*<br/>
Pointeur vers le début de la séquence convertie.

*last2*<br/>
Pointeur vers la fin de la séquence convertie.

*next2*<br/>
Pointeur vers le `CharType` qui vient après le dernier converti `Chartype` vers le premier caractère non modifié dans la séquence de destination.

### <a name="return-value"></a>Valeur de retour

Retour qui indique la réussite, la réussite partielle ou l’échec de l’opération. La fonction retourne :

- `codecvt_base::error` Si la séquence source est malade formée.

- `codecvt_base::noconv` si la fonction n’exécute aucune conversion.

- `codecvt_base::ok` Si la conversion réussit.

- `codecvt_base::partial` Si la source est insuffisante ou si la destination n’est pas assez grande pour que la conversion réussisse.

### <a name="remarks"></a>Notes

*_State* doit représenter l’état de conversion initial au début d’une nouvelle séquence source. La fonction modifie sa valeur stockée selon les besoins pour refléter l’état actuel d’une conversion réussie. Après une conversion partielle, *_State* doit être défini pour permettre la conversion de reprendre quand de nouveaux caractères arrivent.

La fonction membre retourne [do_in](#do_in)( `_State`, _ *First1,  last1,  next1, First2, _Llast2,  next2*).

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

## <a name="intern_type"></a>  codecvt::intern_type

Type de caractère utilisé pour les représentations internes.

```cpp
typedef CharType intern_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du paramètre de modèle `CharType`.

## <a name="length"></a>  codecvt::length

Détermine le nombre de `Byte` d'une séquence donnée de d'`Byte` externes n'ayant pas produit plus d'un nombre donné de d'`CharType` internes, et retourne ce nombre de `Byte`.

```cpp
int length(
    const StateType& _State,
    const Byte* first1,
    const Byte* last1,
    size_t _Len2) const;
```

### <a name="parameters"></a>Paramètres

*_State*<br/>
État de conversion conservé entre les appels à la fonction membre.

*first1*<br/>
Pointeur vers le début de la séquence externe.

*last1*<br/>
Pointeur vers la fin de la séquence externe.

*_Len2*<br/>
Nombre maximal d’objets Byte qui peuvent être retournés par la fonction membre.

### <a name="return-value"></a>Valeur de retour

Entier qui représente le nombre maximal de conversions, non supérieures à *_Len2*, défini par la séquence source externe sur [ `first1`, `last1`).

### <a name="remarks"></a>Notes

La fonction membre retourne [do_length](#do_length)( *_State,  first1*, `last1`, `_Len2`).

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

## <a name="max_length"></a>  codecvt::max_length

Retourne le nombre maximal de `Byte` externes nécessaires pour produire un `CharType` interne.

```cpp
int max_length() const throw();
```

### <a name="return-value"></a>Valeur de retour

Le nombre maximal de `Byte`s nécessaires pour produire un `CharType`.

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

## <a name="out"></a>  codecvt::out

Convertit une séquence de `CharType` internes en une séquence de `Byte` externes.

```cpp
result out(
    StateType& _State,
    const CharType* first1,
    const CharType* last1,
    const CharType*& next1,
    Byte* first2,
    Byte* last2,
    Byte*& next2) const;
```

### <a name="parameters"></a>Paramètres

*_State*<br/>
État de conversion conservé entre les appels à la fonction membre.

*first1*<br/>
Pointeur vers le début de la séquence à convertir.

*last1*<br/>
Pointeur vers la fin de la séquence à convertir.

*next1*<br/>
Référence à un pointeur vers le premier non converti `CharType` après le dernier `CharType` converti.

*first2*<br/>
Pointeur vers le début de la séquence convertie.

*last2*<br/>
Pointeur vers la fin de la séquence convertie.

*next2*<br/>
Référence à un pointeur vers le premier non converti `Byte` converti après le dernier `Byte`.

### <a name="return-value"></a>Valeur de retour

La fonction membre retourne [do_out](#do_out)( `_State`, `first1`, `last1`, `next1`, `first2`, `last2`, `next2`).

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

## <a name="state_type"></a>  codecvt::state_type

Type de caractère utilisé pour représenter les états intermédiaires lors de conversions entre des représentations internes et externes.

```cpp
typedef StateType state_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du paramètre de modèle `StateType`.

## <a name="unshift"></a>  codecvt::unshift

Fournit le `Byte`nécessaires dans une conversion avec dépendance d’état afin d’ajouter le dernier caractère dans une séquence de `Byte`s.

```cpp
result unshift(
    StateType& _State,
    Byte* first2,
    Byte* last2,
    Byte*& next2) const;
```

### <a name="parameters"></a>Paramètres

*_State*<br/>
État de conversion conservé entre les appels à la fonction membre.

*first2*<br/>
Pointeur vers la première position dans la plage de destination.

*last2*<br/>
Pointeur vers la dernière position dans la plage de destination.

*next2*<br/>
Pointeur vers le premier élément non modifié dans la séquence de destination.

### <a name="return-value"></a>Valeur de retour

La fonction retourne :

- `codecvt_base::error` Si l’état représente un état non valide.

- `codecvt_base::noconv` si la fonction n’exécute aucune conversion.

- `codecvt_base::ok` Si la conversion réussit.

- `codecvt_base::partial` Si la destination n’est pas assez grande pour que la conversion réussisse.

### <a name="remarks"></a>Notes

La fonction membre virtuelle protégée tente de convertir l’élément source `CharType`(0) à une séquence de destination qu’elle stocke dans [ `first2`, `last2`), à l’exception de l’élément de fin `Byte`(0). Elle stocke toujours dans *next2* un pointeur vers le premier élément non modifié dans la séquence de destination.

*_State* doit représenter l’état de conversion initial au début d’une nouvelle séquence source. La fonction modifie sa valeur stockée selon les besoins pour refléter l’état actuel d’une conversion réussie. En règle générale, conversion de l’élément source `CharType`(0) conserve l’état actuel dans l’état de conversion initial.

La fonction membre retourne [do_unshift](#do_unshift)( `_State`, `first2`, `last2`, `next2` ).

## <a name="see-also"></a>Voir aussi

[\<locale>](../standard-library/locale.md)<br/>
[Pages de codes](../c-runtime-library/code-pages.md)<br/>
[Chaînes relatives aux noms des paramètres régionaux, aux langues et au pays/à la région](../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
