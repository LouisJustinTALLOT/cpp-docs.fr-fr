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
ms.openlocfilehash: ebf9b87b60cf790a2ca032eb805095f277324178
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688411"
---
# <a name="basic_stringstream-class"></a>basic_stringstream, classe

Décrit un objet qui contrôle l’insertion et l’extraction d’éléments et d’objets codés à l’aide d’une mémoire tampon de flux de classe [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Elem, class Tr = char_traits<Elem>, class Alloc = allocator<Elem>>
class basic_stringstream : public basic_iostream<Elem, Tr>
```

### <a name="parameters"></a>Paramètres

@No__t_1 *Alloc*
Classe allocator.

@No__t_1 *elem*
Type de l'élément de base de la chaîne.

*Tr* \
Caractéristique spécialisée sur l'élément de base de la chaîne.

## <a name="remarks"></a>Notes

Le modèle de classe décrit un objet qui contrôle l’insertion et l’extraction d’éléments et d’objets encodés à l’aide d’une mémoire tampon de flux de classe [basic_stringbuf](../standard-library/basic-stringbuf-class.md) < **elem**, **TR**, `Alloc` >, avec des éléments de type `Elem`, dont les caractéristiques de caractère sont déterminées par la classe `Tr`, et dont les éléments sont alloués par un allocateur de la classe `Alloc`. L’objet stocke un objet de classe basic_stringbuf<**Elem**, **Tr**, `Alloc`>.

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

## <a name="requirements"></a>spécifications

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

*_Mode* \
Une des énumérations dans [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*str* \
Objet de type `basic_string`.

### <a name="remarks"></a>Notes

Le premier constructeur initialise la classe de base en appelant [basic_iostream](../standard-library/basic-iostream-class.md)( **SB**), où `sb` est l’objet stocké de la classe [basic_stringbuf](../standard-library/basic-stringbuf-class.md) < **elem**, **TR**, `Alloc` >. Il initialise également `sb` en appelant basic_stringbuf < **elem**, **Tr**, `Alloc` > (`_Mode`).

Le deuxième constructeur initialise la classe de base en appelant basic_ostream( **sb**). Il initialise également `sb` en appelant basic_stringbuf < **elem**, **Tr**, `Alloc` > (_ *Str*, `_Mode`).

## <a name="rdbuf"></a>  basic_stringstream::rdbuf

Retourne l’adresse de la mémoire tampon de flux stockée de type **pointeur** à [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>.

```cpp
basic_stringbuf<Elem, Tr, Alloc> *rdbuf() const;
```

### <a name="return-value"></a>Valeur de retour

Adresse de la mémoire tampon de flux stockée de type `pointer` à basic_stringbuf < **elem**, **Tr**, `Alloc` >.

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

*_Newstr* \
La nouvelle chaîne.

### <a name="return-value"></a>Valeur de retour

Retourne un objet de classe [basic_string](../standard-library/basic-string-class.md)< **Elem**, **Tr**, `Alloc`> dont la séquence contrôlée est une copie de la séquence contrôlée par **\*this**.

### <a name="remarks"></a>Notes

La première fonction membre retourne [rdbuf](#rdbuf) -> [str](../standard-library/basic-stringbuf-class.md#str). La deuxième fonction membre appelle `rdbuf` -> **str**( `_Newstr`).

### <a name="example"></a>Exemple

Consultez [basic_stringbuf :: Str](../standard-library/basic-stringbuf-class.md#str) pour obtenir un exemple qui utilise `str`.

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream, programmation](../standard-library/iostream-programming.md)\
[iostreams, conventions](../standard-library/iostreams-conventions.md)
