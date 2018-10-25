---
title: IDispEventImpl, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IDispEventImpl
- ATLCOM/ATL::IDispEventImpl
- ATLCOM/ATL::IDispEventImpl::IDispEventImpl
- ATLCOM/ATL::IDispEventImpl::GetFuncInfoFromId
- ATLCOM/ATL::IDispEventImpl::GetIDsOfNames
- ATLCOM/ATL::IDispEventImpl::GetTypeInfo
- ATLCOM/ATL::IDispEventImpl::GetTypeInfoCount
- ATLCOM/ATL::IDispEventImpl::GetUserDefinedType
dev_langs:
- C++
helpviewer_keywords:
- IDispEventImpl class
ms.assetid: a64b5288-35cb-4638-aad6-2d15b1c7cf7b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2419b4da0cad2662a246c167938d673429afbf26
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50060896"
---
# <a name="idispeventimpl-class"></a>IDispEventImpl, classe

Cette classe fournit des implémentations de la `IDispatch` méthodes.

> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

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
Identificateur unique de l’objet source. Lorsque `IDispEventImpl` est la classe de base pour un contrôle composite, utilisez l’ID de ressource du contrôle de contenu souhaité pour ce paramètre. Dans d’autres cas, utilisez un entier positif aléatoire.

*T*<br/>
Classe de l’utilisateur, qui est dérivée de `IDispEventImpl`.

*pdiid*<br/>
Pointeur vers l’IID de l’interface des événements implémentée par cette classe. Cette interface doit être définie dans la bibliothèque de types dénotée par *plibid*, *wMajor*, et *wMinor*.

*plibid*<br/>
Un pointeur vers la bibliothèque de types qui définit l’interface de dispatch vers lequel pointe *pdiid*. Si **& GUID_NULL**, la bibliothèque de types sera chargée à partir de l’objet d’approvisionnement en événements.

*wMajor*<br/>
Version principale de la bibliothèque de types. La valeur par défaut est 0.

*wMinor*<br/>
Version secondaire de la bibliothèque de types. La valeur par défaut est 0.

