---
title: char_traits&lt;wchar_t&gt;, struct
ms.date: 11/04/2016
f1_keywords:
- char_traits<wchar_t>
- iosfwd/std::char_traits<wchar_t>
helpviewer_keywords:
- char_traits<wchar_t> class
ms.assetid: 31f34072-04d6-4871-88fe-48e17d473484
ms.openlocfilehash: 3b2504dbb124ccca7f9b27619585abb2b5795f92
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219168"
---
# <a name="char_traitsltwchar_tgt-struct"></a>char_traits&lt;wchar_t&gt;, struct

Une classe qui est une spécialisation de la structure de modèle **char_traits \<CharType> ** à un élément de type **`wchar_t`** .

## <a name="syntax"></a>Syntaxe

```cpp
template <>
struct char_traits<wchar_t>;
```

## <a name="remarks"></a>Notes

La spécialisation permet au struct de tirer parti des fonctions de bibliothèque qui manipulent des objets de ce type **`wchar_t`** .

## <a name="requirements"></a>Spécifications

**En-tête :**\<string>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Struct char_traits](../standard-library/char-traits-struct.md)\
[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)
