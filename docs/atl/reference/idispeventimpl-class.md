---
title: Classe IDispEventImpl
ms.date: 11/04/2016
f1_keywords:
- IDispEventImpl
- ATLCOM/ATL::IDispEventImpl
- ATLCOM/ATL::IDispEventImpl::IDispEventImpl
- ATLCOM/ATL::IDispEventImpl::GetFuncInfoFromId
- ATLCOM/ATL::IDispEventImpl::GetIDsOfNames
- ATLCOM/ATL::IDispEventImpl::GetTypeInfo
- ATLCOM/ATL::IDispEventImpl::GetTypeInfoCount
- ATLCOM/ATL::IDispEventImpl::GetUserDefinedType
helpviewer_keywords:
- IDispEventImpl class
ms.assetid: a64b5288-35cb-4638-aad6-2d15b1c7cf7b
ms.openlocfilehash: fa6e9f972accd0115d9f1e3248bd97ddde0c3c63
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329756"
---
# <a name="idispeventimpl-class"></a>Classe IDispEventImpl

Cette classe fournit des `IDispatch` implémentations des méthodes.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <UINT nID, class T,
    const IID* pdiid = &IID_NULL,
    const GUID* plibid = &GUID_NULL,
    WORD wMajor = 0,
    WORD wMinor = 0,
    class tihclass = CcomTypeInfoHolder>
