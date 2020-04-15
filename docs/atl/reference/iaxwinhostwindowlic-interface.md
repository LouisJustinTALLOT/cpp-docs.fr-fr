---
title: IAxWinHostWindowLic Interface
ms.date: 11/04/2016
f1_keywords:
- IAxWinHostWindowLic
- ATLIFACE/ATL::IAxWinHostWindowLic
- ATLIFACE/ATL::CreateControlLic
- ATLIFACE/ATL::CreateControlLicEx
helpviewer_keywords:
- IAxWinHostWindowLic interface
ms.assetid: 750f1520-6bce-428c-aca0-fccbe3f063c7
ms.openlocfilehash: 561a65702f1d4f57b4db1afc75769ce4cc523c1c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329920"
---
# <a name="iaxwinhostwindowlic-interface"></a>IAxWinHostWindowLic Interface

Cette interface fournit des méthodes pour manipuler un contrôle sous licence et son objet hôte.

## <a name="syntax"></a>Syntaxe

```
interface IAxWinHostWindowLic : IAxWinHostWindow
```

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|||
|-|-|
|[CreateControlLic](#createcontrollic)|Crée un contrôle sous licence et le fixe à l’objet hôte.|
|[CreateControlLicEx](#createcontrollicex)|Crée un contrôle sous licence, l’attache à l’objet hôte et installe en option un gestionnaire d’événements.|

## <a name="remarks"></a>Notes

`IAxWinHostWindowLic`hérite [d’IAxWinHostWindow](../../atl/reference/iaxwinhostwindow-interface.md) et ajoute des méthodes qui soutiennent la création de contrôles sous licence.

Voir [Les contrôles ActiveX d’hébergement à l’aide d’ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) pour un échantillon qui utilise les membres de cette interface.

## <a name="requirements"></a>Spécifications

La définition de cette interface est disponible sous forme d’IDL ou de C, comme indiqué ci-dessous.

|Type de définition|Fichier|
|---------------------|----------|
|Idl|ATLIFace.idl|
|C++|ATLIFace.h (également inclus dans ATLBase.h)|

## <a name="iaxwinhostwindowliccreatecontrollic"></a><a name="createcontrollic"></a>IAxWinHostWindowLic::CreateControlLic

Crée un contrôle sous licence, l’initialise, et `hWnd`l’héberge dans la fenêtre identifiée par .

```
STDMETHOD(CreateControlLic)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream,
    BSTR bstrLic);
```

### <a name="parameters"></a>Paramètres

*bstrLic bstrLic*<br/>
[dans] Le BSTR qui contient la clé de licence pour le contrôle.

### <a name="remarks"></a>Notes

Voir [IAxWinHostWindow::CreateControl](../../atl/reference/iaxwinhostwindow-interface.md#createcontrol) pour une description des paramètres restants et la valeur de retour.

Appeler cette méthode équivaut à appeler [IAxWinHostWindowLic::CreateControlLicEx](#createcontrollicex)

### <a name="example"></a>Exemple

Voir [Hosting ActiveX Controls À l’aide d’ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) pour un échantillon qui utilise `IAxWinHostWindowLic::CreateControlLic`.

## <a name="iaxwinhostwindowliccreatecontrollicex"></a><a name="createcontrollicex"></a>IAxWinHostWindowLic::CreateControlLicEx

Crée un contrôle ActiveX sous licence, l’initialise et l’héberge dans la fenêtre spécifiée, similaire à [IAxWinHostWindow::CreateControl](../../atl/reference/iaxwinhostwindow-interface.md#createcontrol).

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

*bstrLic bstrLic*<br/>
[dans] Le BSTR qui contient la clé de licence pour le contrôle.

### <a name="remarks"></a>Notes

Voir [IAxWinHostWindow::CreateControlEx](../../atl/reference/iaxwinhostwindow-interface.md#createcontrolex) pour une description des paramètres restants et de la valeur de retour.

### <a name="example"></a>Exemple

Voir [Hosting ActiveX Controls À l’aide d’ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) pour un échantillon qui utilise `IAxWinHostWindowLic::CreateControlLicEx`.
