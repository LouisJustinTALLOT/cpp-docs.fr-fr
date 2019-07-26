---
title: char_traits&lt;char32_t&gt;, struct
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::char_traits<char_32t>
- char_traits<char32_t>
helpviewer_keywords:
- char_traits<char32_t> class
ms.assetid: c0315466-45d0-4a99-b83e-3b1dbfbfbbc3
ms.openlocfilehash: 9a5cf2eb7734a20d04ec5c47ae71e80180a7b29d
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459053"
---
# <a name="chartraitsltchar32tgt-struct"></a>char_traits&lt;char32_t&gt;, struct

Struct qui est une spécialisation du struct de modèle **char_traits\<CharType>** sur un élément de type `char32_t`.

## <a name="syntax"></a>Syntaxe

```cpp
template <>
struct char_traits<char32_t>;
```

## <a name="remarks"></a>Notes

La spécialisation permet au struct de tirer parti des fonctions de bibliothèque qui manipulent les objets du type `char32_t`.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<string>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[\<string>](../standard-library/string.md)\
[char_traits, struct](../standard-library/char-traits-struct.md)