class ATL_NO_VTABLE IDispEventImpl : public IDispEventSimpleImpl<nID, T, pdiid>
```

#### <a name="parameters"></a>Paramètres

*nID*<br/>
Un identifiant unique pour l’objet source. Quand `IDispEventImpl` est la classe de base pour un contrôle composite, utilisez l’ID de ressource du contrôle contenu souhaité pour ce paramètre. Dans d’autres cas, utilisez un integer positif arbitraire.

*T*<br/>
La classe de l’utilisateur, `IDispEventImpl`qui est dérivé de .

*pdiid pdiid*<br/>
Le pointeur de l’IID de l’événement dispinterface mis en œuvre par cette classe. Cette interface doit être définie dans la bibliothèque type dénotée par *plibid*, *wMajor*, et *wMinor*.

*plibid*<br/>
Un pointeur à la bibliothèque de type qui définit l’interface de répartition pointée par *pdiid*. Si **&GUID_NULL,** la bibliothèque de type sera chargée à partir de l’objet s’approvisionnant en événements.

*wMajor (en)*<br/>
Version principale de la bibliothèque de types. La valeur par défaut est 0.

*wMinor (en)*<br/>
Version secondaire de la bibliothèque de types. La valeur par défaut est 0.

*tihclass*<br/>
La classe utilisée pour gérer les informations de type pour *T*. La valeur par défaut `CComTypeInfoHolder`est une catégorie de type ; cependant, vous pouvez remplacer ce paramètre de modèle `CComTypeInfoHolder`en fournissant une classe d’un type autre que .

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|[IDispEventImpl::_tihclass](../../atl/reference/idispeventimpl-class.md)|La classe gérait les informations de type. Par défaut, `CComTypeInfoHolder`.|

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[IDispEventImpl::IDispEventImpl](#idispeventimpl)|Constructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IDispEventImpl::GetFuncInfoDeid](#getfuncinfofromid)|Localise l’indice de fonction pour l’identifiant de répartition spécifié.|
|[IDispEventImpl::GetIDsOfNames IDispEventImpl::GetIDsOfNames](#getidsofnames)|Cartographiez un seul membre et un ensemble facultatif de noms d’arguments à un ensemble correspondant de DISPIDs integer.|
|[IDispEventImpl::GetTypeInfo](#gettypeinfo)|Récupère les informations de type pour un objet.|
|[IDispEventImpl::GetTypeInfoCount](#gettypeinfocount)|Récupère le nombre d’interfaces d’information de type.|
|[IDispEventImpl::GetUserDefinedType](#getuserdefinedtype)|Récupère le type de base d’un type défini par l’utilisateur.|

## <a name="remarks"></a>Notes

`IDispEventImpl`fournit un moyen de mettre en œuvre une dispinterface d’événement sans vous obliger à fournir le code d’implémentation pour chaque méthode/événement sur cette interface. `IDispEventImpl`fournit des implémentations des `IDispatch` méthodes. Vous n’avez qu’à fournir des implémentations pour les événements que vous êtes intéressé à gérer.

`IDispEventImpl`fonctionne en conjonction avec la carte de l’évier de l’événement dans votre classe pour acheminer les événements à la fonction de gestionnaire approprié. Pour utiliser cette classe :

Ajoutez une [SINK_ENTRY](composite-control-macros.md#sink_entry) ou [SINK_ENTRY_EX](composite-control-macros.md#sink_entry_ex) macro à la carte de l’évier de l’événement pour chaque événement sur chaque objet que vous voulez manipuler. Lorsque `IDispEventImpl` vous utilisez comme classe de base d’un contrôle composite, vous pouvez appeler [AtlAdviseSinkMap](connection-point-global-functions.md#atladvisesinkmap) pour établir et briser la connexion avec les sources d’événements pour toutes les entrées dans la carte de l’évier de l’événement. Dans d’autres cas, ou pour un contrôle plus large, appelez [DispEventAdvise](idispeventsimpleimpl-class.md#dispeventadvise) pour établir le lien entre l’objet source et la classe de base. Appelez [DispEventUnadvise](idispeventsimpleimpl-class.md#dispeventunadvise) pour briser la connexion.

Vous devez `IDispEventImpl` dériver (en utilisant une valeur unique pour *nID*) pour chaque objet pour lequel vous avez besoin pour gérer les événements. Vous pouvez réutiliser la classe de base en déconseillant un objet source puis en vous conseillant contre un objet source différent, `IDispEventImpl` mais le nombre maximum d’objets sources qui peuvent être manipulés par un seul objet en même temps est limité par le nombre de classes de base.

`IDispEventImpl`fournit la même fonctionnalité que [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md), sauf qu’il obtient des informations de type sur l’interface à partir d’une bibliothèque de type plutôt que de l’avoir fourni comme un pointeur à une structure [_ATL_FUNC_INFO.](../../atl/reference/atl-func-info-structure.md) Utilisez `IDispEventSimpleImpl` lorsque vous n’avez pas de bibliothèque type décrivant l’interface de l’événement ou que vous voulez éviter les frais généraux associés à l’utilisation de la bibliothèque de type.

> [!NOTE]
> `IDispEventImpl`et `IDispEventSimpleImpl` fournir leur `IUnknown::QueryInterface` propre `IDispEventImpl` mise `IDispEventSimpleImpl` en œuvre de permettre à chaque classe et à la classe de base d’agir comme une identité COM distincte tout en permettant un accès direct aux membres de la classe dans votre objet COM principal.

La mise en œuvre d’ActiveX d’activeX n’appuie que les valeurs de retour du type HRESULT ou les vides de vos méthodes de gestionnaire d’événements; toute autre valeur de retour n’est pas supportée et son comportement n’est pas défini.

Pour plus d’informations, voir [Supporting IDispEventImpl](../../atl/supporting-idispeventimpl.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`_IDispEvent`

`_IDispEventLocator`

[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)

`IDispEventImpl`

## <a name="requirements"></a>Spécifications

**En-tête:** atlcom.h

## <a name="idispeventimplgetfuncinfofromid"></a><a name="getfuncinfofromid"></a>IDispEventImpl::GetFuncInfoDeid

Localise l’indice de fonction pour l’identifiant de répartition spécifié.

```
HRESULT GetFuncInfoFromId(
    const IID& iid,
    DISPID dispidMember,
    LCID lcid,
    _ATL_FUNC_INFO& info);
