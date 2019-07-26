---
title: collate, classe
ms.date: 11/04/2016
f1_keywords:
- locale/std::collate
- locale/std::collate::char_type
- locale/std::collate::string_type
- locale/std::collate::compare
- locale/std::collate::do_compare
- locale/std::collate::do_hash
- locale/std::collate::do_transform
- locale/std::collate::hash
- locale/std::collate::transform
helpviewer_keywords:
- std::collate [C++]
- std::collate [C++], char_type
- std::collate [C++], string_type
- std::collate [C++], compare
- std::collate [C++], do_compare
- std::collate [C++], do_hash
- std::collate [C++], do_transform
- std::collate [C++], hash
- std::collate [C++], transform
ms.assetid: 92168798-9628-4a2e-be6e-fa62dcd4d6a6
ms.openlocfilehash: c506a6a2e1e2c0610f8a6129d2bfb42f762e998a
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458600"
---
# <a name="collate-class"></a>collate, classe

Classe de modèle qui décrit un objet pouvant servir de facette de paramètres régionaux pour contrôler le tri et le regroupement des caractères d'une chaîne, pour leur comparaison et pour le hachage des chaînes.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType>
class collate : public locale::facet;
```

### <a name="parameters"></a>Paramètres

*CharType*\
Type utilisé dans le cadre d'un programme pour encoder des caractères.

## <a name="remarks"></a>Notes

Comme avec n'importe quelle facette de paramètres régionaux, l'ID d'objet statique possède une valeur stockée initiale de zéro. La première tentative d’accès à sa valeur stockée entraîne le stockage d’une valeur positive unique dans `id`. Dans certaines langues, plusieurs caractères peuvent être regroupés et traités comme un seul caractère, et dans d'autres, un caractère peut être traité comme un ensemble de deux caractères. Les services de classement fournis par la classe collate permettent de gérer ces cas.

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[collate](#collate)|Constructeur des objets de la classe `collate` qui sert de facette de paramètres régionaux pour la gestion des conventions de tri de chaînes.|

### <a name="typedefs"></a>Typedef

|Nom de type|Description|
|-|-|
|[char_type](#char_type)|Type qui décrit un caractère de type `CharType`.|
|[string_type](#string_type)|Type qui décrit une chaîne de type `basic_string` qui contient des caractères de type `CharType`.|

### <a name="member-functions"></a>Fonctions membres

|Fonction membre|Description|
|-|-|
|[compare](#compare)|Compare deux séquences de caractères selon leurs règles de facette afin de vérifier leur égalité ou leur inégalité.|
|[do_compare](#do_compare)|Fonction virtuelle appelée pour comparer deux séquences de caractères selon leurs règles de facette afin de vérifier leur égalité ou leur inégalité.|
|[do_hash](#do_hash)|Fonction virtuelle appelée pour déterminer la valeur de hachage des séquences en fonction de leurs règles de facette.|
|[do_transform](#do_transform)|Fonction virtuelle appelée pour convertir une séquence de caractères de paramètres régionaux en une chaîne pouvant être utilisée dans des comparaisons lexicographiques avec d'autres séquences de caractères également converties depuis les mêmes paramètres régionaux.|
|[hash](#hash)|Détermine la valeur de hachage d'une séquence en fonction de ses règles de facette.|
|[transform](#transform)|Convertit une séquence de caractères de paramètres régionaux en une chaîne qui peut être utilisée dans des comparaisons lexicographiques avec d'autres séquences de caractères, elles aussi converties depuis les mêmes paramètres régionaux.|

## <a name="requirements"></a>Configuration requise

**En-tête :** \<locale>

**Espace de noms :** std

## <a name="char_type"></a>  collate::char_type

Type qui décrit un caractère de type `CharType`.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du paramètre de modèle `CharType`.

## <a name="collate"></a>  collate::collate

Constructeur des objets de la classe collate qui sert de facette de paramètres régionaux pour la gestion des conventions de tri de chaînes.

```cpp
public:
    explicit collate(
    size_t _Refs = 0);

protected:
    collate(
const char* _Locname,
    size_t _Refs = 0);
```

### <a name="parameters"></a>Paramètres

*_Refs*\
Valeur entière utilisée pour spécifier le type de gestion de mémoire pour l’objet.

*_Locname*\
Nom des paramètres régionaux.

### <a name="remarks"></a>Notes

Les valeurs possibles pour le paramètre *_Refs* et leur signification sont les suivantes:

- 0 : La durée de vie de l’objet est gérée par les paramètres régionaux qui le contiennent.

- 1 : La durée de vie de l’objet doit être gérée manuellement.

- \>1: Ces valeurs ne sont pas définies.

Le constructeur initialise son objet de base avec **locale::** [facette](../standard-library/locale-class.md#facet_class)(`_Refs`).

## <a name="compare"></a>  collate::compare

Compare deux séquences de caractères selon leurs règles de facette afin de vérifier leur égalité ou leur inégalité.

```cpp
int compare(const CharType* first1,
    const CharType* last1,
    const CharType* first2,
    const CharType* last2) const;
