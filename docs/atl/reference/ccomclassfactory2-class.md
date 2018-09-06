---
title: CComClassFactory2, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComClassFactory2
- ATLCOM/ATL::CComClassFactory2
- ATLCOM/ATL::CComClassFactory2::CreateInstance
- ATLCOM/ATL::CComClassFactory2::CreateInstanceLic
- ATLCOM/ATL::CComClassFactory2::GetLicInfo
- ATLCOM/ATL::CComClassFactory2::LockServer
- ATLCOM/ATL::CComClassFactory2::RequestLicKey
dev_langs:
- C++
helpviewer_keywords:
- CComClassFactory2 class
ms.assetid: 19b66fd6-b9ed-47a0-822c-8132184f5a3e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 45e4b8fe74355d99258677fd4746ad2461f508d3
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43757801"
---
# <a name="ccomclassfactory2-class"></a>CComClassFactory2, classe

Cette classe implémente le [IClassFactory2](/windows/desktop/api/ocidl/nn-ocidl-iclassfactory2) interface.

## <a name="syntax"></a>Syntaxe

```
template <class license>  
class CComClassFactory2 : public IClassFactory2,
    public CComObjectRootEx<CComGlobalsThreadModel>,
    public license
```

#### <a name="parameters"></a>Paramètres

*licence*  
Une classe qui implémente les fonctions statiques suivantes :

- `static BOOL VerifyLicenseKey( BSTR bstr );`

- `static BOOL GetLicenseKey( DWORD dwReserved, BSTR * pBstr );`

