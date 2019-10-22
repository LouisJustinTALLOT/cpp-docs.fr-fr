---
title: char_traits&lt;char&gt;, struct
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::char_traits<char>
- char_traits<char >
helpviewer_keywords:
- char_traits<char> class
ms.assetid: abd9373a-77db-4031-bf4b-f8ac15087581
ms.openlocfilehash: ccb08f3e505122757080129b36558490456fc2c5
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688324"
---
# <a name="char_traitsltchargt-struct"></a>char_traits&lt;char&gt;, struct

Struct qui est une spécialisation de la structure de modèle **char_traits \<CharType >** à un élément de type **char**.

## <a name="syntax"></a>Syntaxe

```cpp
template <>
struct char_traits<char>;
```

## <a name="remarks"></a>Notes

La spécialisation permet au struct de tirer parti des fonctions de bibliothèque qui manipulent des objets de ce type **char**.

## <a name="example"></a>Exemple

Consultez les typedefs et les fonctions membres de la [classe char_traits](../standard-library/char-traits-struct.md) du modèle de classe
