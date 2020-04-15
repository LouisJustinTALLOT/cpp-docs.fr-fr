---
title: ctype, classe
ms.date: 11/04/2016
f1_keywords:
- xlocale/std::ctype
- xlocale/std::ctype::char_type
- xlocale/std::ctype::do_is
- xlocale/std::ctype::do_narrow
- xlocale/std::ctype::do_scan_is
- xlocale/std::ctype::do_scan_not
- xlocale/std::ctype::do_tolower
- xlocale/std::ctype::do_toupper
- xlocale/std::ctype::do_widen
- xlocale/std::ctype::is
- xlocale/std::ctype::narrow
- xlocale/std::ctype::scan_is
- xlocale/std::ctype::scan_not
- xlocale/std::ctype::tolower
- xlocale/std::ctype::toupper
- xlocale/std::ctype::widen
helpviewer_keywords:
- std::ctype [C++]
- std::ctype [C++], char_type
- std::ctype [C++], do_is
- std::ctype [C++], do_narrow
- std::ctype [C++], do_scan_is
- std::ctype [C++], do_scan_not
- std::ctype [C++], do_tolower
- std::ctype [C++], do_toupper
- std::ctype [C++], do_widen
- std::ctype [C++], is
- std::ctype [C++], narrow
- std::ctype [C++], scan_is
- std::ctype [C++], scan_not
- std::ctype [C++], tolower
- std::ctype [C++], toupper
- std::ctype [C++], widen
ms.assetid: 3627154c-49d9-47b5-b28f-5bbedee38e3b
ms.openlocfilehash: dae6f62a0eda9263986a77b82754596d17be94e5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373169"
---
# <a name="ctype-class"></a>ctype, classe

