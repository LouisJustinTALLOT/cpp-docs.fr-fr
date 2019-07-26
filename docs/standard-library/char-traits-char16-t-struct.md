---
title: char_traits&lt;char16_t&gt;, struct
ms.date: 11/04/2016
f1_keywords:
- char_traits<char16_t>
- iosfwd/std::char_traits<char16_t>
helpviewer_keywords:
- char_traits<char16_t> class
ms.assetid: 5daf3b62-dd6e-451f-b189-0350a04ff966
ms.openlocfilehash: d83f5278c2c4f8344334bfce40946612e9ca3e56
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448962"
---
# <a name="chartraitsltchar16tgt-struct"></a>char_traits&lt;char16_t&gt;, struct

Struct qui est une spécialisation du struct de modèle **char_traits\<CharType>** sur un élément de type `char16_t`.

## <a name="syntax"></a>Syntaxe

```cpp
template <>
struct char_traits<char16_t>;
```

## <a name="remarks"></a>Notes

La spécialisation permet au struct de tirer parti des fonctions de bibliothèque qui manipulent les objets du type `char16_t`.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<string>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[\<string>](../standard-library/string.md)\
[char_traits, struct](../standard-library/char-traits-struct.md)\
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
