---
title: Classe IObjectSafetyImpl
ms.date: 11/04/2016
f1_keywords:
- IObjectSafetyImpl
- ATLCTL/ATL::IObjectSafetyImpl
- ATLCTL/ATL::IObjectSafetyImpl::GetInterfaceSafetyOptions
- ATLCTL/ATL::IObjectSafetyImpl::SetInterfaceSafetyOptions
- ATLCTL/ATL::IObjectSafetyImpl::m_dwCurrentSafety
helpviewer_keywords:
- controls [ATL], safe
- safe for scripting and initialization (controls)
- IObjectSafety, ATL implementation
- IObjectSafetyImpl class
ms.assetid: 64e32082-d910-4a8a-a5bf-ebed9145359d
ms.openlocfilehash: 6eee7585bc3c5587e106ab6b0cefb4b7129df59f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329663"
---
# <a name="iobjectsafetyimpl-class"></a>Classe IObjectSafetyImpl

Cette classe fournit une `IObjectSafety` implémentation par défaut de l’interface pour permettre à un client de récupérer et de définir les niveaux de sécurité d’un objet.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class T,DWORD dwSupportedSafety>
class IObjectSafetyImpl
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, `IObjectSafetyImpl`dérivée de .

*dwSupportedSafety dwSupportedSafety dwSupportedSafety dw*<br/>
Spécifie les options de sécurité prises en charge pour le contrôle. Il peut s'agir de l'une des valeurs suivantes :

- INTERFACESAFE_FOR_UNTRUSTED_CALLER L’interface identifiée par le paramètre `riid` [SetInterfaceSafetyOptions](#setinterfacesafetyoptions) doit être sécurisée pour le script.

- INTERFACESAFE_FOR_UNTRUSTED_DATA L’interface identifiée par `SetInterfaceSafetyOptions` `riid` le paramètre doit être sécurisée pour les données non fiables lors de l’initialisation.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IObjectSafetyImpl::GetInterfaceSafetyOptions](#getinterfacesafetyoptions)|Récupère les options de sécurité prises en charge par l’objet, ainsi que les options de sécurité actuellement définies pour l’objet.|
|[IObjectSafetyImpl::SetInterfaceSafetyOptions](#setinterfacesafetyoptions)|Rend l’objet sûr pour l’initialisation ou le script.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[IObjectSafetyImpl::m_dwCurrentSafety](#m_dwcurrentsafety)|Stocke le niveau de sécurité actuel de l’objet.|

## <a name="remarks"></a>Notes

La `IObjectSafetyImpl` classe fournit `IObjectSafety`une mise en œuvre par défaut de . L’interface `IObjectSafety` permet à un client de récupérer et de définir les niveaux de sécurité d’un objet. Par exemple, un navigateur `IObjectSafety::SetInterfaceSafetyOptions` Web peut appeler pour rendre un contrôle sûr pour l’initialisation ou sans danger pour le script.

Notez que l’utilisation de la macro [IMPLEMENTED_CATEGORY](category-macros.md#implemented_category) avec les catégories de composants CATID_SafeForScripting et CATID_SafeForInitializing fournit une autre façon de spécifier qu’un composant est sûr.

**Articles connexes** [ATL Tutorial](../../atl/active-template-library-atl-tutorial.md), Création [d’un projet ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IObjectSafety`

`IObjectSafetyImpl`

## <a name="requirements"></a>Spécifications

**En-tête:** atlctl.h

## <a name="iobjectsafetyimplgetinterfacesafetyoptions"></a><a name="getinterfacesafetyoptions"></a>IObjectSafetyImpl::GetInterfaceSafetyOptions

Récupère les options de sécurité prises en charge par l’objet, ainsi que les options de sécurité actuellement définies pour l’objet.

```
HRESULT GetInterfaceSafetyOptions(
    REFIID riid,
    DWORD* pdwSupportedOptions,
    DWORD* pdwEnabledOptions);
```

### <a name="remarks"></a>Notes

La mise en œuvre renvoie les valeurs `IUnknown::QueryInterface`appropriées pour toute interface supportée par la mise en œuvre de l’objet de .

> [!IMPORTANT]
> Tout objet `IObjectSafety` qui prend en charge est responsable de sa propre sécurité, et de tout objet qu’il délègue. Le programmeur doit tenir compte des problèmes découlant de l’exécution du code dans le contexte de l’utilisateur, le script inter-site et effectuer des vérifications de zone appropriées.

Voir [IObjectSafety:GetInterfaceSafetyOptions](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768223\(v=vs.85\)) in the Windows SDK.

## <a name="iobjectsafetyimplm_dwcurrentsafety"></a><a name="m_dwcurrentsafety"></a>IObjectSafetyImpl::m_dwCurrentSafety

Stocke le niveau de sécurité actuel de l’objet.

```
DWORD m_dwCurrentSafety;
```

## <a name="iobjectsafetyimplsetinterfacesafetyoptions"></a><a name="setinterfacesafetyoptions"></a>IObjectSafetyImpl::SetInterfaceSafetyOptions

Rend l’objet sûr pour l’initialisation ou le script en définissant le [m_dwCurrentSafety](#m_dwcurrentsafety) membre à la valeur appropriée.

```
HRESULT SetInterfaceSafetyOptions(
    REFIID riid,
    DWORD dwOptionsSetMask,
    DWORD dwEnabledOptions);
```

### <a name="remarks"></a>Notes

La mise en œuvre renvoie E_NOINTERFACE pour toute `IUnknown::QueryInterface`interface non prise en charge par la mise en œuvre de l’objet de .

> [!IMPORTANT]
> Tout objet `IObjectSafety` qui prend en charge est responsable de sa propre sécurité, et de tout objet qu’il délègue. Le programmeur doit tenir compte des problèmes découlant de l’exécution du code dans le contexte de l’utilisateur, le script inter-site et effectuer des vérifications de zone appropriées.

Voir [IObjectSafety:SetInterfaceSafetyOptions](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768225\(v=vs.85\)) in the Windows SDK.

## <a name="see-also"></a>Voir aussi

[IObjectSafety Interface](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768224\(v=vs.85\))<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
