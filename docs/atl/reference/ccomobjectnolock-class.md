---
title: Classe de CComObjectNoLock | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComObjectNoLock
- ATLCOM/ATL::CComObjectNoLock
- ATLCOM/ATL::CComObjectNoLock::CComObjectNoLock
- ATLCOM/ATL::CComObjectNoLock::AddRef
- ATLCOM/ATL::CComObjectNoLock::QueryInterface
- ATLCOM/ATL::CComObjectNoLock::Release
dev_langs:
- C++
helpviewer_keywords:
- CComObjectNoLock class
ms.assetid: 288c6506-7da8-4127-8d58-7f4bd779539a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cd7f9fa0ac67592c5fca805eaa4bb4ec4b0ca153
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32361473"
---
# <a name="ccomobjectnolock-class"></a>Classe de CComObjectNoLock
Cette classe implémente **IUnknown** pour un objet brutes et non agrégée, mais ne pas les incrément le module nombre de verrous dans le constructeur.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class Base>  
class CComObjectNoLock : public Base
```  
  
#### <a name="parameters"></a>Paramètres  
 `Base`  
 Votre classe, dérivée de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) ou [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), ainsi que de toute autre interface souhaitées prendre en charge sur l’objet.  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CComObjectNoLock::CComObjectNoLock](#ccomobjectnolock)|Constructeur.|  
|[CComObjectNoLock::~CComObjectNoLock](#dtor)|Destructeur.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CComObjectNoLock::AddRef](#addref)|Incrémente le décompte de références sur l’objet.|  
|[CComObjectNoLock::QueryInterface](#queryinterface)|Retourne un pointeur vers l’interface demandée.|  
|[CComObjectNoLock::Release](#release)|Décrémente le décompte de références sur l’objet.|  
  
## <a name="remarks"></a>Notes  
 `CComObjectNoLock` est semblable à [CComObject](../../atl/reference/ccomobject-class.md) dans la mesure où il implémente [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) pour un objet brutes et non agrégée ; Toutefois, `CComObjectNoLock` ne pas incrémenter le verrou du module compte dans le constructeur.  
  
 ATL utilise `CComObjectNoLock` en interne pour les fabriques de classes. En règle générale, vous ne serez pas utiliser cette classe directement.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `Base`  
  
 `CComObjectNoLock`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlcom.h  
  
##  <a name="addref"></a>  CComObjectNoLock::AddRef  
 Incrémente le décompte de références sur l’objet.  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur qui peut être utile pour les tests de diagnostic ou de test.  
  
##  <a name="ccomobjectnolock"></a>  CComObjectNoLock::CComObjectNoLock  
 Constructeur. Contrairement aux [CComObject](../../atl/reference/ccomobject-class.md), n’incrémente pas le nombre de verrous du module.  
  
```
CComObjectNoLock(void* = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 **void\***  
 [in] Ce paramètre sans nom n’est pas utilisé. Il existe pour une symétrie avec d’autres **CCom***XXX*`Object`*XXX* constructeurs.  
  
##  <a name="dtor"></a>  CComObjectNoLock::~CComObjectNoLock  
 Destructeur.  
  
```
~CComObjectNoLock();
```  
  
### <a name="remarks"></a>Notes  
 Libère toutes les ressources attribuées et les appels [FinalRelease](ccomobjectrootex-class.md#finalrelease).  

  
##  <a name="queryinterface"></a>  CComObjectNoLock::QueryInterface  
 Récupère un pointeur vers l'interface demandée.  
  
```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```  
  
### <a name="parameters"></a>Paramètres  
 `iid`  
 [in] Identificateur de l’interface demandée.  
  
 `ppvObject`  
 [out] Un pointeur vers le pointeur d’interface identifié par `iid`. Si l’objet ne prend pas en charge cette interface, `ppvObject` a la valeur **NULL**.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur `HRESULT` standard.  
  
##  <a name="release"></a>  CComObjectNoLock::Release  
 Décrémente le décompte de références sur l’objet.  
  
```
STDMETHOD_(ULONG, Release)();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Dans les versions debug, **version** retourne une valeur qui peut être utile pour les tests de diagnostic ou de test. Dans les versions non debug, **version** retourne toujours 0.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
