---
title: Classe de CComObject | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComObject
- ATLCOM/ATL::CComObject
- ATLCOM/ATL::CComObject::CComObject
- ATLCOM/ATL::CComObject::AddRef
- ATLCOM/ATL::CComObject::CreateInstance
- ATLCOM/ATL::CComObject::QueryInterface
- ATLCOM/ATL::CComObject::Release
dev_langs:
- C++
helpviewer_keywords:
- CComObject class
ms.assetid: e2b6433b-6349-4749-b4bc-acbd7a22c8b0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: af84d64d326ed7746b76db39ef26181ab96ca88d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32361477"
---
# <a name="ccomobject-class"></a>Classe de CComObject
Cette classe implémente **IUnknown** pour un objet brutes et non agrégée.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class Base>  
class CComObject : public Base
```  
  
#### <a name="parameters"></a>Paramètres  
 `Base`  
 Votre classe, dérivée de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) ou [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), ainsi que d’autres interfaces souhaitées prendre en charge sur l’objet.  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CComObject::CComObject](#ccomobject)|Constructeur.|  
|[CComObject::~CComObject](#dtor)|Destructeur.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CComObject::AddRef](#addref)|Incrémente le décompte de références sur l’objet.|  
|[CComObject::CreateInstance](#createinstance)|(Statique) Crée un nouveau `CComObject` objet.|  
|[CComObject::QueryInterface](#queryinterface)|Récupère un pointeur vers l'interface demandée.|  
|[CComObject::Release](#release)|Décrémente le décompte de références sur l’objet.|  
  
## <a name="remarks"></a>Notes  
 `CComObject` implémente [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) pour un objet brutes et non agrégée. Toutefois, les appels à `QueryInterface`, `AddRef`, et **version** sont déléguées à `CComObjectRootEx`.  
  
 Pour plus d’informations sur l’utilisation de `CComObject`, consultez l’article [notions de base des objets COM ATL](../../atl/fundamentals-of-atl-com-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `Base`  
  
 `CComObject`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlcom.h  
  
##  <a name="addref"></a>  CComObject::AddRef  
 Incrémente le décompte de références sur l’objet.  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Cette fonction retourne le nouveau nombre incrémenté de référence sur l’objet. Cette valeur peut être utile pour les tests de diagnostic ou des tests.  
  
##  <a name="ccomobject"></a>  CComObject::CComObject  
 Le constructeur incrémente le nombre de verrous du module.  
  
```
CComObject(void* = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 **void\***  
 [in] Ce paramètre sans nom n’est pas utilisé. Il existe pour une symétrie avec d’autres **CCom***XXX*`Object`*XXX* constructeurs.  
  
### <a name="remarks"></a>Notes  
 Le décrémente destructeur il.  
  
 Si un `CComObject`-objet dérivé est construit correctement à l’aide de la **nouveau** (opérateur), le nombre de référence initiale est 0. Pour définir le nombre de références à la valeur appropriée (1), effectuez un appel à la [AddRef](#addref) (fonction).  
  
##  <a name="dtor"></a>  CComObject::~CComObject  
 Destructeur.  
  
```
CComObject();
```  
  
### <a name="remarks"></a>Notes  
 Libère toutes les ressources attribuées, les appels [FinalRelease](ccomobjectrootex-class.md#finalrelease), et décrémente le module nombre de verrous.  

  
##  <a name="createinstance"></a>  CComObject::CreateInstance  
 Cette fonction statique vous permet de créer un nouveau **CComObject <** `Base` **>** objet, sans la surcharge de [CoCreateInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615).  
  
```
static HRESULT WINAPI CreateInstance(CComObject<Base>** pp);
```  
  
### <a name="parameters"></a>Paramètres  
 `pp`  
 [out] Un pointeur vers un **CComObject <** `Base` **>** pointeur. Si `CreateInstance` échoue, `pp` a la valeur **NULL**.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur `HRESULT` standard.  
  
### <a name="remarks"></a>Notes  
 L’objet retourné est un décompte de références de zéro, appelez `AddRef` immédiatement, puis utilisez **version** pour libérer la référence sur le pointeur d’objet lorsque vous avez terminé.  
  
 Si vous n’avez besoin d’imposent pas accès à l’objet, mais que vous souhaitez toujours créer un nouvel objet sans subir la surcharge de `CoCreateInstance`, utilisez [CComCoClass::CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance) à la place.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_COM#38](../../atl/codesnippet/cpp/ccomobject-class_1.h)]  
  
 [!code-cpp[NVC_ATL_COM#39](../../atl/codesnippet/cpp/ccomobject-class_2.cpp)]  
  
##  <a name="queryinterface"></a>  CComObject::QueryInterface  
 Récupère un pointeur vers l'interface demandée.  
  
```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
template <class Q>  
HRESULT STDMETHODCALLTYPE QueryInterface(Q** pp);
```  
  
### <a name="parameters"></a>Paramètres  
 `iid`  
 [in] Identificateur de l’interface demandée.  
  
 `ppvObject`  
 [out] Un pointeur vers le pointeur d’interface identifié par `iid`. Si l’objet ne prend pas en charge cette interface, `ppvObject` a la valeur **NULL**.  
  
 `pp`  
 [out] Un pointeur vers le pointeur d’interface identifié par le type `Q`. Si l’objet ne prend pas en charge cette interface, `pp` a la valeur **NULL**.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur `HRESULT` standard.  
  
##  <a name="release"></a>  CComObject::Release  
 Décrémente le décompte de références sur l’objet.  
  
```
STDMETHOD_(ULONG, Release)();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Cette fonction retourne le nouveau nombre de références décrémenté sur l’objet. Dans les versions debug, la valeur de retour peut être utile pour les tests de diagnostic ou de test. Dans les versions non debug, **version** retourne toujours 0.  
  
## <a name="see-also"></a>Voir aussi  
 [Classe de CComAggObject](../../atl/reference/ccomaggobject-class.md)   
 [CComPolyObject (classe)](../../atl/reference/ccompolyobject-class.md)   
 [DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable)   
 [DECLARE_NOT_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_not_aggregatable)   
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
