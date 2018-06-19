---
title: network_link_registry, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- network_link_registry
- AGENTS/concurrency::network_link_registry
- AGENTS/concurrency::network_link_registry::add
- AGENTS/concurrency::network_link_registry::begin
- AGENTS/concurrency::network_link_registry::contains
- AGENTS/concurrency::network_link_registry::count
- AGENTS/concurrency::network_link_registry::remove
dev_langs:
- C++
helpviewer_keywords:
- network_link_registry class
ms.assetid: 3e7b4097-09f1-4252-964e-b15b8f7f7fc6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dab0ad6aff391eb89ac59198fb8c173ecb362bbd
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33688295"
---
# <a name="networklinkregistry-class"></a>network_link_registry, classe
La classe de base abstraite `network_link_registry` gère les liens entre les blocs sources et cibles.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class _Block>
class network_link_registry;
```  
  
#### <a name="parameters"></a>Paramètres  
 `_Block`  
 Le bloc type de données sont stockées dans le `network_link_registry`.  
  
## <a name="members"></a>Membres  
  
### <a name="public-typedefs"></a>Typedefs publics  
  
|Nom|Description|  
|----------|-----------------|  
|`const_pointer`|Type qui fournit un pointeur vers un `const` élément dans un `network_link_registry` objet.|  
|`const_reference`|Type qui fournit une référence à un `const` élément stocké dans un `network_link_registry` objet pour la lecture et exécution d’opérations const.|  
|`iterator`|Un type qui fournit un itérateur qui peut lire ou modifier tout élément dans un `network_link_registry` objet.|  
|`type`|Un type qui représente le type de bloc stocké dans le `network_link_registry` objet.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[add](#add)|En cas de substitution dans une classe dérivée, ajoute un lien vers le `network_link_registry` objet.|  
|[begin](#begin)|En cas de substitution dans une classe dérivée, retourne un itérateur au premier élément dans le `network_link_registry` objet.|  
|[contient](#contains)|En cas de substitution dans une classe dérivée, recherche la `network_link_registry` objet pour un bloc spécifié.|  
|[count](#count)|En cas de substitution dans une classe dérivée, retourne le nombre d’éléments dans le `network_link_registry` objet.|  
|[remove](#remove)|En cas de substitution dans une classe dérivée, supprime un bloc spécifié à partir de la `network_link_registry` objet.|  
  
## <a name="remarks"></a>Notes  
 Le `network link registry` n’est pas sécurisé pour l’accès simultané.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `network_link_registry`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** agents.h  
  
 **Espace de noms :** concurrency  
  
##  <a name="add"></a> Ajouter 

 En cas de substitution dans une classe dérivée, ajoute un lien vers le `network_link_registry` objet.  
  
```
virtual void add(_EType _Link) = 0;
```  
  
### <a name="parameters"></a>Paramètres  
 `_Link`  
 Pointeur vers un bloc à ajouter.  
  
##  <a name="begin"></a> Commencer 

 En cas de substitution dans une classe dérivée, retourne un itérateur au premier élément dans le `network_link_registry` objet.  
  
```
virtual iterator begin() = 0;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un itérateur qui traite le premier élément dans le `network_link_registry` objet.  
  
### <a name="remarks"></a>Notes  
 L’état final de l’itérateur est indiqué par un `NULL` lien.  
  
##  <a name="contains"></a> contient 

 En cas de substitution dans une classe dérivée, recherche la `network_link_registry` objet pour un bloc spécifié.  
  
```
virtual bool contains(_EType _Link) = 0;
```  
  
### <a name="parameters"></a>Paramètres  
 `_Link`  
 Un pointeur vers un bloc qui est recherché dans le `network_link_registry` objet.  
  
### <a name="return-value"></a>Valeur de retour  
 `true` Si le bloc a été trouvé, `false` dans le cas contraire.  
  
##  <a name="count"></a> Nombre 

 En cas de substitution dans une classe dérivée, retourne le nombre d’éléments dans le `network_link_registry` objet.  
  
```
virtual size_t count() = 0;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre d’éléments dans le `network_link_registry` objet.  
  
##  <a name="remove"></a> Supprimer 

 En cas de substitution dans une classe dérivée, supprime un bloc spécifié à partir de la `network_link_registry` objet.  
  
```
virtual bool remove(_EType _Link) = 0;
```  
  
### <a name="parameters"></a>Paramètres  
 `_Link`  
 Un pointeur vers un bloc doit être supprimée, si trouvée.  
  
### <a name="return-value"></a>Valeur de retour  
 `true` Si le lien a été trouvé et supprimé, `false` dans le cas contraire.  
  
## <a name="see-also"></a>Voir aussi  
 [accès concurrentiel Namespace](concurrency-namespace.md)   
 [single_link_registry, classe](single-link-registry-class.md)   
 [multi_link_registry, classe](multi-link-registry-class.md)
