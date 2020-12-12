---
description: 'En savoir plus sur : char_traits &lt; char32_t &gt; struct'
title: char_traits&lt;char32_t&gt;, struct
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::char_traits<char_32t>
- char_traits<char32_t>
helpviewer_keywords:
- char_traits<char32_t> class
ms.assetid: c0315466-45d0-4a99-b83e-3b1dbfbfbbc3
ms.openlocfilehash: 5b1b37421ef5e43c301cf36e1688806c8b6c8724
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97325246"
---
# <a name="char_traitsltchar32_tgt-struct"></a>char_traits&lt;char32_t&gt;, struct

Struct qui est une spécialisation de la structure de **modèle \<CharType> char_traits** à un élément de type **`char32_t`** .

## <a name="syntax"></a>Syntaxe

```cpp
template <>
struct char_traits<char32_t>;
```

## <a name="remarks"></a>Notes

La spécialisation permet au struct de tirer parti des fonctions de bibliothèque qui manipulent des objets de ce type **`char32_t`** .

## <a name="requirements"></a>Spécifications

**En-tête :**\<string>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[\<string>](../standard-library/string.md)\
[Struct char_traits](../standard-library/char-traits-struct.md)
