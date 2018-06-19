---
title: Classe de CComQIPtr | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComQIPtr
- ATLCOMCLI/ATL::CComQIPtr
- ATLCOMCLI/ATL::CComQIPtr::CComQIPtr
dev_langs:
- C++
helpviewer_keywords:
- CComQIPtr class
ms.assetid: 969cacb5-05b6-4af4-b683-24911d70242d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 66c6cc1484ef84ce53ffaf5529575eea43431869
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32359177"
---
# <a name="ccomqiptr-class"></a>Classe de CComQIPtr
Une classe de pointeur intelligent pour la gestion des pointeurs d’interface COM.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class T, const IID* piid= &__uuidof(T)>  
class CComQIPtr: public CComPtr<T>
```  
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 Une interface COM en spécifiant le type de pointeur à stocker.  
  
 `piid`  
 Un pointeur vers l’IID de `T`.  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CComQIPtr::CComQIPtr](#ccomqiptr)|Constructeur.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CComQIPtr::operator =](#operator_eq)|Assigne un pointeur vers le pointeur de membre.|  
  
## <a name="remarks"></a>Notes  
 ATL utilise `CComQIPtr` et [CComPtr](../../atl/reference/ccomptr-class.md) pour gérer les pointeurs d’interface COM, qui dérivent de [CComPtrBase](../../atl/reference/ccomptrbase-class.md). Les deux classes d’effectuent le décompte automatique via des appels de `AddRef` et **version**. Les opérateurs surchargés traiter les opérations de pointeur.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CComPtrBase](../../atl/reference/ccomptrbase-class.md)  
  
 [CComPtr](../../atl/reference/ccomptr-class.md)  
  
 `CComQIPtr`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlcomcli.h  
  
##  <a name="ccomqiptr"></a>  CComQIPtr::CComQIPtr  
 Constructeur.  
  
```
CComQIPtr() throw();
CComQIPtr(T* lp) throw();
CComQIPtr(IUnknown* lp) throw();
CComQIPtr(const CComQIPtr<T, piid>& lp) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `lp`  
 Utilisé pour initialiser le pointeur d’interface.  
  
 `T`  
 Une interface COM.  
  
 `piid`  
 Un pointeur vers l’IID de `T`.  
  
##  <a name="operator_eq"></a>  CComQIPtr::operator =  
 L’opérateur d’assignation.  
  
```
T* operator= (T* lp) throw();
T* operator= (const CComQIPtr<T, piid>& lp) throw();
T* operator= (IUnknown* lp) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `lp`  
 Utilisé pour initialiser le pointeur d’interface.  
  
 `T`  
 Une interface COM.  
  
 `piid`  
 Un pointeur vers l’IID de `T`.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne un pointeur vers la mise à jour `CComQIPtr` objet.  
  
## <a name="see-also"></a>Voir aussi  
 [CComPtr::CComPtr](../../atl/reference/ccomptr-class.md#ccomptr)   
 [CComQIPtr::CComQIPtr](#ccomqiptr)   
 [Classe de CComPtrBase](../../atl/reference/ccomptrbase-class.md)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)   
 [CComQIPtrElementTraits, classe](../../atl/reference/ccomqiptrelementtraits-class.md)
