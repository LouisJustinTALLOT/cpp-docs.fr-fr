---
title: Classe de CComPolyObject | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComPolyObject
- ATLCOM/ATL::CComPolyObject
- ATLCOM/ATL::CComPolyObject::CComPolyObject
- ATLCOM/ATL::CComPolyObject::AddRef
- ATLCOM/ATL::CComPolyObject::CreateInstance
- ATLCOM/ATL::CComPolyObject::FinalConstruct
- ATLCOM/ATL::CComPolyObject::FinalRelease
- ATLCOM/ATL::CComPolyObject::QueryInterface
- ATLCOM/ATL::CComPolyObject::Release
- ATLCOM/ATL::CComPolyObject::m_contained
dev_langs:
- C++
helpviewer_keywords:
- aggregate objects [C++], in ATL
- aggregation [C++], ATL objects
- CComPolyObject class
ms.assetid: eaf67c18-e855-48ca-9b15-f1df3106121b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3518fd5936c4871e99eaf597f12fb3ab7cc8aff6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="ccompolyobject-class"></a>CComPolyObject (classe)
Cette classe implémente **IUnknown** pour un objet regroupé ou.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class contained>  
class CComPolyObject : public IUnknown,
      public CComObjectRootEx<contained::_ThreadModel::ThreadModelNoCS>
```  
  
#### <a name="parameters"></a>Paramètres  
 `contained`  
 Votre classe, dérivée de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) ou [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), ainsi que d’autres interfaces souhaitées prendre en charge sur l’objet.  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CComPolyObject::CComPolyObject](#ccompolyobject)|Constructeur.|  
|[CComPolyObject :: ~ CComPolyObject](#dtor)|Destructeur.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CComPolyObject::AddRef](#addref)|Incrémente le décompte de références de l’objet.|  
|[CComPolyObject::CreateInstance](#createinstance)|(Statique) Vous permet de créer un nouveau **CComPolyObject <** `contained`  **>**  objet sans la surcharge de [CoCreateInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615).|  
|[CComPolyObject::FinalConstruct](#finalconstruct)|Effectue l’initialisation finale de `m_contained`.|  
|[CComPolyObject::FinalRelease](#finalrelease)|Effectue une destruction finale de `m_contained`.|  
|[CComPolyObject::QueryInterface](#queryinterface)|Récupère un pointeur vers l'interface demandée.|  
|[CComPolyObject::Release](#release)|Décrémente de nombre de référence de l’objet.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CComPolyObject::m_contained](#m_contained)|Délégués **IUnknown** appels à inconnu externe si l’objet est agrégée, ou à la **IUnknown** de l’objet si l’objet n’est pas agrégée.|  
  
## <a name="remarks"></a>Notes  
 `CComPolyObject`implémente [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) pour un objet regroupé ou.  
  
 Lorsqu’une instance de `CComPolyObject` est créé, la valeur de l’élément externe inconnu est activée. S’il s’agit **NULL**, **IUnknown** est implémenté pour un objet brutes et non agrégée. Si l’inconnu extérieur n’est pas **NULL**, **IUnknown** est implémenté pour un objet.  
  
 L’avantage d’utiliser `CComPolyObject` est que vous n’avez pas à la fois [CComAggObject](../../atl/reference/ccomaggobject-class.md) et [CComObject](../../atl/reference/ccomobject-class.md) dans votre module pour gérer les cas regroupés et. Un seul `CComPolyObject` objet gère les deux cas. Cela ne signifie qu’une seule copie de vtable et une seule copie des fonctions existent dans votre module. Si votre vtable est volumineuse, cela peut réduire considérablement la taille de votre module. Toutefois, si votre vtable est petite, à l’aide de `CComPolyObject` peut entraîner une taille légèrement supérieure de module, car il n’est pas optimisée pour un objet regroupé ou, comme le sont `CComAggObject` et `CComObject`.  
  
 Si le `DECLARE_POLY_AGGREGATABLE` macro est spécifié dans la définition de classe de votre objet, `CComPolyObject` permet de créer votre objet. `DECLARE_POLY_AGGREGATABLE`sont automatiquement déclarés si vous utilisez l’Assistant Projet ATL pour créer un contrôle complet ou Internet Explorer.  
  
 Si agrégée, la `CComPolyObject` objet possède son propre **IUnknown**, distinct de l’objet externe **IUnknown**et sa propre décompte de références. `CComPolyObject`utilise [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) de déléguer au inconnu externe.  
  
 Pour plus d’informations sur l’agrégation, consultez l’article [notions de base des objets COM ATL](../../atl/fundamentals-of-atl-com-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `CComObjectRootBase`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 `IUnknown`  
  
 `CComPolyObject`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** atlcom.h  
  
##  <a name="addref"></a>CComPolyObject::AddRef  
 Incrémente le décompte de références sur l’objet.  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Une valeur qui peut être utile pour les tests de diagnostic ou de test.  
  
##  <a name="ccompolyobject"></a>CComPolyObject::CComPolyObject  
 Constructeur.  
  
```
CComPolyObject(void* pv);
```  
  
### <a name="parameters"></a>Paramètres  
 `pv`  
 [in] Un pointeur vers l’inconnu extérieur si l’objet doit être agrégée, ou **NULL** si l’objet si l’objet n’est pas agrégée.  
  
### <a name="remarks"></a>Notes  
 Initialise le `CComContainedObject` membre de données, [m_contained](#m_contained)et incrémente le nombre de verrous du module.  
  
 Le décrémente destructeur le module nombre de verrous.  
  
##  <a name="dtor"></a>CComPolyObject :: ~ CComPolyObject  
 Destructeur.  
  
```
~CComPolyObject();
```  
  
### <a name="remarks"></a>Notes  
 Libère toutes les ressources attribuées, les appels [FinalRelease](#finalrelease), et décrémente le module nombre de verrous.  
  
##  <a name="createinstance"></a>CComPolyObject::CreateInstance  
 Vous permet de créer un nouveau **CComPolyObject <** `contained`  **>**  objet sans la surcharge de [CoCreateInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615).  
  
```
static HRESULT WINAPI CreateInstance(  
    LPUNKNOWN pUnkOuter, 
    CComPolyObject<contained>** pp);
