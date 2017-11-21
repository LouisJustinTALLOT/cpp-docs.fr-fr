---
title: source_link_manager, classe | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- source_link_manager
- AGENTS/concurrency::source_link_manager
- AGENTS/concurrency::source_link_manager::source_link_manager
- AGENTS/concurrency::source_link_manager::add
- AGENTS/concurrency::source_link_manager::begin
- AGENTS/concurrency::source_link_manager::contains
- AGENTS/concurrency::source_link_manager::count
- AGENTS/concurrency::source_link_manager::reference
- AGENTS/concurrency::source_link_manager::register_target_block
- AGENTS/concurrency::source_link_manager::release
- AGENTS/concurrency::source_link_manager::remove
- AGENTS/concurrency::source_link_manager::set_bound
dev_langs: C++
helpviewer_keywords: source_link_manager class
ms.assetid: 287487cf-e0fe-4c35-aa3c-24f081d1ddae
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 75be5687e63fe38f1ffa8f91c41963dfa1171e48
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="sourcelinkmanager-class"></a>source_link_manager, classe
L'objet `source_link_manager` gère les liens réseau des blocs de messagerie avec les blocs `ISource`.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class _LinkRegistry>
class source_link_manager;
```  
  
#### <a name="parameters"></a>Paramètres  
 `_LinkRegistry`  
 Registre de liens réseau.  
  
## <a name="members"></a>Membres  
  
### <a name="public-typedefs"></a>Typedefs publics  
  
|Nom|Description|  
|----------|-----------------|  
|`const_pointer`|Type qui fournit un pointeur vers un `const` élément dans un `source_link_manager` objet.|  
|`const_reference`|Type qui fournit une référence à un `const` élément stocké dans un `source_link_manager` objet pour la lecture et exécution d’opérations const.|  
|`iterator`|Un type qui fournit un itérateur qui peut lire ou modifier tout élément dans le `source_link_manager` objet.|  
|`type`|Le type de Registre de liens qui est géré par le `source_link_manager` objet.|  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[source_link_manager](#ctor)|Construit un objet `source_link_manager`.|  
|[~ source_link_manager, destructeur](#dtor)|Détruit le `source_link_manager` objet.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[add](#add)|Ajoute un lien de la source à la `source_link_manager` objet.|  
|[begin](#begin)|Retourne un itérateur au premier élément dans le `source_link_manager` objet.|  
|[contient](#contains)|Recherche le `network_link_registry` dans cette `source_link_manager` objet pour un bloc spécifié.|  
|[count](#count)|Compte le nombre de blocs liés dans le `source_link_manager` objet.|  
|[reference](#reference)|Acquiert une référence sur le `source_link_manager` objet.|  
|[register_target_block](#register_target_block)|Inscrit le bloc cible qui conserve ce `source_link_manager` objet.|  
|[release](#release)|Libère la référence sur le `source_link_manager` objet.|  
|[remove](#remove)|Supprime un lien à partir de la `source_link_manager` objet.|  
|[set_bound](#set_bound)|Définit le nombre maximal de liens source qui peuvent être ajoutés à ce `source_link_manager` objet.|  
  
## <a name="remarks"></a>Remarques  
 Actuellement, les blocs de code source ont un décompte. Il s’agit d’un wrapper un `network_link_registry` objet qui permet l’accès simultané aux liens et offre la possibilité de référencer les liens via des rappels. Blocs de messages ( `target_block`s ou `propagator_block`s) doivent utiliser cette classe pour leurs liens source.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `source_link_manager`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** agents.h  
  
 **Espace de noms :** concurrency  
  
##  <a name="add"></a>ajouter 

 Ajoute un lien de la source à la `source_link_manager` objet.  
  
```
void add(_EType _Link);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Link`  
 Pointeur vers un bloc à ajouter.  
  
##  <a name="begin"></a>commencer 

 Retourne un itérateur au premier élément dans le `source_link_manager` objet.  
  
```
iterator begin();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un itérateur qui traite le premier élément dans le `source_link_manager` objet.  
  
### <a name="remarks"></a>Remarques  
 L’état final de l’itérateur est indiqué par un `NULL` lien.  
  
##  <a name="contains"></a>contient 

 Recherche le `network_link_registry` dans cette `source_link_manager` objet pour un bloc spécifié.  
  
```
bool contains(_EType _Link);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Link`  
 Un pointeur vers un bloc qui consiste à rechercher dans le `source_link_manager` objet.  
  
### <a name="return-value"></a>Valeur de retour  
 `true`Si le bloc spécifié a été trouvé, `false` dans le cas contraire.  
  
##  <a name="count"></a>nombre 

 Compte le nombre de blocs liés dans le `source_link_manager` objet.  
  
```
size_t count();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre de blocs liés dans le `source_link_manager` objet.  
  
##  <a name="reference"></a>référence 

 Acquiert une référence sur le `source_link_manager` objet.  
  
```
void reference();
```  
  
##  <a name="register_target_block"></a>register_target_block 

 Inscrit le bloc cible qui conserve ce `source_link_manager` objet.  
  
```
void register_target_block(_Inout_ ITarget<typename _Block::source_type>* _PTarget);
```  
  
### <a name="parameters"></a>Paramètres  
 `_PTarget`  
 Le bloc cible contenant cet `source_link_manager` objet.  
  
##  <a name="release"></a>mise en production 

 Libère la référence sur le `source_link_manager` objet.  
  
```
void release();
```  
  
##  <a name="remove"></a>supprimer 

 Supprime un lien à partir de la `source_link_manager` objet.  
  
```
bool remove(_EType _Link);
```  
  
### <a name="parameters"></a>Paramètres  
 `_Link`  
 Un pointeur vers un bloc doit être supprimée, si trouvée.  
  
### <a name="return-value"></a>Valeur de retour  
 `true`Si le lien a été trouvé et supprimé, `false` dans le cas contraire.  
  
##  <a name="set_bound"></a>set_bound 

 Définit le nombre maximal de liens source qui peuvent être ajoutés à ce `source_link_manager` objet.  
  
```
void set_bound(size_t _MaxLinks);
```  
  
### <a name="parameters"></a>Paramètres  
 `_MaxLinks`  
 Le nombre maximal de liens.  
  
##  <a name="ctor"></a>source_link_manager 

 Construit un objet `source_link_manager`.  
  
```
source_link_manager();
```  
  
##  <a name="dtor"></a>~ source_link_manager 

 Détruit le `source_link_manager` objet.  
  
```
~source_link_manager();
```  
  
## <a name="see-also"></a>Voir aussi  
 [accès concurrentiel Namespace](concurrency-namespace.md)   
 [single_link_registry, classe](single-link-registry-class.md)   
 [multi_link_registry, classe](multi-link-registry-class.md)
