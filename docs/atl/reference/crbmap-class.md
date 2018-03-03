---
title: Classe de CRBMap | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CRBMap
- ATLCOLL/ATL::CRBMap
- ATLCOLL/ATL::CRBMap::CRBMap
- ATLCOLL/ATL::CRBMap::Lookup
- ATLCOLL/ATL::CRBMap::RemoveKey
- ATLCOLL/ATL::CRBMap::SetAt
dev_langs:
- C++
helpviewer_keywords:
- CRBMap class
ms.assetid: 658e94dc-e835-4356-aed1-1513e1f66969
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3cfa4d6fff6b46341f01b4d5ce18d9ec418738bf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="crbmap-class"></a>Classe de CRBMap
Cette classe représente une structure de mappage à l’aide d’un arbre binaire rouge-noire.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <typename K,
          typename V, 
          class KTraits = CElementTraits<K>, 
          class VTraits = CElementTraits<V>> 
class CRBMap : public CRBTree<K, V, KTraits, VTraits>
```    
  
#### <a name="parameters"></a>Paramètres  
 `K`  
 Le type d’élément de clé.  
  
 *V*  
 Le type d’élément de valeur.  
  
 `KTraits`  
 Le code utilisé pour copier ou déplacer des éléments clés. Consultez [CElementTraits classe](../../atl/reference/celementtraits-class.md) pour plus d’informations.  
  
 `VTraits`  
 Le code utilisé pour copier ou déplacer des éléments de valeur.  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CRBMap::CRBMap](#crbmap)|Constructeur.|  
|[CRBMap :: ~ CRBMap](#dtor)|Destructeur.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CRBMap::Lookup](#lookup)|Appelez cette méthode pour rechercher des clés ou des valeurs dans le `CRBMap` objet.|  
|[CRBMap::RemoveKey](#removekey)|Appelez cette méthode pour supprimer un élément à partir de la `CRBMap` objet, en fonction de la clé.|  
|[CRBMap::SetAt](#setat)|Appelez cette méthode pour insérer une paire de l’élément dans le mappage.|  
  
## <a name="remarks"></a>Notes  
 `CRBMap`prend en charge un tableau de mappage d’un type donné, la gestion d’un tableau ordonné d’éléments clés et leurs valeurs associées. Chaque clé peut avoir qu’une seule valeur associée. Éléments (composé d’une clé et une valeur) sont stockés dans une arborescence binaire de la structure, à l’aide de la [CRBMap::SetAt](#setat) (méthode). Les éléments peuvent être supprimés à l’aide de la [CRBMap::RemoveKey](#removekey) (méthode), ce qui supprime l’élément avec la valeur de clé donnée.  
  
 Parcourir l’arborescence est possible avec des méthodes telles que [CRBTree::GetHeadPosition](../../atl/reference/crbtree-class.md#getheadposition), [CRBTree::GetNext](../../atl/reference/crbtree-class.md#getnext), et [CRBTree::GetNextValue](../../atl/reference/crbtree-class.md#getnextvalue).  
  
 Le `KTraits` et `VTraits` paramètres sont des classes de caractéristiques contenant tout code supplémentaire est nécessaire pour copier ou déplacer des éléments.  
  
 `CRBMap`est dérivé de [CRBTree](../../atl/reference/crbtree-class.md), qui implémente un arbre binaire à l’aide de l’algorithme rouge-noire. [CRBMultiMap](../../atl/reference/crbmultimap-class.md) est une variante qui autorise plusieurs valeurs pour chaque clé. Il est trop dérivé `CRBTree`et donc partage plusieurs fonctionnalités avec `CRBMap`.  
  
 Une alternative à la fois aux `CRBMap` et `CRBMultiMap` est proposé par le [CAtlMap](../../atl/reference/catlmap-class.md) classe. Lorsque seul un petit nombre d’éléments doit être stockée, envisagez d’utiliser le [CSimpleMap](../../atl/reference/csimplemap-class.md) classe à la place.  
  
 Pour obtenir une description plus complète de diverses classes de collection et leurs fonctions et les caractéristiques de performances, consultez [Classes de Collection ATL](../../atl/atl-collection-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CRBTree](../../atl/reference/crbtree-class.md)  
  
 `CRBMap`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** atlcoll.h  
  
##  <a name="crbmap"></a>CRBMap::CRBMap  
 Constructeur.  
  
```
explicit CRBMap(size_t nBlockSize = 10) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `nBlockSize`  
 La taille du bloc.  
  
