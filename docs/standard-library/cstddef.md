---
title: '&lt;cstddef&gt;'
description: Décrit <STDDEF. h>, qui garantit que les noms déclarés à l’aide de la liaison externe dans l’en-tête de la bibliothèque standard C sont déclarés dans l' `std` espace de noms.
ms.date: 9/4/2020
f1_keywords:
- <cstddef>
helpviewer_keywords:
- cstddef header
ms.assetid: be8d1e39-5974-41ee-b41d-eafa6c82ffce
ms.openlocfilehash: 186de0e893c413a25d31d4f1431c280d749e9541
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040026"
---
# <a name="ltcstddefgt"></a>&lt;cstddef&gt;

Inclut l’en-tête de la bibliothèque standard C \<stddef.h> et ajoute les noms associés à l' `std` espace de noms. L’inclusion de cet en-tête garantit que les noms déclarés à l’aide de la liaison externe dans l’en-tête de la bibliothèque standard C sont déclarés dans l' `std` espace de noms.

> [!NOTE]
> \<cstddef> inclut un **octet** de type et n’inclut pas de type **`wchar_t`** .

## <a name="syntax"></a>Syntaxe

```cpp
#include <cstddef>
```

## <a name="namespace-and-macros"></a>Espace de noms et macros

```cpp
namespace std {
    using ptrdiff_t = see definition;
    using size_t = see definition;
    using max_align_t = see definition;
    using nullptr_t = decltype(nullptr);
}

#define NULL  // an implementation-defined null pointer constant
#define offsetof(type, member-designator)
```

### <a name="parameters"></a>Paramètres

*ptrdiff_t*\
Type entier signé défini par l’implémentation qui peut contenir la différence de deux indices dans un objet tableau.

*size_t*\
Type entier non signé défini par l’implémentation qui est suffisamment grand pour contenir la taille en octets d’un objet.

*max_align_t*\
Type POD dont l’exigence d’alignement est au moins aussi grande que celle de chaque type scalaire, et dont l’exigence d’alignement est prise en charge dans chaque contexte.

*nullptr_t*\
Synonyme du type d’une **`nullptr`** expression. Bien qu’une **`nullptr`** adresse ne puisse pas être prise, l’adresse d’un autre objet *nullptr_t* qui est une lvalue peut être prise.

## <a name="byte-class"></a>Byte (classe)

```cpp
enum class byte : unsigned char {};

template <class IntType>
    constexpr byte& operator<<=(byte& b, IntType shift) noexcept;
    constexpr byte operator<<(byte b, IntType shift) noexcept;
    constexpr byte& operator>>=(byte& b, IntType shift) noexcept;
    constexpr byte operator>>(byte b, IntType shift) noexcept;

constexpr byte& operator|=(byte& left, byte right) noexcept;
constexpr byte operator|(byte left, byte right) noexcept;
constexpr byte& operator&=(byte& left, byte right) noexcept;
constexpr byte operator&(byte left, byte right) noexcept;
constexpr byte& operator^=(byte& left, byte right) noexcept;
constexpr byte operator^(byte left, byte right) noexcept;
constexpr byte operator~(byte b) noexcept;

template <class IntType>
    IntType to_integer(byte b) noexcept;
```

## <a name="see-also"></a>Voir aussi

[Référence des fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[Vue d’ensemble de la bibliothèque standard C++](../standard-library/cpp-standard-library-overview.md)\
[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)
