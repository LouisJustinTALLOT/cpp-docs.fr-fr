---
title: Classe de IOleInPlaceActiveObjectImpl | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IOleInPlaceActiveObjectImpl
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::ContextSensitiveHelp
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::EnableModeless
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::GetWindow
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::OnDocWindowActivate
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::OnFrameWindowActivate
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::ResizeBorder
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::TranslateAccelerator
dev_langs:
- C++
helpviewer_keywords:
- IOleInPlaceActiveObjectImpl class
- ActiveX controls [C++], communication between container and control
- IOleInPlaceActiveObject, ATL implementation
ms.assetid: 44e6cc6d-a2dc-4187-98e3-73cf0320dea9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a0d98b8dd082a09de461452b43b70ddeb9431abe
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32365645"
---
# <a name="ioleinplaceactiveobjectimpl-class"></a>Classe de IOleInPlaceActiveObjectImpl
Cette classe fournit des méthodes d’assistance de communication entre un contrôle sur place et son conteneur.  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class T>
class IOleInPlaceActiveObjectImpl
```  
  
#### <a name="parameters"></a>Paramètres  
 `T`  
 Votre classe, dérivée de `IOleInPlaceActiveObjectImpl`.  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[IOleInPlaceActiveObjectImpl::ContextSensitiveHelp](#contextsensitivehelp)|Permet à l’aide contextuelle. L’implémentation ATL retourne **E_NOTIMPL**.|  
|[IOleInPlaceActiveObjectImpl::EnableModeless](#enablemodeless)|Permet de boîtes de dialogue non modale. L’implémentation ATL retourne `S_OK`.|  
|[IOleInPlaceActiveObjectImpl::GetWindow](#getwindow)|Obtient un handle de fenêtre.|  
|[IOleInPlaceActiveObjectImpl::OnDocWindowActivate](#ondocwindowactivate)|Avertit le contrôle lors de la fenêtre de document du conteneur est activée ou désactivée. L’implémentation ATL retourne `S_OK`.|  
|[IOleInPlaceActiveObjectImpl::OnFrameWindowActivate](#onframewindowactivate)|Avertit le contrôle lors de la fenêtre du frame de niveau supérieur du conteneur est activée ou désactivée. L’implémentation ATL retourne|  
|[IOleInPlaceActiveObjectImpl::ResizeBorder](#resizeborder)|Indique au contrôle qu’il a besoin redimensionner ses bordures. L’implémentation ATL retourne `S_OK`.|  
|[IOleInPlaceActiveObjectImpl::TranslateAccelerator](#translateaccelerator)|Traite les messages de touche d’accès rapide de menu à partir du conteneur. L’implémentation ATL retourne **E_NOTIMPL**.|  
  
  
## <a name="remarks"></a>Notes  
 Le [IOleInPlaceActiveObject](http://msdn.microsoft.com/library/windows/desktop/ms691299) interface vous aide à la communication entre un contrôle sur place et de son conteneur ; par exemple, la communication de l’état actif du contrôle et le conteneur et informe le contrôle qu’il doit redimensionner lui-même. Classe `IOleInPlaceActiveObjectImpl` fournit une implémentation par défaut de `IOleInPlaceActiveObject` et prend en charge **IUnknown** en envoyant des informations pour le vidage de builds périphérique en mode débogage.  
  
 **Articles connexes** [didacticiel ATL](../../atl/active-template-library-atl-tutorial.md), [création d’un projet ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `IOleInPlaceActiveObject`  
  
 `IOleInPlaceActiveObjectImpl`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlctl.h  
  
##  <a name="contextsensitivehelp"></a>  IOleInPlaceActiveObjectImpl::ContextSensitiveHelp  
 Permet à l’aide contextuelle.  
  
```
HRESULT ContextSensitiveHelp(BOOL fEnterMode);
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne **E_NOTIMPL**.  
  
