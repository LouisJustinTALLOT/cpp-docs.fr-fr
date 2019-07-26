---
title: '&lt;sstream&gt;'
ms.date: 11/04/2016
f1_keywords:
- <sstream>
helpviewer_keywords:
- sstream header
ms.assetid: 56f55bc5-549d-4e7f-aaad-99e0ffa49c9e
ms.openlocfilehash: 8284e56e8afb1e5518cbcbb772079b4f19d57b18
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451732"
---
# <a name="ltsstreamgt"></a>&lt;sstream&gt;

Définit plusieurs classes de modèle qui prennent en charge les opérations iostreams sur les séquences stockées dans un objet tableau alloué. Ces séquences sont facilement converties vers et depuis les objets de la classe de modèle [basic_string](../standard-library/basic-string-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
namespace std {
template <class CharType, class Traits = char_traits<CharType>, class Allocator = allocator<CharType>>
class basic_stringbuf;
typedef basic_stringbuf<char>
stringbuf;
typedef basic_stringbuf<wchar_t> wstringbuf;

template <class CharType, class Traits = char_traits<CharType>, class Allocator = allocator<CharType>>
class basic_istringstream;
typedef basic_istringstream<char>
istringstream;
typedef basic_istringstream<wchar_t> wistringstream;

template <class CharType, class Traits = char_traits<CharType>, class Allocator = allocator<CharType>>
class basic_ostringstream;
typedef basic_ostringstream<char>
ostringstream;
typedef basic_ostringstream<wchar_t> wostringstream;

template <class CharType, class Traits = char_traits<CharType>, class Allocator = allocator<CharType>>
class basic_stringstream;
typedef basic_stringstream<char>
stringstream;
typedef basic_stringstream<wchar_t> wstringstream;
// TEMPLATE FUNCTIONS
template <class CharType, class Traits, class Allocator>
void swap(
    basic_stringbuf<CharType, Traits, Allocator>& left,
    basic_stringbuf<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
void swap(
    basic_istringstream<CharType, Traits, Allocator>& left,
    basic_istringstream<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
void swap(
    basic_ostringstream<CharType, Traits, Allocator>& left,
    basic_ostringstream<CharType, Traits, Allocator>& right);

template <class CharType, class Traits, class Allocator>
void swap (
    basic_stringstream<CharType, Traits, Allocator>& left,
    basic_stringstream<CharType, Traits, Allocator>& right);

}  // namespace std
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*left*|Référence à un objet `sstream`.|
|*right*|Référence à un objet `sstream`.|

## <a name="remarks"></a>Notes

Les objets de type `char *` peuvent utiliser la fonctionnalité de [ \<strstream>](../standard-library/strstream.md) pour les flux. Toutefois, \<strstream > est déconseillé et l’utilisation de \<sstream > est encouragée.

### <a name="typedefs"></a>Typedef

|Nom de type|Description|
|-|-|
|[istringstream](../standard-library/sstream-typedefs.md#istringstream)|Crée un type `basic_istringstream` spécialisé sur un paramètre de modèle **char** .|
|[ostringstream](../standard-library/sstream-typedefs.md#ostringstream)|Crée un type `basic_ostringstream` spécialisé sur un paramètre de modèle **char** .|
|[stringbuf](../standard-library/sstream-typedefs.md#stringbuf)|Crée un type `basic_stringbuf` spécialisé sur un paramètre de modèle **char** .|
|[stringstream](../standard-library/sstream-typedefs.md#stringstream)|Crée un type `basic_stringstream` spécialisé sur un paramètre de modèle **char** .|
|[wistringstream](../standard-library/sstream-typedefs.md#wistringstream)|Crée un type `basic_istringstream` spécialisé sur un paramètre de modèle **wchar_t** .|
|[wostringstream](../standard-library/sstream-typedefs.md#wostringstream)|Crée un type `basic_ostringstream` spécialisé sur un paramètre de modèle **wchar_t** .|
|[wstringbuf](../standard-library/sstream-typedefs.md#wstringbuf)|Crée un type `basic_stringbuf` spécialisé sur un paramètre de modèle **wchar_t** .|
|[wstringstream](../standard-library/sstream-typedefs.md#wstringstream)|Crée un type `basic_stringstream` spécialisé sur un paramètre de modèle **wchar_t** .|

### <a name="manipulators"></a>Manipulateurs

|||
|-|-|
|[swap](../standard-library/sstream-functions.md#sstream_swap)|Échange les valeurs entre deux objets `sstream`.|

### <a name="classes"></a>Classes

|Classe|Description|
|-|-|
|[basic_stringbuf](../standard-library/basic-stringbuf-class.md)|Décrit une mémoire tampon de flux qui contrôle la transmission d'éléments de type `Elem`, dont les caractéristiques sont déterminées par la classe `Tr`, vers et à partir d'une séquence d'éléments stockés dans un objet de tableau.|
|[basic_istringstream](../standard-library/basic-istringstream-class.md)|Décrit un objet qui contrôle l’extraction d’éléments et d’objets encodés à partir d’une mémoire tampon de flux de `Alloc`classe [basic_stringbuf](../standard-library/basic-stringbuf-class.md)<**elem**, **TR**, `Elem`>, avec des éléments de type, dont le caractère les caractéristiques sont déterminées par `Tr`la classe, et dont les éléments sont alloués par un `Alloc`allocateur de classe.|
|[basic_ostringstream](../standard-library/basic-ostringstream-class.md)|Décrit un objet qui contrôle l’insertion d’éléments et d’objets encodés dans une mémoire tampon [](../standard-library/basic-stringbuf-class.md)<de flux de classe basic_stringbuf `Alloc`**elem**, TR, >, `Elem`avec des éléments de type, dont les caractéristiques sont déterminés par la classe `Tr`, et dont les éléments sont alloués par un allocateur de classe. `Alloc`|
|[basic_stringstream](../standard-library/basic-stringstream-class.md)|Décrit un objet qui contrôle l’insertion et l’extraction d’éléments et d’objets encodés à l’aide d’une mémoire tampon de `Alloc`flux de classe [basic_stringbuf](../standard-library/basic-stringbuf-class.md)<**elem**, `Elem` **TR**, >, avec des éléments de type, dont les caractéristiques de caractère sont déterminées `Tr`par la classe, et dont les éléments sont alloués par `Alloc`un allocateur de classe.|

## <a name="requirements"></a>Configuration requise

- **En-tête :** \<sstream>

- **Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[Sécurité des threads dans la bibliothèque C++ Standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream, programmation](../standard-library/iostream-programming.md)\
[iostreams, conventions](../standard-library/iostreams-conventions.md)
