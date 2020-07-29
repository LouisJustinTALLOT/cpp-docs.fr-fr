---
title: char_traits&lt;char16_t&gt;, struct
ms.date: 11/04/2016
f1_keywords:
- char_traits<char16_t>
- iosfwd/std::char_traits<char16_t>
helpviewer_keywords:
- char_traits<char16_t> class
ms.assetid: 5daf3b62-dd6e-451f-b189-0350a04ff966
ms.openlocfilehash: 53a77ff993d3a99cae1ec8e48a06dd7800ce74c7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230218"
---
# <a name="char_traitsltchar16_tgt-struct"></a>char_traits&lt;char16_t&gt;, struct

Struct qui est une spécialisation de la structure de **modèle \<CharType> char_traits** à un élément de type **`char16_t`** .

## <a name="syntax"></a>Syntaxe

```cpp
template <>
struct char_traits<char16_t>;
```

## <a name="remarks"></a>Notes

La spécialisation permet au struct de tirer parti des fonctions de bibliothèque qui manipulent des objets du type **`char16_t`** .

## <a name="requirements"></a>Spécifications

**En-tête :**\<string>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[\<string>](../standard-library/string.md)\
[Struct char_traits](../standard-library/char-traits-struct.md)\
[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)