### <a name="remarks"></a>Notes  
 Consultez [IOleWindow::ContextSensitiveHelp](http://msdn.microsoft.com/library/windows/desktop/ms680059) dans le Kit de développement logiciel Windows.  
  
##  <a name="enablemodeless"></a>  IOleInPlaceActiveObjectImpl::EnableModeless  
 Permet de boîtes de dialogue non modale.  
  
```
HRESULT EnableModeless(BOOL fEnable);
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne `S_OK`.  
  
### <a name="remarks"></a>Notes  
 Consultez [IOleInPlaceActiveObject::EnableModeless](http://msdn.microsoft.com/library/windows/desktop/ms680115) dans le Kit de développement logiciel Windows.  
  
##  <a name="getwindow"></a>  IOleInPlaceActiveObjectImpl::GetWindow  
 Le conteneur appelle cette fonction pour obtenir le handle de fenêtre du contrôle.  
  
```
HRESULT GetWindow(HWND* phwnd);
```  
  
### <a name="remarks"></a>Notes  
 Certains conteneurs ne fonctionnera pas avec un contrôle qui a été sans fenêtre, même si elle est actuellement fenêtrée. Dans l’implémentation de d’ATL, si le **CComControl::m_bWasOnceWindowless** membre de données est **TRUE**, la fonction retourne **E_FAIL**. Sinon, si \* *phwnd* n’est pas **NULL**, `GetWindow` assigne *phwnd* au membre de données de la classe du contrôle `m_hWnd` et retourne `S_OK`.  
  
 Consultez [IOleWindow::GetWindow](http://msdn.microsoft.com/library/windows/desktop/ms687282) dans le Kit de développement logiciel Windows.  
  
##  <a name="ondocwindowactivate"></a>  IOleInPlaceActiveObjectImpl::OnDocWindowActivate  
 Avertit le contrôle lors de la fenêtre de document du conteneur est activée ou désactivée.  
  
```
HRESULT OnDocWindowActivate(BOOL fActivate);
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne `S_OK`.  
  
### <a name="remarks"></a>Notes  
 Consultez [IOleInPlaceActiveObject::OnDocWindowActivate](http://msdn.microsoft.com/library/windows/desktop/ms687281) dans le Kit de développement logiciel Windows.  
  
##  <a name="onframewindowactivate"></a>  IOleInPlaceActiveObjectImpl::OnFrameWindowActivate  
 Avertit le contrôle lors de la fenêtre du frame de niveau supérieur du conteneur est activée ou désactivée.  
  
```
HRESULT OnFrameWindowActivate(BOOL fActivate);
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne `S_OK`.  
  
### <a name="remarks"></a>Notes  
 Consultez [IOleInPlaceActiveObject::OnFrameWindowActivate](http://msdn.microsoft.com/library/windows/desktop/ms683969) dans le Kit de développement logiciel Windows.  
  
##  <a name="resizeborder"></a>  IOleInPlaceActiveObjectImpl::ResizeBorder  
 Indique au contrôle qu’il a besoin redimensionner ses bordures.  
  
```
HRESULT ResizeBorder(
    LPRECT prcBorder,
    IOleInPlaceUIWindow* pUIWindow,
    BOOL fFrameWindow);
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne `S_OK`.  
  
### <a name="remarks"></a>Notes  
 Consultez [IOleInPlaceActiveObject::ResizeBorder](http://msdn.microsoft.com/library/windows/desktop/ms680053) dans le Kit de développement logiciel Windows.  
  
##  <a name="translateaccelerator"></a>  IOleInPlaceActiveObjectImpl::TranslateAccelerator  
 Traite les messages de touche d’accès rapide de menu à partir du conteneur.  
  
```
HRESULT TranslateAccelerator(LPMSG lpmsg);
```  
  
### <a name="return-value"></a>Valeur de retour  
 Cette méthode prend en charge les valeurs de retour suivantes :  
  
 `S_OK` Si le message a été traduit correctement.  
  
 **S_FALSE** si le message a été traduit pas.  
  
### <a name="remarks"></a>Notes  
 Consultez [IOleInPlaceActiveObject::TranslateAccelerator](http://msdn.microsoft.com/library/windows/desktop/ms693360) dans le Kit de développement logiciel Windows.  
  
## <a name="see-also"></a>Voir aussi  
 [CComControl, classe](../../atl/reference/ccomcontrol-class.md)  
 [Interfaces de contrôles ActiveX](http://msdn.microsoft.com/library/windows/desktop/ms692724)  
 [Vue d’ensemble de la classe](../../atl/atl-class-overview.md)
