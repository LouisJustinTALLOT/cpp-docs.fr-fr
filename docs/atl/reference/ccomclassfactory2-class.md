---
title: Classe CComClassFactory2
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
ms.openlocfilehash: 0cb2064cfaea6317c4522ff917f3963fca2219b8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321014"
---
# <a name="ccomclassfactory2-class"></a>Classe CComClassFactory2

Cette classe implémente l’interface [IClassFactory2.](/windows/win32/api/ocidl/nn-ocidl-iclassfactory2)

## <a name="syntax"></a>Syntaxe

```
template <class license>
class CComClassFactory2 : public IClassFactory2,
    public CComObjectRootEx<CComGlobalsThreadModel>,
    public license
```

#### <a name="parameters"></a>Paramètres

*Licence*<br/>
Une classe qui met en œuvre les fonctions statiques suivantes :

- `static BOOL VerifyLicenseKey( BSTR bstr );`

- `static BOOL GetLicenseKey( DWORD dwReserved, BSTR * pBstr );`

- `static BOOL IsLicenseValid( );`

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CComClassFactory2::CréerInstance](#createinstance)|Crée un objet du CLSID spécifié.|
|[CComClassFactory2::CréerInstanceLic](#createinstancelic)|Compte tenu d’une clé de licence, crée un objet du CLSID spécifié.|
|[CComClassFactory2::GetLicInfo](#getlicinfo)|Récupère les informations décrivant les capacités de licence de l’usine de classe.|
|[CComClassFactory2::LockServer](#lockserver)|Verrouille l’usine de classe dans la mémoire.|
|[CComClassFactory2::RequestLicKey](#requestlickey)|Crée et renvoie une clé de licence.|

## <a name="remarks"></a>Notes

`CComClassFactory2`implémente l’interface [IClassFactory2,](/windows/win32/api/ocidl/nn-ocidl-iclassfactory2) qui est une extension [d’IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory). `IClassFactory2`contrôle la création d’objets par le biais d’une licence. Une usine de classe exécutant sur une machine sous licence peut fournir une clé de licence de temps d’exécution. Cette clé de licence permet à une application d’instantané des objets lorsqu’une licence de machine complète n’existe pas.

Les objets ATL acquièrent normalement une usine de classe en dérivé de [CComCoClass](../../atl/reference/ccomcoclass-class.md). Cette classe comprend la macro [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory), qui déclare [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) comme l’usine de classe par défaut. Pour `CComClassFactory2`l’utiliser, spécifiez la [macro DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2) dans la définition de classe de votre objet. Par exemple :

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/ccomclassfactory2-class_1.h)]

`CMyLicense`, le paramètre de modèle `CComClassFactory2`pour `VerifyLicenseKey` `GetLicenseKey`, `IsLicenseValid`doit implémenter les fonctions statiques , , et . Voici un exemple de classe de licence simple :

[!code-cpp[NVC_ATL_COM#3](../../atl/codesnippet/cpp/ccomclassfactory2-class_2.h)]

`CComClassFactory2`dérive des `CComClassFactory2Base` deux et *de la licence*. `CComClassFactory2Base`, à son tour, dérive de `IClassFactory2` et `CComObjectRootEx< CComGlobalsThreadModel >`.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CComObjectRootBase`

`license`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IClassFactory2`

`CComClassFactory2`

## <a name="requirements"></a>Spécifications

**En-tête:** atlcom.h

## <a name="ccomclassfactory2createinstance"></a><a name="createinstance"></a>CComClassFactory2::CréerInstance

Crée un objet du CLSID spécifié et récupère un pointeur d’interface sur cet objet.

```
STDMETHOD(CreateInstance)(LPUNKNOWN pUnkOuter, REFIID riid, void** ppvObj);
```

### <a name="parameters"></a>Paramètres

*pUnkOuter*<br/>
[dans] Si l’objet est créé dans le cadre d’un agrégat, puis *pUnkOuter* doit être l’inconnu extérieur. Sinon, *pUnkOuter* doit être NULL.

*riid*<br/>
[dans] L’IID de l’interface demandée. Si *pUnkOuter* n’est pas- `IID_IUnknown`NULL, *riid* doit être .

*ppvObj*<br/>
[out] Un pointeur au pointeur d’interface identifié par *riid*. Si l’objet ne prend pas en charge cette interface, *ppvObj* est réglé sur NULL.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Nécessite que la machine soit entièrement sous licence. Si une licence de machine complète n’existe pas, appelez [CreateInstanceLic](#createinstancelic).

## <a name="ccomclassfactory2createinstancelic"></a><a name="createinstancelic"></a>CComClassFactory2::CréerInstanceLic

Semblable à [CreateInstance](#createinstance) `CreateInstanceLic` , sauf que nécessite une clé de licence.

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
[dans] Si l’objet est créé dans le cadre d’un agrégat, puis *pUnkOuter* doit être l’inconnu extérieur. Sinon, *pUnkOuter* doit être NULL.

*pUnkReserved*<br/>
[in] Non utilisé. Doit être NULL.

*riid*<br/>
[dans] L’IID de l’interface demandée. Si *pUnkOuter* n’est pas- `IID_IUnknown`NULL, *riid* doit être .

*bstrKey (en)*<br/>
[dans] La clé de licence de run-time `RequestLicKey`précédemment obtenue à partir d’un appel à . Cette clé est nécessaire pour créer l’objet.

*ppvObject*<br/>
[out] Un pointeur au pointeur d’interface spécifié par *riid*. Si l’objet ne prend pas en charge cette interface, *ppvObject* est réglé sur NULL.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Vous pouvez obtenir une clé de licence à l’aide [de RequestLicKey](#requestlickey). Afin de créer un objet sur une machine sans `CreateInstanceLic`licence, vous devez appeler .

## <a name="ccomclassfactory2getlicinfo"></a><a name="getlicinfo"></a>CComClassFactory2::GetLicInfo

Remplit une structure [LICINFO](/windows/win32/api/ocidl/ns-ocidl-licinfo) d’informations décrivant les capacités de licence de l’usine de classe.

```
STDMETHOD(GetLicInfo)(LICINFO* pLicInfo);
```

### <a name="parameters"></a>Paramètres

*pLicInfo (en anglais)*<br/>
[out] Pointeur `LICINFO` vers une structure.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Le `fRuntimeKeyAvail` membre de cette structure indique si, compte tenu d’une clé de licence, l’usine de classe permet de créer des objets sur une machine sans licence. Le membre *fLicVerified indique s’il* existe une licence de machine complète.

## <a name="ccomclassfactory2lockserver"></a><a name="lockserver"></a>CComClassFactory2::LockServer

Incréments et décroissements le `_Module::Lock` module `_Module::Unlock`verrou compte en appelant et , respectivement.

```
STDMETHOD(LockServer)(BOOL fLock);
```

### <a name="parameters"></a>Paramètres

*Troupeau*<br/>
[dans] Si VRAI, le nombre de serrures est incrémenté; autrement, le nombre de serrures est décrète.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

`_Module`se réfère à l’exemple global de [CComModule](../../atl/reference/ccommodule-class.md) ou d’une classe qui en découle.

L’appel `LockServer` permet à un client de s’accrocher à une usine de classe afin que plusieurs objets puissent être rapidement créés.

## <a name="ccomclassfactory2requestlickey"></a><a name="requestlickey"></a>CComClassFactory2::RequestLicKey

Crée et renvoie une clé `fRuntimeKeyAvail` de licence, à condition que le membre de la structure [LICINFO](/windows/win32/api/ocidl/ns-ocidl-licinfo) soit VRAI.

```
STDMETHOD(RequestLicKey)(DWORD dwReserved, BSTR* pbstrKey);
```

### <a name="parameters"></a>Paramètres

*dwReserved*<br/>
[in] Non utilisé. Doit être zéro.

*pbstrKey (en)*<br/>
[out] Pointeur vers la clé de licence.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Une clé de licence est nécessaire pour appeler [CreateInstanceLic](#createinstancelic) pour créer un objet sur une machine non autorisée. Si `fRuntimeKeyAvail` est FALSE, alors les objets ne peuvent être créés que sur une machine entièrement sous licence.

Appelez [GetLicInfo](#getlicinfo) pour récupérer `fRuntimeKeyAvail`la valeur de .

## <a name="see-also"></a>Voir aussi

[Classe CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)<br/>
[Classe CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md)<br/>
[Classe CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
