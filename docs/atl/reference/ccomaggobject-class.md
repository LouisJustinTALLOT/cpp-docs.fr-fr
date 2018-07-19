---
title: CComAggObject, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComAggObject
- ATLCOM/ATL::CComAggObject
- ATLCOM/ATL::CComAggObject::CComAggObject
- ATLCOM/ATL::CComAggObject::AddRef
- ATLCOM/ATL::CComAggObject::CreateInstance
- ATLCOM/ATL::CComAggObject::FinalConstruct
- ATLCOM/ATL::CComAggObject::FinalRelease
- ATLCOM/ATL::CComAggObject::QueryInterface
- ATLCOM/ATL::CComAggObject::Release
- ATLCOM/ATL::CComAggObject::m_contained
dev_langs:
- C++
helpviewer_keywords:
- aggregate objects [C++], in ATL
- aggregation [C++], ATL objects
- CComAggObject class
ms.assetid: 7aa90d69-d399-477b-880d-e2cdf0ef7881
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5699f4c8c49bd35e85479572e1b49f8080415e65
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37884991"
---
# <a name="ccomaggobject-class"></a>CComAggObject, classe
Cette classe implémente le [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) interface pour un objet agrégé. Par définition, un objet est contenu dans un objet externe. Le `CComAggObject` classe est semblable à la [CComObject, classe](../../atl/reference/ccomobject-class.md), à ceci près qu’il expose une interface qui est directement accessible aux clients externes.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class contained>  
class CComAggObject : public IUnknown, 
   public CComObjectRootEx<contained::_ThreadModel::ThreadModelNoCS>
```  
  
#### <a name="parameters"></a>Paramètres  
 *contenu*  
 Votre classe, dérivée de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) ou [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), bien que toutes les autres interfaces souhaitées prendre en charge sur l’objet.  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CComAggObject::CComAggObject](#ccomaggobject)|Constructeur.|  
|[CComAggObject :: ~ CComAggObject](#dtor)|Destructeur.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CComAggObject::AddRef](#addref)|Incrémente le décompte de références sur l’objet agrégée.|  
|[CComAggObject::CreateInstance](#createinstance)|Cette fonction statique vous permet de créer un nouveau **CComAggObject <** `contained` **>** objet sans la surcharge de [CoCreateInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615).|  
|[CComAggObject::FinalConstruct](#finalconstruct)|Effectue l’initialisation finale de `m_contained`.|  
|[CComAggObject::FinalRelease](#finalrelease)|Effectue une destruction finale des `m_contained`.|  
|[CComAggObject::QueryInterface](#queryinterface)|Récupère un pointeur vers l'interface demandée.|  
|[CComAggObject::Release](#release)|Décrémente le décompte de références sur l’objet agrégée.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CComAggObject::m_contained](#m_contained)|Délégués `IUnknown` appels à inconnu externe.|  
  
## <a name="remarks"></a>Notes  
 `CComAggObject` implémente [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) pour un objet agrégé. `CComAggObject` possède son propre `IUnknown` interface, distinct de l’objet externe `IUnknown` interface et gère son propre nombre de références.  
  
 Pour plus d’informations sur l’agrégation, consultez l’article [principes de base des objets COM ATL](../../atl/fundamentals-of-atl-com-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `CComObjectRootBase`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 `IUnknown`  
  
 `CComAggObject`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** atlcom.h  
  
##  <a name="addref"></a>  CComAggObject::AddRef  
 Incrémente le décompte de références sur l’objet agrégée.  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur qui peut-être être utiles pour le diagnostic ou de test.  
  
##  <a name="ccomaggobject"></a>  CComAggObject::CComAggObject  
 Constructeur.  
  
```
CComAggObject(void* pv);
```  
  
### <a name="parameters"></a>Paramètres  
 *PV*  
 [in] Inconnu externe.  
  
### <a name="remarks"></a>Notes  
 Initialise le `CComContainedObject` membre, [m_contained](#m_contained)et incrémente le nombre de verrous du module.  
  
 Le destructeur décrémente le module nombre de verrous.  
  
##  <a name="dtor"></a>  CComAggObject :: ~ CComAggObject  
 Destructeur.  
  
```
~CComAggObject();
```  
  
### <a name="remarks"></a>Notes  
 Libère toutes les ressources allouées, appels [FinalRelease](#finalrelease), et décrémente le module nombre de verrous.  
  
##  <a name="createinstance"></a>  CComAggObject::CreateInstance  
 Cette fonction statique vous permet de créer un nouveau **CComAggObject <** `contained` **>** objet sans la surcharge de [CoCreateInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615).  
  
```
static HRESULT WINAPI CreateInstance(
    LPUNKNOWN pUnkOuter,
    CComAggObject<contained>** pp);
