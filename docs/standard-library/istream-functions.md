---
title: '&lt;istream&gt;, fonction'
ms.date: 11/04/2016
f1_keywords:
- istream/std::swap
- istream/std::ws
ms.assetid: 0301ea0d-4ded-4841-83dd-4253b55b3188
ms.openlocfilehash: 3d647c7b05a3868ec0359410cc0e703306b874ba
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363080"
---
# <a name="ltistreamgt-functions"></a>&lt;istream&gt;, fonction

|||
|-|-|
|[swap](#istream_swap)|[Ws](#ws)|

## <a name="swap"></a><a name="istream_swap"></a>Swap

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

*Gauche*\
Flux.

*Oui*\
Flux.

## <a name="ws"></a><a name="ws"></a>Ws

Ignore l'espace blanc dans le flux.

```cpp
template class<Elem, Tr> basic_istream<Elem, Tr>& ws(basic_istream<Elem, Tr>& _Istr);
```

### <a name="parameters"></a>Paramètres

*_Istr*\
Flux.

### <a name="return-value"></a>Valeur de retour

Flux.

### <a name="remarks"></a>Notes

Le manipulateur extrait et rejette `ch` tous les éléments pour lesquels [use_facet](../standard-library/basic-filebuf-class.md#open)< **ctype** \< **Elem**> > [(getloc).](../standard-library/ios-base-class.md#getloc) **is**( **ctype**\< **Elem**>:: **space**, **ch**) a la valeur true.

La fonction appelle [setstate](../standard-library/basic-ios-class.md#setstate)( **eofbit**) si elle rencontre la fin du fichier pendant l’extraction d’éléments. Il revient *_Istr*.

### <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de `ws`, consultez [operator>>](../standard-library/istream-operators.md#op_gt_gt).

## <a name="see-also"></a>Voir aussi

[\<>istream](../standard-library/istream.md)