```

### <a name="parameters"></a>Paramètres

*Iid*<br/>
[dans] Une référence à l’ID de la fonction.

*dispidMember*<br/>
[dans] L’ID de répartition de la fonction.

*lcid*<br/>
[dans] Le contexte local de l’ID de fonction.

*info*<br/>
[dans] La structure indiquant comment la fonction est appelée.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

## <a name="idispeventimplgetidsofnames"></a><a name="getidsofnames"></a>IDispEventImpl::GetIDsOfNames IDispEventImpl::GetIDsOfNames

Cartographie un seul membre et un ensemble facultatif de noms d’arguments à un ensemble correspondant de DISPIDs integer, qui peuvent être utilisés sur les appels ultérieurs à [IDispatch::Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke).

```
STDMETHOD(GetIDsOfNames)(
    REFIID riid,
    LPOLESTR* rgszNames,
    UINT cNames,
    LCID lcid,
    DISPID* rgdispid);
```

### <a name="remarks"></a>Notes

Voir [IDispatch::GetIDsOfNames](/windows/win32/api/oaidl/nf-oaidl-idispatch-getidsofnames) dans le SDK Windows.

## <a name="idispeventimplgettypeinfo"></a><a name="gettypeinfo"></a>IDispEventImpl::GetTypeInfo

Récupère les informations de type pour un objet, qui peuvent être utilisées ensuite pour obtenir les informations de type d'une interface.

```
STDMETHOD(GetTypeInfo)(
    UINT itinfo,
    LCID lcid,
    ITypeInfo** pptinfo);
```

### <a name="remarks"></a>Notes

## <a name="idispeventimplgettypeinfocount"></a><a name="gettypeinfocount"></a>IDispEventImpl::GetTypeInfoCount

Récupère le nombre d'interfaces d'informations de type fourni par un objet (0 ou 1).

```
STDMETHOD(GetTypeInfoCount)(UINT* pctinfo);
```

### <a name="remarks"></a>Notes

Voir [IDispatch::GetTypeInfoCount](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfocount) in the Windows SDK.

## <a name="idispeventimplgetuserdefinedtype"></a><a name="getuserdefinedtype"></a>IDispEventImpl::GetUserDefinedType

Récupère le type de base d’un type défini par l’utilisateur.

```
VARTYPE GetUserDefinedType(
    ITypeInfo* pTI,
    HREFTYPE hrt);
```

### <a name="parameters"></a>Paramètres

*Pti*<br/>
[dans] Un pointeur sur l’interface [ITypeInfo](/windows/win32/api/oaidl/nn-oaidl-itypeinfo) contenant le type défini par l’utilisateur.

*Hrt*<br/>
[dans] Une poignée à la description de type à récupérer.

### <a name="return-value"></a>Valeur de retour

Le type de variante.

### <a name="remarks"></a>Notes

Voir [ITypeInfo::GetRefTypeInfo](/windows/win32/api/oaidl/nf-oaidl-itypeinfo-getreftypeinfo).

## <a name="idispeventimplidispeventimpl"></a><a name="idispeventimpl"></a>IDispEventImpl::IDispEventImpl

Constructeur. Stocke les valeurs des paramètres de modèle de classe *plibid*, *pdiid*, *wMajor*, et *wMinor*.

```
IDispEventImpl();
```

## <a name="idispeventimpltihclass"></a><a name="tihclass"></a>IDispEventImpl::tihclass

Ce typedef est une instance du paramètre de la classe *tihclass*.

```
typedef tihclass _tihclass;
```

### <a name="remarks"></a>Notes

Par défaut, la `CComTypeInfoHolder`classe est . `CComTypeInfoHolder`gère les informations de type pour la classe.

## <a name="see-also"></a>Voir aussi

[Structure _ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md)<br/>
[Classe IDispatchImpl](../../atl/reference/idispatchimpl-class.md)<br/>
[Classe IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)<br/>
[SINK_ENTRY](composite-control-macros.md#sink_entry)<br/>
[SINK_ENTRY_EX](composite-control-macros.md#sink_entry_ex)<br/>
[SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
