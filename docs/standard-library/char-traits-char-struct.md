---
title: char_traits&lt;char&gt;, struct | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- iosfwd/std::char_traits<char>
- char_traits<char >
dev_langs:
- C++
helpviewer_keywords:
- char_traits<char> class
ms.assetid: abd9373a-77db-4031-bf4b-f8ac15087581
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6a20e9c1df241feb8dd7f16891f1e2a67068f772
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33840392"
---
# <a name="chartraitsltchargt-struct"></a>char_traits&lt;char&gt;, struct

Struct qui est une spécialisation du struct de modèle **char_traits\<CharType>** sur un élément de type `char`.

## <a name="syntax"></a>Syntaxe

```cpp
template <>
struct char_traits<char>;
```

## <a name="remarks"></a>Notes

La spécialisation permet au struct de tirer parti des fonctions de bibliothèque qui manipulent des objets du type `char`.

## <a name="example"></a>Exemple

Consultez les typedefs et les fonctions membres de la classe de modèle [char_traits, classe](../standard-library/char-traits-struct.md)
