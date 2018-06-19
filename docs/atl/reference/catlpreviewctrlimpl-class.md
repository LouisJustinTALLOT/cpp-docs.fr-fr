---
title: Classe de CAtlPreviewCtrlImpl | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAtlPreviewCtrlImpl
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::CAtlPreviewCtrlImpl
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::Create
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::Destroy
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::Focus
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::OnPaint
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::Redraw
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::SetHost
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::SetPreviewVisuals
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::SetRect
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::DoPaint
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::m_plf
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::m_clrBack
- ATLPREVIEWCTRLIMPL/ATL::CAtlPreviewCtrlImpl::m_clrText
dev_langs:
- C++
helpviewer_keywords:
- CAtlPreviewCtrlImpl class
ms.assetid: 39b3299e-07e4-4abc-9b6e-b54bfa3b0802
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 926076115a19b8c9669ec03958d841f08417e89c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32362185"
---
# <a name="catlpreviewctrlimpl-class"></a>Classe de CAtlPreviewCtrlImpl
Cette classe est une implémentation d’une fenêtre qui est placée dans une fenêtre hôte fournie par l’interpréteur de commandes pour l’aperçu riche d’ATL.  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CAtlPreviewCtrlImpl : public CWindowImpl<CAtlPreviewCtrlImpl>, public IPreviewCtrl;
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CAtlPreviewCtrlImpl :: ~ CAtlPreviewCtrlImpl](#dtor)|Destruction d’un objet de contrôle de version préliminaire.|  
|[CAtlPreviewCtrlImpl::CAtlPreviewCtrlImpl](#catlpreviewctrlimpl)|Construit un objet de contrôle de version préliminaire.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CAtlPreviewCtrlImpl::Create](#create)|Appelée par un gestionnaire d’aperçu riche pour créer la fenêtre Windows.|  
|[CAtlPreviewCtrlImpl::Destroy](#destroy)|Appelée par un gestionnaire d’aperçu riche lorsqu’il a besoin détruire ce contrôle.|  
|[CAtlPreviewCtrlImpl::Focus](#focus)|Définit le focus à ce contrôle.|  
|[CAtlPreviewCtrlImpl::OnPaint](#onpaint)|Gère le message WM_PAINT.|  
|[CAtlPreviewCtrlImpl::Redraw](#redraw)|Indique à ce contrôle à redessiner.|  
|[CAtlPreviewCtrlImpl::SetHost](#sethost)|Définit un nouveau parent pour ce contrôle.|  
|[CAtlPreviewCtrlImpl::SetPreviewVisuals](#setpreviewvisuals)|Appelée par un gestionnaire d’aperçu riche lorsqu’il a besoin définir les éléments visuels de l’aperçu riche contenu.|  
|[CAtlPreviewCtrlImpl::SetRect](#setrect)|Définit un nouveau rectangle englobant pour ce contrôle.|  
  
### <a name="protected-methods"></a>Méthodes protégées  
  
|Nom|Description|  
|----------|-----------------|  
|[CAtlPreviewCtrlImpl::DoPaint](#dopaint)|Appelé par l’infrastructure pour afficher l’aperçu.|  
  
### <a name="protected-constants"></a>Constantes protégés  
  
|Name|Description|  
|----------|-----------------|  
|[CAtlPreviewCtrlImpl::m_plf](#m_plf)|Police utilisée pour afficher le texte dans la fenêtre d’aperçu.|  
  
### <a name="protected-data-members"></a>Membres de données protégés  
  
|Name|Description|  
|----------|-----------------|  
|[CAtlPreviewCtrlImpl::m_clrBack](#m_clrback)|Couleur d’arrière-plan de la fenêtre d’aperçu.|  
|[CAtlPreviewCtrlImpl::m_clrText](#m_clrtext)|Couleur du texte de la fenêtre d’aperçu.|  

  
## <a name="remarks"></a>Notes  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `TBase`  
  
 `ATL::CMessageMap`  
  
 `ATL::CWindowImplRoot<TBase>`  
  
 `ATL::CWindowImplBaseT<TBase,TWinTraits>`  
  
 [ATL::CWindowImpl\<CAtlPreviewCtrlImpl >](../../atl/reference/cwindowimpl-class.md)  
  
 `IPreviewCtrl`  
  
 `ATL::CAtlPreviewCtrlImpl`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlpreviewctrlimpl.h  
  
##  <a name="catlpreviewctrlimpl"></a>  CAtlPreviewCtrlImpl::CAtlPreviewCtrlImpl  
 Construit un objet de contrôle de version préliminaire.  
  
```
CAtlPreviewCtrlImpl(void) : m_clrText(0),
   m_clrBack(RGB(255, 255, 255)), m_plf(NULL);
```  
  
### <a name="remarks"></a>Notes  
  
##  <a name="dtor"></a>  CAtlPreviewCtrlImpl :: ~ CAtlPreviewCtrlImpl  
 Destruction d’un objet de contrôle de version préliminaire.  
  
```
virtual ~CAtlPreviewCtrlImpl(void);
```  
  
### <a name="remarks"></a>Notes  
  
##  <a name="create"></a>  CAtlPreviewCtrlImpl::Create  
 Appelée par un gestionnaire d’aperçu riche pour créer la fenêtre Windows.  
  
```
virtual BOOL Create(HWND hWndParent, const RECT* prc);
```  
  
### <a name="parameters"></a>Paramètres  
 `hWndParent`  
 Handle vers la fenêtre hôte fournie par l’interpréteur de commandes pour l’aperçu riche.  
  
 `prc`  
 Spécifie la taille initiale et la position de la fenêtre.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` en cas de réussite ; sinon, `FALSE`.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="destroy"></a>  CAtlPreviewCtrlImpl::Destroy  
 Appelée par un gestionnaire d’aperçu riche lorsqu’il a besoin détruire ce contrôle.  
  
```
virtual void Destroy();
```  
  
### <a name="remarks"></a>Notes  
  
##  <a name="dopaint"></a>  CAtlPreviewCtrlImpl::DoPaint  
 Appelé par l’infrastructure pour afficher l’aperçu.  
  
```
virtual void DoPaint(HDC hdc);
```  
  
### <a name="parameters"></a>Paramètres  
 `hdc`  
 Handle vers un contexte de périphérique pour la peinture.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="focus"></a>  CAtlPreviewCtrlImpl::Focus  
 Définit le focus à ce contrôle.  
  
```
virtual void Focus();
```  
  
### <a name="remarks"></a>Notes  
  
##  <a name="m_clrback"></a>  CAtlPreviewCtrlImpl::m_clrBack  
 Couleur d’arrière-plan de la fenêtre d’aperçu.  
  
```
COLORREF m_clrBack;
```  
  
### <a name="remarks"></a>Notes  
  
##  <a name="m_clrtext"></a>  CAtlPreviewCtrlImpl::m_clrText  
 Couleur du texte de la fenêtre d’aperçu.  
  
```
COLORREF m_clrText;
```  
  
### <a name="remarks"></a>Notes  
  
##  <a name="m_plf"></a>  CAtlPreviewCtrlImpl::m_plf  
 Police utilisée pour afficher le texte dans la fenêtre d’aperçu.  
  
```
const LOGFONTW* m_plf;
```  
  
### <a name="remarks"></a>Notes  
  
##  <a name="onpaint"></a>  CAtlPreviewCtrlImpl::OnPaint  
 Gère le message WM_PAINT.  
  
```
LRESULT OnPaint(  
    UINT nMsg,
    WPARAM wParam,
    LPARAM lParam,
    BOOL& bHandled);
```  
  
### <a name="parameters"></a>Paramètres  
 `nMsg`  
 La valeur WM_PAINT.  
  
 `wParam`  
 Ce paramètre n'est pas utilisé.  
  
 `lParam`  
 Ce paramètre n'est pas utilisé.  
  
 `bHandled`  
 Lorsque cette fonction est retournée, elle contient `TRUE`.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne toujours 0.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="redraw"></a>  CAtlPreviewCtrlImpl::Redraw  
 Indique à ce contrôle à redessiner.  
  
```
virtual void Redraw();
```  
  
### <a name="remarks"></a>Notes  
  
##  <a name="sethost"></a>  CAtlPreviewCtrlImpl::SetHost  
 Définit un nouveau parent pour ce contrôle.  
  
```
virtual void SetHost(HWND hWndParent);
```  
  
### <a name="parameters"></a>Paramètres  
 `hWndParent`  
 Handle vers la nouvelle fenêtre parent.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="setpreviewvisuals"></a>  CAtlPreviewCtrlImpl::SetPreviewVisuals  
 Appelée par un gestionnaire d’aperçu riche lorsqu’il a besoin définir les éléments visuels de l’aperçu riche contenu.  
  
```
virtual void SetPreviewVisuals(
    COLORREF clrBack,
    COLORREF clrText,
    const LOGFONTW* plf);
```  
  
### <a name="parameters"></a>Paramètres  
 `clrBack`  
 Couleur d’arrière-plan de la fenêtre d’aperçu.  
  
 `clrText`  
 Couleur du texte de la fenêtre d’aperçu.  
  
 `plf`  
 Police utilisée pour afficher le texte dans la fenêtre d’aperçu.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="setrect"></a>  CAtlPreviewCtrlImpl::SetRect  
 Définit un nouveau rectangle englobant pour ce contrôle.  
  
```
virtual void SetRect(const RECT* prc, BOOL bRedraw);
```  
  
### <a name="parameters"></a>Paramètres  
 `prc`  
 Spécifie la nouvelle taille et la position du contrôle de version préliminaire.  
  
 `bRedraw`  
 Spécifie si le contrôle doit être redessiné.  
  
### <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Composants de bureau COM ATL](../../atl/atl-com-desktop-components.md)
