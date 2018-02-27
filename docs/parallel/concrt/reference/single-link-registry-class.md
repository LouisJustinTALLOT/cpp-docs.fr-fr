---
title: single_link_registry, classe | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- single_link_registry
- AGENTS/concurrency::single_link_registry
- AGENTS/concurrency::single_link_registry::single_link_registry
- AGENTS/concurrency::single_link_registry::add
- AGENTS/concurrency::single_link_registry::begin
- AGENTS/concurrency::single_link_registry::contains
- AGENTS/concurrency::single_link_registry::count
- AGENTS/concurrency::single_link_registry::remove
dev_langs:
- C++
helpviewer_keywords:
- single_link_registry class
ms.assetid: 09540a4e-c34e-4ff9-af49-21b8612b6ab3
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 74167dcc03754c7f25d83058ec814798d40931a2
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/23/2018
---
# <a name="singlelinkregistry-class"></a>single_link_registry, classe
L'objet `single_link_registry` est un `network_link_registry` qui gère uniquement un seul bloc source ou cible.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class _Block>
class single_link_registry : public network_link_registry<_Block>;
```  
  
#### <a name="parameters"></a>Paramètres  
 `_Block`  
 Le bloc type de données sont stockées dans le `single_link_registry` objet.  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[single_link_registry](#ctor)|Construit un objet `single_link_registry`.|  
|[~single_link_registry Destructor](#dtor)|Détruit le `single_link_registry` objet.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[add](#add)|Ajoute un lien vers le `single_link_registry` objet. (Overrides [network_link_registry::add](network-link-registry-class.md#add).)|  
|[begin](#begin)|Retourne un itérateur au premier élément dans le `single_link_registry` objet. (Overrides [network_link_registry::begin](network-link-registry-class.md#begin).)|  
|[contains](#contains)|Recherche le `single_link_registry` objet pour un bloc spécifié. (Substitue [network_link_registry::contains](network-link-registry-class.md#contains).)|  
|[count](#count)|Compte le nombre d’éléments dans le `single_link_registry` objet. (Overrides [network_link_registry::count](network-link-registry-class.md#count).)|  
|[remove](#remove)|Supprime un lien à partir de la `single_link_registry` objet. (Overrides [network_link_registry::remove](network-link-registry-class.md#remove).)|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [network_link_registry](network-link-registry-class.md)  
  
 `single_link_registry`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** agents.h  
  
 **Espace de noms :** concurrency  
  
##  <a name="add"></a> Ajouter 

 Ajoute un lien vers le `single_link_registry` objet.  
  
```
virtual void add(_EType _Link);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Link`  
 Pointeur vers un bloc à ajouter.  
  
### <a name="remarks"></a>Notes  
 La méthode lève un [invalid_link_target](invalid-link-target-class.md) exception s’il existe déjà un lien dans ce Registre.  
  
##  <a name="begin"></a> Commencer 

 Retourne un itérateur au premier élément dans le `single_link_registry` objet.  
  
```
virtual iterator begin();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un itérateur qui traite le premier élément dans le `single_link_registry` objet.  
  
### <a name="remarks"></a>Notes  
 L’état de fin est indiqué par un `NULL` lien.  
  
##  <a name="contains"></a> contient 

 Recherche le `single_link_registry` objet pour un bloc spécifié.  
  
```
virtual bool contains(_EType _Link);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Link`  
 Un pointeur vers un bloc qui consiste à rechercher dans le `single_link_registry` objet.  
  
### <a name="return-value"></a>Valeur de retour  
 `true` Si le lien a été trouvé, `false` dans le cas contraire.  
  
##  <a name="count"></a> Nombre 

 Compte le nombre d’éléments dans le `single_link_registry` objet.  
  
```
virtual size_t count();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre d’éléments dans le `single_link_registry` objet.  
  
##  <a name="remove"></a> Supprimer 

 Supprime un lien à partir de la `single_link_registry` objet.  
  
```
virtual bool remove(_EType _Link);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Link`  
 Un pointeur vers un bloc doit être supprimée, si trouvée.  
  
### <a name="return-value"></a>Valeur de retour  
 `true` Si le lien a été trouvé et supprimé, `false` dans le cas contraire.  
  
##  <a name="ctor"></a> single_link_registry 

 Construit un objet `single_link_registry`.  
  
```
single_link_registry();
```  
  
##  <a name="dtor"></a> ~single_link_registry 

 Détruit le `single_link_registry` objet.  
  
```
virtual ~single_link_registry();
```  
  
### <a name="remarks"></a>Notes  
 La méthode lève un [invalid_operation](invalid-operation-class.md) exception si elle est appelée avant que le lien est supprimé.  
  
## <a name="see-also"></a>Voir aussi  
 [accès concurrentiel Namespace](concurrency-namespace.md)   
 [multi_link_registry, classe](multi-link-registry-class.md)
