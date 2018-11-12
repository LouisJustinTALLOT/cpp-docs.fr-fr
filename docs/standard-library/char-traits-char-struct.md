---
title: char_traits&lt;char&gt;, struct
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::char_traits<char>
- char_traits<char >
helpviewer_keywords:
- char_traits<char> class
ms.assetid: abd9373a-77db-4031-bf4b-f8ac15087581
ms.openlocfilehash: 6793a039b94a1ddc2daa80c5eb4d47fbdf6d6222
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50509978"
---
# <a name="chartraitsltchargt-struct"></a>char_traits&lt;char&gt;, struct

Un struct est une spécialisation de la structure de modèle **char_traits\<CharType >** à un élément de type **char**.

## <a name="syntax"></a>Syntaxe

```cpp
template <>
struct char_traits<char>;
```

## <a name="remarks"></a>Notes

La spécialisation permet au struct de tirer parti des fonctions de bibliothèque qui manipulent des objets de ce type **char**.

## <a name="example"></a>Exemple

Consultez les typedefs et les fonctions membres de la classe de modèle [char_traits, classe](../standard-library/char-traits-struct.md)
