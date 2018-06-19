---
title: Classe de CElementTraits | Documents Microsoft
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
ms.openlocfilehash: c530622f096ef14d4eb3de56e5219e8f7df4f082
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32359743"
---
# <a name="celementtraits-class"></a>Classe de CElementTraits
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
 Cette classe fournit des méthodes et les fonctions statiques par défaut pour le déplacement, la copie, la comparaison et de hachage des éléments stockés dans un objet de classe de collection. `CElementTraits` le fournisseur par défaut de ces opérations est indiqué par les classes de collection [CAtlArray](../../atl/reference/catlarray-class.md), [CAtlList](../../atl/reference/catllist-class.md), [CRBMap](../../atl/reference/crbmap-class.md), [CRBMultiMap](../../atl/reference/crbmultimap-class.md), et [CRBTree](../../atl/reference/crbtree-class.md).  
  
 Les implémentations par défaut seront suffisante pour les types de données simples, mais si les classes de collection sont utilisés pour stocker des objets plus complexes, les fonctions et les méthodes doivent être substituées par les implémentations de fourni par l’utilisateur.  
  
 Pour plus d’informations, consultez [Classes de Collection ATL](../../atl/atl-collection-classes.md).  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlcoll.h  
  
## <a name="see-also"></a>Voir aussi  
 [Classe de CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
