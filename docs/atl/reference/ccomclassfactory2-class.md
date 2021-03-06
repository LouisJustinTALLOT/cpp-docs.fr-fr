---
description: 'En savoir plus sur : classe CComClassFactory2'
title: CComClassFactory2, classe
ms.date: 11/04/2016
f1_keywords:
- CComClassFactory2
- ATLCOM/ATL::CComClassFactory2
- ATLCOM/ATL::CComClassFactory2::CreateInstance
- ATLCOM/ATL::CComClassFactory2::CreateInstanceLic
- ATLCOM/ATL::CComClassFactory2::GetLicInfo
- ATLCOM/ATL::CComClassFactory2::LockServer
- ATLCOM/ATL::CComClassFactory2::RequestLicKey
helpviewer_keywords:
- CComClassFactory2 class
ms.assetid: 19b66fd6-b9ed-47a0-822c-8132184f5a3e
ms.openlocfilehash: 7aebf09616c7fc4e85f6c44aee4db84886033f8b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97146885"
---
# <a name="ccomclassfactory2-class"></a>CComClassFactory2, classe

Cette classe implémente l’interface [IClassFactory2](/windows/win32/api/ocidl/nn-ocidl-iclassfactory2) .

## <a name="syntax"></a>Syntaxe

```
template <class license>
class CComClassFactory2 : public IClassFactory2,
    public CComObjectRootEx<CComGlobalsThreadModel>,
    public license
```

#### <a name="parameters"></a>Paramètres

*licence*<br/>
Classe qui implémente les fonctions statiques suivantes :

- `static BOOL VerifyLicenseKey( BSTR bstr );`

- `static BOOL GetLicenseKey( DWORD dwReserved, BSTR * pBstr );`

