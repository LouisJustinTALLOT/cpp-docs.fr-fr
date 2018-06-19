---
title: Classe de CComTearOffObject | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComTearOffObject
- ATLCOM/ATL::CComTearOffObject
- ATLCOM/ATL::CComTearOffObject::CComTearOffObject
- ATLCOM/ATL::CComTearOffObject::AddRef
- ATLCOM/ATL::CComTearOffObject::QueryInterface
- ATLCOM/ATL::CComTearOffObject::Release
- ATLCOM/ATL::CComTearOffObjectBase
- ATLCOM/ATL::m_pOwner
dev_langs:
- C++
helpviewer_keywords:
- tear-off interfaces, ATL
- tear-off interfaces
- CComTearOffObject class
ms.assetid: d974b598-c6b2-42b1-8360-9190d9d0fbf3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: be47c9525098cb3bd444cefff39dbbf25b88d396
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32364987"
---
# <a name="ccomtearoffobject-class"></a>Classe de CComTearOffObject
Cette classe implémente une interface détachable.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class Base>
class CComTearOffObject : public Base
```  
  
#### <a name="parameters"></a>Paramètres  
 `Base`  
 Votre classe détachables, dérivée de `CComTearOffObjectBase` et les interfaces pour que votre objet détachable pour prendre en charge.  
  
 ATL implémente ses interfaces détachables en deux phases : la `CComTearOffObjectBase` méthodes gèrent le décompte de références et `QueryInterface`, tandis que `CComTearOffObject` implémente [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509).  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CComTearOffObject::CComTearOffObject](#ccomtearoffobject)|Constructeur.|  
|[CComTearOffObject :: ~ CComTearOffObject](#dtor)|Destructeur.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CComTearOffObject::AddRef](#addref)|Incrémente le décompte de références pour un `CComTearOffObject` objet.|  
|[CComTearOffObject::QueryInterface](#queryinterface)|Retourne un pointeur vers l’interface demandée sur votre classe détachable ou de la classe propriétaire.|  
|[CComTearOffObject::Release](#release)|Décrémente le décompte de références pour un `CComTearOffObject` de l’objet et détruit.|  
  
### <a name="ccomtearoffobjectbase-methods"></a>Méthodes CComTearOffObjectBase  
  
|||  
|-|-|  
|[CComTearOffObjectBase](#ccomtearoffobjectbase)|Constructeur.|  
  
### <a name="ccomtearoffobjectbase-data-members"></a>Membres de données de CComTearOffObjectBase  
  
|||  
|-|-|  
|[m_pOwner](#m_powner)|Un pointeur vers un `CComObject` dérivée de la classe propriétaire.|  
  
## <a name="remarks"></a>Notes  
 `CComTearOffObject` implémente une interface détachable comme un objet distinct est instancié uniquement lorsque vous interrogez pour cette interface. Le détachable est supprimé lorsque son décompte de références devient égal à zéro. En règle générale, vous générez une interface détachable pour une interface qui est rarement utilisée, car à l’aide un détachable enregistre un pointeur vtable dans toutes les instances de votre objet principal.  
  
 Vous devez dériver la classe qui implémente le détachable de `CComTearOffObjectBase` et à partir de quelle que soit l’interfaces votre objet détachable pour prendre en charge. `CComTearOffObjectBase` transformer en modèle sur la classe propriétaire et le modèle de thread. La classe propriétaire est la classe de l’objet pour lequel un détachable est implémentée. Si vous ne spécifiez pas un modèle de thread, le modèle de thread par défaut est utilisé.  
  
 Vous devez créer un mappage COM pour votre classe détachable. Lorsque ATL instancie le détachable, il créera **CComTearOffObject\<CYourTearOffClass >** ou **CComCachedTearOffObject\<CYourTearOffClass >**.  
  
 Par exemple, dans l’exemple BEEPER, le `CBeeper2` est la classe détachable et `CBeeper` est le propriétaire de la classe :  
  
 [!code-cpp[NVC_ATL_COM#43](../../atl/codesnippet/cpp/ccomtearoffobject-class_1.h)]  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `Base`  
  
 `CComTearOffObject`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlcom.h  
  
##  <a name="addref"></a>  CComTearOffObject::AddRef  
 Incrémente le décompte de références de le `CComTearOffObject` l’objet d’une unité.  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur qui peut être utile pour les tests de diagnostic et de test.  
  
##  <a name="ccomtearoffobject"></a>  CComTearOffObject::CComTearOffObject  
 Constructeur.  
  
```
CComTearOffObject(void* pv);
```  
  
### <a name="parameters"></a>Paramètres  
 `pv`  
 [in] Pointeur qui sera converti en un pointeur vers un **CComObject\<propriétaire >** objet.  
  
### <a name="remarks"></a>Notes  
 Incrémente le décompte de références du propriétaire d’une unité.  
  
##  <a name="dtor"></a>  CComTearOffObject :: ~ CComTearOffObject  
 Destructeur.  
  
```
~CComTearOffObject();
```  
  
### <a name="remarks"></a>Notes  
 Libère toutes les ressources attribuées, les appels FinalRelease et décrémente le module de verrouillage de compte.  
  
##  <a name="ccomtearoffobjectbase"></a>  CComTearOffObject::CComTearOffObjectBase  
 Constructeur.  
  
```
CComTearOffObjectBase();
```  
  
### <a name="remarks"></a>Notes  
 Initialise le [m_pOwner](#m_powner) membre **NULL**.  
  
##  <a name="m_powner"></a>  CComTearOffObject::m_pOwner  
 Un pointeur vers un [CComObject](../../atl/reference/ccomobject-class.md) objet dérivé *propriétaire*.  
  
```
CComObject<Owner>* m_pOwner;
```  
  
### <a name="parameters"></a>Paramètres  
 *Propriétaire*  
 [in] La classe pour laquelle un détachable est implémentée.  
  
### <a name="remarks"></a>Notes  
 Le pointeur est initialisé à **NULL** pendant la construction.  
  
##  <a name="queryinterface"></a>  CComTearOffObject::QueryInterface  
 Récupère un pointeur vers l'interface demandée.  
  
```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```  
  
### <a name="parameters"></a>Paramètres  
 `iid`  
 [in] IID de l’interface demandée.  
  
 `ppvObject`  
 [out] Un pointeur vers le pointeur d’interface identifié par `iid`, ou **NULL** si l’interface est introuvable.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur `HRESULT` standard.  
  
### <a name="remarks"></a>Notes  
 Recherche tout d’abord les interfaces sur votre classe détachable. Si l’interface n’est pas, les requêtes pour l’interface sur l’objet propriétaire. Si l’interface demandée est **IUnknown**, retourne le **IUnknown** du propriétaire.  
  
##  <a name="release"></a>  CComTearOffObject::Release  
 Décrémente le décompte de références d’une unité et, si le décompte de références est égal à zéro, supprime la `CComTearOffObject`.  
  
```
STDMETHOD_ULONG Release();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Dans les versions non debug, retourne toujours zéro. Dans les versions debug, retourne une valeur qui peut être utile pour les tests de diagnostic ou de test.  
  
## <a name="see-also"></a>Voir aussi  
 [Classe de CComCachedTearOffObject](../../atl/reference/ccomcachedtearoffobject-class.md)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
