---
title: Celementtraits, classe
ms.date: 11/04/2016
f1_keywords:
- CElementTraits
- atlcoll/ATL::CElementTraits
helpviewer_keywords:
- CElementTraits class
ms.assetid: 496528e5-7f80-4b45-be0c-6f646feb43c5
ms.openlocfilehash: 646b445aed93c9041932c60442f61792f5e1a7e8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62245766"
---
# <a name="celementtraits-class"></a>Celementtraits, classe

Cette classe est utilisée par les classes de collection pour fournir des fonctions et méthodes pour déplacer, copier, de comparaison et opérations de hachage.

## <a name="syntax"></a>Syntaxe

```
template<typename T>
class CElementTraits : public CDefaultElementTraits<T>
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Le type de données à stocker dans la collection.

## <a name="remarks"></a>Notes

Cette classe fournit des méthodes et des fonctions statiques par défaut pour le déplacement, la copie, la comparaison et de hachage des éléments stockés dans un objet de classe de collection. `CElementTraits` est spécifié en tant que le fournisseur par défaut de ces opérations par les classes de collection [CAtlArray](../../atl/reference/catlarray-class.md), [CAtlList](../../atl/reference/catllist-class.md), [CRBMap](../../atl/reference/crbmap-class.md), [CRBMultiMap](../../atl/reference/crbmultimap-class.md), et [CRBTree](../../atl/reference/crbtree-class.md).

Les implémentations par défaut seront suffisante pour les types de données simples, mais si les classes de collection sont utilisés pour stocker des objets plus complexes, les fonctions et les méthodes doivent être remplacées par les implémentations fournies par l’utilisateur.

Pour plus d’informations, consultez [ATL, Classes de Collection](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Configuration requise

**En-tête :** atlcoll.h

## <a name="see-also"></a>Voir aussi

[CDefaultElementTraits, classe](../../atl/reference/cdefaultelementtraits-class.md)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
