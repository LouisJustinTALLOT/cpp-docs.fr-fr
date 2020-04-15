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
ms.openlocfilehash: 6a8ead5f1014e7f750e01988241ab020431312da
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376804"
---
# <a name="basic_istringstream-class"></a>basic_istringstream, classe

Décrit un objet qui contrôle l’extraction d’éléments et d’objets codés à `Alloc` partir d’un tampon de flux de classe [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**,>.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Elem, class Tr = char_traits<Elem>, class Alloc = allocator<Elem>>
class basic_istringstream : public basic_istream<Elem, Tr>
```

### <a name="parameters"></a>Paramètres

*Alloc*\
Classe allocator.

*Elem*\
Type de l'élément de base de la chaîne.

*Tr*\
Caractéristique spécialisée sur l'élément de base de la chaîne.

## <a name="remarks"></a>Notes

Le modèle de classe décrit un objet qui contrôle l’extraction d’éléments et d’objets `Alloc` codés à partir d’un tampon de flux de classe [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**,>, avec des éléments de type *Elem*, dont les traits de caractère sont déterminés par la classe *Tr*, et dont les éléments sont attribués par un allocateur de classe *Alloc*. L’objet stocke un objet de classe basic_stringbuf<**Elem**, **Tr**, `Alloc`>.

### <a name="constructors"></a>Constructeurs

|Constructeur|Description|
|-|-|
|[basic_istringstream](#basic_istringstream)|Construit un objet de type `basic_istringstream`.|

### <a name="typedefs"></a>Typedefs

|Nom de type|Description|
|-|-|
|[allocator_type](#allocator_type)|Le type est un synonyme du paramètre de modèle `Alloc`.|

### <a name="member-functions"></a>Fonctions Membre

|Fonction membre|Description|
|-|-|
|[rdbuf](#rdbuf)|Retourne l’adresse du tampon `pointer` de flux stocké de `Alloc` type à [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< `Elem`, `Tr`>.|
|[Str](#str)|Obtient ou définit le texte dans une mémoire tampon de chaîne sans modifier la position d'écriture.|
|[swap](#swap)|Échange les valeurs de cet objet `basic_istringstream` avec celles de l'objet fourni.|

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[opérateur](#op_eq)|Assigne les valeurs à cet objet `basic_istringstream` à partir du paramètre d'objet.|

## <a name="requirements"></a>Spécifications

**En-tête :** \<sstream>

**Espace de noms :** std

## <a name="basic_istringstreamallocator_type"></a><a name="allocator_type"></a>basic_istringstream::allocator_type

Le type est un synonyme du paramètre de modèle `Alloc`.

```cpp
typedef Alloc allocator_type;
```

## <a name="basic_istringstreambasic_istringstream"></a><a name="basic_istringstream"></a>basic_istringstream::basic_istringstream

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

*_Mode*\
Une des énumérations dans [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*Str*\
Objet de type `basic_string`.

*Oui*\
Référence rvalue d’un objet `basic_istringstream`.

### <a name="remarks"></a>Notes

Le premier constructeur initialise la classe de base`sb`en `sb` appelant [basic_istream](../standard-library/basic-istream-class.md)( ), où `Tr` `Alloc` est l’objet stocké de la classe [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< `Elem`, ,>. Il initialise également `sb` en appelant `basic_stringbuf`< `Elem`, `Tr`, `Alloc`>( `_Mode` &#124; `ios_base::in`).

Le deuxième constructeur initialise la classe de base en appelant `basic_istream(sb)`. Il initialise également `sb` en appelant `basic_stringbuf`< `Elem`, `Tr`, `Alloc`>( `str`, `_Mode` &#124; `ios_base::in`).

Le troisième constructeur initialise l’objet avec le contenu du *droit,* traité comme une référence rvalue.

## <a name="basic_istringstreamoperator"></a><a name="op_eq"></a>basic_istringstream::opérateur

Assigne les valeurs à cet objet `basic_istringstream` à partir du paramètre d'objet.

```cpp
basic_istringstream& operator=(basic_istringstream&& right);
```

### <a name="parameters"></a>Paramètres

*Oui*\
Référence rvalue à un objet `basic_istringstream`.

### <a name="remarks"></a>Notes

L’opérateur membre remplace le contenu de l’objet par le contenu du *droit,* traité comme une affectation de transfert de référence rvalue.

## <a name="basic_istringstreamrdbuf"></a><a name="rdbuf"></a>basic_istringstream::rdbuf

Retourne l’adresse du tampon `pointer` de flux stocké de type `Alloc` à [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**,>.

```cpp
basic_stringbuf<Elem, Tr, Alloc> *rdbuf() const;
```

### <a name="return-value"></a>Valeur de retour

L’adresse du tampon de `pointer` flux stocké de type pour basic_stringbuf< `Alloc` **Elem**, **Tr**,>.

### <a name="example"></a>Exemple

Consultez [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close) pour obtenir un exemple d’utilisation de `rdbuf`.

## <a name="basic_istringstreamstr"></a><a name="str"></a>basic_istringstream::str

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

## <a name="basic_istringstreamswap"></a><a name="swap"></a>basic_istringstream::swap

Échange les valeurs de deux objets `basic_istringstream`.

```cpp
void swap(basic_istringstream& right);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*Oui*|Référence `lvalue` à un objet `basic_istringstream`.|

### <a name="remarks"></a>Notes

La fonction membre échange les valeurs de cet objet et les valeurs de *droit*.

## <a name="see-also"></a>Voir aussi

[Sécurité des fils dans la bibliothèque standard de CMD](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programmation iostream](../standard-library/iostream-programming.md)\
[iostreams, conventions](../standard-library/iostreams-conventions.md)