- `static BOOL IsLicenseValid( );`

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComClassFactory2 :: CreateInstance](#createinstance)|Crée un objet du CLSID spécifié.|
|[CComClassFactory2::CreateInstanceLic](#createinstancelic)|En fonction d’une clé de licence, crée un objet du CLSID spécifié.|
|[CComClassFactory2::GetLicInfo](#getlicinfo)|Récupère des informations décrivant les fonctionnalités de gestion des licences de la fabrique de classes.|
|[CComClassFactory2 :: LockServer,](#lockserver)|Verrouille la fabrique de classe en mémoire.|
|[CComClassFactory2::RequestLicKey](#requestlickey)|Crée et retourne une clé de licence.|

## <a name="remarks"></a>Notes

`CComClassFactory2` implémente l’interface [IClassFactory2](/windows/win32/api/ocidl/nn-ocidl-iclassfactory2) , qui est une extension de [IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory). `IClassFactory2` contrôle la création d’objets via une licence. Une fabrique de classes s’exécutant sur un ordinateur sous licence peut fournir une clé de licence d’exécution. Cette clé de licence permet à une application d’instancier des objets lorsqu’une licence d’ordinateur complet n’existe pas.

Les objets ATL acquièrent normalement une fabrique de classe en dérivant de [CComCoClass](../../atl/reference/ccomcoclass-class.md). Cette classe comprend la macro [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory), qui déclare [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) comme fabrique de classe par défaut. Pour utiliser `CComClassFactory2` , spécifiez la macro [DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2) dans la définition de classe de votre objet. Par exemple :

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/ccomclassfactory2-class_1.h)]

`CMyLicense`, le paramètre de modèle de `CComClassFactory2` , doit implémenter les fonctions statiques `VerifyLicenseKey` , `GetLicenseKey` et `IsLicenseValid` . Voici un exemple de classe de licence simple :

[!code-cpp[NVC_ATL_COM#3](../../atl/codesnippet/cpp/ccomclassfactory2-class_2.h)]

`CComClassFactory2` dérive de et de la `CComClassFactory2Base` *licence*. `CComClassFactory2Base`, à son tour, dérive de `IClassFactory2` et `CComObjectRootEx< CComGlobalsThreadModel >` .

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CComObjectRootBase`

`license`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IClassFactory2`

`CComClassFactory2`

## <a name="requirements"></a>Spécifications

**En-tête :** atlcom. h

## <a name="ccomclassfactory2createinstance"></a><a name="createinstance"></a> CComClassFactory2 :: CreateInstance

Crée un objet du CLSID spécifié et récupère un pointeur d’interface vers cet objet.

```
STDMETHOD(CreateInstance)(LPUNKNOWN pUnkOuter, REFIID riid, void** ppvObj);
```

### <a name="parameters"></a>Paramètres

*pUnkOuter*<br/>
dans Si l’objet est créé dans le cadre d’un agrégat, *pUnkOuter* doit être l’élément externe inconnu. Sinon, *pUnkOuter* doit avoir la valeur null.

*riid*<br/>
dans IID de l’interface demandée. Si *pUnkOuter* n’est pas null, *riid* doit avoir la valeur `IID_IUnknown` .

*ppvObj*<br/>
à Pointeur vers le pointeur d’interface identifié par *riid*. Si l’objet ne prend pas en charge cette interface, *ppvObj* a la valeur null.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

Requiert une licence complète de l’ordinateur. Si aucune licence d’ordinateur complète n’existe, appelez [CreateInstanceLic](#createinstancelic).

## <a name="ccomclassfactory2createinstancelic"></a><a name="createinstancelic"></a> CComClassFactory2::CreateInstanceLic

Semblable à [CreateInstance](#createinstance), sauf que `CreateInstanceLic` requiert une clé de licence.

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

*pUnkOuter*<br/>
dans Si l’objet est créé dans le cadre d’un agrégat, *pUnkOuter* doit être l’élément externe inconnu. Sinon, *pUnkOuter* doit avoir la valeur null.

*pUnkReserved*<br/>
[in] Non utilisé. Doit être NULL.

*riid*<br/>
dans IID de l’interface demandée. Si *pUnkOuter* n’est pas null, *riid* doit avoir la valeur `IID_IUnknown` .

*bstrKey*<br/>
dans La clé de licence Runtime obtenue précédemment à partir d’un appel à `RequestLicKey` . Cette clé est requise pour créer l’objet.

*ppvObject*<br/>
à Pointeur vers le pointeur d’interface spécifié par *riid*. Si l’objet ne prend pas en charge cette interface, *ppvObject* a la valeur null.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

Vous pouvez obtenir une clé de licence à l’aide de [RequestLicKey](#requestlickey). Pour créer un objet sur un ordinateur sans licence, vous devez appeler `CreateInstanceLic` .

## <a name="ccomclassfactory2getlicinfo"></a><a name="getlicinfo"></a> CComClassFactory2::GetLicInfo

Remplit une structure [LICINFO](/windows/win32/api/ocidl/ns-ocidl-licinfo) avec des informations qui décrivent les fonctionnalités de gestion des licences de la fabrique de classes.

```
STDMETHOD(GetLicInfo)(LICINFO* pLicInfo);
```

### <a name="parameters"></a>Paramètres

*pLicInfo*<br/>
à Pointeur vers une `LICINFO` structure.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

Le `fRuntimeKeyAvail` membre de cette structure indique si, étant donné une clé de licence, la fabrique de classe autorise la création d’objets sur un ordinateur sans licence. Le membre *fLicVerified* indique si une licence d’ordinateur complète existe.

## <a name="ccomclassfactory2lockserver"></a><a name="lockserver"></a> CComClassFactory2 :: LockServer,

Incrémente et décrémente le nombre de verrous de module en appelant `_Module::Lock` et `_Module::Unlock` , respectivement.

```
STDMETHOD(LockServer)(BOOL fLock);
```

### <a name="parameters"></a>Paramètres

*Troupeau*<br/>
dans Si la valeur est TRUE, le nombre de verrous est incrémenté ; dans le cas contraire, le nombre de verrous est décrémenté.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

`_Module` fait référence à l’instance globale de [CComModule](../../atl/reference/ccommodule-class.md) ou à une classe dérivée de celle-ci.

L’appel de `LockServer` permet à un client de conserver une fabrique de classes pour que plusieurs objets puissent être créés rapidement.

## <a name="ccomclassfactory2requestlickey"></a><a name="requestlickey"></a> CComClassFactory2::RequestLicKey

Crée et retourne une clé de licence, à condition que le `fRuntimeKeyAvail` membre de la structure [LICINFO](/windows/win32/api/ocidl/ns-ocidl-licinfo) ait la valeur true.

```
STDMETHOD(RequestLicKey)(DWORD dwReserved, BSTR* pbstrKey);
```

### <a name="parameters"></a>Paramètres

*dwReserved*<br/>
[in] Non utilisé. Doit être zéro.

*pbstrKey*<br/>
à Pointeur vers la clé de licence.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

Une clé de licence est nécessaire pour appeler [CreateInstanceLic](#createinstancelic) afin de créer un objet sur un ordinateur sans licence. Si `fRuntimeKeyAvail` a la valeur false, les objets ne peuvent être créés que sur un ordinateur sous licence complète.

Appelez [GetLicInfo](#getlicinfo) pour récupérer la valeur de `fRuntimeKeyAvail` .

## <a name="see-also"></a>Voir aussi

[CComClassFactoryAutoThread, classe](../../atl/reference/ccomclassfactoryautothread-class.md)<br/>
[CComClassFactorySingleton, classe](../../atl/reference/ccomclassfactorysingleton-class.md)<br/>
[CComObjectRootEx (classe)](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
