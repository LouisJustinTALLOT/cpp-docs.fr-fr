---
title: basic_stringbuf, classe
ms.date: 11/04/2016
f1_keywords:
- sstream/std::basic_stringbuf
- sstream/std::basic_stringbuf::allocator_type
- sstream/std::basic_stringbuf::char_type
- sstream/std::basic_stringbuf::int_type
- sstream/std::basic_stringbuf::off_type
- sstream/std::basic_stringbuf::pos_type
- sstream/std::basic_stringbuf::traits_type
- sstream/std::basic_stringbuf::overflow
- sstream/std::basic_stringbuf::pbackfail
- sstream/std::basic_stringbuf::seekoff
- sstream/std::basic_stringbuf::seekpos
- sstream/std::basic_stringbuf::str
- sstream/std::basic_stringbuf::underflow
helpviewer_keywords:
- std::basic_stringbuf [C++]
- std::basic_stringbuf [C++], allocator_type
- std::basic_stringbuf [C++], char_type
- std::basic_stringbuf [C++], int_type
- std::basic_stringbuf [C++], off_type
- std::basic_stringbuf [C++], pos_type
- std::basic_stringbuf [C++], traits_type
- std::basic_stringbuf [C++], overflow
- std::basic_stringbuf [C++], pbackfail
- std::basic_stringbuf [C++], seekoff
- std::basic_stringbuf [C++], seekpos
- std::basic_stringbuf [C++], str
- std::basic_stringbuf [C++], underflow
ms.assetid: 40c85f9e-42a5-4a65-af5c-23c8e3bf8113
ms.openlocfilehash: 578d0e31e08f3e077a908c4344f77da5495df40d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364888"
---
# <a name="basic_stringbuf-class"></a>basic_stringbuf, classe

Décrit une mémoire tampon de flux qui contrôle la transmission d'éléments de type `Elem`, dont les caractéristiques sont déterminées par la classe `Tr`, vers et à partir d'une séquence d'éléments stockés dans un objet de tableau.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Elem, class Tr = char_traits<Elem>,
    class Alloc = allocator<Elem>>
class basic_stringbuf : public basic_streambuf<Elem, Tr>
```

### <a name="parameters"></a>Paramètres

*Alloc*\
Classe allocator.

*Elem*\
Type de l'élément de base de la chaîne.

*Tr*\
Caractéristique spécialisée sur l'élément de base de la chaîne.

## <a name="remarks"></a>Notes

L'objet est alloué, étendu et libéré en fonction des modifications apportées à la séquence.

Un objet de classe basic_stringbuf < `Elem`, `Tr`, `Alloc`> stocke une copie de l’argument `ios_base::`[openmode](../standard-library/ios-base-class.md#openmode) de son constructeur comme mode `stringbuf`**mode** :

- Si `mode & ios_base::in` est différent de zéro, la mémoire tampon d'entrée est accessible. Pour plus d’informations, consultez [basic_streambuf, classe](../standard-library/basic-streambuf-class.md).

- Si `mode & ios_base::out` est différent de zéro, la mémoire tampon de sortie est accessible.

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[basic_stringbuf](#basic_stringbuf)|Construit un objet de type `basic_stringbuf`.|

### <a name="typedefs"></a>Typedefs

|Nom de type|Description|
|-|-|
|[allocator_type](#allocator_type)|Le type est synonyme du paramètre du modèle *Alloc*.|
|[char_type](#char_type)|Associe un nom de type au paramètre de modèle *Elem*.|
|[int_type](#int_type)|Rend ce `basic_filebuf`type dans la portée de 's équivalent au type du même nom dans la portée *Tr.*|
|[off_type](#off_type)|Rend ce `basic_filebuf`type dans la portée de 's équivalent au type du même nom dans la portée *Tr.*|
|[pos_type](#pos_type)|Rend ce `basic_filebuf`type dans la portée de 's équivalent au type du même nom dans la portée *Tr.*|
|[traits_type](#traits_type)|Associe un nom de type au paramètre de modèle *Tr*.|

### <a name="member-functions"></a>Fonctions Membre

|Fonction membre|Description|
|-|-|
|[Débordement](#overflow)|Fonction virtuelle protégée qui peut être appelée quand un nouveau caractère est inséré dans une mémoire tampon saturée.|
|[pbackfail](#pbackfail)|La fonction membre virtuelle protégée tente de remettre un élément dans la mémoire tampon d'entrée, puis en fait l'élément actif (vers lequel pointe le pointeur suivant).|
|[seekoff](#seekoff)|La fonction membre virtuelle protégée tente de modifier les positions actuelles des flux contrôlés.|
|[seekpos](#seekpos)|La fonction membre virtuelle protégée tente de modifier les positions actuelles des flux contrôlés.|
|[Str](#str)|Obtient ou définit le texte dans une mémoire tampon de chaîne sans modifier la position d'écriture.|
|swap||
|[underflow](#underflow)|Fonction membre virtuelle protégée pour extraire l'élément actif du flux d'entrée.|

## <a name="requirements"></a>Spécifications

**En-tête :** \<sstream>

**Espace de noms :** std

## <a name="basic_stringbufallocator_type"></a><a name="allocator_type"></a>basic_stringbuf::allocator_type

Le type est synonyme du paramètre du modèle *Alloc*.

```cpp
typedef Alloc allocator_type;
```

## <a name="basic_stringbufbasic_stringbuf"></a><a name="basic_stringbuf"></a>basic_stringbuf::basic_stringbuf

Construit un objet de type `basic_stringbuf`.

```cpp
basic_stringbuf(
    ios_base::openmode _Mode = ios_base::in | ios_base::out);

