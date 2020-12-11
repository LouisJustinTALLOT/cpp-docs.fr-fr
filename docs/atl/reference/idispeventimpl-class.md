---
description: 'En savoir plus sur : IDispEventImpl, classe'
title: IDispEventImpl (classe)
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
ms.openlocfilehash: 7266052da8985791bdb85682b37572241cb0535b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97158385"
---
# <a name="idispeventimpl-class"></a>IDispEventImpl (classe)

Cette classe fournit des implémentations des `IDispatch` méthodes.

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
Identificateur unique de l’objet source. Quand `IDispEventImpl` est la classe de base d’un contrôle composite, utilisez l’ID de ressource du contrôle contenu de votre choix pour ce paramètre. Dans d’autres cas, utilisez un entier positif arbitraire.

*T*<br/>
Classe de l’utilisateur, dérivée de `IDispEventImpl` .

*pdiid*<br/>
Pointeur vers l’IID de l’dispinterface d’événement implémentée par cette classe. Cette interface doit être définie dans la bibliothèque de types dénotée par *plibid*, *wMajor* et *wMinor*.

*plibid*<br/>
Pointeur vers la bibliothèque de types qui définit l’interface de dispatch vers laquelle pointe *pdiid*. Si **&GUID_NULL**, la bibliothèque de types est chargée à partir de l’objet source des événements.

*wMajor*<br/>
Version principale de la bibliothèque de types. La valeur par défaut est 0.

*wMinor*<br/>
Version secondaire de la bibliothèque de types. La valeur par défaut est 0.

