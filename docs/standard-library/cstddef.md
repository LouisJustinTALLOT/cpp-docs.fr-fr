---
title: '&lt;cstddef&gt;'
ms.date: 11/04/2016
f1_keywords:
- <cstddef>
helpviewer_keywords:
- cstddef header
ms.assetid: be8d1e39-5974-41ee-b41d-eafa6c82ffce
ms.openlocfilehash: 15d13a3af35cb41950df8aeba0c86d779e701ddb
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68244444"
---
# <a name="ltcstddefgt"></a>&lt;cstddef&gt;

Inclut l’en-tête de la bibliothèque standard C \<stddef.h > et ajoute les noms associés à la `std` espace de noms. Inclusion de cet en-tête garantit également que les noms déclarés à l’aide d’une liaison externe dans l’en-tête de la bibliothèque standard C sont déclarés dans le `std` espace de noms.

> [!NOTE]
> \<cstddef > inclut le type **octets** et n’inclut pas type **wchar_t**.

## <a name="syntax"></a>Syntaxe

```cpp
#include <cstddef>
```

## <a name="namespace-and-macros"></a>Namespace et Macros

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
Un défini par l’implémentation d’un type entier qui peut contenir la différence entre deux indices dans un objet tableau signé.

*size_t*\
Un type défini par l’implémentation d’entier non signé qui est assez grand pour contenir la taille en octets d’un objet.

*max_align_t*\
Un type POD dont spécification d’alignement est au moins aussi grande que celle de tous les types scalaires et spécification d’alignement est pris en charge dans tous les contextes.

*nullptr_t*\
Un synonyme du type d’un **nullptr** expression. Bien qu’un **nullptr** adresse ne peut pas être effectuée, l’adresse d’un autre *nullptr_t* objet qui est une lvalue peut être effectuée.

## <a name="byte-class"></a>octet, classe

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

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)<br/>
[Vue d’ensemble de la bibliothèque standard C++](../standard-library/cpp-standard-library-overview.md)<br/>
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
