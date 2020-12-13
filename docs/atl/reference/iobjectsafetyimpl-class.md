---
description: 'En savoir plus sur : classe IObjectSafetyImpl'
title: IObjectSafetyImpl, classe
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
ms.openlocfilehash: ac19fe24d12d7d09968b3e2d76f77741e83e1f81
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97139462"
---
# <a name="iobjectsafetyimpl-class"></a>IObjectSafetyImpl, classe

Cette classe fournit une implémentation par défaut de l' `IObjectSafety` interface pour permettre à un client de récupérer et de définir les niveaux de sécurité d’un objet.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class T,DWORD dwSupportedSafety>
class IObjectSafetyImpl
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, dérivée de `IObjectSafetyImpl` .

*dwSupportedSafety*<br/>
Spécifie les options de sécurité prises en charge pour le contrôle. Il peut s'agir de l'une des valeurs suivantes :

- INTERFACESAFE_FOR_UNTRUSTED_CALLER l’interface identifiée par le paramètre [SetInterfaceSafetyOptions](#setinterfacesafetyoptions) `riid` doit être rendue sécurisée pour les scripts.

- INTERFACESAFE_FOR_UNTRUSTED_DATA l’interface identifiée par le `SetInterfaceSafetyOptions` paramètre `riid` doit être rendue sécurisée pour les données non fiables pendant l’initialisation.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IObjectSafetyImpl :: GetInterfaceSafetyOptions](#getinterfacesafetyoptions)|Récupère les options de sécurité prises en charge par l’objet, ainsi que les options de sécurité actuellement définies pour l’objet.|
|[IObjectSafetyImpl :: SetInterfaceSafetyOptions](#setinterfacesafetyoptions)|Rend l’objet sécurisé pour l’initialisation ou l’écriture de scripts.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[IObjectSafetyImpl :: m_dwCurrentSafety](#m_dwcurrentsafety)|Stocke le niveau de sécurité actuel de l’objet.|

## <a name="remarks"></a>Notes

`IObjectSafetyImpl`La classe fournit une implémentation par défaut de `IObjectSafety` . L' `IObjectSafety` interface permet à un client de récupérer et de définir les niveaux de sécurité d’un objet. Par exemple, un navigateur Web peut appeler `IObjectSafety::SetInterfaceSafetyOptions` pour rendre un contrôle sécurisé pour l’initialisation ou pour l’écriture de scripts sécurisés.

Notez que l’utilisation de la macro [IMPLEMENTED_CATEGORY](category-macros.md#implemented_category) avec les catégories de composants CATID_SafeForScripting et CATID_SafeForInitializing offre une autre manière de spécifier la sécurité d’un composant.

**Articles connexes** [Didacticiel ATL](../../atl/active-template-library-atl-tutorial.md), [création d’un projet ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IObjectSafety`

`IObjectSafetyImpl`

## <a name="requirements"></a>Spécifications

**En-tête :** atlctl. h

## <a name="iobjectsafetyimplgetinterfacesafetyoptions"></a><a name="getinterfacesafetyoptions"></a> IObjectSafetyImpl :: GetInterfaceSafetyOptions

Récupère les options de sécurité prises en charge par l’objet, ainsi que les options de sécurité actuellement définies pour l’objet.

```
HRESULT GetInterfaceSafetyOptions(
    REFIID riid,
    DWORD* pdwSupportedOptions,
    DWORD* pdwEnabledOptions);
```

### <a name="remarks"></a>Notes

L’implémentation retourne les valeurs appropriées pour toutes les interfaces prises en charge par l’implémentation de l’objet de `IUnknown::QueryInterface` .

> [!IMPORTANT]
> Tout objet qui prend en charge `IObjectSafety` est responsable de sa propre sécurité et de tout objet qu’il délègue. Le programmeur doit prendre en compte les problèmes liés à l’exécution du code dans le contexte de l’utilisateur, aux scripts intersites et à l’exécution de la vérification de zone appropriée.

Consultez [IObjectSafety :: GetInterfaceSafetyOptions](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768223\(v=vs.85\)) dans la SDK Windows.

## <a name="iobjectsafetyimplm_dwcurrentsafety"></a><a name="m_dwcurrentsafety"></a> IObjectSafetyImpl :: m_dwCurrentSafety

Stocke le niveau de sécurité actuel de l’objet.

```
DWORD m_dwCurrentSafety;
```

## <a name="iobjectsafetyimplsetinterfacesafetyoptions"></a><a name="setinterfacesafetyoptions"></a> IObjectSafetyImpl :: SetInterfaceSafetyOptions

Rend l’objet sécurisé pour l’initialisation ou l’écriture de scripts en affectant à la [m_dwCurrentSafety](#m_dwcurrentsafety) membre la valeur appropriée.

```
HRESULT SetInterfaceSafetyOptions(
    REFIID riid,
    DWORD dwOptionsSetMask,
    DWORD dwEnabledOptions);
```

### <a name="remarks"></a>Notes

L’implémentation retourne E_NOINTERFACE pour toute interface non prise en charge par l’implémentation de l’objet de `IUnknown::QueryInterface` .

> [!IMPORTANT]
> Tout objet qui prend en charge `IObjectSafety` est responsable de sa propre sécurité et de tout objet qu’il délègue. Le programmeur doit prendre en compte les problèmes liés à l’exécution du code dans le contexte de l’utilisateur, aux scripts intersites et à l’exécution de la vérification de zone appropriée.

Consultez [IObjectSafety :: SetInterfaceSafetyOptions](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768225\(v=vs.85\)) dans la SDK Windows.

## <a name="see-also"></a>Voir aussi

[Interface IObjectSafety](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768224\(v=vs.85\))<br/>
[Vue d'ensemble des classes](../../atl/atl-class-overview.md)
