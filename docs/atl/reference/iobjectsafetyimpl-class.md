---
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
ms.openlocfilehash: e9035a8573a917e732f3452aeb7fd07af160517f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50471784"
---
# <a name="iobjectsafetyimpl-class"></a>IObjectSafetyImpl, classe

Cette classe fournit une implémentation par défaut de la `IObjectSafety` interface pour permettre à un client récupérer et définir des niveaux de sécurité d’un objet.

> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class T,DWORD dwSupportedSafety>
class IObjectSafetyImpl
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Votre classe, dérivée de `IObjectSafetyImpl`.

*dwSupportedSafety*<br/>
Spécifie les options de sécurité pris en charge pour le contrôle. Peut avoir l'une des valeurs suivantes :

- INTERFACESAFE_FOR_UNTRUSTED_CALLER l’interface identifiée par le [SetInterfaceSafetyOptions](#setinterfacesafetyoptions) paramètre `riid` doivent être effectuées sans échec pour le script.

- INTERFACESAFE_FOR_UNTRUSTED_DATA l’interface identifiée par le `SetInterfaceSafetyOptions` paramètre `riid` doivent être effectuées sans échec pour les données non fiables pendant l’initialisation.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[IObjectSafetyImpl::GetInterfaceSafetyOptions](#getinterfacesafetyoptions)|Récupère les options de sécurité pris en charge par l’objet, ainsi que les options de sécurité actuellement définies pour l’objet.|
|[IObjectSafetyImpl::SetInterfaceSafetyOptions](#setinterfacesafetyoptions)|Sécurise l’objet pour l’initialisation ou de script.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[IObjectSafetyImpl::m_dwCurrentSafety](#m_dwcurrentsafety)|Stocke le niveau actuel de la sécurité de l’objet.|

## <a name="remarks"></a>Notes

Classe `IObjectSafetyImpl` fournit une implémentation par défaut de `IObjectSafety`. Le `IObjectSafety` interface permet à un client récupérer et définir des niveaux de sécurité d’un objet. Par exemple, un navigateur web peut appeler `IObjectSafety::SetInterfaceSafetyOptions` pour rendre un contrôle pour l’initialisation ou sécurisé pour le script.

Notez que l’utilisation du [IMPLEMENTED_CATEGORY](category-macros.md#implemented_category) macro avec les catégories de composant CATID_SafeForScripting et CATID_SafeForInitializing vous permet également de spécifier qu’un composant est sécurisé.

**Articles connexes** [didacticiel ATL](../../atl/active-template-library-atl-tutorial.md), [création d’un projet ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`IObjectSafety`

`IObjectSafetyImpl`

## <a name="requirements"></a>Configuration requise

**En-tête :** atlctl.h

##  <a name="getinterfacesafetyoptions"></a>  IObjectSafetyImpl::GetInterfaceSafetyOptions

Récupère les options de sécurité pris en charge par l’objet, ainsi que les options de sécurité actuellement définies pour l’objet.

```
HRESULT GetInterfaceSafetyOptions(
    REFIID riid,
    DWORD* pdwSupportedOptions,
    DWORD* pdwEnabledOptions);
```

### <a name="remarks"></a>Notes

L’implémentation retourne les valeurs appropriées pour n’importe quelle interface prise en charge par l’implémentation de l’objet de `IUnknown::QueryInterface`.

> [!IMPORTANT]
>  N’importe quel objet qui prend en charge `IObjectSafety` est responsable de sa propre sécurité et celle de n’importe quel objet elle délègue. Le programmeur doit prendre en considération les questions découlant de l’exécution de code dans le contexte de l’utilisateur, les scripts entre sites et effectuer une vérification de la zone appropriée.

Consultez [IObjectSafety::GetInterfaceSafetyOptions](https://msdn.microsoft.com/library/aa768223.aspx) dans le Kit de développement logiciel Windows.

##  <a name="m_dwcurrentsafety"></a>  IObjectSafetyImpl::m_dwCurrentSafety

Stocke le niveau actuel de la sécurité de l’objet.

```
DWORD m_dwCurrentSafety;
```

##  <a name="setinterfacesafetyoptions"></a>  IObjectSafetyImpl::SetInterfaceSafetyOptions

Rend l’objet sécurisé pour l’initialisation ou de scripts en définissant le [m_dwCurrentSafety](#m_dwcurrentsafety) membre à la valeur appropriée.

```
HRESULT SetInterfaceSafetyOptions(
    REFIID riid,
    DWORD dwOptionsSetMask,
    DWORD dwEnabledOptions);
```

### <a name="remarks"></a>Notes

L’implémentation retourne E_NOINTERFACE pour n’importe quelle interface ne pas pris en charge par l’implémentation de l’objet de `IUnknown::QueryInterface`.

> [!IMPORTANT]
>  N’importe quel objet qui prend en charge `IObjectSafety` est responsable de sa propre sécurité et celle de n’importe quel objet elle délègue. Le programmeur doit prendre en considération les questions découlant de l’exécution de code dans le contexte de l’utilisateur, les scripts entre sites et effectuer une vérification de la zone appropriée.

Consultez [IObjectSafety::SetInterfaceSafetyOptions](https://msdn.microsoft.com/library/aa768225.aspx) dans le Kit de développement logiciel Windows.

## <a name="see-also"></a>Voir aussi

[Interface IObjectSafety](https://msdn.microsoft.com/library/aa768224.aspx)<br/>
[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