*tihclass*<br/>
La classe utilisée pour gérer les informations de type pour *T*. La valeur par défaut est une classe de type `CComTypeInfoHolder`; Toutefois, vous pouvez remplacer ce paramètre de modèle en fournissant une classe d’un type autre que `CComTypeInfoHolder`.

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|[IDispEventImpl::_tihclass](../../atl/reference/idispeventimpl-class.md)|La classe utilisée pour gérer les informations de type. Par défaut, `CComTypeInfoHolder`.|

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[IDispEventImpl::IDispEventImpl](#idispeventimpl)|Constructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IDispEventImpl::GetFuncInfoFromId](#getfuncinfofromid)|Recherche l’index de la fonction pour l’identificateur de dispatch spécifié.|
|[IDispEventImpl::GetIDsOfNames](#getidsofnames)|Mappe un membre unique et un ensemble facultatif de noms d’arguments à un jeu correspondant d’entier DISPID.|
|[IDispEventImpl::GetTypeInfo](#gettypeinfo)|Récupère les informations de type pour un objet.|
|[IDispEventImpl::GetTypeInfoCount](#gettypeinfocount)|Récupère le nombre d’interfaces d’informations de type.|
|[IDispEventImpl::GetUserDefinedType](#getuserdefinedtype)|Récupère le type de base d’un type défini par l’utilisateur.|

## <a name="remarks"></a>Notes

`IDispEventImpl` offre un moyen de l’implémentation d’une interface des événements sans avoir à fournir un code d’implémentation pour chaque méthode/événement sur cette interface. `IDispEventImpl` Fournit des implémentations de la `IDispatch` méthodes. Vous devez uniquement fournir des implémentations pour les événements que vous êtes intéressé par la gestion des.

`IDispEventImpl` fonctionne conjointement avec la table de récepteur d’événements dans votre classe pour acheminer les événements à la fonction gestionnaire approprié. Pour utiliser cette classe :

Ajouter un [aide de SINK_ENTRY](composite-control-macros.md#sink_entry) ou [SINK_ENTRY_EX](composite-control-macros.md#sink_entry_ex) macro à la table de récepteur d’événements pour chaque événement sur chaque objet que vous souhaitez gérer. Lorsque vous utilisez `IDispEventImpl` une classe de base d’un contrôle composite, vous pouvez appeler la méthode [AtlAdviseSinkMap](connection-point-global-functions.md#atladvisesinkmap) à établir et rompre la connexion avec les sources d’événements pour toutes les entrées de table de récepteur de l’événement. Dans d’autres cas, ou pour un meilleur contrôle, appelez [DispEventAdvise](idispeventsimpleimpl-class.md#dispeventadvise) pour établir la connexion entre l’objet source et la classe de base. Appelez [DispEventUnadvise](idispeventsimpleimpl-class.md#dispeventunadvise) interrompre la connexion.

Vous devez dériver de `IDispEventImpl` (à l’aide d’une valeur unique pour *nID*) pour chaque objet pour lequel vous avez besoin gérer les événements. Vous pouvez réutiliser la classe de base en désinformation par rapport à l’objet d’une seule source puis il conseille ses par rapport à un objet source différente, mais le nombre maximal d’objets de source qui peut être gérée par un seul objet à la fois est limité par le nombre de `IDispEventImpl` classes de base.

`IDispEventImpl` fournit les mêmes fonctionnalités que [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md), sauf qu’il obtient le type d’informations sur l’interface à partir d’une bibliothèque de types, plutôt que d’avoir elle fournie comme un pointeur vers un [les structures _ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md) structure. Utilisez `IDispEventSimpleImpl` lorsque vous sans une bibliothèque de types décrivant l’interface d’événement ou souhaitez éviter la surcharge associée à l’aide de la bibliothèque de types.

> [!NOTE]
> `IDispEventImpl` et `IDispEventSimpleImpl` fournir leur propre implémentation de `IUnknown::QueryInterface` chaque activation `IDispEventImpl` et `IDispEventSimpleImpl` classe d’agir comme une identité COM distincte tout en autorisant un accès direct aux membres de classe dans votre objet COM principal de base.

Implémentation de CE ATL de ActiveX événement récepteurs uniquement prend en charge valeurs de retour de type HRESULT ou void à partir de vos méthodes de gestionnaire d’événements ; toute autre valeur de retour est non pris en charge et son comportement est indéfini.

Pour plus d’informations, consultez [IDispEventImpl prenant en charge](../../atl/supporting-idispeventimpl.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`_IDispEvent`

`_IDispEventLocator`

[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)

`IDispEventImpl`

## <a name="requirements"></a>Configuration requise

**En-tête :** atlcom.h

##  <a name="getfuncinfofromid"></a>  IDispEventImpl::GetFuncInfoFromId

Recherche l’index de la fonction pour l’identificateur de dispatch spécifié.

```
HRESULT GetFuncInfoFromId(
    const IID& iid,
    DISPID dispidMember,
    LCID lcid,
    _ATL_FUNC_INFO& info);
```

### <a name="parameters"></a>Paramètres

*IID*<br/>
[in] Une référence à l’ID de la fonction.

*dispidMember*<br/>
[in] L’ID de dispatch de la fonction.

*lcid*<br/>
[in] Contexte des paramètres régionaux de l’ID de fonction.

*Info*<br/>
[in] La structure indiquant comment la fonction est appelée.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

##  <a name="getidsofnames"></a>  IDispEventImpl::GetIDsOfNames

Mappe un membre unique et un ensemble facultatif de noms d’arguments avec un jeu correspondant d’entier DISPID, ce qui peut être utilisée lors des appels ultérieurs à [IDispatch::Invoke](/previous-versions/windows/desktop/api/oaidl/nf-oaidl-idispatch-invoke).

```
STDMETHOD(GetIDsOfNames)(
    REFIID riid,
    LPOLESTR* rgszNames,
    UINT cNames,
    LCID lcid,
    DISPID* rgdispid);
```

### <a name="remarks"></a>Notes

Consultez [IDispatch::GetIDsOfNames](/previous-versions/windows/desktop/api/oaidl/nf-oaidl-idispatch-getidsofnames) dans le Kit de développement logiciel Windows.

##  <a name="gettypeinfo"></a>  IDispEventImpl::GetTypeInfo

Récupère les informations de type pour un objet, qui peuvent être utilisées ensuite pour obtenir les informations de type d'une interface.

```
STDMETHOD(GetTypeInfo)(
    UINT itinfo,
    LCID lcid,
    ITypeInfo** pptinfo);
```

### <a name="remarks"></a>Notes

##  <a name="gettypeinfocount"></a>  IDispEventImpl::GetTypeInfoCount

Récupère le nombre d'interfaces d'informations de type fourni par un objet (0 ou 1).

```
STDMETHOD(GetTypeInfoCount)(UINT* pctinfo);
```

### <a name="remarks"></a>Notes

Consultez [IDispatch::GetTypeInfoCount](/previous-versions/windows/desktop/api/oaidl/nf-oaidl-idispatch-gettypeinfocount) dans le Kit de développement logiciel Windows.

##  <a name="getuserdefinedtype"></a>  IDispEventImpl::GetUserDefinedType

Récupère le type de base d’un type défini par l’utilisateur.

```
VARTYPE GetUserDefinedType(
    ITypeInfo* pTI,
    HREFTYPE hrt);
```

### <a name="parameters"></a>Paramètres

*PTI*<br/>
[in] Un pointeur vers le [ITypeInfo](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-itypeinfo) interface qui contient le type défini par l’utilisateur.

*hrt*<br/>
[in] Handle vers la description de type à récupérer.

### <a name="return-value"></a>Valeur de retour

Le type de variante.

### <a name="remarks"></a>Notes

Consultez [ITypeInfo::GetRefTypeInfo a](/previous-versions/windows/desktop/api/oaidl/nf-oaidl-itypeinfo-getreftypeinfo).

##  <a name="idispeventimpl"></a>  IDispEventImpl::IDispEventImpl

Constructeur. Stocke les valeurs des paramètres du modèle de classe *plibid*, *pdiid*, *wMajor*, et *wMinor*.

```
IDispEventImpl();
```

##  <a name="tihclass"></a>  IDispEventImpl::tihclass

Ce typedef est une instance du paramètre de modèle de classe *tihclass*.

```
typedef tihclass _tihclass;
```

### <a name="remarks"></a>Notes

Par défaut, la classe est `CComTypeInfoHolder`. `CComTypeInfoHolder` gère les informations de type pour la classe.

## <a name="see-also"></a>Voir aussi

[_ATL_FUNC_INFO, structure](../../atl/reference/atl-func-info-structure.md)<br/>
[IDispatchImpl, classe](../../atl/reference/idispatchimpl-class.md)<br/>
[IDispEventSimpleImpl, classe](../../atl/reference/idispeventsimpleimpl-class.md)<br/>
[AIDE DE SINK_ENTRY](composite-control-macros.md#sink_entry)<br/>
[SINK_ENTRY_EX](composite-control-macros.md#sink_entry_ex)<br/>
[MACRO SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)