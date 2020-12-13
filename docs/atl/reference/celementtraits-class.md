---
description: 'En savoir plus sur : classe CElementTraits'
title: CElementTraits, classe
ms.date: 11/04/2016
f1_keywords:
- CElementTraits
- atlcoll/ATL::CElementTraits
helpviewer_keywords:
- CElementTraits class
ms.assetid: 496528e5-7f80-4b45-be0c-6f646feb43c5
ms.openlocfilehash: 1bcb6c9da2bca733efe68b634eebd7f379ba0d10
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97141802"
---
# <a name="celementtraits-class"></a>CElementTraits, classe

Cette classe est utilisée par les classes de collection pour fournir des méthodes et des fonctions pour les opérations de déplacement, de copie, de comparaison et de hachage.

## <a name="syntax"></a>Syntaxe

```
template<typename T>
class CElementTraits : public CDefaultElementTraits<T>
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Type de données à stocker dans la collection.

## <a name="remarks"></a>Notes

Cette classe fournit des fonctions et des méthodes statiques par défaut pour déplacer, copier, comparer et hacher des éléments stockés dans un objet de classe de collection. `CElementTraits` est spécifié comme fournisseur par défaut de ces opérations par les classes de collection [CAtlArray](../../atl/reference/catlarray-class.md), [CAtlList](../../atl/reference/catllist-class.md), [CRBMap](../../atl/reference/crbmap-class.md), [CRBMultiMap](../../atl/reference/crbmultimap-class.md)et [CRBTree](../../atl/reference/crbtree-class.md).

Les implémentations par défaut sont suffisantes pour les types de données simples, mais si les classes de collection sont utilisées pour stocker des objets plus complexes, les fonctions et les méthodes doivent être substituées par les implémentations fournies par l’utilisateur.

Pour plus d’informations, consultez [classes de collection ATL](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Spécifications

**En-tête :** atlcoll. h

## <a name="see-also"></a>Voir aussi

[CDefaultElementTraits, classe](../../atl/reference/cdefaultelementtraits-class.md)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
