---
title: Cautovectorptr, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAutoVectorPtr
- ATLBASE/ATL::CAutoVectorPtr
- ATLBASE/ATL::CAutoVectorPtr::CAutoVectorPtr
- ATLBASE/ATL::CAutoVectorPtr::Allocate
- ATLBASE/ATL::CAutoVectorPtr::Attach
- ATLBASE/ATL::CAutoVectorPtr::Detach
- ATLBASE/ATL::CAutoVectorPtr::Free
- ATLBASE/ATL::CAutoVectorPtr::m_p
dev_langs:
- C++
helpviewer_keywords:
- CAutoVectorPtr class
ms.assetid: 0030362b-6bc4-4a47-9b5b-3c3899dceab4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 520e23432ee4691a5018221aa3a8d44553875f80
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37882073"
---
# <a name="cautovectorptr-class"></a>Cautovectorptr, classe
Cette classe représente un objet pointeur intelligent à l’aide de vecteur nouveaux et supprimer des opérateurs.  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<typename T>  
class CAutoVectorPtr
```  
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 Le type de pointeur.  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CAutoVectorPtr::CAutoVectorPtr](#cautovectorptr)|Constructeur.|  
|[CAutoVectorPtr :: ~ CAutoVectorPtr](#dtor)|Destructeur.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CAutoVectorPtr::Allocate](#allocate)|Appelez cette méthode pour allouer la mémoire requise par le tableau d’objets vers lequel pointé `CAutoVectorPtr`.|  
|[CAutoVectorPtr::Attach](#attach)|Appelez cette méthode pour prendre possession d’un pointeur existant.|  
|[CAutoVectorPtr::Detach](#detach)|Appelez cette méthode pour libérer la possession d’un pointeur.|  
|[CAutoVectorPtr::Free](#free)|Appelez cette méthode pour supprimer un objet vers lequel pointé un `CAutoVectorPtr`.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CAutoVectorPtr::operator T *](#operator_t__star)|L’opérateur de cast.|  
|[CAutoVectorPtr::operator =](#operator_eq)|L’opérateur d’assignation.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CAutoVectorPtr::m_p](#m_p)|La variable de membre de données de pointeur.|  
  
## <a name="remarks"></a>Notes  
 Cette classe fournit des méthodes pour créer et gérer un pointeur intelligent, ce qui permet de se protéger contre les fuites de mémoire en libérant les ressources d’automatiquement lorsqu’elle se trouve hors de portée. `CAutoVectorPtr` est similaire à `CAutoPtr`, la seule différence étant que `CAutoVectorPtr` utilise [new (vecteur)&#91; &#93; ](../../standard-library/new-operators.md#op_new_arr) et [vecteur delete&#91; &#93; ](../../standard-library/new-operators.md#op_delete_arr) pour allouer et libérer de la mémoire au lieu du C++ **nouveau** et **supprimer** opérateurs. Consultez [CAutoVectorPtrElementTraits](../../atl/reference/cautovectorptrelementtraits-class.md) si les classes de collection de `CAutoVectorPtr` sont requis.  

  
 Consultez [CAutoPtr](../../atl/reference/cautoptr-class.md) pour obtenir un exemple d’utilisation d’une classe de pointeur intelligent.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** atlbase.h  
  
##  <a name="allocate"></a>  CAutoVectorPtr::Allocate  
 Appelez cette méthode pour allouer la mémoire requise par le tableau d’objets vers lequel pointé `CAutoVectorPtr`.  
  
```
bool Allocate(size_t nElements) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 *nElements*  
 Nombre d’éléments dans le tableau.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur true si la mémoire est correctement alloué, false en cas d’échec.  
  