### <a name="remarks"></a>Notes  
 Le `nBlockSize` paramètre est une mesure de la quantité de mémoire allouée lorsqu’un nouvel élément est requis. Tailles de bloc supérieures réduisent les appels aux routines d’allocation de mémoire, mais utilisent davantage de ressources. La valeur par défaut alloue de l’espace de 10 éléments à la fois.  
  
 Consultez la documentation de la classe de base [CRBTree](../../atl/reference/crbtree-class.md) pour plus d’informations sur les méthodes disponibles.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Utilities#81](../../atl/codesnippet/cpp/crbmap-class_1.cpp)]  
  
##  <a name="dtor"></a>CRBMap :: ~ CRBMap  
 Destructeur.  
  
```
~CRBMap() throw();
```  
  
### <a name="remarks"></a>Notes  
 Libère les ressources allouées.  
  
 Consultez la documentation de la classe de base [CRBTree](../../atl/reference/crbtree-class.md) pour plus d’informations sur les méthodes disponibles.  
  
##  <a name="lookup"></a>CRBMap::Lookup  
 Appelez cette méthode pour rechercher des clés ou des valeurs dans le `CRBMap` objet.  
  
```
bool Lookup(KINARGTYPE key, VOUTARGTYPE value) const throw(...);
const CPair* Lookup(KINARGTYPE key) const throw();
CPair* Lookup(KINARGTYPE key) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `key`  
 Spécifie la clé qui identifie l’élément à rechercher.  
  
 *valeur*  
 Variable qui reçoit la valeur recherchée.  
  
### <a name="return-value"></a>Valeur de retour  
 La première forme de la méthode retourne la valeur true si la clé est trouvée, sinon false. Les deuxième et troisième forms retournent un pointeur vers un [CPair](crbtree-class.md#cpair_class).  
  
### <a name="remarks"></a>Notes  
 Consultez la documentation de la classe de base [CRBTree](../../atl/reference/crbtree-class.md) pour plus d’informations sur les méthodes disponibles.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Utilities#82](../../atl/codesnippet/cpp/crbmap-class_2.cpp)]  
  
##  <a name="removekey"></a>CRBMap::RemoveKey  
 Appelez cette méthode pour supprimer un élément à partir de la `CRBMap` objet, en fonction de la clé.  
  
```
bool RemoveKey(KINARGTYPE key) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `key`  
 La clé correspondant à la paire de l’élément que vous souhaitez supprimer.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur true si la clé est trouvée et supprimée, false en cas d’échec.  
  
### <a name="remarks"></a>Notes  
 Consultez la documentation de la classe de base [CRBTree](../../atl/reference/crbtree-class.md) pour plus d’informations sur les méthodes disponibles.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Utilities#83](../../atl/codesnippet/cpp/crbmap-class_3.cpp)]  
  
##  <a name="setat"></a>CRBMap::SetAt  
 Appelez cette méthode pour insérer une paire de l’élément dans le mappage.  
  
```
POSITION SetAt(
    KINARGTYPE key,
    VINARGTYPE value) throw(...);
```  
  
### <a name="parameters"></a>Paramètres  
 `key`  
 La valeur de clé à ajouter à la `CRBMap` objet.  
  
 *valeur*  
 La valeur à ajouter à la `CRBMap` objet.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la position de la paire d’élément clé/valeur dans la `CRBMap` objet.  
  
### <a name="remarks"></a>Notes  
 `SetAt`remplace un élément existant si une clé est trouvée. Si la clé est introuvable, une nouvelle paire clé/valeur est créée.  
  
 Consultez la documentation de la classe de base [CRBTree](../../atl/reference/crbtree-class.md) pour plus d’informations sur les méthodes disponibles.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Utilities#84](../../atl/codesnippet/cpp/crbmap-class_4.cpp)]  
  
## <a name="see-also"></a>Voir aussi  
 [Classe de CRBTree](../../atl/reference/crbtree-class.md)   
 [Classe de CAtlMap](../../atl/reference/catlmap-class.md)   
 [Classe de CRBMultiMap](../../atl/reference/crbmultimap-class.md)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
