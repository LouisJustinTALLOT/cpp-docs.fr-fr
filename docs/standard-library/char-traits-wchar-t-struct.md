---
description: 'En savoir plus sur : char_traits &lt; wchar_t &gt; struct'
title: char_traits&lt;wchar_t&gt;, struct
ms.date: 11/04/2016
f1_keywords:
- char_traits<wchar_t>
- iosfwd/std::char_traits<wchar_t>
helpviewer_keywords:
- char_traits<wchar_t> class
ms.assetid: 31f34072-04d6-4871-88fe-48e17d473484
ms.openlocfilehash: 0276f4b50cb0039d0bec49b1b3eb2a0b3b2463aa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97325220"
---
# <a name="char_traitsltwchar_tgt-struct"></a>char_traits&lt;wchar_t&gt;, struct

Une classe qui est une spécialisation de la structure de modèle **char_traits \<CharType>** à un élément de type **`wchar_t`** .

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
