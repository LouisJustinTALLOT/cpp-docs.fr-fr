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
ms.openlocfilehash: 1150de3c94f8a656d46d54b673cb2d08dc05a7be
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38959324"
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