*tihclass*<br/>
Classe utilisée pour gérer les informations de type pour *T*. La valeur par défaut est une classe de type `CComTypeInfoHolder` ; Toutefois, vous pouvez substituer ce paramètre de modèle en fournissant une classe d’un type autre que `CComTypeInfoHolder` .

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|[IDispEventImpl :: _tihclass](../../atl/reference/idispeventimpl-class.md)|Classe utilisée pour gérer les informations de type. Par défaut, `CComTypeInfoHolder`.|

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[IDispEventImpl :: IDispEventImpl](#idispeventimpl)|Constructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IDispEventImpl :: GetFuncInfoFromId](#getfuncinfofromid)|Localise l’index de fonction pour l’identificateur de dispatch spécifié.|
|[IDispEventImpl :: GetIDsOfNames](#getidsofnames)|Mappe un membre unique et un ensemble facultatif de noms d’arguments à un jeu correspondant de DISPID entier.|
|[IDispEventImpl :: GetTypeInfo](#gettypeinfo)|Récupère les informations de type pour un objet.|
|[IDispEventImpl :: GetTypeInfoCount](#gettypeinfocount)|Récupère le nombre d’interfaces d’informations de type.|
|[IDispEventImpl :: GetUserDefinedType](#getuserdefinedtype)|Récupère le type de base d’un type défini par l’utilisateur.|

## <a name="remarks"></a>Notes

`IDispEventImpl` fournit un moyen d’implémenter une dispinterface d’événement sans vous obliger à fournir le code d’implémentation pour chaque méthode/événement sur cette interface. `IDispEventImpl` fournit des implémentations des `IDispatch` méthodes. Il vous suffit de fournir des implémentations pour les événements que vous souhaitez gérer.

`IDispEventImpl` fonctionne conjointement avec le mappage de récepteur d’événements dans votre classe pour acheminer les événements vers la fonction de gestionnaire appropriée. Pour utiliser cette classe :

Ajoutez une macro [SINK_ENTRY](composite-control-macros.md#sink_entry) ou [SINK_ENTRY_EX](composite-control-macros.md#sink_entry_ex) au mappage de récepteur d’événements pour chaque événement de chaque objet que vous souhaitez gérer. Quand `IDispEventImpl` vous utilisez comme classe de base d’un contrôle composite, vous pouvez appeler [AtlAdviseSinkMap](connection-point-global-functions.md#atladvisesinkmap) pour établir et rompre la connexion avec les sources d’événements pour toutes les entrées dans la table de récepteurs d’événements. Dans d’autres cas, ou pour un contrôle plus important, appelez [DispEventAdvise](idispeventsimpleimpl-class.md#dispeventadvise) pour établir la connexion entre l’objet source et la classe de base. Appelez [DispEventUnadvise](idispeventsimpleimpl-class.md#dispeventunadvise) pour rompre la connexion.

Vous devez dériver de `IDispEventImpl` (à l’aide d’une valeur unique pour *nid*) pour chaque objet pour lequel vous devez gérer des événements. Vous pouvez réutiliser la classe de base en désexaminant un objet source, puis en vous avertissant par rapport à un objet source différent, mais le nombre maximal d’objets sources qui peuvent être gérés par un seul objet à la fois est limité par le nombre de `IDispEventImpl` classes de base.

`IDispEventImpl` fournit les mêmes fonctionnalités que [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md), sauf qu’il obtient des informations de type sur l’interface à partir d’une bibliothèque de types au lieu de l’avoir fournie comme pointeur vers une structure [_ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md) . Utilisez `IDispEventSimpleImpl` si vous n’avez pas de bibliothèque de types décrivant l’interface d’événement ou si vous souhaitez éviter la surcharge associée à l’utilisation de la bibliothèque de types.

> [!NOTE]
> `IDispEventImpl` et `IDispEventSimpleImpl` fournissent leur propre implémentation de `IUnknown::QueryInterface` permettant `IDispEventImpl` à chaque `IDispEventSimpleImpl` classe de base d’agir en tant qu’identité com distincte tout en autorisant l’accès direct aux membres de classe dans votre objet com principal.

L’implémentation ATL CE des récepteurs d’événements ActiveX ne prend en charge que les valeurs de retour de type HRESULT ou void de vos méthodes de gestionnaire d’événements ; toute autre valeur de retour n’est pas prise en charge et son comportement n’est pas défini.

Pour plus d’informations, consultez [prise en charge de IDispEventImpl](../../atl/supporting-idispeventimpl.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`_IDispEvent`

`_IDispEventLocator`

[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)

`IDispEventImpl`

## <a name="requirements"></a>Spécifications

**En-tête :** atlcom. h

## <a name="idispeventimplgetfuncinfofromid"></a><a name="getfuncinfofromid"></a> IDispEventImpl :: GetFuncInfoFromId

Localise l’index de fonction pour l’identificateur de dispatch spécifié.

```
HRESULT GetFuncInfoFromId(
    const IID& iid,
    DISPID dispidMember,
    LCID lcid,
    _ATL_FUNC_INFO& info);
```

### <a name="parameters"></a>Paramètres

*vaut*<br/>
dans Référence à l’ID de la fonction.

*dispidMember*<br/>
dans ID de dispatch de la fonction.

*lcid*<br/>
dans Contexte des paramètres régionaux de l’ID de la fonction.

*info*<br/>
dans Structure indiquant comment la fonction est appelée.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

## <a name="idispeventimplgetidsofnames"></a><a name="getidsofnames"></a> IDispEventImpl :: GetIDsOfNames

Mappe un membre unique et un ensemble facultatif de noms d’arguments à un ensemble correspondant de DISPID entier, qui peut être utilisé lors des appels suivants à [IDispatch :: Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke).

```
STDMETHOD(GetIDsOfNames)(
    REFIID riid,
    LPOLESTR* rgszNames,
    UINT cNames,
    LCID lcid,
    DISPID* rgdispid);
```

### <a name="remarks"></a>Notes

Consultez [IDispatch :: GetIDsOfNames](/windows/win32/api/oaidl/nf-oaidl-idispatch-getidsofnames) dans le SDK Windows.

## <a name="idispeventimplgettypeinfo"></a><a name="gettypeinfo"></a> IDispEventImpl :: GetTypeInfo

Récupère les informations de type pour un objet, qui peuvent être utilisées ensuite pour obtenir les informations de type d'une interface.

```
STDMETHOD(GetTypeInfo)(
    UINT itinfo,
    LCID lcid,
    ITypeInfo** pptinfo);
```

### <a name="remarks"></a>Notes

## <a name="idispeventimplgettypeinfocount"></a><a name="gettypeinfocount"></a> IDispEventImpl :: GetTypeInfoCount

Récupère le nombre d'interfaces d'informations de type fourni par un objet (0 ou 1).

```
STDMETHOD(GetTypeInfoCount)(UINT* pctinfo);
```

### <a name="remarks"></a>Notes

Consultez [IDispatch :: GetTypeInfoCount](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfocount) dans la SDK Windows.

## <a name="idispeventimplgetuserdefinedtype"></a><a name="getuserdefinedtype"></a> IDispEventImpl :: GetUserDefinedType

Récupère le type de base d’un type défini par l’utilisateur.

```
VARTYPE GetUserDefinedType(
    ITypeInfo* pTI,
    HREFTYPE hrt);
```

### <a name="parameters"></a>Paramètres

*pTI*<br/>
dans Pointeur vers l’interface [ITypeInfo](/windows/win32/api/oaidl/nn-oaidl-itypeinfo) contenant le type défini par l’utilisateur.

*hrt*<br/>
dans Handle de la description de type à récupérer.

### <a name="return-value"></a>Valeur renvoyée

Type de variant.

### <a name="remarks"></a>Notes

Consultez [ITypeInfo :: GetRefTypeInfo](/windows/win32/api/oaidl/nf-oaidl-itypeinfo-getreftypeinfo).

## <a name="idispeventimplidispeventimpl"></a><a name="idispeventimpl"></a> IDispEventImpl :: IDispEventImpl

Constructeur. Stocke les valeurs des paramètres de modèle de classe *plibid*, *pdiid*, *wMajor* et *wMinor*.

```
IDispEventImpl();
```

## <a name="idispeventimpltihclass"></a><a name="tihclass"></a> IDispEventImpl :: tihclass

Ce typedef est une instance du paramètre de modèle de classe *tihclass*.

```
typedef tihclass _tihclass;
```

### <a name="remarks"></a>Notes

Par défaut, la classe est `CComTypeInfoHolder` . `CComTypeInfoHolder` gère les informations de type pour la classe.

## <a name="see-also"></a>Voir aussi

[Structure _ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md)<br/>
[Classe IDispatchImpl](../../atl/reference/idispatchimpl-class.md)<br/>
[IDispEventSimpleImpl, classe](../../atl/reference/idispeventsimpleimpl-class.md)<br/>
[SINK_ENTRY](composite-control-macros.md#sink_entry)<br/>
[SINK_ENTRY_EX](composite-control-macros.md#sink_entry_ex)<br/>
[SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
