---
title: basic_stringstream, classe
ms.date: 11/04/2016
f1_keywords:
- sstream/std::basic_stringstream
- sstream/std::basic_stringstream::allocator_type
- sstream/std::basic_stringstream::rdbuf
- sstream/std::basic_stringstream::str
helpviewer_keywords:
- std::basic_stringstream [C++]
- std::basic_stringstream [C++], allocator_type
- std::basic_stringstream [C++], rdbuf
- std::basic_stringstream [C++], str
ms.assetid: 49629814-ca37-45c5-931b-4ff894e6ebd2
ms.openlocfilehash: f08689b1080837f042abfb3c4c52bb0ad558a448
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364871"
---
# <a name="basic_stringstream-class"></a>basic_stringstream, classe

Décrit un objet qui contrôle l’insertion et l’extraction d’éléments et d’objets codés à l’aide d’un tampon de flux de classe [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Elem, class Tr = char_traits<Elem>, class Alloc = allocator<Elem>>
class basic_stringstream : public basic_iostream<Elem, Tr>
```

### <a name="parameters"></a>Paramètres

*Alloc*\
Classe allocator.

*Elem*\
Type de l'élément de base de la chaîne.

*Tr*\
Caractéristique spécialisée sur l'élément de base de la chaîne.

## <a name="remarks"></a>Notes

Le modèle de classe décrit un objet qui contrôle l’insertion et l’extraction des éléments et `Alloc` des objets codés à `Elem`l’aide d’un tampon `Tr`de flux de classe [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**,>, avec des éléments de type , dont les traits de caractère sont déterminés par la classe , et dont les éléments sont attribués par un allocateur de classe `Alloc`. L’objet stocke un objet de classe basic_stringbuf<**Elem**, **Tr**, `Alloc`>.

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[basic_stringstream](#basic_stringstream)|Construit un objet de type `basic_stringstream`.|

### <a name="typedefs"></a>Typedefs

|Nom de type|Description|
|-|-|
|[allocator_type](#allocator_type)|Le type est un synonyme du paramètre de modèle `Alloc`.|

### <a name="member-functions"></a>Fonctions Membre

|Fonction membre|Description|
|-|-|
|[rdbuf](#rdbuf)|Retourne l’adresse du tampon `pointer` de flux stocké de `Alloc` type à [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< `Elem`, `Tr`>.|
|[Str](#str)|Obtient ou définit le texte dans une mémoire tampon de chaîne sans modifier la position d'écriture.|

## <a name="requirements"></a>Spécifications

**En-tête :** \<sstream>

**Espace de noms :** std

## <a name="basic_stringstreamallocator_type"></a><a name="allocator_type"></a>basic_stringstream::allocator_type

Le type est un synonyme du paramètre de modèle `Alloc`.

```cpp
typedef Alloc allocator_type;
```

## <a name="basic_stringstreambasic_stringstream"></a><a name="basic_stringstream"></a>basic_stringstream::basic_stringstream

Construit un objet de type `basic_stringstream`.

```cpp
explicit basic_stringstream(ios_base::openmode _Mode = ios_base::in | ios_base::out);

explicit basic_stringstream(const basic_string<Elem, Tr, Alloc>& str, ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Paramètres

*_Mode*\
Une des énumérations dans [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*Str*\
Objet de type `basic_string`.

### <a name="remarks"></a>Notes

Le premier constructeur initialise la classe de base en appelant `sb` [basic_iostream](../standard-library/basic-iostream-class.md)( sb ), où est **l’objet**stocké de la classe [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>. Il est également `sb` parasémis en appelant basic_stringbuf< `Alloc` **Elem**, `_Mode` **Tr**,> (

Le deuxième constructeur initialise la classe de base en appelant basic_ostream( **sb**). Il est également `sb` parasémis en appelant basic_stringbuf< `Alloc` **Elem**, **Tr**, `_Mode`> *(- Str*, ).

## <a name="basic_stringstreamrdbuf"></a><a name="rdbuf"></a>basic_stringstream::rdbuf

Retourne l’adresse de la mémoire tampon de flux stockée de type **pointeur** à [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>.

```cpp
basic_stringbuf<Elem, Tr, Alloc> *rdbuf() const;
```

### <a name="return-value"></a>Valeur de retour

L’adresse du tampon de `pointer` flux stocké de type pour basic_stringbuf< `Alloc` **Elem**, **Tr**,>.

### <a name="example"></a>Exemple

Consultez [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) pour obtenir un exemple d’utilisation de `rdbuf`.

## <a name="basic_stringstreamstr"></a><a name="str"></a>basic_stringstream::str

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

Retourne un objet de classe [basic_string](../standard-library/basic-string-class.md)< **Elem**, **Tr**, `Alloc`>, dont la séquence contrôlée est une copie de la séquence contrôlée par ** \*ce**.

### <a name="remarks"></a>Notes

La première fonction de membre retourne [rdbuf](#rdbuf) -> [str](../standard-library/basic-stringbuf-class.md#str). La deuxième fonction `rdbuf`  -> de `_Newstr`membre appelle **str**( ).

### <a name="example"></a>Exemple

Voir [basic_stringbuf::str](../standard-library/basic-stringbuf-class.md#str) par exemple qui `str`utilise .

## <a name="see-also"></a>Voir aussi

[Sécurité des fils dans la bibliothèque standard de CMD](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programmation iostream](../standard-library/iostream-programming.md)\
[iostreams, conventions](../standard-library/iostreams-conventions.md)
