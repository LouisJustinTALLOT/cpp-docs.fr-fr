---
title: Celementtraits, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CElementTraits
- atlcoll/ATL::CElementTraits
dev_langs:
- C++
helpviewer_keywords:
- CElementTraits class
ms.assetid: 496528e5-7f80-4b45-be0c-6f646feb43c5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 45139b16ebb923acd004d995cd9466ea9e39e163
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43765734"
---
# <a name="celementtraits-class"></a>Celementtraits, classe

Cette classe est utilisée par les classes de collection pour fournir des fonctions et méthodes pour déplacer, copier, de comparaison et opérations de hachage.

## <a name="syntax"></a>Syntaxe

```
template<typename T>  
class CElementTraits : public CDefaultElementTraits<T>
```

#### <a name="parameters"></a>Paramètres

`T`  
Le type de données à stocker dans la collection.

## <a name="remarks"></a>Notes

Cette classe fournit des méthodes et des fonctions statiques par défaut pour le déplacement, la copie, la comparaison et de hachage des éléments stockés dans un objet de classe de collection. `CElementTraits` est spécifié en tant que le fournisseur par défaut de ces opérations par les classes de collection [CAtlArray](../../atl/reference/catlarray-class.md), [CAtlList](../../atl/reference/catllist-class.md), [CRBMap](../../atl/reference/crbmap-class.md), [CRBMultiMap](../../atl/reference/crbmultimap-class.md), et [CRBTree](../../atl/reference/crbtree-class.md).

Les implémentations par défaut seront suffisante pour les types de données simples, mais si les classes de collection sont utilisés pour stocker des objets plus complexes, les fonctions et les méthodes doivent être remplacées par les implémentations fournies par l’utilisateur.

Pour plus d’informations, consultez [ATL, Classes de Collection](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Configuration requise

**En-tête :** atlcoll.h

## <a name="see-also"></a>Voir aussi

[Cdefaultelementtraits, classe](../../atl/reference/cdefaultelementtraits-class.md)   
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
