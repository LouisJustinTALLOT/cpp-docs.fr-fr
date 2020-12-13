---
description: 'En savoir plus sur : classe CDefaultElementTraits'
title: CDefaultElementTraits, classe
ms.date: 11/04/2016
f1_keywords:
- CDefaultElementTraits
- atlcoll/ATL::CDefaultElementTraits
helpviewer_keywords:
- CDefaultElementTraits class
ms.assetid: ac5ee610-7957-4b7c-92b6-38ff72e4118e
ms.openlocfilehash: f4dd1bae67ef626ef793ecee946d88879a07f194
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97141893"
---
# <a name="cdefaultelementtraits-class"></a>CDefaultElementTraits, classe

Cette classe fournit des méthodes et des fonctions par défaut pour une classe de collection.

## <a name="syntax"></a>Syntaxe

```
template <typename T>
class CDefaultElementTraits : public CElementTraitsBase<T>,
    public CDefaultHashTraits<T>,
    public CDefaultCompareTraits<T>
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Type de données à stocker dans la collection.

## <a name="remarks"></a>Notes

Cette classe fournit des fonctions et des méthodes statiques par défaut pour déplacer, copier, comparer et hacher des éléments stockés dans un objet de classe de collection. Cette classe dérive ses fonctions et méthodes de [CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md), [CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)et [CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md), et est utilisée par [CElementTraits](../../atl/reference/celementtraits-class.md), [CPrimitiveElementTraits](../../atl/reference/cprimitiveelementtraits-class.md)et [CHeapPtrElementTraits](../../atl/reference/cheapptrelementtraits-class.md).

Pour plus d’informations, consultez [classes de collection ATL](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Spécifications

**En-tête :** atlcoll. h

## <a name="see-also"></a>Voir aussi

[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
