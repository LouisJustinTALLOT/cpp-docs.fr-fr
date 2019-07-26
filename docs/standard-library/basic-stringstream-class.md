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
ms.openlocfilehash: 9278b6ce0fa23fa875f1af57ea15719111439372
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447806"
---
# <a name="basicstringstream-class"></a>basic_stringstream, classe

Décrit un objet qui contrôle l’insertion et l’extraction d’éléments et d’objets codés à l’aide d’une mémoire tampon de flux de classe [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Elem, class Tr = char_traits<Elem>, class Alloc = allocator<Elem>>
class basic_stringstream : public basic_iostream<Elem, Tr>
```

### <a name="parameters"></a>Paramètres

*Utilis*\
Classe allocator.

*Elem*\
Type de l'élément de base de la chaîne.

*TR*\
Caractéristique spécialisée sur l'élément de base de la chaîne.

## <a name="remarks"></a>Notes

La classe de modèle décrit un objet qui contrôle l’insertion et l’extraction d’éléments et d’objets encodés à l’aide d’une mémoire tampon `Alloc`de flux de classe [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **elem**, **TR**, >, avec des éléments de type `Elem`, dont les caractéristiques sont déterminées par la `Tr`classe, et dont les éléments sont alloués par un allocateur de classe `Alloc`. L’objet stocke un objet de classe basic_stringbuf<**Elem**, **Tr**, `Alloc`>.

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[basic_stringstream](#basic_stringstream)|Construit un objet de type `basic_stringstream`.|

### <a name="typedefs"></a>Typedef

|Nom de type|Description|
|-|-|
|[allocator_type](#allocator_type)|Le type est un synonyme du paramètre de modèle `Alloc`.|

### <a name="member-functions"></a>Fonctions membres

|Fonction membre|Description|
|-|-|
|[rdbuf](#rdbuf)|Retourne l’adresse de la mémoire tampon de flux stockée de type `pointer` à [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< `Elem`, `Tr`, `Alloc`>.|
|[str](#str)|Obtient ou définit le texte dans une mémoire tampon de chaîne sans modifier la position d'écriture.|

## <a name="requirements"></a>Configuration requise

**En-tête :** \<sstream>

**Espace de noms :** std

## <a name="allocator_type"></a>  basic_stringstream::allocator_type

Le type est un synonyme du paramètre de modèle `Alloc`.

```cpp
typedef Alloc allocator_type;
```

## <a name="basic_stringstream"></a>  basic_stringstream::basic_stringstream

Construit un objet de type `basic_stringstream`.

```cpp
explicit basic_stringstream(ios_base::openmode _Mode = ios_base::in | ios_base::out);

explicit basic_stringstream(const basic_string<Elem, Tr, Alloc>& str, ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Paramètres

*_Mode*\
Une des énumérations dans [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*Str*\
Objet de type `basic_string`.

### <a name="remarks"></a>Notes

Le premier constructeur initialise la classe de base en appelant [basic_iostream](../standard-library/basic-iostream-class.md)( **SB**), où `sb` est l’objet stocké de la classe [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **elem**, `Alloc` **TR**, >. Elle `sb` s’initialise également en appelant basic_stringbuf < **elem**, **TR**, `Alloc`> ( `_Mode`).

Le deuxième constructeur initialise la classe de base en appelant basic_ostream( **sb**). Elle s’initialise `sb` également en appelant basic_stringbuf < **elem**, **TR**, `Alloc`> (_ *Str*, `_Mode`).

## <a name="rdbuf"></a>  basic_stringstream::rdbuf

Retourne l’adresse de la mémoire tampon de flux stockée de type **pointeur** à [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>.

```cpp
basic_stringbuf<Elem, Tr, Alloc> *rdbuf() const;
```

### <a name="return-value"></a>Valeur de retour

Adresse de la mémoire tampon de flux stockée `pointer` de type à basic_stringbuf < **elem**, `Alloc` **TR**, >.

### <a name="example"></a>Exemple

Consultez [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) pour obtenir un exemple d’utilisation de `rdbuf`.

## <a name="str"></a>  basic_stringstream::str

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

Retourne un objet de classe [basic_string](../standard-library/basic-string-class.md)< **Elem**, **Tr**, `Alloc`> dont la séquence contrôlée est une copie de la séquence contrôlée par **\*this**.

### <a name="remarks"></a>Notes

La première fonction membre retourne [rdbuf](#rdbuf) -> [str](../standard-library/basic-stringbuf-class.md#str). La deuxième fonction membre appelle `rdbuf` -> **str**( `_Newstr`).

### <a name="example"></a>Exemple

Pour obtenir un exemple qui utilise `str`, consultez [basic_stringbuf:: Str](../standard-library/basic-stringbuf-class.md#str) .

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque C++ Standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream, programmation](../standard-library/iostream-programming.md)\
[iostreams, conventions](../standard-library/iostreams-conventions.md)
