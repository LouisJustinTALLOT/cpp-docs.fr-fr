---
title: char_traits&lt;char16_t&gt;, struct | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- char_traits<char16_t>
- iosfwd/std::char_traits<char16_t>
dev_langs:
- C++
helpviewer_keywords:
- char_traits<char16_t> class
ms.assetid: 5daf3b62-dd6e-451f-b189-0350a04ff966
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 24d6c3d5dd11290ce4151b5d54885ba492b8ee45
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33845282"
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

## <a name="requirements"></a>Spécifications

**En-tête :** \<string>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[\<string>](../standard-library/string.md)<br/>
[char_traits, struct](../standard-library/char-traits-struct.md)<br/>
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
