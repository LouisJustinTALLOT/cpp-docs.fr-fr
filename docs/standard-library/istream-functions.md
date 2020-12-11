---
description: 'En savoir plus sur : &lt; IStream, &gt; fonctions'
title: '&lt;istream&gt;, fonction'
ms.date: 11/04/2016
f1_keywords:
- istream/std::swap
- istream/std::ws
ms.assetid: 0301ea0d-4ded-4841-83dd-4253b55b3188
ms.openlocfilehash: c71770d8c6e86829eb4e0153abc924d612d3eff6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97154173"
---
# <a name="ltistreamgt-functions"></a>&lt;istream&gt;, fonction

[échange](#istream_swap)\
[ws](#ws)

## <a name="swap"></a><a name="istream_swap"></a> échange

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

*gauche*\
Un flux.

*Oui*\
Un flux.

## <a name="ws"></a><a name="ws"></a> Web

Ignore l'espace blanc dans le flux.

```cpp
template class<Elem, Tr> basic_istream<Elem, Tr>& ws(basic_istream<Elem, Tr>& _Istr);
```

### <a name="parameters"></a>Paramètres

*_Istr*\
Un flux.

### <a name="return-value"></a>Valeur renvoyée

Flux.

### <a name="remarks"></a>Notes

Le manipulateur extrait et ignore tous les éléments `ch` pour lesquels [use_facet](../standard-library/basic-filebuf-class.md#open) <  **CType** \< **Elem**> > ( [getloc](../standard-library/ios-base-class.md#getloc)). **is**( **CType** \< **Elem**> :: **Space**, **ch**) a la valeur true.

La fonction appelle [setstate](../standard-library/basic-ios-class.md#setstate)( **eofbit**) si elle rencontre la fin du fichier pendant l’extraction d’éléments. Elle retourne *_Istr*.

### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de `ws`, consultez [operator>>](../standard-library/istream-operators.md#op_gt_gt).

## <a name="see-also"></a>Voir aussi

[\<istream>](../standard-library/istream.md)
