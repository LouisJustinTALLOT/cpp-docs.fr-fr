---
title: Interface IAxWinHostWindowLic | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IAxWinHostWindowLic
- No header/ATL::IAxWinHostWindowLic
- No header/ATL::CreateControlLic
- No header/ATL::CreateControlLicEx
dev_langs: C++
helpviewer_keywords: IAxWinHostWindowLic interface
ms.assetid: 750f1520-6bce-428c-aca0-fccbe3f063c7
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2e74029025daeb18a3c63459845ef9edf4ca69cb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="iaxwinhostwindowlic-interface"></a>Interface IAxWinHostWindowLic
Cette interface fournit des méthodes pour manipuler un contrôle sous licence et son objet ordinateur hôte.  
  
## <a name="syntax"></a>Syntaxe  
  
```
interface IAxWinHostWindowLic : IAxWinHostWindow
```  
  
## <a name="members"></a>Membres  
  
### <a name="methods"></a>Méthodes  
  
|||  
|-|-|  
|[CreateControlLic](#createcontrollic)|Crée un contrôle sous licence et l’attache à l’objet hôte.|  
|[CreateControlLicEx](#createcontrollicex)|Crée un contrôle sous licence, attache à l’objet hôte et définit éventuellement un gestionnaire d’événements.|  
  
## <a name="remarks"></a>Remarques  
 `IAxWinHostWindowLic`hérite de [interface IAxWinHostWindow](../../atl/reference/iaxwinhostwindow-interface.md) et ajoute des méthodes qui prennent en charge la création de contrôles sous licence.  
  
 Consultez [hébergement ActiveX des contrôles à l’aide de ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) pour obtenir un exemple qui utilise les membres de cette interface.  
  
## <a name="requirements"></a>Spécifications  
 La définition de cette interface est disponible en tant que fichier IDL ou C++, comme indiqué ci-dessous.  
  
|Type de définition|Fichier|  
|---------------------|----------|  
|IDL|ATLIFace.idl|  
|C++|ATLIFace.h (également inclus dans ATLBase.h)|  
  
##  <a name="createcontrollic"></a>IAxWinHostWindowLic::CreateControlLic  
 Crée un contrôle sous licence, il initialise et héberge ce dernier dans la fenêtre identifiée par `hWnd`.  
  
```
STDMETHOD(CreateControlLic)(
    LPCOLESTR lpTricsData,
    HWND hWnd,
    IStream* pStream,
    BSTR bstrLic);
```  
  
### <a name="parameters"></a>Paramètres  
 `bstrLic`  
 [in] Le BSTR qui contient la clé de licence pour le contrôle.  
  
### <a name="remarks"></a>Remarques  
 Consultez [IAxWinHostWindow::CreateControl](../../atl/reference/iaxwinhostwindow-interface.md#createcontrol) pour obtenir une description de la valeur de retour et de paramètres restants.  
  
 Appel de cette méthode équivaut à appeler la méthode [IAxWinHostWindowLic::CreateControlLicEx](#createcontrollicex)  
  
### <a name="example"></a>Exemple  
 Consultez [hébergement ActiveX des contrôles à l’aide de ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) pour obtenir un exemple qui utilise `IAxWinHostWindowLic::CreateControlLic`.  
  
##  <a name="createcontrollicex"></a>IAxWinHostWindowLic::CreateControlLicEx  
 Crée un contrôle ActiveX sous licence, il initialise et héberge ce dernier dans la fenêtre spécifiée, semblable à [IAxWinHostWindow::CreateControl](../../atl/reference/iaxwinhostwindow-interface.md#createcontrol).  
  
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
 `bstrLic`  
 [in] Le BSTR qui contient la clé de licence pour le contrôle.  
  
### <a name="remarks"></a>Remarques  
 Consultez [IAxWinHostWindow::CreateControlEx](../../atl/reference/iaxwinhostwindow-interface.md#createcontrolex) pour obtenir une description de la valeur de retour et de paramètres restants.  
  
### <a name="example"></a>Exemple  
 Consultez [hébergement ActiveX des contrôles à l’aide de ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) pour obtenir un exemple qui utilise `IAxWinHostWindowLic::CreateControlLicEx`.









