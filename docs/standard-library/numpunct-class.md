---
title: numpunct, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xlocnum/std::numpunct
- xlocnum/std::numpunct::char_type
- xlocnum/std::numpunct::string_type
- xlocnum/std::numpunct::decimal_point
- xlocnum/std::numpunct::do_decimal_point
- xlocnum/std::numpunct::do_falsename
- xlocnum/std::numpunct::do_grouping
- xlocnum/std::numpunct::do_thousands_sep
- xlocnum/std::numpunct::do_truename
- xlocnum/std::numpunct::falsename
- xlocnum/std::numpunct::grouping
- xlocnum/std::numpunct::thousands_sep
- xlocnum/std::numpunct::truename
dev_langs:
- C++
helpviewer_keywords:
- std::numpunct [C++]
- std::numpunct [C++], char_type
- std::numpunct [C++], string_type
- std::numpunct [C++], decimal_point
- std::numpunct [C++], do_decimal_point
- std::numpunct [C++], do_falsename
- std::numpunct [C++], do_grouping
- std::numpunct [C++], do_thousands_sep
- std::numpunct [C++], do_truename
- std::numpunct [C++], falsename
- std::numpunct [C++], grouping
- std::numpunct [C++], thousands_sep
- std::numpunct [C++], truename
ms.assetid: 73fb93cc-ac11-4c98-987c-bfa6267df596
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1ae2acae1664656883f4f2eba85c57c8e7725b26
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38965563"
---
# <a name="numpunct-class"></a>numpunct, classe

Classe de modèle qui décrit un objet pouvant servir de facette locale pour décrire les séquences de type `CharType` utilisées pour représenter des informations sur la mise en forme et la ponctuation d'expressions numériques et booléennes.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType>
class numpunct : public locale::facet;
```

### <a name="parameters"></a>Paramètres

*CharType* le type utilisé dans un programme pour encoder des caractères dans des paramètres régionaux.

## <a name="remarks"></a>Notes

Comme avec n'importe quelle facette de paramètres régionaux, l'ID d'objet statique possède une valeur stockée initiale de zéro. La première tentative d’accès à sa valeur stockée entraîne le stockage d’une valeur positive unique dans **id.**

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[numpunct](#numpunct)|Constructeur des objets de type `numpunct`.|

### <a name="typedefs"></a>Typedef

|Nom de type|Description|
|-|-|
|[char_type](#char_type)|Type utilisé pour décrire un caractère utilisé par des paramètres régionaux.|
|[string_type](#string_type)|Type qui décrit une chaîne contenant des caractères de type `CharType`.|

### <a name="member-functions"></a>Fonctions membres

|Fonction membre|Description|
|-|-|
|[decimal_point](#decimal_point)|Retourne un élément spécifique aux paramètres régionaux devant être utilisé comme séparateur décimal.|
|[do_decimal_point](#do_decimal_point)|Une fonction membre virtuelle est appelée pour retourner un élément spécifique aux paramètres régionaux devant être utilisé comme séparateur décimal.|
|[do_falsename](#do_falsename)|Une fonction membre protégée virtuelle appelée pour retourner une chaîne à utiliser comme représentation textuelle de la valeur **false**.|
|[do_grouping](#do_grouping)|Fonction membre virtuelle protégée appelée pour retourner une règle spécifique aux paramètres régionaux permettant de déterminer la manière dont les chiffres sont regroupés à gauche de la virgule décimale.|
|[do_thousands_sep](#do_thousands_sep)|Une fonction membre virtuelle est appelée pour retourner un élément spécifique aux paramètres régionaux devant être utilisé comme séparateur des milliers.|
|[do_truename](#do_truename)|Fonction membre virtuelle protégée qui est appelée pour retourner une chaîne à utiliser comme représentation textuelle de la valeur **true**.|
|[falsename](#falsename)|Retourne une chaîne à utiliser comme représentation textuelle de la valeur **false**.|
|[grouping](#grouping)|Retourne une règle spécifique aux paramètres régionaux pour déterminer la manière dont les chiffres sont regroupés à gauche de la virgule décimale.|
|[thousands_sep](#thousands_sep)|Retourne un élément spécifique aux paramètres régionaux devant être utilisé comme séparateur des milliers.|
|[truename](#truename)|Retourne une chaîne à utiliser comme représentation textuelle de la valeur **true**.|

## <a name="requirements"></a>Configuration requise

**En-tête :** \<locale>

**Espace de noms :** std

## <a name="char_type"></a>  numpunct::char_type

Type utilisé pour décrire un caractère utilisé par des paramètres régionaux.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du paramètre de modèle **CharType**.

## <a name="decimal_point"></a>  numpunct::decimal_point

Retourne un élément spécifique aux paramètres régionaux devant être utilisé comme séparateur décimal.

```cpp
CharType decimal_point() const;
```

### <a name="return-value"></a>Valeur de retour

Élément spécifique aux paramètres régionaux devant être utilisé comme séparateur décimal.

### <a name="remarks"></a>Notes

La fonction membre retourne [do_decimal_point](#do_decimal_point).

### <a name="example"></a>Exemple

```cpp
// numpunct_decimal_point.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "german_germany" );

   const numpunct <char> &npunct =
   use_facet <numpunct <char> >( loc);
   cout << loc.name( ) << " decimal point "<<
   npunct.decimal_point( ) << endl;
   cout << loc.name( ) << " thousands separator "
   << npunct.thousands_sep( ) << endl;
};
```

```Output
German_Germany.1252 decimal point ,
German_Germany.1252 thousands separator .
```

## <a name="do_decimal_point"></a>  numpunct::do_decimal_point

Une fonction membre virtuelle est appelée pour retourner un élément spécifique aux paramètres régionaux devant être utilisé comme séparateur décimal.

```cpp
virtual CharType do_decimal_point() const;
```

### <a name="return-value"></a>Valeur de retour

Élément spécifique aux paramètres régionaux devant être utilisé comme séparateur décimal.

### <a name="example"></a>Exemple

Consultez l’exemple relatif à [decimal_point](#decimal_point), où la fonction membre virtuelle est appelée par `decimal_point`.

## <a name="do_falsename"></a>  numpunct::do_falsename

La fonction membre virtuelle protégée retourne une séquence à utiliser comme représentation textuelle de la valeur **false**.

```cpp
virtual string_type do_falsename() const;
```

### <a name="return-value"></a>Valeur de retour

Chaîne contenant une séquence à utiliser comme représentation textuelle de la valeur **false**.

### <a name="remarks"></a>Notes

La fonction membre retourne la chaîne « false » pour représenter la valeur **false** dans tous les paramètres régionaux.

### <a name="example"></a>Exemple

Consultez l’exemple relatif à [falsename](#falsename), où la fonction membre virtuelle est appelée par `falsename`.

## <a name="do_grouping"></a>  numpunct::do_grouping

Fonction membre virtuelle protégée appelée pour retourner une règle spécifique aux paramètres régionaux permettant de déterminer la manière dont les chiffres sont regroupés à gauche de la virgule décimale.

```cpp
virtual string do_grouping() const;
```

### <a name="return-value"></a>Valeur de retour

Règle propre aux paramètres régionaux pour déterminer comment les chiffres sont regroupés à gauche de la virgule décimale.

### <a name="remarks"></a>Notes

Cette fonction membre virtuelle protégée retourne une règle spécifique aux paramètres régionaux permettant de déterminer la manière dont les chiffres sont regroupés à gauche de la virgule décimale. L’encodage est le même que pour **lconv::grouping**.

### <a name="example"></a>Exemple

Consultez l’exemple de [regroupement](#grouping), où la fonction membre virtuelle est appelée par `grouping`.

## <a name="do_thousands_sep"></a>  numpunct::do_thousands_sep

Une fonction membre virtuelle est appelée pour retourner un élément spécifique aux paramètres régionaux devant être utilisé comme séparateur des milliers.

```cpp
virtual CharType do_thousands_sep() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne un élément spécifique aux paramètres régionaux devant être utilisé comme séparateur des milliers.

