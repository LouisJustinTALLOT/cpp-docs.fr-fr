---
title: basic_ostringstream, classe
ms.date: 11/04/2016
f1_keywords:
- sstream/std::basic_ostringstream
- sstream/std::basic_ostringstream::allocator_type
- sstream/std::basic_ostringstream::rdbuf
- sstream/std::basic_ostringstream::str
helpviewer_keywords:
- std::basic_ostringstream [C++]
- std::basic_ostringstream [C++], allocator_type
- std::basic_ostringstream [C++], rdbuf
- std::basic_ostringstream [C++], str
ms.assetid: aea699f7-350f-432a-acca-adbae7b483fb
ms.openlocfilehash: 9e10474d3e4fb2a37e8ab52f77495758c37e8a5b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376779"
---
# <a name="basic_ostringstream-class"></a>basic_ostringstream, classe

Décrit un objet qui contrôle l’insertion d’éléments et d’objets codés dans `Alloc` un tampon de flux de classe [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**,>.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Elem, class Tr = char_traits<Elem>, class Alloc = allocator<Elem>>
class basic_ostringstream : public basic_ostream<Elem, Tr>
```

### <a name="parameters"></a>Paramètres

*Alloc*\
Classe allocator.

*Elem*\
Type de l'élément de base de la chaîne.

*Tr*\
Caractéristique spécialisée sur l'élément de base de la chaîne.

## <a name="remarks"></a>Notes

La classe décrit un objet qui contrôle l’insertion d’éléments et d’objets codés dans un tampon de flux, avec des éléments de type, `Elem`dont les traits de caractère sont déterminés par la classe `Tr`, et dont les éléments sont attribués par un allocateur de classe `Alloc`. L’objet stocke un objet de classe basic_stringbuf<**Elem**, **Tr**, `Alloc`>.

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[basic_ostringstream](#basic_ostringstream)|Construit un objet de type `basic_ostringstream`.|

### <a name="typedefs"></a>Typedefs

|Nom de type|Description|
|-|-|
|[allocator_type](#allocator_type)|Le type est synonyme du paramètre du modèle *Alloc*.|

### <a name="member-functions"></a>Fonctions Membre

|Fonction membre|Description|
|-|-|
|[rdbuf](#rdbuf)|Retourne l’adresse du tampon `pointer` de flux stocké de `Alloc` type à [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< `Elem`, `Tr`>.|
|[Str](#str)|Obtient ou définit le texte dans une mémoire tampon de chaîne sans modifier la position d'écriture.|

## <a name="requirements"></a>Spécifications

**En-tête :** \<sstream>

**Espace de noms :** std

## <a name="basic_ostringstreamallocator_type"></a><a name="allocator_type"></a>basic_ostringstream::allocator_type

Le type est synonyme du paramètre du modèle *Alloc*.

```cpp
typedef Alloc allocator_type;
```

## <a name="basic_ostringstreambasic_ostringstream"></a><a name="basic_ostringstream"></a>basic_ostringstream::basic_ostringstream

Construit un objet de type basic_ostringstream.

```cpp
explicit basic_ostringstream(ios_base::openmode _Mode = ios_base::out);

explicit basic_ostringstream(const basic_string<Elem, Tr, Alloc>& str, ios_base::openmode _Mode = ios_base::out);
```

### <a name="parameters"></a>Paramètres

*_Mode*\
Une des énumérations dans [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*Str*\
Objet de type `basic_string`.

### <a name="remarks"></a>Notes

Le premier constructeur initialise la classe de base en appelant `sb` [basic_ostream](../standard-library/basic-ostream-class.md)( sb ), où est `Alloc` **l’objet**stocké de la classe [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**,>. Il initialise également **sb** en appelant basic_stringbuf< **Elem**, **Tr**, `Alloc`>( `_Mode` &#124; `ios_base::out`).

Le deuxième constructeur initialise la classe de base en appelant basic_ostream( **sb**). Il est également `sb` parasémis en appelant basic_stringbuf< `Alloc` **Elem**, *Str* **Tr** `_Mode` ,> `ios_base::out`, &#124; ).

## <a name="basic_ostringstreamrdbuf"></a><a name="rdbuf"></a>basic_ostringstream::rdbuf

Retourne l’adresse du tampon `pointer` de flux stocké de type `Alloc` à [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**,>.

```cpp
basic_stringbuf<Elem, Tr, Alloc> *rdbuf() const;
```

### <a name="return-value"></a>Valeur de retour

L’adresse du tampon de `pointer` flux stocké, de type pour basic_stringbuf `Alloc`< **Elem**, **Tr**,>.

### <a name="remarks"></a>Notes

La fonction membre renvoie l’adresse `pointer` du tampon de flux stocké de type `Alloc` à basic_stringbuf< **Elem**, **Tr**,>.

### <a name="example"></a>Exemple

Consultez [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) pour obtenir un exemple d’utilisation de `rdbuf`.

## <a name="basic_ostringstreamstr"></a><a name="str"></a>basic_ostringstream::str

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