- `static BOOL IsLicenseValid( );`

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComClassFactory2::CreateInstance](#createinstance)|Crée un objet du CLSID spécifié.|
|[CComClassFactory2::CreateInstanceLic](#createinstancelic)|Une clé de licence, crée un objet du CLSID spécifié.|
|[CComClassFactory2::GetLicInfo](#getlicinfo)|Récupère des informations décrivant les fonctionnalités de gestion des licences de la fabrique de classe.|
|[CComClassFactory2::LockServer](#lockserver)|Verrouille la fabrique de classe en mémoire.|
|[CComClassFactory2::RequestLicKey](#requestlickey)|Crée et retourne une clé de licence.|

## <a name="remarks"></a>Notes

`CComClassFactory2` implémente le [IClassFactory2](/windows/desktop/api/ocidl/nn-ocidl-iclassfactory2) interface, qui est une extension de [IClassFactory](/windows/desktop/api/unknwnbase/nn-unknwnbase-iclassfactory). `IClassFactory2` Création d’objet de contrôles avec une licence. Une fabrique de classe s’exécutant sur un ordinateur sous licence peut fournir une clé de licence de l’exécution. Cette clé de licence permet à une application instancier des objets lorsqu’il n’existe pas d’une licence de la totalité de la machine.

Objets ATL acquièrent normalement une fabrique de classe en dérivant de [CComCoClass](../../atl/reference/ccomcoclass-class.md). Cette classe inclut la macro [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory), qui déclare [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) en tant que la fabrique de classe par défaut. Pour utiliser `CComClassFactory2`, spécifiez la [macro DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2) macro dans la définition de classe de votre objet. Exemple :

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/ccomclassfactory2-class_1.h)]

`CMyLicense`, le paramètre de modèle à `CComClassFactory2`, doivent implémenter les fonctions statiques `VerifyLicenseKey`, `GetLicenseKey`, et `IsLicenseValid`. Voici un exemple d’une classe de licence simple :

[!code-cpp[NVC_ATL_COM#3](../../atl/codesnippet/cpp/ccomclassfactory2-class_2.h)]

`CComClassFactory2` dérive les deux `CComClassFactory2Base` et *licence*. `CComClassFactory2Base`, à son tour, dérive `IClassFactory2` et `CComObjectRootEx< CComGlobalsThreadModel >`.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CComObjectRootBase`

`license`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IClassFactory2`

`CComClassFactory2`

## <a name="requirements"></a>Configuration requise

**En-tête :** atlcom.h

##  <a name="createinstance"></a>  CComClassFactory2::CreateInstance

Crée un objet du CLSID spécifié et récupère un pointeur d’interface vers cet objet.

```
STDMETHOD(CreateInstance)(LPUNKNOWN pUnkOuter, REFIID riid, void** ppvObj);
```

### <a name="parameters"></a>Paramètres

*pUnkOuter*  
[in] Si l’objet est créé dans le cadre d’un agrégat, puis *pUnkOuter* doit être inconnu externe. Sinon, *pUnkOuter* doit être NULL.

*riid*  
[in] IID de l’interface demandée. Si *pUnkOuter* n’est pas NULL, *riid* doit être `IID_IUnknown`.

*ppvObj*  
[out] Un pointeur vers le pointeur d’interface identifié par *riid*. Si l’objet ne prend pas en charge cette interface, *ppvObj* est définie sur NULL.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Nécessite que la machine être sous licence. Si une licence de la totalité de la machine n’existe pas, appelez [CreateInstanceLic](#createinstancelic).

##  <a name="createinstancelic"></a>  CComClassFactory2::CreateInstanceLic

Semblable à [CreateInstance](#createinstance), sauf que `CreateInstanceLic` nécessite une clé de licence.

```
STDMETHOD(CreateInstanceLic)(
    IUnknown* pUnkOuter,
    IUnknown* /* pUnkReserved
*/,
    REFIID riid,
    BSTR bstrKey,
    void** ppvObject);
```

### <a name="parameters"></a>Paramètres

*pUnkOuter*  
[in] Si l’objet est créé dans le cadre d’un agrégat, puis *pUnkOuter* doit être inconnu externe. Sinon, *pUnkOuter* doit être NULL.

*pUnkReserved*  
[in] Non utilisé. Doit être NULL.

*riid*  
[in] IID de l’interface demandée. Si *pUnkOuter* n’est pas NULL, *riid* doit être `IID_IUnknown`.

*bstrKey*  
[in] La clé de licence de l’exécution obtenue précédemment à partir d’un appel à `RequestLicKey`. Cette clé est nécessaire pour créer l’objet.

*ppvObject*  
[out] Un pointeur vers le pointeur d’interface spécifié par *riid*. Si l’objet ne prend pas en charge cette interface, *ppvObject* est définie sur NULL.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Vous pouvez obtenir une clé de licence à l’aide [RequestLicKey](#requestlickey). Pour créer un objet sur un ordinateur sans licence, vous devez appeler `CreateInstanceLic`.

##  <a name="getlicinfo"></a>  CComClassFactory2::GetLicInfo

Remplit un [LICINFO](/windows/desktop/api/ocidl/ns-ocidl-taglicinfo) structure avec des informations qui décrivent la fabrique de classe de licences de fonctionnalités.

```
STDMETHOD(GetLicInfo)(LICINFO* pLicInfo);
```

### <a name="parameters"></a>Paramètres

*pLicInfo*  
[out] Pointeur vers un `LICINFO` structure.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Le `fRuntimeKeyAvail` membre de cette structure indique si, étant donné une clé de licence, la fabrique de classe permet aux objets d’être créé sur un ordinateur sans licence. Le *fLicVerified* membre indique l’existence d’une licence de la totalité de la machine.

##  <a name="lockserver"></a>  CComClassFactory2::LockServer

Incrémente et décrémente le module nombre de verrous en appelant `_Module::Lock` et `_Module::Unlock`, respectivement.

```
STDMETHOD(LockServer)(BOOL fLock);
```

### <a name="parameters"></a>Paramètres

*Troupeau*  
[in] Si la valeur est TRUE, le nombre de verrous est incrémenté ; Sinon, le nombre de verrous est décrémenté.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

`_Module` fait référence à l’instance globale de [CComModule](../../atl/reference/ccommodule-class.md) ou une classe dérivée à partir de celui-ci.

Appel `LockServer` permet à un client à maintenir une fabrique de classe afin que plusieurs objets peuvent être créés rapidement.

##  <a name="requestlickey"></a>  CComClassFactory2::RequestLicKey

Crée et retourne une clé de licence, à condition que le `fRuntimeKeyAvail` membre de la [LICINFO](/windows/desktop/api/ocidl/ns-ocidl-taglicinfo) structure a la valeur TRUE.

```
STDMETHOD(RequestLicKey)(DWORD dwReserved, BSTR* pbstrKey);
```

### <a name="parameters"></a>Paramètres

*dwReserved*  
[in] Non utilisé. Doit être égal à zéro.

*pbstrKey*  
[out] Pointeur vers la clé de licence.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Une clé de licence est nécessaire pour appeler [CreateInstanceLic](#createinstancelic) pour créer un objet sur un ordinateur sans licence. Si `fRuntimeKeyAvail` a la valeur FALSE, puis les objets peuvent uniquement être créés sur un ordinateur sous licence complète.

Appelez [GetLicInfo](#getlicinfo) pour récupérer la valeur de `fRuntimeKeyAvail`.

## <a name="see-also"></a>Voir aussi

[Ccomclassfactoryautothread, classe](../../atl/reference/ccomclassfactoryautothread-class.md)   
[Ccomclassfactorysingleton, classe](../../atl/reference/ccomclassfactorysingleton-class.md)   
[CComObjectRootEx, classe](../../atl/reference/ccomobjectrootex-class.md)   
[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)   
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