Classe fournissant une facette utilisée pour la classification des caractères et la conversion entre majuscules et minuscules et entre le jeu de caractères natif et celui utilisé par les paramètres régionaux.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType>
class ctype : public ctype_base;
```

### <a name="parameters"></a>Paramètres

*CharType CharType*\
Type utilisé dans le cadre d'un programme pour encoder des caractères.

## <a name="remarks"></a>Notes

Comme avec n'importe quelle facette de paramètres régionaux, l'ID d'objet statique possède une valeur stockée initiale de zéro. La première tentative d’accès à sa valeur stockée entraîne le stockage d’une valeur positive unique dans `id`. Les critères de classification sont fournis par un type de masque de bits imbriqué dans la classe de base ctype_base.

La Bibliothèque standard de la CMD définit deux spécialisations explicites de ce modèle de classe :

- `ctype<char>`, une spécialisation explicite dont les différences sont décrites séparément. Pour plus d’informations, voir [ctype&lt;char&gt; Class](../standard-library/ctype-char-class.md).

- `ctype<wchar_t>`, qui traite les éléments comme des personnages larges.

Autres spécialisations du `ctype<CharType>`modèle de classe :

- Convertir un *ch* de valeur de type *CharType* `(char)ch`à une valeur de type **char** avec l’expression .

- Convertir un *byte* de valeur de type **char** à une valeur de type *CharType* avec l’expression `CharType(byte)`.

Toutes les autres opérations sont effectuées sur des valeurs `ctype<char>` **d’omble chevalier** de la même manière que pour la spécialisation explicite.

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[ctype](#ctype)|Constructeur des objets de classe `ctype` qui servent de facettes de paramètres régionaux pour les caractères.|

### <a name="typedefs"></a>Typedefs

|Nom de type|Description|
|-|-|
|[char_type](#char_type)|Type qui décrit un caractère utilisé par les paramètres régionaux.|

### <a name="member-functions"></a>Fonctions Membre

|Fonction membre|Description|
|-|-|
|[do_is](#do_is)|Fonction virtuelle appelée pour vérifier si un caractère unique possède un attribut particulier, ou pour classer les attributs de chaque caractère dans une plage et les stocker dans un tableau.|
|[do_narrow](#do_narrow)|Une fonction virtuelle appelée à `CharType` convertir un personnage de type utilisé par un lieu au caractère correspondant de l’omble de type dans l’ensemble de caractères indigènes. **char**|
|[do_scan_is](#do_scan_is)|Fonction virtuelle appelée pour rechercher le premier caractère d'une plage qui correspond au masque spécifié.|
|[do_scan_not](#do_scan_not)|Fonction virtuelle appelée pour rechercher le premier caractère d'une plage qui ne correspond pas au masque spécifié.|
|[do_tolower](#do_tolower)|Fonction virtuelle appelée pour convertir un caractère ou une plage de caractères en minuscules.|
|[do_toupper](#do_toupper)|Fonction virtuelle appelée pour convertir un caractère ou une plage de caractères en majuscules.|
|[do_widen](#do_widen)|Une fonction virtuelle appelée à convertir un personnage de type **char** dans `CharType` le personnage natif réglé sur le caractère correspondant du type utilisé par un lieu.|
|[Est](#is)|Vérifie si un caractère possède un attribut spécifique, ou classe les attributs de chaque caractère dans une plage et les stocke dans un tableau.|
|[narrow](#narrow)|Convertit un caractère de type `CharType` utilisé par les paramètres régionaux en caractère correspondant de type char dans le jeu de caractères natif.|
|[scan_is](#scan_is)|Localise le premier caractère d'une plage qui correspond au masque spécifié.|
|[scan_not](#scan_not)|Localise le premier caractère d'une plage qui ne correspond pas au masque spécifié.|
|[Tolower](#tolower)|Convertit un caractère ou une plage de caractères en minuscules.|
|[Toupper](#toupper)|Convertit un caractère ou une plage de caractères en majuscules.|
|[widen](#widen)|Convertit un caractère de type **char** dans le personnage `CharType` natif réglé au caractère correspondant du type utilisé par un lieu.|

## <a name="requirements"></a>Spécifications

**En-tête :** \<locale>

**Espace de noms :** std

## <a name="ctypechar_type"></a><a name="char_type"></a>ctype::char_type

Type qui décrit un caractère utilisé par les paramètres régionaux.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du paramètre de modèle *CharType*.

### <a name="example"></a>Exemple

Consultez la fonction membre [widen](#widen) pour obtenir un exemple d’utilisation de `char_type` comme valeur de retour.

## <a name="ctypectype"></a><a name="ctype"></a>ctype::ctype

Constructeur des objets de classe ctype qui servent de facettes de paramètres régionaux pour les caractères.

```cpp
explicit ctype(size_t _Refs = 0);
```

### <a name="parameters"></a>Paramètres

*_Refs*\
Valeur entière utilisée pour spécifier le type de gestion de mémoire pour l’objet.

### <a name="remarks"></a>Notes

Les valeurs possibles pour le *_Refs* paramètre et leur signification sont les suivante :

- 0 : la durée de vie de l’objet est gérée par les paramètres régionaux qui le contiennent.

- 1 : la durée de vie de l’objet doit être gérée manuellement.

- \>1: Ces valeurs ne sont pas définies.

Aucun exemple direct n’est possible, car le destructeur est protégé.

Le constructeur initialise `locale::facet` son objet de base avec `_Refs` **local::**[facette](../standard-library/locale-class.md#facet_class)( ).

## <a name="ctypedo_is"></a><a name="do_is"></a>ctype::do est

Fonction virtuelle appelée pour vérifier si un caractère unique possède un attribut particulier, ou pour classer les attributs de chaque caractère dans une plage et les stocker dans un tableau.

```cpp
virtual bool do_is(
    mask maskVal,
    CharType ch) const;

virtual const CharType *do_is(
    const CharType* first,
    const CharType* last,
    mask* dest) const;
```

### <a name="parameters"></a>Paramètres

*masqueVal*\
Valeur de masque pour laquelle le caractère doit être vérifié.

*Ch*\
Caractère dont les attributs doivent être vérifiés.

*Première*\
Pointeur vers le premier caractère de la plage dont les attributs doivent être classés.

*Dernière*\
Pointeur vers le caractère juste après le dernier caractère de la plage dont les attributs doivent être classés.

*Dest*\
Pointeur vers le début du tableau dans lequel les valeurs de masque qui caractérisent les attributs de chaque caractère doivent être stockées.

### <a name="return-value"></a>Valeur de retour

La première fonction membre retourne une valeur booléenne qui est **true** si le caractère vérifié a l’attribut décrit par la valeur de masque ; **false** s’il n’a pas l’attribut.

La seconde fonction membre retourne un tableau contenant les valeurs de masque qui caractérisent les attributs de chaque caractère de la plage.

### <a name="remarks"></a>Notes

Les valeurs de masque qui classent les attributs des caractères sont fournies par la classe [ctype_base](../standard-library/ctype-base-class.md) de laquelle dérive ctype. La première fonction membre peut accepter pour son premier paramètre des expressions appelées masques de bits et formées à partir de la combinaison de valeurs de masque par les opérateurs logiques au niveau du bit (&#124; , & , ^ , ~).

### <a name="example"></a>Exemple

Consultez l’exemple relatif à [is](#is), qui appelle `do_is`.

## <a name="ctypedo_narrow"></a><a name="do_narrow"></a>ctype::do-étroite

Une fonction virtuelle appelée à `CharType` convertir un personnage de type utilisé par un lieu au caractère correspondant de l’omble de type dans l’ensemble de caractères indigènes. **char**

```cpp
virtual char do_narrow(
    CharType ch,
    char default = '\0') const;

