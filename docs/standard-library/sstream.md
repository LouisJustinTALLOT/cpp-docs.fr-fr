---
title: '&lt;sstream&gt;'
ms.date: 11/04/2016
f1_keywords:
- <sstream>
helpviewer_keywords:
- sstream header
ms.assetid: 56f55bc5-549d-4e7f-aaad-99e0ffa49c9e
ms.openlocfilehash: 31a445fcc7deb5e5bade5437058cb36e28dacd40
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88844325"
---
# <a name="ltsstreamgt"></a>&lt;sstream&gt;

Définit plusieurs modèles de classe qui prennent en charge les opérations iostreams sur les séquences stockées dans un objet de tableau alloué. Ces séquences sont facilement converties vers et à partir des objets du modèle de classe [basic_string](../standard-library/basic-string-class.md).

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

*gauche*\
Référence à un objet `sstream`.

*Oui*\
Référence à un objet `sstream`.

## <a name="remarks"></a>Notes

Les objets de type `char *` peuvent utiliser la fonctionnalité dans [\<strstream>](../standard-library/strstream.md) pour la diffusion en continu. Toutefois, \<strstream> étant déprécié, il est préférable d’utiliser \<sstream>.

### <a name="typedefs"></a>Typedefs

|Nom de type|Description|
|-|-|
|[istringstream](../standard-library/sstream-typedefs.md#istringstream)|Crée un type `basic_istringstream` spécialisé sur un **`char`** paramètre de modèle.|
|[ostringstream](../standard-library/sstream-typedefs.md#ostringstream)|Crée un type `basic_ostringstream` spécialisé sur un **`char`** paramètre de modèle.|
|[stringbuf](../standard-library/sstream-typedefs.md#stringbuf)|Crée un type `basic_stringbuf` spécialisé sur un **`char`** paramètre de modèle.|
|[StringStream](../standard-library/sstream-typedefs.md#stringstream)|Crée un type `basic_stringstream` spécialisé sur un **`char`** paramètre de modèle.|
|[wistringstream](../standard-library/sstream-typedefs.md#wistringstream)|Crée un type `basic_istringstream` spécialisé sur un **`wchar_t`** paramètre de modèle.|
|[wostringstream](../standard-library/sstream-typedefs.md#wostringstream)|Crée un type `basic_ostringstream` spécialisé sur un **`wchar_t`** paramètre de modèle.|
|[wstringbuf](../standard-library/sstream-typedefs.md#wstringbuf)|Crée un type `basic_stringbuf` spécialisé sur un **`wchar_t`** paramètre de modèle.|
|[wstringstream](../standard-library/sstream-typedefs.md#wstringstream)|Crée un type `basic_stringstream` spécialisé sur un **`wchar_t`** paramètre de modèle.|

### <a name="manipulators"></a>Manipulateurs

|Nom|Description|
|-|-|
|[swap](../standard-library/sstream-functions.md#sstream_swap)|Échange les valeurs entre deux objets `sstream`.|

### <a name="classes"></a>Classes

|Classe|Description|
|-|-|
|[basic_stringbuf](../standard-library/basic-stringbuf-class.md)|Décrit une mémoire tampon de flux qui contrôle la transmission d'éléments de type `Elem`, dont les caractéristiques sont déterminées par la classe `Tr`, vers et à partir d'une séquence d'éléments stockés dans un objet de tableau.|
|[basic_istringstream](../standard-library/basic-istringstream-class.md)|Décrit un objet qui contrôle l’extraction d’éléments et d’objets encodés à partir d’une mémoire tampon de flux de classe [basic_stringbuf](../standard-library/basic-stringbuf-class.md) < **elem**, **TR**, `Alloc`>, avec des éléments de type `Elem` , dont les caractéristiques sont déterminées par la classe `Tr` , et dont les éléments sont alloués par un allocateur de classe `Alloc` .|
|[basic_ostringstream](../standard-library/basic-ostringstream-class.md)|Décrit un objet qui contrôle l’insertion d’éléments et d’objets encodés dans une mémoire tampon de flux de classe [basic_stringbuf](../standard-library/basic-stringbuf-class.md) < **elem**, **TR**, `Alloc`>, avec des éléments de type `Elem` , dont les caractéristiques sont déterminées par la classe `Tr` , et dont les éléments sont alloués par un allocateur de classe `Alloc` .|
|[basic_stringstream](../standard-library/basic-stringstream-class.md)|Décrit un objet qui contrôle l’insertion et l’extraction d’éléments et d’objets encodés à l’aide d’une mémoire tampon de flux de classe [basic_stringbuf](../standard-library/basic-stringbuf-class.md) < **elem**, **TR**, `Alloc`>, avec des éléments de type `Elem` , dont les caractéristiques sont déterminées par la classe `Tr` , et dont les éléments sont alloués par un allocateur de classe `Alloc` .|

## <a name="requirements"></a>Configuration requise

- **En-tête :**\<sstream>

- **Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Référence des fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream, programmation](../standard-library/iostream-programming.md)\
[Conventions iostreams](../standard-library/iostreams-conventions.md)
