---
title: '&lt;sstream&gt;, fonctions'
ms.date: 11/04/2016
f1_keywords:
- sstream/std::swap
ms.assetid: bc9607e8-7c6b-44ef-949b-19e917b450ad
ms.openlocfilehash: 707d35123797b84b2b7cef1d1cfd9005e4becb1c
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79419510"
---
# <a name="ltsstreamgt-functions"></a>&lt;sstream&gt;, fonctions

||
|-|
|[swap](#sstream_swap)|

## <a name="sstream_swap"></a>  swap

Échange les valeurs entre deux objets `sstream`.

```cpp
template <class Elem, class Tr, class Alloc>
void swap(
    basic_stringbuf<Elem, Tr, Alloc>& left,
    basic_stringbuf<Elem, Tr, Alloc>& right);

template <class Elem, class Tr, class Alloc>
void swap(
    basic_istringstream<Elem, Tr, Alloc>& left,
    basic_istringstream<Elem, Tr, Alloc>& right);

template <class Elem, class Tr, class Alloc>
void swap(
    basic_ostringstream<Elem, Tr, Alloc>& left,
    basic_ostringstream<Elem, Tr, Alloc>& right);

template <class Elem, class Tr, class Alloc>
void swap(
    basic_stringstream<Elem, Tr, Alloc>& left,
    basic_stringstream<Elem, Tr, Alloc>& right);
```

### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*left*|Référence à un objet `sstream`.|
|*right*|Référence à un objet `sstream`.|

### <a name="remarks"></a>Notes

La fonction de modèle exécute `left.swap(right)`.

## <a name="see-also"></a>Voir aussi

[\<sstream>](../standard-library/sstream.md)
