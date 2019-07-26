---
title: char_traits&lt;wchar_t&gt;, struct
ms.date: 11/04/2016
f1_keywords:
- char_traits<wchar_t>
- iosfwd/std::char_traits<wchar_t>
helpviewer_keywords:
- char_traits<wchar_t> class
ms.assetid: 31f34072-04d6-4871-88fe-48e17d473484
ms.openlocfilehash: a2f8a882020ddb3d87436d08b3d85ea9407b1c08
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458978"
---
# <a name="chartraitsltwchartgt-struct"></a>char_traits&lt;wchar_t&gt;, struct

Une classe qui est une spécialisation de la structure de modèle **char_traits\<CharType >** à un élément de type **wchar_t**.

## <a name="syntax"></a>Syntaxe

```cpp
template <>
struct char_traits<wchar_t>;
```

## <a name="remarks"></a>Notes

La spécialisation permet au struct de tirer parti des fonctions de bibliothèque qui manipulent des objets de ce type **wchar_t**.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<string>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[char_traits, struct](../standard-library/char-traits-struct.md)\
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
