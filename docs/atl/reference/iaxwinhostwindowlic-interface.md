---
title: IAxWinHostWindowLic, Interface | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IAxWinHostWindowLic
- ATLIFACE/ATL::IAxWinHostWindowLic
- ATLIFACE/ATL::CreateControlLic
- ATLIFACE/ATL::CreateControlLicEx
dev_langs:
- C++
helpviewer_keywords:
- IAxWinHostWindowLic interface
ms.assetid: 750f1520-6bce-428c-aca0-fccbe3f063c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8c6b2537f4a4c7ba92a87bfeff2765c3c5e1b274
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46088707"
---
# <a name="iaxwinhostwindowlic-interface"></a>IAxWinHostWindowLic, Interface

Cette interface fournit des méthodes pour manipuler un contrôle sous licence et son objet hôte.

## <a name="syntax"></a>Syntaxe

```
interface IAxWinHostWindowLic : IAxWinHostWindow
```

## <a name="members"></a>Membres

### <a name="methods"></a>Méthodes

|||
|-|-|
|[CreateControlLic](#createcontrollic)|Crée un contrôle sous licence et l’attache à l’objet hôte.|
|[CreateControlLicEx](#createcontrollicex)|Crée un contrôle sous licence, attache à l’objet ordinateur hôte et éventuellement configure un gestionnaire d’événements.|

## <a name="remarks"></a>Notes

`IAxWinHostWindowLic` hérite de [interface IAxWinHostWindow](../../atl/reference/iaxwinhostwindow-interface.md) et ajoute des méthodes qui prennent en charge la création de contrôles sous licence.

Consultez [hébergement ActiveX des contrôles à l’aide de ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) pour obtenir un exemple qui utilise les membres de cette interface.

## <a name="requirements"></a>Configuration requise

La définition de cette interface est disponible en tant que fichier IDL ou C++, comme indiqué ci-dessous.

|Type de définition|Fichier|
|---------------------|----------|
|IDL|ATLIFace.idl|
|C++|ATLIFace.h (également inclus dans ATLBase.h)|

##  <a name="createcontrollic"></a>  IAxWinHostWindowLic::CreateControlLic

Crée un contrôle sous licence, il initialise et héberge ce dernier dans la fenêtre identifiée par `hWnd`.

```
STDMETHOD(CreateControlLic)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream,
    BSTR bstrLic);
```

### <a name="parameters"></a>Paramètres

*bstrLic*<br/>
[in] BSTR contenant la clé de licence pour le contrôle.

### <a name="remarks"></a>Notes

Consultez [IAxWinHostWindow::CreateControl](../../atl/reference/iaxwinhostwindow-interface.md#createcontrol) pour obtenir une description de la valeur de retour et de paramètres restants.

Appel de cette méthode équivaut à appeler [IAxWinHostWindowLic::CreateControlLicEx](#createcontrollicex)

### <a name="example"></a>Exemple

Consultez [hébergement ActiveX des contrôles à l’aide de ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) pour obtenir un exemple qui utilise `IAxWinHostWindowLic::CreateControlLic`.

##  <a name="createcontrollicex"></a>  IAxWinHostWindowLic::CreateControlLicEx

Crée un contrôle ActiveX sous licence, il initialise et héberge ce dernier dans la fenêtre spécifiée, similaire à [IAxWinHostWindow::CreateControl](../../atl/reference/iaxwinhostwindow-interface.md#createcontrol).

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
[in] BSTR contenant la clé de licence pour le contrôle.

### <a name="remarks"></a>Notes

Consultez [IAxWinHostWindow::CreateControlEx](../../atl/reference/iaxwinhostwindow-interface.md#createcontrolex) pour obtenir une description de la valeur de retour et de paramètres restants.

### <a name="example"></a>Exemple

Consultez [hébergement ActiveX des contrôles à l’aide de ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) pour obtenir un exemple qui utilise `IAxWinHostWindowLic::CreateControlLicEx`.

