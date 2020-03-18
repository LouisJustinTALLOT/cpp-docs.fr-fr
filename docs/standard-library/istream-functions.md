---
title: '&lt;istream&gt;, fonction'
ms.date: 11/04/2016
f1_keywords:
- istream/std::swap
- istream/std::ws
ms.assetid: 0301ea0d-4ded-4841-83dd-4253b55b3188
ms.openlocfilehash: fc512558969bc25d2b16afa2b93219e13d0b28ca
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79420154"
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

\ *gauche*
Un flux.

\ *droit*
Un flux.

## <a name="ws"></a>  ws

Ignore l'espace blanc dans le flux.

```cpp
template class<Elem, Tr> basic_istream<Elem, Tr>& ws(basic_istream<Elem, Tr>& _Istr);
```

### <a name="parameters"></a>Paramètres

*_Istr*\
Un flux.

### <a name="return-value"></a>Valeur de retour

Flux.

### <a name="remarks"></a>Notes

Le manipulateur extrait et ignore tous les éléments `ch` pour lesquels [use_facet](../standard-library/basic-filebuf-class.md#open)< **ctype**\< **elem**> > ( [getloc](../standard-library/ios-base-class.md#getloc)). **is**( **ctype**\< **elem**>:: **Space**, **ch**) a la valeur true.

La fonction appelle [setstate](../standard-library/basic-ios-class.md#setstate)( **eofbit**) si elle rencontre la fin du fichier pendant l’extraction d’éléments. Elle retourne *_Istr*.

### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de [, consultez ](../standard-library/istream-operators.md#op_gt_gt)operator>>`ws`.

## <a name="see-also"></a>Voir aussi

[\<istream>](../standard-library/istream.md)