```  
  
### <a name="parameters"></a>Paramètres  
 *PP*  
 [out] Un pointeur vers un **CComAggObject\<*** contenus* **>** pointeur. Si `CreateInstance` échoue, *pp* est définie sur NULL.  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur HRESULT standard.  
  
### <a name="remarks"></a>Notes  
 L’objet retourné est un décompte de références de zéro, appelez `AddRef` immédiatement, utilisez `Release` pour libérer la référence sur le pointeur d’objet lorsque vous avez terminé.  
  
 Si vous ne pas nécessitant un accès direct à l’objet, mais que vous souhaitez toujours créer un nouvel objet sans la surcharge de `CoCreateInstance`, utilisez [CComCoClass::CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance) à la place.  
  
##  <a name="finalconstruct"></a>  CComAggObject::FinalConstruct  
 Appelée au cours des dernières étapes de la construction d’objet, cette méthode exécute toute initialisation finale sur le [m_contained](#m_contained) membre.  
  
```
HRESULT FinalConstruct();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur HRESULT standard.  
  
##  <a name="finalrelease"></a>  CComAggObject::FinalRelease  
 Appelé lors de la destruction d’objets, cette méthode libère le [m_contained](#m_contained) membre.  
  
```
void FinalRelease();
```  
  
##  <a name="m_contained"></a>  CComAggObject::m_contained  
 Un [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) objet dérivé de votre classe.  
  
```
CComContainedObject<contained> m_contained;
```  
  
### <a name="parameters"></a>Paramètres  
 *contenu*  
 [in] Votre classe, dérivée de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) ou [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), bien que toutes les autres interfaces souhaitées prendre en charge sur l’objet.  
  
### <a name="remarks"></a>Notes  
 Tous les `IUnknown` appelle via `m_contained` sont déléguées à inconnu externe.  
  
##  <a name="queryinterface"></a>  CComAggObject::QueryInterface  
 Récupère un pointeur vers l'interface demandée.  
  
```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
template <class Q>
HRESULT STDMETHODCALLTYPE QueryInterface(Q** pp);
```  
  
### <a name="parameters"></a>Paramètres  
 *IID*  
 [in] L’identificateur de l’interface demandée.  
  
 *ppvObject*  
 [out] Un pointeur vers le pointeur d’interface identifié par *iid*. Si l’objet ne prend pas en charge cette interface, *ppvObject* est définie sur NULL.  
  
 *PP*  
 [out] Un pointeur vers le pointeur d’interface identifié par le type `Q`. Si l’objet ne prend pas en charge cette interface, *pp* est définie sur NULL.  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur HRESULT standard.  
  
### <a name="remarks"></a>Notes  
 Si l’interface demandée est `IUnknown`, `QueryInterface` retourne un pointeur vers l’agrégées propre à l’objet `IUnknown` et incrémente le décompte de références. Sinon, cette méthode exécute une requête pour l’interface via la `CComContainedObject` membre, [m_contained](#m_contained).  
  
##  <a name="release"></a>  CComAggObject::Release  
 Décrémente le décompte de références sur l’objet agrégée.  
  
```
STDMETHOD_(ULONG, Release)();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Dans les versions debug, `Release` retourne une valeur qui peut-être être utiles pour le diagnostic ou de test. Dans les versions non debug `Release` retourne toujours 0.  
  
## <a name="see-also"></a>Voir aussi  
 [CComObject, classe](../../atl/reference/ccomobject-class.md)   
 [CComPolyObject, classe](../../atl/reference/ccompolyobject-class.md)   
 [DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable)   
 [DECLARE_ONLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_only_aggregatable)   
 [DECLARE_NOT_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_not_aggregatable)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
