---
title: Cdefaultelementtraits, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CDefaultElementTraits
- atlcoll/ATL::CDefaultElementTraits
dev_langs:
- C++
helpviewer_keywords:
- CDefaultElementTraits class
ms.assetid: ac5ee610-7957-4b7c-92b6-38ff72e4118e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: de61165ecac24e9c892dd5e95b1bb4e042a34fa1
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43763781"
---
# <a name="cdefaultelementtraits-class"></a>Cdefaultelementtraits, classe

Cette classe fournit des fonctions et des méthodes par défaut pour une classe de collection.

## <a name="syntax"></a>Syntaxe

```
template <typename T>  
class CDefaultElementTraits : public CElementTraitsBase<T>,
    public CDefaultHashTraits<T>,
    public CDefaultCompareTraits<T>
```

#### <a name="parameters"></a>Paramètres

*T*  
Le type de données à stocker dans la collection.

## <a name="remarks"></a>Notes

Cette classe fournit des méthodes et des fonctions statiques par défaut pour le déplacement, la copie, la comparaison et de hachage des éléments stockés dans un objet de classe de collection. Cette classe est dérivée de ses fonctions et des méthodes de [CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md), [CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md), et [CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)et est utilisé par [ CElementTraits](../../atl/reference/celementtraits-class.md), [CPrimitiveElementTraits](../../atl/reference/cprimitiveelementtraits-class.md), et [CHeapPtrElementTraits](../../atl/reference/cheapptrelementtraits-class.md).

Pour plus d’informations, consultez [ATL, Classes de Collection](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Configuration requise

**En-tête :** atlcoll.h

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