### <a name="remarks"></a>Notes  
 Dans les versions debug, un échec d’assertion se produit si le [CAutoVectorPtr::m_p](#m_p) variable membre pointe actuellement vers une valeur existante ; autrement dit, il n’est pas égal à NULL.  
  
##  <a name="attach"></a>  CAutoVectorPtr::Attach  
 Appelez cette méthode pour prendre possession d’un pointeur existant.  
  
```
void Attach(T* p) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 *p*  
 Le `CAutoVectorPtr` objet prendra possession de ce pointeur.  
  
### <a name="remarks"></a>Notes  
 Quand un `CAutoVectorPtr` objet prend possession d’un pointeur, il supprime automatiquement le pointeur et les données allouées lorsqu’il devient hors de portée. Si [CAutoVectorPtr::Detach](#detach) est appelée, le programmeur à nouveau compte tenu de la responsabilité de libérer les ressources est alloué.  
  
 Dans les versions debug, un échec d’assertion se produit si le [CAutoVectorPtr::m_p](#m_p) variable membre pointe actuellement vers une valeur existante ; autrement dit, il n’est pas égal à NULL.  
  
##  <a name="cautovectorptr"></a>  CAutoVectorPtr::CAutoVectorPtr  
 Constructeur.  
  
```
CAutoVectorPtr() throw();
explicit CAutoVectorPtr(T* p) throw();
CAutoVectorPtr(CAutoVectorPtr<T>& p) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 *p*  
 Un pointeur existant.  
  
### <a name="remarks"></a>Notes  
 Le `CAutoVectorPtr` objet peut être créé à l’aide d’un pointeur existant, auquel cas il transfère la propriété du pointeur.  
  
##  <a name="dtor"></a>  CAutoVectorPtr :: ~ CAutoVectorPtr  
 Destructeur.  
  
```
~CAutoVectorPtr() throw();
```  
  
### <a name="remarks"></a>Notes  
 Libère toutes les ressources allouées. Appels [CAutoVectorPtr::Free](#free).  
  
##  <a name="detach"></a>  CAutoVectorPtr::Detach  
 Appelez cette méthode pour libérer la possession d’un pointeur.  
  
```
T* Detach() throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne une copie du pointeur.  
  
### <a name="remarks"></a>Notes  
 Libère la propriété d’un pointeur, définit le [CAutoVectorPtr::m_p](#m_p) variable de membre avec la valeur NULL et retourne une copie du pointeur. Après avoir appelé `Detach`, il jusqu'à le programmeur pour libérer les ressources est allouée sur laquelle le `CAutoVectorPtr` objet peut avoir précédemment la responsabilité.  
  
##  <a name="free"></a>  CAutoVectorPtr::Free  
 Appelez cette méthode pour supprimer un objet vers lequel pointé un `CAutoVectorPtr`.  
  
```
void Free() throw();
```  
  
### <a name="remarks"></a>Notes  
 L’objet vers lequel pointe le `CAutoVectorPtr` est libéré et la [CAutoVectorPtr::m_p](#m_p) variable membre est définie sur NULL.  
  
##  <a name="m_p"></a>  CAutoVectorPtr::m_p  
 La variable de membre de données de pointeur.  
  
```
T* m_p;
```  
  
### <a name="remarks"></a>Notes  
 Cette variable membre conserve les informations de pointeur.  
  
##  <a name="operator_eq"></a>  CAutoVectorPtr::operator =  
 L’opérateur d’assignation.  
  
```
CAutoVectorPtr<T>& operator= (CAutoVectorPtr<T>& p) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 *p*  
 Un pointeur.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne une référence à un **CAutoVectorPtr\< T >**.  
  
### <a name="remarks"></a>Notes  
 L’opérateur d’assignation détache le `CAutoVectorPtr` objet à partir de n’importe quel pointeur actuel et attache le nouveau pointeur, *p*, à la place.  
  
##  <a name="operator_t__star"></a>  CAutoVectorPtr::operator T *  
 L’opérateur de cast.  
  
```  
operator T*() const throw();
```  
  
### <a name="remarks"></a>Notes  
 Retourne un pointeur vers le type de données d’objet défini dans le modèle de classe.  
  
## <a name="see-also"></a>Voir aussi  
 [Cautoptr, classe](../../atl/reference/cautoptr-class.md)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
