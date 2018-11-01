---
title: '&lt;istream&gt;, fonction'
ms.date: 11/04/2016
f1_keywords:
- istream/std::swap
- istream/std::ws
ms.assetid: 0301ea0d-4ded-4841-83dd-4253b55b3188
ms.openlocfilehash: b590559b01bb8f5db21fca9f78d220d8bad5c27e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50537642"
---
# <a name="ltistreamgt-functions"></a>&lt;istream&gt;, fonction

|||
|-|-|
|[swap](#istream_swap)|[ws](#ws)|

## <a name="istream_swap"></a>  swap

Échange les éléments de deux objets de flux.

```cpp
template <class Elem, class Tr>
void swap(
    basic_istream<Elem, Tr>& left,
    basic_istream<Elem, Tr>& right);

template <class Elem, class Tr>
void swap(
    basic_iostream<Elem, Tr>& left,
    basic_iostream<Elem, Tr>& right);
```

### <a name="parameters"></a>Paramètres

*left*<br/>
Un flux.

*right*<br/>
Un flux.

## <a name="ws"></a>  ws

Ignore l'espace blanc dans le flux.

```cpp
template class<Elem, Tr> basic_istream<Elem, Tr>& ws(basic_istream<Elem, Tr>& _Istr);
```

### <a name="parameters"></a>Paramètres

*_Istr*<br/>
Un flux.

### <a name="return-value"></a>Valeur de retour

flux.

### <a name="remarks"></a>Notes

Le manipulateur extrait et ignore tout élément `ch` pour lequel [use_facet](../standard-library/basic-filebuf-class.md#open)< **ctype**\< **Elem**> >( [getloc](../standard-library/ios-base-class.md#getloc)). **is**( **ctype**\< **Elem**>:: **space**, **ch**) a la valeur true.

La fonction appelle [setstate](../standard-library/basic-ios-class.md#setstate)( **eofbit**) si elle rencontre la fin du fichier pendant l’extraction d’éléments. Elle retourne *_Istr*.

### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de `ws`, consultez [operator>>](../standard-library/istream-operators.md#op_gt_gt).

## <a name="see-also"></a>Voir aussi

[\<istream>](../standard-library/istream.md)<br/>
