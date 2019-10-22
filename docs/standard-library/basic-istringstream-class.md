---
title: basic_istringstream, classe
ms.date: 11/04/2016
f1_keywords:
- sstream/std::basic_istringstream
- sstream/std::basic_istringstream::allocator_type
- sstream/std::basic_istringstream::rdbuf
- sstream/std::basic_istringstream::str
- sstream/std::basic_istringstream::swap
helpviewer_keywords:
- std::basic_istringstream [C++]
- std::basic_istringstream [C++], allocator_type
- std::basic_istringstream [C++], rdbuf
- std::basic_istringstream [C++], str
- std::basic_istringstream [C++], swap
ms.assetid: 1d5bb4b5-793d-4833-98e5-14676c451915
ms.openlocfilehash: b88411316ae247499100a044a0a2dfb3c53bc84f
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689993"
---
# <a name="basic_istringstream-class"></a>basic_istringstream, classe

Décrit un objet qui contrôle l’extraction d’éléments et d’objets codés à partir d’une mémoire tampon de flux de classe [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Elem, class Tr = char_traits<Elem>, class Alloc = allocator<Elem>>
class basic_istringstream : public basic_istream<Elem, Tr>
```

### <a name="parameters"></a>Paramètres

@No__t_1 *Alloc*
Classe allocator.

@No__t_1 *elem*
Type de l'élément de base de la chaîne.

*Tr* \
Caractéristique spécialisée sur l'élément de base de la chaîne.

## <a name="remarks"></a>Notes

Le modèle de classe décrit un objet qui contrôle l’extraction d’éléments et d’objets encodés à partir d’une mémoire tampon de flux de classe [basic_stringbuf](../standard-library/basic-stringbuf-class.md) < **elem**, **TR**, `Alloc` >, avec des éléments de type *elem*, dont le caractère les caractéristiques sont déterminées par la classe *TR*, et dont les éléments sont alloués par un allocateur de la classe *Alloc*. L’objet stocke un objet de classe basic_stringbuf<**Elem**, **Tr**, `Alloc`>.

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[basic_istringstream](#basic_istringstream)|Construit un objet de type `basic_istringstream`.|

### <a name="typedefs"></a>Typedef

|Nom de type|Description|
|-|-|
|[allocator_type](#allocator_type)|Le type est un synonyme du paramètre de modèle `Alloc`.|

### <a name="member-functions"></a>Fonctions membres

|Fonction membre|Description|
|-|-|
|[rdbuf](#rdbuf)|Retourne l’adresse de la mémoire tampon de flux stockée de type `pointer` à [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< `Elem`, `Tr`, `Alloc`>.|
|[str](#str)|Obtient ou définit le texte dans une mémoire tampon de chaîne sans modifier la position d'écriture.|
|[swap](#swap)|Échange les valeurs de cet objet `basic_istringstream` avec celles de l'objet fourni.|

### <a name="operators"></a>Opérateurs

|opérateur|Description|
|-|-|
|[operator=](#op_eq)|Assigne les valeurs à cet objet `basic_istringstream` à partir du paramètre d'objet.|

## <a name="requirements"></a>spécifications

**En-tête :** \<sstream>

**Espace de noms :** std

## <a name="allocator_type"></a>  basic_istringstream::allocator_type

Le type est un synonyme du paramètre de modèle `Alloc`.

```cpp
typedef Alloc allocator_type;
```

## <a name="basic_istringstream"></a>  basic_istringstream::basic_istringstream

Construit un objet de type `basic_istringstream`.

```cpp
explicit basic_istringstream(
    ios_base::openmode _Mode = ios_base::in);

explicit basic_istringstream(
    const basic_string<Elem, Tr, Alloc>& str,
    ios_base::openmode _Mode = ios_base::in);

basic_istringstream(
    basic_istringstream&& right);
```

### <a name="parameters"></a>Paramètres

*_Mode* \
Une des énumérations dans [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*str* \
Objet de type `basic_string`.

\ *droit*
Référence rvalue d’un objet `basic_istringstream`.

### <a name="remarks"></a>Notes

Le premier constructeur initialise la classe de base en appelant [basic_istream](../standard-library/basic-istream-class.md)(`sb`), où `sb` est l’objet stocké de classe [basic_stringbuf](../standard-library/basic-stringbuf-class.md) <  `Elem`, `Tr`, `Alloc` >. Il initialise également `sb` en appelant `basic_stringbuf`< `Elem`, `Tr`, `Alloc`>( `_Mode` &#124; `ios_base::in`).

Le deuxième constructeur initialise la classe de base en appelant `basic_istream(sb)`. Il initialise également `sb` en appelant `basic_stringbuf`< `Elem`, `Tr`, `Alloc`>( `str`, `_Mode` &#124; `ios_base::in`).

Le troisième constructeur initialise l’objet avec le contenu de *droite*, traité comme une référence rvalue.

## <a name="op_eq"></a>  basic_istringstream::operator=

Assigne les valeurs à cet objet `basic_istringstream` à partir du paramètre d'objet.

```cpp
basic_istringstream& operator=(basic_istringstream&& right);
```

### <a name="parameters"></a>Paramètres

\ *droit*
Référence rvalue à un objet `basic_istringstream`.

### <a name="remarks"></a>Notes

L’opérateur membre remplace le contenu de l’objet par le contenu de *droite*, traité comme une assignation de déplacement de référence rvalue.

## <a name="rdbuf"></a>  basic_istringstream::rdbuf

Retourne l’adresse de la mémoire tampon de flux stockée de type `pointer` à [basic_stringbuf](../standard-library/basic-stringbuf-class.md) < **elem**, **TR**, `Alloc` >.

```cpp
basic_stringbuf<Elem, Tr, Alloc> *rdbuf() const;
```

### <a name="return-value"></a>Valeur de retour

Adresse de la mémoire tampon de flux stockée de type `pointer` à basic_stringbuf < **elem**, **Tr**, `Alloc` >.

### <a name="example"></a>Exemple

Consultez [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) pour obtenir un exemple d’utilisation de `rdbuf`.

## <a name="str"></a>  basic_istringstream::str

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

## <a name="swap"></a>  basic_istringstream::swap

Échange les valeurs de deux objets `basic_istringstream`.

```cpp
void swap(basic_istringstream& right);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*right*|Référence `lvalue` à un objet `basic_istringstream`.|

### <a name="remarks"></a>Notes

La fonction membre échange les valeurs de cet objet et les valeurs de *Right*.

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream, programmation](../standard-library/iostream-programming.md)\
[iostreams, conventions](../standard-library/iostreams-conventions.md)