### <a name="remarks"></a>Notes

La fonction membre virtuelle protégée retourne un élément spécifique aux paramètres régionaux de type `CharType` à utiliser comme séparateur de groupes à gauche de la virgule décimale.

### <a name="example"></a>Exemple

Consultez l’exemple relatif à [thousands_sep](#thousands_sep), où la fonction membre virtuelle est appelée par `thousands_sep`.

## <a name="do_truename"></a>  numpunct::do_truename

Fonction membre virtuelle protégée qui est appelée pour retourner une chaîne à utiliser comme représentation textuelle de la valeur **true**.

```cpp
virtual string_type do_truename() const;
```

### <a name="remarks"></a>Notes

Chaîne à utiliser comme représentation textuelle de la valeur **true**.

Tous les paramètres régionaux retournent une chaîne « true » pour représenter la valeur **true**.

### <a name="example"></a>Exemple

Consultez l’exemple relatif à [truename](#truename), où la fonction membre virtuelle est appelée par `truename`.

## <a name="falsename"></a>  numpunct::falsename

Retourne une chaîne à utiliser comme représentation textuelle de la valeur **false**.

```cpp
string_type falsename() const;
```

### <a name="return-value"></a>Valeur de retour

Une chaîne contenant une séquence de `CharType`s à utiliser comme représentation textuelle de la valeur **false**.

### <a name="remarks"></a>Notes

La fonction membre retourne la chaîne « false » pour représenter la valeur **false** dans tous les paramètres régionaux.

La fonction membre retourne [do_falsename](#do_falsename).

### <a name="example"></a>Exemple

```cpp
// numpunct_falsename.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "English" );

   const numpunct <char> &npunct = use_facet <numpunct <char> >( loc );
   cout << loc.name( ) << " truename "<< npunct.truename( ) << endl;
   cout << loc.name( ) << " falsename "<< npunct.falsename( ) << endl;

   locale loc2( "French" );
   const numpunct <char> &npunct2 = use_facet <numpunct <char> >(loc2);
   cout << loc2.name( ) << " truename "<< npunct2.truename( ) << endl;
   cout << loc2.name( ) << " falsename "<< npunct2.falsename( ) << endl;
}
```

```Output
English_United States.1252 truename true
English_United States.1252 falsename false
French_France.1252 truename true
French_France.1252 falsename false
```

## <a name="grouping"></a>  numpunct::grouping

Retourne une règle spécifique aux paramètres régionaux pour déterminer la manière dont les chiffres sont regroupés à gauche de la virgule décimale.

```cpp
string grouping() const;
```

### <a name="return-value"></a>Valeur de retour

Règle propre aux paramètres régionaux pour déterminer comment les chiffres sont regroupés à gauche de la virgule décimale.

### <a name="remarks"></a>Notes

La fonction membre retourne [do_grouping](#do_grouping).

### <a name="example"></a>Exemple

```cpp
// numpunct_grouping.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "german_germany");

   const numpunct <char> &npunct =
       use_facet < numpunct <char> >( loc );
   for (unsigned int i = 0; i < npunct.grouping( ).length( ); i++)
   {
      cout << loc.name( ) << " international grouping:\n the "
           << i <<"th group to the left of the radix character "
           << "is of size " << (int)(npunct.grouping ( )[i])
           << endl;
   }
}
```

```Output
German_Germany.1252 international grouping:
 the 0th group to the left of the radix character is of size 3
```

## <a name="numpunct"></a>  numpunct::numpunct

Constructeur des objets de type `numpunct`.

```cpp
explicit numpunct(size_t _Refs = 0);
```

### <a name="parameters"></a>Paramètres

*_Refs* valeur entière utilisée pour spécifier le type de gestion de la mémoire pour l’objet.

### <a name="remarks"></a>Notes

Les valeurs possibles pour le *_Refs* paramètre et leur signification sont :

- 0 : la durée de vie de l’objet est gérée par les paramètres régionaux qui le contiennent.

- 1 : la durée de vie de l’objet doit être gérée manuellement.

- \> 1 : ces valeurs ne sont pas définies.

Aucun exemple direct n’est possible, car le destructeur est protégé.

Le constructeur initialise son objet de base avec **paramètres régionaux ::**[facette](../standard-library/locale-class.md#facet_class)(`_Refs`).

## <a name="string_type"></a>  numpunct::string_type

Type qui décrit une chaîne contenant des caractères de type **CharType**.

```cpp
typedef basic_string<CharType, Traits, Allocator> string_type;
```

### <a name="remarks"></a>Notes

Le type décrit une spécialisation de la classe de modèle [basic_string](../standard-library/basic-string-class.md) dont les objets peuvent stocker des copies des séquences de ponctuation.

## <a name="thousands_sep"></a>  numpunct::thousands_sep

Retourne un élément spécifique aux paramètres régionaux devant être utilisé comme séparateur des milliers.

```cpp
CharType thousands_sep() const;
```

### <a name="return-value"></a>Valeur de retour

Élément spécifique aux paramètres régionaux devant être utilisé comme séparateur des milliers.

### <a name="remarks"></a>Notes

La fonction membre retourne [do_thousands_sep](#do_thousands_sep).

### <a name="example"></a>Exemple

```cpp
// numpunct_thou_sep.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "german_germany" );

   const numpunct <char> &npunct =
   use_facet < numpunct < char > >( loc );
   cout << loc.name( ) << " decimal point "<<
   npunct.decimal_point( ) << endl;
   cout << loc.name( ) << " thousands separator "
   << npunct.thousands_sep( ) << endl;
};
```

```Output
German_Germany.1252 decimal point ,
German_Germany.1252 thousands separator .
```

## <a name="truename"></a>  numpunct::truename

Retourne une chaîne à utiliser comme représentation textuelle de la valeur **true**.

```cpp
string_type falsename() const;
```

### <a name="return-value"></a>Valeur de retour

Chaîne à utiliser comme représentation textuelle de la valeur **true**.

### <a name="remarks"></a>Notes

La fonction membre retourne [do_truename](#do_truename).

Tous les paramètres régionaux retournent une chaîne « true » pour représenter la valeur **true**.

### <a name="example"></a>Exemple

```cpp
// numpunct_truename.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "English" );

   const numpunct < char> &npunct = use_facet <numpunct <char> >( loc );
   cout << loc.name( ) << " truename "<< npunct.truename( ) << endl;
   cout << loc.name( ) << " falsename "<< npunct.falsename( ) << endl;

   locale loc2("French");
   const numpunct <char> &npunct2 = use_facet <numpunct <char> >( loc2 );
   cout << loc2.name( ) << " truename "<< npunct2.truename( ) << endl;
   cout << loc2.name( ) << " falsename "<< npunct2.falsename( ) << endl;
}
```

```Output
English_United States.1252 truename true
English_United States.1252 falsename false
French_France.1252 truename true
French_France.1252 falsename false
```

## <a name="see-also"></a>Voir aussi

[\<locale>](../standard-library/locale.md)<br/>
[Facet, classe](../standard-library/locale-class.md#facet_class)<br/>
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