```

### <a name="parameters"></a>Paramètres

*First1*\
Pointeur vers le premier élément de la première séquence à comparer.

*last1*\
Pointeur vers le dernier élément de la première séquence à comparer.

*First2*\
Pointeur vers le premier élément de la deuxième séquence à comparer.

*last2*\
Pointeur vers le dernier élément de la deuxième séquence à comparer.

### <a name="return-value"></a>Valeur de retour

La fonction membre retourne :

- -1 si la première séquence est inférieure à la deuxième séquence.

- +1 si la deuxième séquence est inférieure à la première séquence.

- 0 si les séquences sont équivalentes.

### <a name="remarks"></a>Notes

La première séquence est inférieure si elle a le plus petit élément dans la première paire inégale des séquences ou si aucune paire inégale n’existe, mais que la première séquence est plus courte.

La fonction membre retourne [do_compare](#do_compare)( `first1`, `last1`, `first2`, `last2`).

### <a name="example"></a>Exemple

```cpp
// collate_compare.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <tchar.h>
using namespace std;

int main() {
   locale loc ( "German_germany" );
   _TCHAR * s1 = _T("Das ist wei\x00dfzz."); // \x00df is the German sharp-s, it comes before z in the German alphabet
   _TCHAR * s2 = _T("Das ist weizzz.");
   int result1 = use_facet<collate<_TCHAR> > ( loc ).
      compare ( s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << result1 << endl;

   locale loc2 ( "C" );
   int result2 = use_facet<collate<_TCHAR> > ( loc2 ).
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << result2 << endl;
}
```

## <a name="do_compare"></a>  collate::do_compare

Fonction virtuelle appelée pour comparer deux séquences de caractères selon leurs règles de facette afin de vérifier leur égalité ou leur inégalité.

```cpp
virtual int do_compare(const CharType* first1,
    const CharType* last1,
    const CharType* first2,
    const CharType* last2) const;
```

### <a name="parameters"></a>Paramètres

*First1*\
Pointeur vers le premier élément de la première séquence à comparer.

*last1*\
Pointeur vers le dernier élément de la première séquence à comparer.

*First2*\
Pointeur vers le premier élément de la deuxième séquence à comparer.

*last2*\
Pointeur vers le dernier élément de la deuxième séquence à comparer.

### <a name="return-value"></a>Valeur de retour

La fonction membre retourne :

- -1 si la première séquence est inférieure à la deuxième séquence.

- +1 si la deuxième séquence est inférieure à la première séquence.

- 0 si les séquences sont équivalentes.

### <a name="remarks"></a>Notes

La fonction membre virtuelle protégée compare la séquence à [* First1, Last1) * à la séquence à *[First2, last2*). Il compare les valeurs en `operator<` appliquant entre les paires d’éléments `CharType`correspondants de type. La première séquence est inférieure si elle a le plus petit élément dans la première paire inégale des séquences ou si aucune paire inégale n’existe, mais que la première séquence est plus courte.

### <a name="example"></a>Exemples

Consultez l’exemple relatif à [collate::compare](#compare), qui appelle `do_compare`.

## <a name="do_hash"></a>  collate::do_hash

Fonction virtuelle appelée pour déterminer la valeur de hachage des séquences en fonction de leurs règles de facette.

```cpp
virtual long do_hash(const CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Paramètres

*premier*\
Pointeur vers le premier caractère de la séquence dont la valeur doit être déterminée.

*famille*\
Pointeur vers le dernier caractère de la séquence dont la valeur doit être déterminée.

### <a name="return-value"></a>Valeur de retour

Valeur de hachage de type **long** pour la séquence.

### <a name="remarks"></a>Notes

Une valeur de hachage peut être utile, par exemple, dans la répartition des séquences de manière pseudo-aléatoire sur un tableau de listes.

### <a name="example"></a>Exemples

Consultez l’exemple relatif à [hash](#hash), qui appelle `do_hash`.

## <a name="do_transform"></a>  collate::do_transform

Fonction virtuelle appelée pour convertir une séquence de caractères de paramètres régionaux en une chaîne pouvant être utilisée dans des comparaisons lexicographiques avec d'autres séquences de caractères également converties depuis les mêmes paramètres régionaux.

```cpp
virtual string_type do_transform(const CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Paramètres

*premier*\
Pointeur vers le premier caractère de la séquence à convertir.

*famille*\
Pointeur vers le dernier caractère de la séquence à convertir.

### <a name="return-value"></a>Valeur de retour

Chaîne qui est la séquence de caractères transformée.

### <a name="remarks"></a>Notes

La fonction membre virtuelle protégée retourne un objet de la classe [string_type](#string_type) dont la séquence contrôlée est une copie de la séquence [ `first`, `last`). Si une classe dérivée de collate\< **CharType**> remplace [do_compare](#do_compare), elle doit également remplacer `do_transform` pour établir la correspondance. Quand elles sont passées à `collate::compare`, deux chaînes transformées doivent générer le même résultat que si vous passez les chaînes non transformées à comparer dans la classe dérivée.

### <a name="example"></a>Exemple

Consultez l’exemple relatif à [transform](#transform), qui appelle `do_transform`.

## <a name="hash"></a>  collate::hash

Détermine la valeur de hachage d'une séquence en fonction de ses règles de facette.

```cpp
long hash(const CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Paramètres

*premier*\
Pointeur vers le premier caractère de la séquence dont la valeur doit être déterminée.

*famille*\
Pointeur vers le dernier caractère de la séquence dont la valeur doit être déterminée.

### <a name="return-value"></a>Valeur de retour

Valeur de hachage de type **long** pour la séquence.

### <a name="remarks"></a>Notes

La fonction membre retourne [do_hash](#do_hash)( `first`, `last`).

Une valeur de hachage peut être utile, par exemple, dans la répartition des séquences de manière pseudo-aléatoire sur un tableau de listes.

### <a name="example"></a>Exemples

```cpp
// collate_hash.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <tchar.h>
using namespace std;

int main( )
{
   locale loc ( "German_germany" );
   _TCHAR * s1 = _T("\x00dfzz abc."); // \x00df is the German sharp-s (looks like beta), it comes before z in the alphabet
   _TCHAR * s2 = _T("zzz abc."); // \x00df is the German sharp-s (looks like beta), it comes before z in the alphabet

   long r1 = use_facet< collate<_TCHAR> > ( loc ).
      hash (s1, &s1[_tcslen( s1 )-1 ]);
   long r2 =  use_facet< collate<_TCHAR> > ( loc ).
      hash (s2, &s2[_tcslen( s2 )-1 ] );
   cout << r1 << " " << r2 << endl;
}
```

```Output
541187293 551279837
```

## <a name="string_type"></a>  collate::string_type

Type qui décrit une chaîne de type `basic_string` qui contient des caractères de type `CharType`.

```cpp
typedef basic_string<CharType> string_type;
```

### <a name="remarks"></a>Notes

Le type décrit une spécialisation de la classe de modèle [basic_string](../standard-library/basic-string-class.md) dont les objets peuvent stocker des copies de la séquence source.

### <a name="example"></a>Exemples

Pour savoir comment déclarer et utiliser `string_type`, consultez [transform](#transform).

## <a name="transform"></a>  collate::transform

Convertit une séquence de caractères de paramètres régionaux en une chaîne qui peut être utilisée dans des comparaisons lexicographiques avec d'autres séquences de caractères, elles aussi converties depuis les mêmes paramètres régionaux.

```cpp
string_type transform(const CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Paramètres

*premier*\
Pointeur vers le premier caractère de la séquence à convertir.

*famille*\
Pointeur vers le dernier caractère de la séquence à convertir.

### <a name="return-value"></a>Valeur de retour

Chaîne qui contient la séquence de caractères transformée.

### <a name="remarks"></a>Notes

La fonction membre retourne [do_transform](#do_transform)(`first`, `last`).

### <a name="example"></a>Exemple

```cpp
// collate_transform.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <tchar.h>
using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   _TCHAR* s1 = _T("\x00dfzz abc.");
   // \x00df is the German sharp-s (looks like beta),
   // it comes before z in the alphabet
   _TCHAR* s2 = _T("zzz abc.");

   collate<_TCHAR>::string_type r1;   // OK for typedef
   r1 = use_facet< collate<_TCHAR> > ( loc ).
      transform (s1, &s1[_tcslen( s1 )-1 ]);

   cout << r1 << endl;

   basic_string<_TCHAR> r2 = use_facet< collate<_TCHAR> > ( loc ).
      transform (s2, &s2[_tcslen( s2 )-1 ]);

   cout << r2 << endl;

   int result1 = use_facet<collate<_TCHAR> > ( loc ).compare
      (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );

   cout << _tcscmp(r1.c_str( ),r2.c_str( )) << result1
      << _tcscmp(s1,s2) <<endl;
}
```

```Output

-1-11
```

## <a name="see-also"></a>Voir aussi

[\<locale>](../standard-library/locale.md)\
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