basic_stringbuf(
    const basic_string<Elem, Tr, Alloc>& str,
    ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Paramètres

*_Mode*\
Une des énumérations dans [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*Str*\
Objet de type [basic_string](../standard-library/basic-string-class.md).

### <a name="remarks"></a>Notes

Le premier constructeur stocke un pointeur null dans tous les pointeurs contrôlant la mémoire tampon d’entrée et la mémoire tampon de sortie. Pour plus d’informations, consultez la section Notes de [basic_streambuf, classe](../standard-library/basic-streambuf-class.md). Il stocke également *_Mode* comme mode stringbuf. Pour plus d’informations, consultez la section Notes de [basic_streambuf, classe](../standard-library/basic-stringbuf-class.md).

Le deuxième constructeur alloue une copie de la séquence contrôlée par *l’objet*à chaîne str . Si `_Mode & ios_base::in` est différent de zéro, elle définit la mémoire tampon d’entrée pour commencer la lecture au début de la séquence. Si `_Mode & ios_base::out` est différent de zéro, elle définit la mémoire tampon de sortie pour commencer l’écriture au début de la séquence. Il stocke également *_Mode* comme mode stringbuf. Pour plus d’informations, consultez la section Notes de [basic_streambuf, classe](../standard-library/basic-stringbuf-class.md).

## <a name="basic_stringbufchar_type"></a><a name="char_type"></a>basic_stringbuf::char_type

Associe un nom de type au paramètre de modèle *Elem*.

```cpp
typedef Elem char_type;
```

## <a name="basic_stringbufint_type"></a><a name="int_type"></a>basic_stringbuf::int_type

Rend ce type dans la portée de basic_filebuf équivalent au `Tr` type du même nom dans la portée.

```cpp
typedef typename traits_type::int_type int_type;
```

## <a name="basic_stringbufoff_type"></a><a name="off_type"></a>basic_stringbuf::off_type

Rend ce type dans la portée de basic_filebuf équivalent au `Tr` type du même nom dans la portée.

```cpp
typedef typename traits_type::off_type off_type;
```

## <a name="basic_stringbufoverflow"></a><a name="overflow"></a>basic_stringbuf::débordement

Fonction virtuelle protégée qui peut être appelée quand un nouveau caractère est inséré dans une mémoire tampon saturée.

```cpp
virtual int_type overflow(int_type _Meta = traits_type::eof());
```

### <a name="parameters"></a>Paramètres

*_Meta*\
Caractère à insérer dans la mémoire tampon, ou `traits_type::eof`.

### <a name="return-value"></a>Valeur de retour

Si la fonction ne peut pas réussir, elle retourne `traits_type::eof`. Sinon, elle retourne **traits_type::**[not_eof](../standard-library/char-traits-struct.md#not_eof)(_ *Meta*).

### <a name="remarks"></a>Notes

Si * \_Meta* ne compare pas égal à **traits_type::**[eof](../standard-library/char-traits-struct.md#eof), la fonction de membre virtuel protégé tente d’insérer l’élément **traits_type::**[to_char_type](../standard-library/char-traits-struct.md#to_char_type)(*\_Meta*) dans le tampon de sortie. Elle peut le faire de différentes manières :

- Si une position d’écriture est disponible, elle peut stocker l’élément dans la position d’écriture et incrémenter le pointeur suivant pour la mémoire tampon de sortie.

- Elle peut rendre disponible une position d’écriture en allouant du stockage nouveau ou supplémentaire à la mémoire tampon de sortie. Cette façon d’étendre la mémoire tampon de sortie permet également d’étendre les mémoires tampons d’entrée associées.

## <a name="basic_stringbufpbackfail"></a><a name="pbackfail"></a>basic_stringbuf::pbackfail

La fonction membre virtuelle protégée tente de replacer un élément dans la mémoire tampon d’entrée, puis d’en faire l’élément actif (vers lequel pointe le pointeur suivant).

```cpp
virtual int_type pbackfail(int_type _Meta = traits_type::eof());
```

### <a name="parameters"></a>Paramètres

*_Meta*\
Caractère à insérer dans la mémoire tampon, ou `traits_type::eof`.

### <a name="return-value"></a>Valeur de retour

Si la fonction ne peut pas réussir, elle retourne `traits_type::eof`. Sinon, elle retourne **traits_type::**[not_eof](../standard-library/char-traits-struct.md#not_eof)(_ *Meta*).

### <a name="remarks"></a>Notes

Si *_Meta* compare égale à **traits_type::**[eof](../standard-library/char-traits-struct.md#eof), l’élément à repousser est effectivement celui déjà dans le flux avant l’élément actuel. Sinon, cet élément est remplacé par**le traits_type byte::** **byte** = [to_char_type](../standard-library/char-traits-struct.md#to_char_type) *(Meta*). La fonction peut replacer un élément de différentes manières :

- Si une position de remise est disponible et que la valeur de l’élément stocké est égale à byte, elle peut décrémenter le pointeur suivant pour la mémoire tampon d’entrée.

- Si une position de remise est disponible et si le mode stringbuf permet de modifier la séquence ( **mode & ios_base::out** différent de zéro), elle peut stocker byte dans la position de remise et décrémenter le pointeur suivant pour la mémoire tampon d’entrée.

## <a name="basic_stringbufpos_type"></a><a name="pos_type"></a>basic_stringbuf::pos-type

Rend ce type dans la portée de basic_filebuf équivalent au `Tr` type du même nom dans la portée.

```cpp
typedef typename traits_type::pos_type pos_type;
```

## <a name="basic_stringbufseekoff"></a><a name="seekoff"></a>basic_stringbuf::seekoff

La fonction membre virtuelle protégée tente de modifier les positions actuelles des flux contrôlés.

```cpp
virtual pos_type seekoff(
    off_type _Off,
    ios_base::seekdir _Way,
    ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Paramètres

*_Off*\
La position à rechercher par rapport à *_Way*. Pour plus d’informations, consultez [basic_stringbuf::off_type](#off_type).

*_Way*\
Point de départ des opérations de décalage. Consultez [ios_base::seekdir](../standard-library/ios-base-class.md#seekdir) pour connaître les valeurs possibles.

*_Mode*\
Spécifie le mode pour la position du pointeur. La valeur par défaut est de vous autoriser à modifier les positions de lecture et d’écriture. Pour plus d’informations, consultez [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

### <a name="return-value"></a>Valeur de retour

Retourne la nouvelle position ou une position de flux non valide.

### <a name="remarks"></a>Notes

Pour un objet de classe `basic_stringbuf<Elem, Tr, Alloc>`, une position de flux se compose uniquement d’un décalage de flux. Le décalage zéro désigne le premier élément de la séquence contrôlée.

La nouvelle position est déterminée comme suit :

- `_Way`  == Si `ios_base::beg`, la nouvelle position est le début du flux plus *_Off*.

- `_Way`  == Si `ios_base::cur`, la nouvelle position est la position actuelle du flux plus *_Off*.

- `_Way`  == Si `ios_base::end`, la nouvelle position est la fin du flux plus *_Off*.

Si `_Mode & ios_base::in` est différent de zéro, la fonction modifie la position suivante à lire dans la mémoire tampon d’entrée. Si `_Mode & ios_base::out` est différent de zéro, la fonction modifie la position suivante à écrire dans la mémoire tampon de sortie. Pour qu’un flux soit affecté, sa mémoire tampon doit exister. Pour qu’une opération de positionnement réussisse, la position de flux obtenue doit se trouver dans la séquence contrôlée. Si la fonction affecte les deux positions `ios_base::beg` du `ios_base::end` flux, *_Way* doit être ou et les deux flux sont positionnés au même élément. Sinon (ou si aucune position n’est affectée), l’opération de positionnement échoue.

Si la fonction réussit à modifier une ou les deux positions de flux, elle retourne la position de flux obtenue. Sinon, elle échoue et retourne une position de flux non valide.

## <a name="basic_stringbufseekpos"></a><a name="seekpos"></a>basic_stringbuf::seekpos

La fonction membre virtuelle protégée tente de modifier les positions actuelles des flux contrôlés.

```cpp
virtual pos_type seekpos(pos_type _Sp, ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Paramètres

*_Sp*\
Position à rechercher.

*_Mode*\
Spécifie le mode pour la position du pointeur. La valeur par défaut est de vous autoriser à modifier les positions de lecture et d’écriture.

### <a name="return-value"></a>Valeur de retour

Si la fonction réussit à modifier une ou les deux positions de flux, elle retourne la position de flux obtenue. Sinon, elle échoue et retourne une position de flux non valide. Pour déterminer si la position du flux n’est pas valide, comparez la valeur de retour à `pos_type(off_type(-1))`.

### <a name="remarks"></a>Notes

Pour un objet de classe basic_stringbuf<**Elem**, **Tr**, `Alloc`>, une position de flux se compose uniquement d’un décalage de flux. Le décalage zéro désigne le premier élément de la séquence contrôlée. La nouvelle position est déterminée par _ *Sp*.

Si **mode & ios_base::in** est différent de zéro, la fonction modifie la position suivante à lire dans la mémoire tampon d’entrée. Si **mode & ios_base::out** est différent de zéro, la fonction modifie la position suivante à écrire dans la mémoire tampon de sortie. Pour qu’un flux soit affecté, sa mémoire tampon doit exister. Pour qu’une opération de positionnement réussisse, la position de flux obtenue doit se trouver dans la séquence contrôlée. Sinon (ou si aucune position n’est affectée), l’opération de positionnement échoue.

## <a name="basic_stringbufstr"></a><a name="str"></a>basic_stringbuf::str

Obtient ou définit le texte dans une mémoire tampon de chaîne sans modifier la position d'écriture.

```cpp
basic_string<Elem, Tr, Alloc> str() const;
void str(
    const basic_string<Elem, Tr, Alloc>& _Newstr);
```

### <a name="parameters"></a>Paramètres

*_Newstr*\
La nouvelle chaîne.

### <a name="return-value"></a>Valeur de retour

Retourne un objet de classe [basic_string](../standard-library/basic-string-class.md)\< **Elem**, **Tr**, Alloc **>,** dont la séquence contrôlée est une copie de la séquence contrôlée par **\*this**.

### <a name="remarks"></a>Notes

La première fonction membre retourne un objet de classe basic_string< **Elem**, **Tr**, `Alloc`>, dont la séquence contrôlée est une copie de la séquence contrôlée par **\*this**. La séquence copiée dépend du mode stringbuf stocké :

- Si **mode & ios_base::out** est différent de zéro et qu’une mémoire tampon de sortie existe, la séquence est la mémoire tampon de sortie entière ( [epptr](../standard-library/basic-streambuf-class.md#epptr) - [pbase](../standard-library/basic-streambuf-class.md#pbase) éléments commençant par `pbase`).

- Si **mode & ios_base::in** est différent de zéro et qu’une mémoire tampon d’entrée existe, la séquence est la mémoire tampon d’entrée entière ( [egptr](../standard-library/basic-streambuf-class.md#egptr) - [eback](../standard-library/basic-streambuf-class.md#eback) éléments commençant par `eback`).

- Sinon, la séquence copiée est vide.

La deuxième fonction de membre traite toute ** \*** séquence actuellement contrôlée par ceci . Il alloue ensuite une copie de la séquence contrôlée par *_Newstr*. Si **mode & ios_base::in** est différent de zéro, elle définit la mémoire tampon d’entrée pour commencer la lecture au début de la séquence. Si **mode & ios_base::out** est différent de zéro, elle définit la mémoire tampon de sortie pour commencer l’écriture au début de la séquence.

### <a name="example"></a>Exemple

```cpp
// basic_stringbuf_str.cpp
// compile with: /EHsc
#include <iostream>
#include <sstream>

using namespace std;

int main( )
{
   basic_string<char> i( "test" );
   stringstream ss;

   ss.rdbuf( )->str( i );
   cout << ss.str( ) << endl;

   ss << "z";
   cout << ss.str( ) << endl;

   ss.rdbuf( )->str( "be" );
   cout << ss.str( ) << endl;
}
```

```Output
test
zest
be
```

## <a name="basic_stringbuftraits_type"></a><a name="traits_type"></a>basic_stringbuf::traits_type

Associe un nom de type au paramètre de modèle *Tr*.

```cpp
typedef Tr traits_type;
```

### <a name="remarks"></a>Notes

Le type est un synonyme du paramètre de modèle *Tr*.

## <a name="basic_stringbufunderflow"></a><a name="underflow"></a>basic_stringbuf::underflow

Fonction virtuelle protégée pour extraire l'élément actif du flux d'entrée.

```cpp
virtual int_type underflow();
```

### <a name="return-value"></a>Valeur de retour

Si la fonction ne peut pas réussir, elle revient **traits_type::**[eof](../standard-library/char-traits-struct.md#eof). Sinon, elle retourne l’élément actuel dans le flux d’entrée, qui est converti.

### <a name="remarks"></a>Notes

La fonction de membre virtuel protégée `byte` tente d’extraire l’élément actuel du tampon d’entrée, de faire progresser la position actuelle du flux et de retourner l’élément comme **traits_type : :**[to_int_type](../standard-library/char-traits-struct.md#to_int_type)( **byte**). Il peut le faire d’une manière: Si `byte` une position de lecture est disponible, il prend comme l’élément stocké dans la position de lecture et avance le pointeur suivant pour le tampon d’entrée.

## <a name="basic_streambufswap"></a><a name="swap"></a>basic_streambuf::swap

Permute le contenu de cette mémoire tampon de chaîne avec une autre mémoire tampon de chaîne.

```cpp
void basic_stringbuf<T>::swap(basic_stringbuf& other)
```

### <a name="parameters"></a>Paramètres

*Autres*\
basic_stringbuf dont le contenu sera permuté avec ce basic_stringbuf.

### <a name="remarks"></a>Notes

## <a name="basic_stringbufoperator"></a><a name="op_eq"></a>basic_stringbuf::opérateur

Assigne le contenu de basic_stringbuf à droite de l’opérateur à basic_stringbuf à gauche.

```cpp
basic_stringbuf& basic_stringbuf:: operator=(const basic_stringbuf& other)
```

### <a name="parameters"></a>Paramètres

*Autres*\
Un basic_stringbuf dont le contenu, y compris les caractéristiques des paramètres régionaux, sera assigné au stringbuf à gauche de l'opérateur.

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Sécurité des fils dans la bibliothèque standard de CMD](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programmation iostream](../standard-library/iostream-programming.md)\
[iostreams, conventions](../standard-library/iostreams-conventions.md)