virtual const CharType* do_narrow(
    const CharType* first,
    const CharType* last,
    char default,
    char* dest) const;
```

### <a name="parameters"></a>Paramètres

*Ch*\
Caractère de type `Chartype` utilisé par les paramètres régionaux à convertir.

*Par défaut*\
La valeur par défaut à attribuer par `CharType` la fonction membre à des caractères de type qui n’ont pas de caractères homologues de type **char**.

*Première*\
Pointeur vers le premier caractère de la plage de caractères à convertir.

*Dernière*\
Pointeur vers le caractère juste après le dernier caractère de la plage de caractères à convertir.

*Dest*\
Un pointeur const au premier caractère de **l’omble** de type dans la gamme de destination qui stocke la gamme convertie de caractères.

### <a name="return-value"></a>Valeur de retour

La première fonction de membre protégée renvoie le caractère indigène `CharType` de l’omble de type qui correspond au caractère paramètre de type ou *par défaut* si aucune contrepartie n’est définie.

La deuxième fonction membre protégée retourne un pointeur vers la plage de destination de caractères natifs convertis à partir de caractères de type `CharType`.

### <a name="remarks"></a>Notes

La deuxième fonction de `dest`modèle `I`protégé `do_narrow`de `first` `I`membre `default`stocke `I` dans [ ] `last`  - la valeur ( [ ], ), pour dans l’intervalle [0, `first`).

### <a name="example"></a>Exemple

Consultez l’exemple relatif à [narrow](#narrow), qui appelle `do_narrow`.

## <a name="ctypedo_scan_is"></a><a name="do_scan_is"></a>ctype::do-scan

Fonction virtuelle appelée pour rechercher le premier caractère d'une plage qui correspond au masque spécifié.

```cpp
virtual const CharType *do_scan_is(
    mask maskVal,
    const CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Paramètres

*masqueVal*\
Valeur de masque qui doit correspondre à un caractère.

*Première*\
Pointeur vers le premier caractère de la plage à analyser.

*Dernière*\
Pointeur vers le caractère juste après le dernier caractère de la plage à analyser.

### <a name="return-value"></a>Valeur de retour

Pointeur vers le premier caractère d’une plage qui correspond à un masque spécifié. Si cette valeur n’existe pas, la fonction renvoie *en dernier*.

### <a name="remarks"></a>Notes

La fonction de membre `ptr` protégée renvoie `first` `last`le plus petit pointeur de la gamme [, ) pour lequel [do_is](#do_is)( `maskVal`, \* `ptr`) est vrai.

### <a name="example"></a>Exemple

Consultez l’exemple relatif à [scan_is](#scan_is), qui appelle `do_scan_is`.

## <a name="ctypedo_scan_not"></a><a name="do_scan_not"></a>ctype::do-scan

Fonction virtuelle appelée pour rechercher le premier caractère d'une plage qui ne correspond pas au masque spécifié.

```cpp
virtual const CharType *do_scan_not(
    mask maskVal,
    const CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Paramètres

*masqueVal*\
Valeur de masque qui ne doit pas correspondre à un caractère.

*Première*\
Pointeur vers le premier caractère de la plage à analyser.

*Dernière*\
Pointeur vers le caractère juste après le dernier caractère de la plage à analyser.

### <a name="return-value"></a>Valeur de retour

Pointeur vers le premier caractère d’une plage qui ne correspond pas à un masque spécifié. Si cette valeur n’existe pas, la fonction renvoie *en dernier*.

### <a name="remarks"></a>Notes

La fonction de membre `ptr` protégée renvoie `first` `last`le plus petit pointeur \* `ptr`de la plage [, ) pour lequel [do_is](#do_is)( `maskVal`, ) est faux.

### <a name="example"></a>Exemple

Consultez l’exemple relatif à [scan_not](#scan_not), qui appelle `do_scan_not`.

## <a name="ctypedo_tolower"></a><a name="do_tolower"></a>ctype::do-tolower

Fonction virtuelle appelée pour convertir un caractère ou une plage de caractères en minuscules.

```cpp
virtual CharType do_tolower(CharType ch) const;

virtual const CharType *do_tolower(
    CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Paramètres

*Ch*\
Caractère à convertir en minuscule.

*Première*\
Pointeur vers le premier caractère de la plage de caractères dont la casse doit être convertie.

*Dernière*\
Pointeur vers le caractère juste après le dernier caractère de la plage de caractères dont la casse doit être convertie.

### <a name="return-value"></a>Valeur de retour

La première fonction protégée de membre renvoie la forme inférieure du *paramètre ch.* S’il n’existe pas de forme inférieure, elle retourne *ch*. La deuxième fonction protégée des membres renvoie *en dernier*.

### <a name="remarks"></a>Notes

La deuxième fonction de modèle `first` de `I`membre `I` protégée remplace chaque élément `last`  -  `first`[], car dans l’intervalle [0, ), par `do_tolower`( `first` [ `I`]).

### <a name="example"></a>Exemple

Consultez l’exemple relatif à [tolower](#tolower), qui appelle `do_tolower`.

## <a name="ctypedo_toupper"></a><a name="do_toupper"></a>ctype::do-toupper

Fonction virtuelle appelée pour convertir un caractère ou une plage de caractères en majuscules.

```cpp
virtual CharType do_toupper(CharType ch) const;

virtual const CharType *do_toupper(
    CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Paramètres

*Ch*\
Caractère à convertir en majuscule.

*Première*\
Pointeur vers le premier caractère de la plage de caractères dont la casse doit être convertie.

*Dernière*\
Pointeur vers le caractère juste après le dernier caractère de la plage de caractères dont la casse doit être convertie.

### <a name="return-value"></a>Valeur de retour

La première fonction protégée de membre renvoie la forme supérieure du *paramètre ch.* Si aucune forme de majuscule n’existe, elle retourne *ch*. La deuxième fonction protégée des membres renvoie *en dernier*.

### <a name="remarks"></a>Notes

La deuxième fonction de modèle `first` de `I`membre `I` protégée remplace chaque élément `last`  -  `first`[], car dans l’intervalle [0, ), par `do_toupper`( `first` [ `I`]).

### <a name="example"></a>Exemple

Consultez l’exemple relatif à [toupper](#toupper), qui appelle `do_toupper`.

## <a name="ctypedo_widen"></a><a name="do_widen"></a>ctype::do-widen

Une fonction virtuelle appelée à convertir un personnage de type **char** dans `CharType` le personnage natif réglé sur le caractère correspondant du type utilisé par un lieu.

```cpp
virtual CharType do_widen(char byte) const;

virtual const char *do_widen(
    const char* first,
    const char* last,
    CharType* dest) const;
```

### <a name="parameters"></a>Paramètres

*Octet*\
Le caractère de **l’omble** de type dans le personnage natif mis à convertir.

*Première*\
Pointeur vers le premier caractère de la plage de caractères à convertir.

*Dernière*\
Pointeur vers le caractère juste après le dernier caractère de la plage de caractères à convertir.

*Dest*\
Pointeur vers le premier caractère de type `CharType` dans la plage de destination qui stocke la plage de caractères convertis.

### <a name="return-value"></a>Valeur de retour

La première fonction de membre `CharType` protégée renvoie le caractère de type qui correspond au caractère paramètre de l’omble **de**type indigène.

La deuxième fonction protégée des membres renvoie un `CharType` pointeur à la gamme de destination des caractères de type utilisés par un lieu converti à partir de caractères indigènes de type **char**.

### <a name="remarks"></a>Notes

La deuxième fonction membre de modèle protégée stocke dans `dest`[ `I`] la valeur `do_widen`( `first`[ `I`]) pour `I` dans l’intervalle [0, `last` - `first`).

### <a name="example"></a>Exemple

Consultez l’exemple relatif à [widen](#widen), qui appelle `do_widen`.

## <a name="ctypeis"></a><a name="is"></a>ctype::est

Vérifie si un seul caractère a un attribut spécifique, ou classe les attributs de chaque caractère dans une plage et les stocke dans un tableau.

```cpp
bool is(mask maskVal, CharType ch) const;

const CharType *is(
    const CharType* first,
    const CharType* last,
    mask* dest) const;
```

### <a name="parameters"></a>Paramètres

*masqueVal*\
Valeur de masque pour laquelle le caractère doit être vérifié.

*Ch*\
Caractère dont les attributs doivent être vérifiés.

*Première*\
Pointeur vers le premier caractère de la plage dont les attributs doivent être classés.

*Dernière*\
Pointeur vers le caractère juste après le dernier caractère de la plage dont les attributs doivent être classés.

*Dest*\
Pointeur vers le début du tableau dans lequel les valeurs de masque qui caractérisent les attributs de chaque caractère doivent être stockées.

### <a name="return-value"></a>Valeur de retour

La fonction du premier membre revient **vrai** si le personnage testé a l’attribut décrit par la valeur du masque; **faux** s’il n’a pas l’attribut.

La deuxième fonction membre retourne un pointeur vers le dernier caractère de la plage dont les attributs doivent être classés.

### <a name="remarks"></a>Notes

Les valeurs de masque qui classent les attributs des caractères sont fournies par la classe [ctype_base](../standard-library/ctype-base-class.md) de laquelle dérive ctype. La première fonction membre peut accepter pour son premier paramètre des expressions appelées masques de bits et formées à partir de la combinaison de valeurs de masque par les opérateurs logiques au niveau du bit (&#124; , & , ^ , ~).

### <a name="example"></a>Exemple

```cpp
// ctype_is.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main() {
   locale loc1 ( "German_Germany" ), loc2 ( "English_Australia" );

   if (use_facet<ctype<char> > ( loc1 ).is( ctype_base::alpha, 'a' ))
      cout << "The character 'a' in locale loc1 is alphabetic."
           << endl;
   else
      cout << "The character 'a' in locale loc1 is not alphabetic."
           << endl;

   if (use_facet<ctype<char> > ( loc2 ).is( ctype_base::alpha, '!' ))
      cout << "The character '!' in locale loc2 is alphabetic."
           << endl;
   else
      cout << "The character '!' in locale loc2 is not alphabetic."
           << endl;

   char *string = "Hello, my name is John!";
   ctype<char>::mask maskarray[30];
   use_facet<ctype<char> > ( loc2 ).is(
      string, string + strlen(string), maskarray );
   for (unsigned int i = 0; i < strlen(string); i++) {
      cout << string[i] << ": "
           << (maskarray[i] & ctype_base::alpha  "alpha"
                                                : "not alpha")
           << endl;;
   };
}
```

## <a name="ctypenarrow"></a><a name="narrow"></a>ctype::étroit

Convertit les `CharType` caractères de type utilisés par un lieu aux caractères correspondants de l’omble **de** type dans l’ensemble de caractères indigènes.

```cpp
char narrow(CharType ch, char default = '\0') const;

const CharType* narrow(
    const CharType* first,
    const CharType* last,
    char default,
    char* dest) const;
```

### <a name="parameters"></a>Paramètres

*Ch*\
Caractère de type `Chartype` utilisé par les paramètres régionaux à convertir.

*Par défaut*\
La valeur par défaut à attribuer par `CharType` la fonction membre à des caractères de type qui n’ont pas de caractères homologues de type **char**.

*Première*\
Pointeur vers le premier caractère de la plage de caractères à convertir.

*Dernière*\
Pointeur vers le caractère juste après le dernier caractère de la plage de caractères à convertir.

*Dest*\
Un pointeur const au premier caractère de **l’omble** de type dans la gamme de destination qui stocke la gamme convertie de caractères.

### <a name="return-value"></a>Valeur de retour

La fonction de premier membre renvoie le caractère natif de `CharType default` l’omble de type qui correspond au caractère paramètre du type s’il n’est pas de la contrepartie est défini. **char**

La deuxième fonction membre retourne un pointeur vers la plage de destination de caractères natifs convertis à partir de caractères de type `CharType`.

### <a name="remarks"></a>Notes

La première fonction [do_narrow](#do_narrow)de membre`ch`renvoie do_narrow ( , `default`). La fonction de deuxième membre`first`renvoie `default` `dest` [do_narrow](#do_narrow) ( , `last`, . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . Seuls les caractères sources de base ont la garantie d’avoir une image unique inverse `CharType` sous `narrow`. Pour ces caractères sources de base, l’invariant suivant contient : `narrow` ( [élargir](#widen) ( **c** ), 0) == **c**.

### <a name="example"></a>Exemple

```cpp
// ctype_narrow.cpp
// compile with: /EHsc /W3
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc1 ( "english" );
   wchar_t *str1 = L"\x0392fhello everyone";
   char str2 [16];
   bool result1 = (use_facet<ctype<wchar_t> > ( loc1 ).narrow
      ( str1, str1 + wcslen(str1), 'X', &str2[0] ) != 0);  // C4996
   str2[wcslen(str1)] = '\0';
   wcout << str1 << endl;
   cout << &str2[0] << endl;
}
```

```Output
Xhello everyone
```

## <a name="ctypescan_is"></a><a name="scan_is"></a>ctype::scan_is

Localise le premier caractère d'une plage qui correspond au masque spécifié.

```cpp
const CharType *scan_is(
    mask maskVal,
    const CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Paramètres

*masqueVal*\
Valeur de masque qui doit correspondre à un caractère.

*Première*\
Pointeur vers le premier caractère de la plage à analyser.

*Dernière*\
Pointeur vers le caractère juste après le dernier caractère de la plage à analyser.

### <a name="return-value"></a>Valeur de retour

Pointeur vers le premier caractère d’une plage qui correspond à un masque spécifié. Si cette valeur n’existe pas, la fonction renvoie *en dernier*.

### <a name="remarks"></a>Notes

La fonction [do_scan_is](#do_scan_is)membre retourne`maskVal`do_scan_is `first` `last`( , , ).

### <a name="example"></a>Exemple

```cpp
// ctype_scan_is.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc1 ( "German_Germany" );

   char *string = "Hello, my name is John!";

   const char* i = use_facet<ctype<char> > ( loc1 ).scan_is
      ( ctype_base::punct, string, string + strlen(string) );
   cout << "The first punctuation is \"" << *i << "\" at position: "
      << i - string << endl;
}
```

```Output
The first punctuation is "," at position: 5
```

## <a name="ctypescan_not"></a><a name="scan_not"></a>ctype::scan_not

Localise le premier caractère d'une plage qui ne correspond pas au masque spécifié.

```cpp
const CharType *scan_not(
    mask maskVal,
    const CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Paramètres

*masqueVal*\
Valeur de masque qui ne doit pas correspondre à un caractère.

*Première*\
Pointeur vers le premier caractère de la plage à analyser.

*Dernière*\
Pointeur vers le caractère juste après le dernier caractère de la plage à analyser.

### <a name="return-value"></a>Valeur de retour

Pointeur vers le premier caractère d’une plage qui ne correspond pas à un masque spécifié. Si cette valeur n’existe pas, la fonction renvoie *en dernier*.

### <a name="remarks"></a>Notes

La fonction [do_scan_not](#do_scan_not)membre retourne do_scan_not`maskVal` `first`( `last`, , ).

### <a name="example"></a>Exemple

```cpp
// ctype_scan_not.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc1 ( "German_Germany" );

   char *string = "Hello, my name is John!";

   const char* i = use_facet<ctype<char> > ( loc1 ).scan_not
      ( ctype_base::alpha, string, string + strlen(string) );
   cout << "First nonalpha character is \"" << *i << "\" at position: "
      << i - string << endl;
}
```

```Output
First nonalpha character is "," at position: 5
```

## <a name="ctypetolower"></a><a name="tolower"></a>ctype::tolower

Convertit un caractère ou une plage de caractères en minuscules.

```cpp
CharType tolower(CharType ch) const;

const CharType *tolower(CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Paramètres

*Ch*\
Caractère à convertir en minuscule.

*Première*\
Pointeur vers le premier caractère de la plage de caractères dont la casse doit être convertie.

*Dernière*\
Pointeur vers le caractère juste après le dernier caractère de la plage de caractères dont la casse doit être convertie.

### <a name="return-value"></a>Valeur de retour

La fonction du premier membre renvoie la forme inférieure du *paramètre ch*. S’il n’existe pas de forme inférieure, elle retourne *ch*.

La deuxième fonction de membre renvoie *en dernier*.

### <a name="remarks"></a>Notes

La première fonction [do_tolower](#do_tolower)de membre`ch`renvoie do_tolower ( ). La fonction du [do_tolower](#do_tolower)deuxième membre`first`revient do_tolower ( , `last`).

### <a name="example"></a>Exemple

```cpp
// ctype_tolower.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc1 ( "German_Germany" );

   char string[] = "HELLO, MY NAME IS JOHN";

   use_facet<ctype<char> > ( loc1 ).tolower
      ( string, string + strlen(string) );
   cout << "The lowercase string is: " << string << endl;
}
```

```Output
The lowercase string is: hello, my name is john
```

## <a name="ctypetoupper"></a><a name="toupper"></a>ctype::toupper

Convertit un caractère ou une plage de caractères en majuscules.

```cpp
CharType toupper(CharType ch) const;
const CharType *toupper(CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Paramètres

*Ch*\
Caractère à convertir en majuscule.

*Première*\
Pointeur vers le premier caractère de la plage de caractères dont la casse doit être convertie.

*Dernière*\
Pointeur vers le caractère juste après le dernier caractère de la plage de caractères dont la casse doit être convertie.

### <a name="return-value"></a>Valeur de retour

La fonction du premier membre renvoie la forme supérieure du *paramètre ch*. Si aucune forme de majuscule n’existe, elle retourne *ch*.

La deuxième fonction de membre renvoie *en dernier*.

### <a name="remarks"></a>Notes

La première fonction [do_toupper](#do_toupper)de membre`ch`renvoie do_toupper ( ). La fonction du deuxième membre `first` `last`revient [do_toupper](#do_toupper)( , ).

### <a name="example"></a>Exemple

```cpp
// ctype_toupper.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc1 ( "German_Germany" );

   char string[] = "Hello, my name is John";

   use_facet<ctype<char> > ( loc1 ).toupper
      ( string, string + strlen(string) );
   cout << "The uppercase string is: " << string << endl;
}
```

```Output
The uppercase string is: HELLO, MY NAME IS JOHN
```

## <a name="ctypewiden"></a><a name="widen"></a>ctype::widen

Convertit un caractère de type **char** dans le personnage `CharType` natif réglé au caractère correspondant du type utilisé par un lieu.

```cpp
CharType widen(char byte) const;
const char *widen(const char* first, const char* last, CharType* dest) const;
```

### <a name="parameters"></a>Paramètres

*Octet*\
Caractère de type char du jeu de caractères natifs à convertir.

*Première*\
Pointeur vers le premier caractère de la plage de caractères à convertir.

*Dernière*\
Pointeur vers le caractère juste après le dernier caractère de la plage de caractères à convertir.

*Dest*\
Pointeur vers le premier caractère de type `CharType` dans la plage de destination qui stocke la plage de caractères convertis.

### <a name="return-value"></a>Valeur de retour

La première fonction de membre `CharType` renvoie le caractère de type qui correspond au caractère paramètre de l’omble **de**type natif.

La deuxième fonction de membre renvoie un `CharType` pointeur à la gamme de destination des caractères de type utilisé par un lieu converti à partir de caractères indigènes de type **char**.

### <a name="remarks"></a>Notes

La première fonction [do_widen](#do_widen)de membre`byte`renvoie do_widen ( ). La fonction de deuxième membre`first`renvoie `dest` [do_widen](#do_widen)( , `last`, ).

### <a name="example"></a>Exemple

```cpp
// ctype_widen.cpp
// compile with: /EHsc /W3
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc1 ( "English" );
   char *str1 = "Hello everyone!";
   wchar_t str2 [16];
   bool result1 = (use_facet<ctype<wchar_t> > ( loc1 ).widen
      ( str1, str1 + strlen(str1), &str2[0] ) != 0);  // C4996
   str2[strlen(str1)] = '\0';
   cout << str1 << endl;
   wcout << &str2[0] << endl;

   ctype<wchar_t>::char_type charT;
   charT = use_facet<ctype<char> > ( loc1 ).widen( 'a' );
}
```

```Output
Hello everyone!
Hello everyone!
```

## <a name="see-also"></a>Voir aussi

[\<local>](../standard-library/locale.md)\
[Sécurité des fils dans la bibliothèque standard de CMD](../standard-library/thread-safety-in-the-cpp-standard-library.md)
