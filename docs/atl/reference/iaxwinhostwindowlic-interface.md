---
title: Interface IAxWinHostWindowLic
ms.date: 11/04/2016
f1_keywords:
- IAxWinHostWindowLic
- ATLIFACE/ATL::IAxWinHostWindowLic
- ATLIFACE/ATL::CreateControlLic
- ATLIFACE/ATL::CreateControlLicEx
helpviewer_keywords:
- IAxWinHostWindowLic interface
ms.assetid: 750f1520-6bce-428c-aca0-fccbe3f063c7
ms.openlocfilehash: d7a63fc63b8abcf8574ea9a2fed2556635dba045
ms.sourcegitcommit: d9c94dcabd94537e304be0261b3263c2071b437b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2020
ms.locfileid: "91352945"
---
# <a name="iaxwinhostwindowlic-interface"></a>Interface IAxWinHostWindowLic

Cette interface fournit des méthodes pour manipuler un contrôle sous licence et son objet hôte.

## <a name="syntax"></a>Syntaxe

```
interface IAxWinHostWindowLic : IAxWinHostWindow
```

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|Nom|Description|
|-|-|
|[CreateControlLic](#createcontrollic)|Crée un contrôle sous licence et l’attache à l’objet hôte.|
|[CreateControlLicEx](#createcontrollicex)|Crée un contrôle sous licence, l’attache à l’objet hôte et configure éventuellement un gestionnaire d’événements.|

## <a name="remarks"></a>Notes

`IAxWinHostWindowLic` hérite de [IAxWinHostWindow](../../atl/reference/iaxwinhostwindow-interface.md) et ajoute des méthodes qui prennent en charge la création de contrôles sous licence.

Consultez [Hébergement de contrôles ActiveX à l’aide d’ATL AxHost](../../atl/atl-control-containment-faq.md#hosting-activex-controls-using-atl-axhost) pour obtenir un exemple qui utilise les membres de cette interface.

## <a name="requirements"></a>Spécifications

La définition de cette interface est disponible en tant que IDL ou C++, comme indiqué ci-dessous.

|Type de définition|Fichier|
|---------------------|----------|
|MIDL|ATLIFace. idl|
|C++|ATLIFace. h (également inclus dans ATLBase. h)|

## <a name="iaxwinhostwindowliccreatecontrollic"></a><a name="createcontrollic"></a> IAxWinHostWindowLic::CreateControlLic

Crée un contrôle sous licence, l’initialise et l’héberge dans la fenêtre identifiée par `hWnd` .

```
STDMETHOD(CreateControlLic)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream,
    BSTR bstrLic);
```

### <a name="parameters"></a>Paramètres

*bstrLic*<br/>
dans BSTR qui contient la clé de licence du contrôle.

### <a name="remarks"></a>Notes

Pour obtenir une description des paramètres restants et de la valeur de retour, consultez [IAxWinHostWindow :: CreateControl](../../atl/reference/iaxwinhostwindow-interface.md#createcontrol) .

L’appel de cette méthode équivaut à appeler [IAxWinHostWindowLic :: CreateControlLicEx](#createcontrollicex)

### <a name="example"></a> Exemple

Consultez [Hébergement de contrôles ActiveX à l’aide d’ATL AxHost](../../atl/atl-control-containment-faq.md#hosting-activex-controls-using-atl-axhost) pour obtenir un exemple qui utilise `IAxWinHostWindowLic::CreateControlLic` .

## <a name="iaxwinhostwindowliccreatecontrollicex"></a><a name="createcontrollicex"></a> IAxWinHostWindowLic::CreateControlLicEx

Crée un contrôle ActiveX sous licence, l’initialise et l’héberge dans la fenêtre spécifiée, similaire à [IAxWinHostWindow :: CreateControl](../../atl/reference/iaxwinhostwindow-interface.md#createcontrol).

```
STDMETHOD(CreateControlLicEx)(
    LPCOLESTR lpszTricsData,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnk,
    REFIID riidAdvise,
    IUnknown* punkAdvise,
    BSTR bstrLic);
```

### <a name="parameters"></a>Paramètres

*bstrLic*<br/>
dans BSTR qui contient la clé de licence du contrôle.

### <a name="remarks"></a>Notes

Pour obtenir une description des paramètres restants et de la valeur de retour, consultez [IAxWinHostWindow :: CreateControlEx](../../atl/reference/iaxwinhostwindow-interface.md#createcontrolex) .

### <a name="example"></a> Exemple

Consultez [Hébergement de contrôles ActiveX à l’aide d’ATL AxHost](../../atl/atl-control-containment-faq.md#hosting-activex-controls-using-atl-axhost) pour obtenir un exemple qui utilise `IAxWinHostWindowLic::CreateControlLicEx` .