```  
  
### <a name="parameters"></a>Paramètres  
 `pp`  
 [out] Un pointeur vers un **CComPolyObject <** `contained`  **>**  pointeur. Si `CreateInstance` échoue, `pp` a la valeur **NULL**.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur `HRESULT` standard.  
  
### <a name="remarks"></a>Notes  
 L’objet retourné est un décompte de références de zéro, appelez `AddRef` immédiatement, puis utilisez **version** pour libérer la référence sur le pointeur d’objet lorsque vous avez terminé.  
  
 Si vous ne devez un accès direct à l’objet, mais que vous souhaitez toujours créer un nouvel objet sans subir la surcharge de `CoCreateInstance`, utilisez [CComCoClass::CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance) à la place.  
  
##  <a name="finalconstruct"></a>CComPolyObject::FinalConstruct  
 Appelée au cours des dernières étapes de la construction d’objet, cette méthode effectue une initialisation finale sur le [m_contained](#m_contained) membre de données.  
  
```
HRESULT FinalConstruct();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur `HRESULT` standard.  
  
##  <a name="finalrelease"></a>CComPolyObject::FinalRelease  
 Appelé lors de la destruction d’objets, cette méthode libère le [m_contained](#m_contained) membre de données.  
  
```
void FinalRelease();
```  
  
##  <a name="m_contained"></a>CComPolyObject::m_contained  
 A [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) objet dérivé de votre classe.  
  
```
CComContainedObject<contained> m_contained;
```  
  
### <a name="parameters"></a>Paramètres  
 `contained`  
 [in] Votre classe, dérivée de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) ou [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), ainsi que d’autres interfaces souhaitées prendre en charge sur l’objet.  
  
### <a name="remarks"></a>Notes  
 **IUnknown** appelle via `m_contained` sont déléguées à inconnu externe si l’objet est agrégée, ou à la **IUnknown** de cet objet si l’objet n’est pas agrégée.  
  
##  <a name="queryinterface"></a>CComPolyObject::QueryInterface  
 Récupère un pointeur vers l'interface demandée.  
  
```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
template <class Q>  
HRESULT QueryInterface(Q** pp);
```  
  
### <a name="parameters"></a>Paramètres  
 `Q`  
 L’interface COM.  
  
 `iid`  
 [in] Identificateur de l’interface demandée.  
  
 `ppvObject`  
 [out] Un pointeur vers le pointeur d’interface identifié par `iid`. Si l’objet ne prend pas en charge cette interface, `ppvObject` a la valeur **NULL**.  
  
 `pp`  
 [out] Un pointeur vers l’interface identifiée par **__uuidof(Q)**.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur `HRESULT` standard.  
  
### <a name="remarks"></a>Notes  
 Pour un objet, si l’interface demandée est **IUnknown**, `QueryInterface` retourne un pointeur vers l’agrégées propre à l’objet **IUnknown** et incrémente le décompte de références. Sinon, cette méthode recherche l’interface via la `CComContainedObject` membre de données, [m_contained](#m_contained).  
  
##  <a name="release"></a>CComPolyObject::Release  
 Décrémente le décompte de références sur l’objet.  
  
```
STDMETHOD_(ULONG, Release)();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Dans les versions debug, **version** retourne une valeur qui peut être utile pour les tests de diagnostic ou de test. Dans les versions non Debug **version** retourne toujours 0.  
  
## <a name="see-also"></a>Voir aussi  
 [CComObjectRootEx (classe)](../../atl/reference/ccomobjectrootex-class.md)   
 [DECLARE_POLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_poly_aggregatable)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
