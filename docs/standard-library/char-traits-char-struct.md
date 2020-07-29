---
title: char_traits&lt;char&gt;, struct
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::char_traits<char>
- char_traits<char >
helpviewer_keywords:
- char_traits<char> class
ms.assetid: abd9373a-77db-4031-bf4b-f8ac15087581
ms.openlocfilehash: 04e3a3d067c7fd0e4513d1e1e4463ff6e9f7fe22
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224888"
---
# <a name="char_traitsltchargt-struct"></a>char_traits&lt;char&gt;, struct

Struct qui est une spécialisation de la structure de **modèle \<CharType> char_traits** à un élément de type **`char`** .

## <a name="syntax"></a>Syntaxe

```cpp
template <>
struct char_traits<char>;
```

## <a name="remarks"></a>Notes

La spécialisation permet au struct de tirer parti des fonctions de bibliothèque qui manipulent des objets de ce type **`char`** .

## <a name="example"></a>Exemple

Consultez les typedefs et les fonctions membres du modèle de classe [Char_traits classe](../standard-library/char-traits-struct.md)
