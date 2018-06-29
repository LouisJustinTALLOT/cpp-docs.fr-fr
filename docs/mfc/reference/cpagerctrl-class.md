---
title: Classe de CPagerCtrl | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CPagerCtrl
- AFXCMN/CPagerCtrl
- AFXCMN/CPagerCtrl::CPagerCtrl
- AFXCMN/CPagerCtrl::Create
- AFXCMN/CPagerCtrl::CreateEx
- AFXCMN/CPagerCtrl::ForwardMouse
- AFXCMN/CPagerCtrl::GetBkColor
- AFXCMN/CPagerCtrl::GetBorder
- AFXCMN/CPagerCtrl::GetButtonSize
- AFXCMN/CPagerCtrl::GetButtonState
- AFXCMN/CPagerCtrl::GetDropTarget
- AFXCMN/CPagerCtrl::GetScrollPos
- AFXCMN/CPagerCtrl::IsButtonDepressed
- AFXCMN/CPagerCtrl::IsButtonGrayed
- AFXCMN/CPagerCtrl::IsButtonHot
- AFXCMN/CPagerCtrl::IsButtonInvisible
- AFXCMN/CPagerCtrl::IsButtonNormal
- AFXCMN/CPagerCtrl::RecalcSize
- AFXCMN/CPagerCtrl::SetBkColor
- AFXCMN/CPagerCtrl::SetBorder
- AFXCMN/CPagerCtrl::SetButtonSize
- AFXCMN/CPagerCtrl::SetChild
- AFXCMN/CPagerCtrl::SetScrollPos
dev_langs:
- C++
helpviewer_keywords:
- CPagerCtrl [MFC], CPagerCtrl
- CPagerCtrl [MFC], Create
- CPagerCtrl [MFC], CreateEx
- CPagerCtrl [MFC], ForwardMouse
- CPagerCtrl [MFC], GetBkColor
- CPagerCtrl [MFC], GetBorder
- CPagerCtrl [MFC], GetButtonSize
- CPagerCtrl [MFC], GetButtonState
- CPagerCtrl [MFC], GetDropTarget
- CPagerCtrl [MFC], GetScrollPos
- CPagerCtrl [MFC], IsButtonDepressed
- CPagerCtrl [MFC], IsButtonGrayed
- CPagerCtrl [MFC], IsButtonHot
- CPagerCtrl [MFC], IsButtonInvisible
- CPagerCtrl [MFC], IsButtonNormal
- CPagerCtrl [MFC], RecalcSize
- CPagerCtrl [MFC], SetBkColor
- CPagerCtrl [MFC], SetBorder
- CPagerCtrl [MFC], SetButtonSize
- CPagerCtrl [MFC], SetChild
- CPagerCtrl [MFC], SetScrollPos
ms.assetid: 65ac58dd-4f5e-4b7e-b15c-e0d435a7e884
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ad0d928f7190d3908c41560c7fb106e3024ebc6e
ms.sourcegitcommit: be0e3457f2884551f18e183ef0ea65c3ded7f689
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37079642"
---
# <a name="cpagerctrl-class"></a>Classe de CPagerCtrl
La classe `CPagerCtrl` inclut dans un wrapper le contrôle pager Windows, qui peut afficher une fenêtre contenue qui ne tient pas dans la fenêtre conteneur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CPagerCtrl : public CWnd  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CPagerCtrl::CPagerCtrl](#cpagerctrl)|Construit un objet `CPagerCtrl`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CPagerCtrl::Create](#create)|Crée un contrôle pager avec des styles spécifiés et l’attache à actuel `CPagerCtrl` objet.|  
|[CPagerCtrl::CreateEx](#createex)|Crée un contrôle pager avec les styles étendus spécifiés et l’attache à actuel `CPagerCtrl` objet.|  
|[CPagerCtrl::ForwardMouse](#forwardmouse)|Active ou désactive le transfert [WM_MOUSEMOVE](http://msdn.microsoft.com/library/windows/desktop/ms645616) messages dans la fenêtre qui est contenue dans le contrôle pager actuel.|  
|[CPagerCtrl::GetBkColor](#getbkcolor)|Récupère la couleur d’arrière-plan du contrôle pager actuel.|  
|[CPagerCtrl::GetBorder](#getborder)|Récupère la taille de bordure du contrôle pager actuel.|  
|[CPagerCtrl::GetButtonSize](#getbuttonsize)|Récupère la taille des boutons du contrôle pager actuel.|  
|[CPagerCtrl::GetButtonState](#getbuttonstate)|Récupère l’état du bouton spécifié dans le contrôle pager actuel.|  
|[CPagerCtrl::GetDropTarget](#getdroptarget)|Récupère le [IDropTarget](http://msdn.microsoft.com/library/windows/desktop/ms679679) interface pour le contrôle pager actuel.|  
|[CPagerCtrl::GetScrollPos](#getscrollpos)|Récupère la position de défilement du contrôle pager actuel.|  
|[CPagerCtrl::IsButtonDepressed](#isbuttondepressed)|Indique si le bouton spécifié du contrôle pager actuel est en `pressed` état.|  
|[CPagerCtrl::IsButtonGrayed](#isbuttongrayed)|Indique si le bouton spécifié du contrôle pager actuel est en `grayed` état.|  
|[CPagerCtrl::IsButtonHot](#isbuttonhot)|Indique si le bouton spécifié du contrôle pager actuel est en `hot` état.|  
|[CPagerCtrl::IsButtonInvisible](#isbuttoninvisible)|Indique si le bouton spécifié du contrôle pager actuel est en `invisible` état.|  
|[CPagerCtrl::IsButtonNormal](#isbuttonnormal)|Indique si le bouton spécifié du contrôle pager actuel est en `normal` état.|  
|[CPagerCtrl::RecalcSize](#recalcsize)|Force le contrôle pager actuel recalculer la taille de la fenêtre contenue.|  
|[CPagerCtrl::SetBkColor](#setbkcolor)|Définit la couleur d’arrière-plan du contrôle pager actuel.|  
|[CPagerCtrl::SetBorder](#setborder)|Définit la taille de bordure du contrôle pager actuel.|  
|[CPagerCtrl::SetButtonSize](#setbuttonsize)|Définit la taille des boutons du contrôle pager actuel.|  
|[CPagerCtrl::SetChild](#setchild)|Définit la fenêtre de relation contenant-contenue pour le contrôle pager actuel.|  
|[CPagerCtrl::SetScrollPos](#setscrollpos)|Définit la position de défilement du contrôle pager actuel.|  
  
## <a name="remarks"></a>Notes  
 Un contrôle pager est une fenêtre qui contient une autre fenêtre linéaire et est supérieure à la fenêtre conteneur, et vous permet de faire défiler la fenêtre contenue dans la vue. Le contrôle pager affiche deux boutons de défilement disparaissent automatiquement lorsque vous faites défiler la fenêtre contenue dans sa mesure plus éloignée et réapparaître dans le cas contraire. Vous pouvez créer un contrôle pager qui défile horizontalement ou verticalement.  
  
 Par exemple, si votre application comporte une barre d’outils n’est pas assez large pour afficher tous ses éléments, vous pouvez affecter la barre d’outils à un contrôle pager et vous pourrez faire défiler la barre d’outils vers la gauche ou la droite pour accéder à tous les éléments. Microsoft Internet Explorer Version 4.0 (version commctrl.dll 4.71) introduit le contrôle pager.  
  
 Le `CPagerCtrl` classe est dérivée de la [CWnd](../../mfc/reference/cwnd-class.md) classe. Pour plus d’informations et obtenir une illustration d’un contrôle de pagineur, consultez [contrôles Pager](http://msdn.microsoft.com/library/windows/desktop/bb760855).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CPagerCtrl`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxcmn.h  
  
##  <a name="cpagerctrl"></a>  CPagerCtrl::CPagerCtrl  
 Construit un objet `CPagerCtrl`.  
  
```  
CPagerCtrl();
```  
  
### <a name="remarks"></a>Notes  
 Utilisez le [CPagerCtrl::Create](#create) ou [CPagerCtrl::CreateEx](#createex) méthode pour créer un contrôle pager et l’attacher à la `CPagerCtrl` objet.  
  
##  <a name="create"></a>  CPagerCtrl::Create  
 Crée un contrôle pager avec des styles spécifiés et l’attache à actuel `CPagerCtrl` objet.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,   
    const RECT& rect,   
    CWnd* pParentWnd,   
    UINT nID);
```  
  
### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|[in] *dwStyle*|Combinaison de bits de (OR) [styles de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles) et [styles de contrôle pager](http://msdn.microsoft.com/library/windows/desktop/bb760859) à appliquer au contrôle.|  
|[in] *rect*|Une référence à un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) structure qui contient la position et la taille du contrôle en coordonnées clientes.|  
|[in] *pParentWnd*|Un pointeur vers un [CWnd](../../mfc/reference/cwnd-class.md) objet qui est la fenêtre parente du contrôle. Ce paramètre ne peut pas être `NULL`.|  
|[in] *nID*|L’ID du contrôle.|  
  
### <a name="return-value"></a>Valeur de retour  
 `true` Si cette méthode a réussi ; dans le cas contraire, `false`.  
  
### <a name="remarks"></a>Notes  
 Pour créer un contrôle pager, déclarez un `CPagerCtrl` variable, puis appelez le [CPagerCtrl::Create](#create) ou [CPagerCtrl::CreateEx](#createex) méthode sur cette variable.  
  
### <a name="example"></a>Exemple  
 L’exemple suivant crée un contrôle pager, puis utilise le [CPagerCtrl::SetChild](#setchild) méthode permet d’associer un contrôle bouton très longue avec le contrôle pager. L’exemple utilise ensuite la [CPagerCtrl::SetButtonSize](#setbuttonsize) pour définir la hauteur du contrôle pager 20 pixels et le [CPagerCtrl::SetBorder](#setborder) pour définir l’épaisseur de bordure de 1 pixel.  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]  
  
##  <a name="createex"></a>  CPagerCtrl::CreateEx  
 Crée un contrôle pager avec les styles étendus spécifiés et l’attache à actuel `CPagerCtrl` objet.  
  
```  
virtual BOOL CreateEx(
    DWORD dwExStyle,   
    DWORD dwStyle,   
    const RECT& rect,   
    CWnd* pParentWnd,   
    UINT nID);
```  
  
### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|[in] *dwExStyle*|Combinaison de bits de styles étendus à appliquer au contrôle. Pour plus d’informations, consultez la *dwExStyle* paramètre de la [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) (fonction).|  
|[in] *dwStyle*|Combinaison de bits de (OR) [styles de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles) et [styles de contrôle pager](http://msdn.microsoft.com/library/windows/desktop/bb760859) à appliquer au contrôle.|  
|[in] *rect*|Une référence à un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) structure qui contient la position et la taille du contrôle en coordonnées clientes.|  
|[in] *pParentWnd*|Un pointeur vers un [CWnd](../../mfc/reference/cwnd-class.md) objet qui est la fenêtre parente du contrôle. Ce paramètre ne peut pas être `NULL`.|  
|[in] *nID*|L’ID du contrôle.|  
  
### <a name="return-value"></a>Valeur de retour  
 `true` Si cette méthode a réussi ; dans le cas contraire, `false`.  
  
### <a name="remarks"></a>Notes  
 Pour créer un contrôle pager, déclarez un `CPagerCtrl` variable, puis appelez le [CPagerCtrl::Create](#create) ou [CPagerCtrl::CreateEx](#createex) méthode sur cette variable.  
  
##  <a name="forwardmouse"></a>  CPagerCtrl::ForwardMouse  
 Active ou désactive le transfert [WM_MOUSEMOVE](http://msdn.microsoft.com/library/windows/desktop/ms645616) messages dans la fenêtre qui est contenue dans le contrôle pager actuel.  
  
```  
void ForwardMouse(BOOL bForward);
```  
  
### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|[in] *bForward*|`true` pour transférer les messages de la souris, ou `false` pour ne pas transférer les messages de la souris.|  
  
### <a name="remarks"></a>Notes  
 Cette méthode envoie le [PGM_FORWARDMOUSE](http://msdn.microsoft.com/library/windows/desktop/bb760867) message, ce qui est décrit dans le Kit de développement logiciel Windows.  
  
##  <a name="getborder"></a>  CPagerCtrl::GetBorder  
 Récupère la taille de bordure du contrôle pager actuel.  
  
```  
int GetBorder() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 La taille actuelle de la bordure, en pixels.  
  
### <a name="remarks"></a>Notes  
 Cette méthode envoie le [PGM_GETBORDER](http://msdn.microsoft.com/library/windows/desktop/bb760869) message, ce qui est décrit dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
 L’exemple suivant utilise le [CPagerCtrl::GetBorder](#getborder) méthode pour récupérer l’épaisseur de bordure du contrôle de la radiomessagerie.  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2#5](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_2.cpp)]  
  
##  <a name="getbkcolor"></a>  CPagerCtrl::GetBkColor  
 Récupère la couleur d’arrière-plan du contrôle pager actuel.  
  
```  
COLORREF GetBkColor() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) valeur qui contient la couleur d’arrière-plan actuelle du contrôle pager.  
  
### <a name="remarks"></a>Notes  
 Cette méthode envoie le [PGM_GETBKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb760868) message, ce qui est décrit dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
 L’exemple suivant utilise le [CPagerCtrl::SetBkColor](#setbkcolor) pour définir la couleur d’arrière-plan du contrôle pager en rouge et la [CPagerCtrl::GetBkColor](#getbkcolor) méthode pour vérifier que la modification a été apportée.  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2#4](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_3.cpp)]  
  
##  <a name="getbuttonsize"></a>  CPagerCtrl::GetButtonSize  
 Récupère la taille des boutons du contrôle pager actuel.  
  
```  
int GetButtonSize() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 La taille actuelle du bouton, en pixels.  
  
### <a name="remarks"></a>Notes  
 Cette méthode envoie le [PGM_GETBUTTONSIZE](http://msdn.microsoft.com/library/windows/desktop/bb760870) message, ce qui est décrit dans le Kit de développement logiciel Windows.  
  
 Si le contrôle pager a la `PGS_HORZ` style, la taille du bouton détermine la largeur des boutons du pagineur, et si le contrôle pager a la `PGS_VERT` style, la taille du bouton détermine la hauteur des boutons du pagineur. Pour plus d’informations, consultez [Styles de contrôle Pager](http://msdn.microsoft.com/library/windows/desktop/bb760859).  
  
##  <a name="getbuttonstate"></a>  CPagerCtrl::GetButtonState  
 Récupère l’état du bouton de défilement spécifiée dans le contrôle pager actuel.  
  
```  
DWORD GetButtonState(int iButton) const;  
```  
  
### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|[in] *iButton*|Indique le bouton pour lequel l’état est récupéré. Si le style du contrôle pager est `PGS_HORZ`, spécifiez `PGB_TOPORLEFT` pour le bouton gauche et `PGB_BOTTOMORRIGHT` pour le bouton droit. Si le style du contrôle pager est `PGS_VERT`, spécifiez `PGB_TOPORLEFT` pour le bouton du haut et `PGB_BOTTOMORRIGHT` pour le bouton bas. Pour plus d’informations, consultez [Styles de contrôle Pager](http://msdn.microsoft.com/library/windows/desktop/bb760859).|  
  
### <a name="return-value"></a>Valeur de retour  
 L’état du bouton spécifié par le *iButton* paramètre. L’état est `PGF_INVISIBLE`, `PGF_NORMAL`, `PGF_GRAYED`, `PGF_DEPRESSED`, ou `PGF_HOT`. Pour plus d’informations, consultez la section de la valeur de retour de la [PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871) message.  
  
### <a name="remarks"></a>Notes  
 Cette méthode envoie le [PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871) message, ce qui est décrit dans le Kit de développement logiciel Windows.  
  
##  <a name="getdroptarget"></a>  CPagerCtrl::GetDropTarget  
 Récupère le [IDropTarget](http://msdn.microsoft.com/library/windows/desktop/ms679679) interface pour le contrôle pager actuel.  
  
```  
IDropTarget* GetDropTarget() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers le `IDropTarget` interface pour le contrôle pager actuel.  
  
### <a name="remarks"></a>Notes  
 `IDropTarget` est une des interfaces que vous implémentez pour prendre en charge les opérations de glisser-déplacer dans votre application.  
  
 Cette méthode envoie le [PGM_GETDROPTARGET](http://msdn.microsoft.com/library/windows/desktop/bb760872) message, ce qui est décrit dans le Kit de développement logiciel Windows. L’appelant de cette méthode est chargée d’appeler le `Release` membre de la [IDropTarget](http://msdn.microsoft.com/library/windows/desktop/ms679679) interface lorsque l’interface n’est plus nécessaire.  
  
##  <a name="getscrollpos"></a>  CPagerCtrl::GetScrollPos  
 Récupère la position de défilement du contrôle pager actuel.  
  
```  
int GetScrollPos() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 La position de défilement actuelle, en pixels.  
  
### <a name="remarks"></a>Notes  
 Cette méthode envoie le [PGM_GETPOS](http://msdn.microsoft.com/library/windows/desktop/bb760874) message, ce qui est décrit dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
 L’exemple suivant utilise le [CPagerCtrl::GetScrollPos](#getscrollpos) pour récupérer la position de défilement actuelle du contrôle pager. Si le contrôle pager n’est pas atteint à zéro, la position à l’extrême gauche, l’exemple utilise le [CPagerCtrl::SetScrollPos](#setscrollpos) pour définir la position de défilement à zéro.  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2#7](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_4.cpp)]  
  
##  <a name="isbuttondepressed"></a>  CPagerCtrl::IsButtonDepressed  
 Indique si le bouton de défilement spécifiée du contrôle pager actuel est dans l’état enfoncé.  
  
```  
BOOL IsButtonDepressed(int iButton) const;  
```  
  
### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|[in] *iButton*|Indique le bouton pour lequel l’état est récupéré. Si le style du contrôle pager est `PGS_HORZ`, spécifiez `PGB_TOPORLEFT` pour le bouton gauche et `PGB_BOTTOMORRIGHT` pour le bouton droit. Si le style du contrôle pager est `PGS_VERT`, spécifiez `PGB_TOPORLEFT` pour le bouton du haut et `PGB_BOTTOMORRIGHT` pour le bouton bas. Pour plus d’informations, consultez [Styles de contrôle Pager](http://msdn.microsoft.com/library/windows/desktop/bb760859).|  
  
### <a name="return-value"></a>Valeur de retour  
 `true` Si le bouton spécifié est dans l’état enfoncé ; dans le cas contraire, `false`.  
  
### <a name="remarks"></a>Notes  
 Cette méthode envoie le [PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871) message, ce qui est décrit dans le Kit de développement logiciel Windows. Il vérifie ensuite si l’état renvoyé est `PGF_DEPRESSED`. Pour plus d’informations, consultez la section de la valeur de retour de la [PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871) message.  
  
##  <a name="isbuttongrayed"></a>  CPagerCtrl::IsButtonGrayed  
 Indique si le bouton de défilement spécifiée du contrôle pager actuel est en état grisé.  
  
```  
BOOL IsButtonGrayed(int iButton) const;  
```  
  
### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|[in] *iButton*|Indique le bouton pour lequel l’état est récupéré. Si le style du contrôle pager est `PGS_HORZ`, spécifiez `PGB_TOPORLEFT` pour le bouton gauche et `PGB_BOTTOMORRIGHT` pour le bouton droit. Si le style du contrôle pager est `PGS_VERT`, spécifiez `PGB_TOPORLEFT` pour le bouton du haut et `PGB_BOTTOMORRIGHT` pour le bouton bas. Pour plus d’informations, consultez [Styles de contrôle Pager](http://msdn.microsoft.com/library/windows/desktop/bb760859).|  
  
### <a name="return-value"></a>Valeur de retour  
 `true` Si le bouton spécifié est dans un état grisé ; dans le cas contraire, `false`.  
  
### <a name="remarks"></a>Notes  
 Cette méthode envoie le [PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871) message, ce qui est décrit dans le Kit de développement logiciel Windows. Il vérifie ensuite si l’état renvoyé est `PGF_GRAYED`. Pour plus d’informations, consultez la section de la valeur de retour de la [PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871) message.  
  
##  <a name="isbuttonhot"></a>  CPagerCtrl::IsButtonHot  
 Indique si le bouton de défilement spécifiée du contrôle pager actuel est dans un état actif.  
  
```  
BOOL IsButtonHot(int iButton) const;  
```  
  
### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|[in] *iButton*|Indique le bouton pour lequel l’état est récupéré. Si le style du contrôle pager est `PGS_HORZ`, spécifiez `PGB_TOPORLEFT` pour le bouton gauche et `PGB_BOTTOMORRIGHT` pour le bouton droit. Si le style du contrôle pager est `PGS_VERT`, spécifiez `PGB_TOPORLEFT` pour le bouton du haut et `PGB_BOTTOMORRIGHT` pour le bouton bas. Pour plus d’informations, consultez [Styles de contrôle Pager](http://msdn.microsoft.com/library/windows/desktop/bb760859).|  
  
### <a name="return-value"></a>Valeur de retour  
 `true` Si le bouton spécifié est dans un état actif ; dans le cas contraire, `false`.  
  
### <a name="remarks"></a>Notes  
 Cette méthode envoie le [PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871) message, ce qui est décrit dans le Kit de développement logiciel Windows. Il vérifie ensuite si l’état renvoyé est `PGF_HOT`. Pour plus d’informations, consultez la section de la valeur de retour de la [PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871) message.  
  
##  <a name="isbuttoninvisible"></a>  CPagerCtrl::IsButtonInvisible  
 Indique si le bouton de défilement spécifiée du contrôle pager actuel est en état invisible.  
  
```  
BOOL IsButtonInvisible(int iButton) const;  
```  
  
### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|[in] *iButton*|Indique le bouton pour lequel l’état est récupéré. Si le style du contrôle pager est `PGS_HORZ`, spécifiez `PGB_TOPORLEFT` pour le bouton gauche et `PGB_BOTTOMORRIGHT` pour le bouton droit. Si le style du contrôle pager est `PGS_VERT`, spécifiez `PGB_TOPORLEFT` pour le bouton du haut et `PGB_BOTTOMORRIGHT` pour le bouton bas. Pour plus d’informations, consultez [Styles de contrôle Pager](http://msdn.microsoft.com/library/windows/desktop/bb760859).|  
  
### <a name="return-value"></a>Valeur de retour  
 `true` Si le bouton spécifié est dans un état invisible ; dans le cas contraire, `false`.  
  
### <a name="remarks"></a>Notes  
 Windows rend le bouton de défilement dans une direction particulière invisible lorsque le défilement de la fenêtre contenue dans sa plus éloignée mesure, car en cliquant sur le bouton supplémentaire ne peut pas afficher de plus de la fenêtre contenue dans la vue.  
  
 Cette méthode envoie le [PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871) message, ce qui est décrit dans le Kit de développement logiciel Windows. Il vérifie ensuite si l’état renvoyé est `PGF_INVISIBLE`. Pour plus d’informations, consultez la section de la valeur de retour de la [PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871) message.  
  
### <a name="example"></a>Exemple  
 L’exemple suivant utilise le [CPagerCtrl::IsButtonInvisible](#isbuttoninvisible) méthode pour déterminer si le contrôle pager left et boutons de défilement vers la droite sont visibles.  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2#6](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_5.cpp)]  
  
##  <a name="isbuttonnormal"></a>  CPagerCtrl::IsButtonNormal  
 Indique si le bouton de défilement spécifiée du contrôle pager actuel est dans un état normal.  
  
```  
BOOL IsButtonNormal(int iButton) const;  
```  
  
### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|[in] *iButton*|Indique le bouton pour lequel l’état est récupéré. Si le style du contrôle pager est `PGS_HORZ`, spécifiez `PGB_TOPORLEFT` pour le bouton gauche et `PGB_BOTTOMORRIGHT` pour le bouton droit. Si le style du contrôle pager est `PGS_VERT`, spécifiez `PGB_TOPORLEFT` pour le bouton du haut et `PGB_BOTTOMORRIGHT` pour le bouton bas. Pour plus d’informations, consultez [Styles de contrôle Pager](http://msdn.microsoft.com/library/windows/desktop/bb760859).|  
  
### <a name="return-value"></a>Valeur de retour  
 `true` Si le bouton spécifié se trouve dans un état normal ; dans le cas contraire, `false`.  
  
### <a name="remarks"></a>Notes  
 Cette méthode envoie le [PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871) message, ce qui est décrit dans le Kit de développement logiciel Windows. Il vérifie ensuite si l’état renvoyé est `PGF_NORMAL`. Pour plus d’informations, consultez la section de la valeur de retour de la [PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871) message.  
  
##  <a name="recalcsize"></a>  CPagerCtrl::RecalcSize  
 Force le contrôle pager actuel recalculer la taille de la fenêtre contenue.  
  
```  
void RecalcSize();
```  
  
### <a name="remarks"></a>Notes  
 Cette méthode envoie le [PGM_RECALCSIZE](http://msdn.microsoft.com/library/windows/desktop/bb760876) message, ce qui est décrit dans le Kit de développement logiciel Windows. Par conséquent, le contrôle pager envoie le [PGN_CALCSIZE](http://msdn.microsoft.com/library/windows/desktop/bb760864) notification pour obtenir les dimensions déroulantes de la fenêtre contenue.  
  
### <a name="example"></a>Exemple  
 L’exemple suivant utilise le [CPagerCtrl::RecalcSize](#recalcsize) méthode pour demander le contrôle pager actuel à recalculer sa taille.  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2#3](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_6.cpp)]  
  
### <a name="example"></a>Exemple  
 L’exemple suivant utilise [réflexion de message](../../mfc/tn062-message-reflection-for-windows-controls.md) pour activer le contrôle pager recalculer sa taille au lieu de demander la boîte de dialogue du contrôle parent pour effectuer le calcul. Dérive de l’exemple le `MyPagerCtrl` classe à partir de la [CPagerCtrl classe](../../mfc/reference/cpagerctrl-class.md), puis utilise une table des messages pour associer le [PGN_CALCSIZE](http://msdn.microsoft.com/library/windows/desktop/bb760864) notification avec le `OnCalcsize` Gestionnaire de notification. Dans cet exemple, le Gestionnaire de notification définit la largeur et la hauteur du contrôle par radiomessagerie à des valeurs fixes.  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2#8](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_7.cpp)]  
  
##  <a name="setbkcolor"></a>  CPagerCtrl::SetBkColor  
 Définit la couleur d’arrière-plan du contrôle pager actuel.  
  
```  
COLORREF SetBkColor(COLORREF clrBk);
```  
  
### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|[in] *clrBk*|A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) valeur qui contient la nouvelle couleur d’arrière-plan du contrôle pager.|  
  
### <a name="return-value"></a>Valeur de retour  
 A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) valeur qui contient la couleur d’arrière-plan précédente du contrôle pager.  
  
### <a name="remarks"></a>Notes  
 Cette méthode envoie le [PGM_SETBKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb760878) message, ce qui est décrit dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
 L’exemple suivant utilise le [CPagerCtrl::SetBkColor](#setbkcolor) pour définir la couleur d’arrière-plan du contrôle pager en rouge et la [CPagerCtrl::GetBkColor](#getbkcolor) méthode pour vérifier que la modification a été apportée.  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2#4](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_3.cpp)]  
  
##  <a name="setborder"></a>  CPagerCtrl::SetBorder  
 Définit la taille de bordure du contrôle pager actuel.  
  
```  
int SetBorder(int iBorder);
```  
  
### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|[in] *iBorder*|La nouvelle taille de bordure en pixels. Si le *iBorder* paramètre est négatif, la taille de la bordure est définie sur zéro.|  
  
### <a name="return-value"></a>Valeur de retour  
 La taille de bordure précédente, en pixels.  
  
### <a name="remarks"></a>Notes  
 Cette méthode envoie le [PGM_SETBORDER](http://msdn.microsoft.com/library/windows/desktop/bb760880) message, ce qui est décrit dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
 L’exemple suivant crée un contrôle pager, puis utilise le [CPagerCtrl::SetChild](#setchild) méthode permet d’associer un contrôle bouton très longue avec le contrôle pager. L’exemple utilise ensuite la [CPagerCtrl::SetButtonSize](#setbuttonsize) pour définir la hauteur du contrôle pager 20 pixels et le [CPagerCtrl::SetBorder](#setborder) pour définir l’épaisseur de bordure de 1 pixel.  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]  
  
##  <a name="setbuttonsize"></a>  CPagerCtrl::SetButtonSize  
 Définit la taille des boutons du contrôle pager actuel.  
  
```  
int SetButtonSize(int iButtonSize);
```  
  
### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|[in] *iButtonSize*|La taille du bouton Nouveau, en pixels.|  
  
### <a name="return-value"></a>Valeur de retour  
 La taille du bouton précédent, en pixels.  
  
### <a name="remarks"></a>Notes  
 Cette méthode envoie le [PGM_SETBUTTONSIZE](http://msdn.microsoft.com/library/windows/desktop/bb760886) message, ce qui est décrit dans le Kit de développement logiciel Windows.  
  
 Si le contrôle pager a la `PGS_HORZ` style, la taille du bouton détermine la largeur des boutons du pagineur, et si le contrôle pager a la `PGS_VERT` style, la taille du bouton détermine la hauteur des boutons du pagineur. La taille du bouton par défaut est trois quarts de la largeur de la barre de défilement, et la taille de bouton minimale est de 12 pixels. Pour plus d’informations, consultez [Styles de contrôle Pager](http://msdn.microsoft.com/library/windows/desktop/bb760859).  
  
### <a name="example"></a>Exemple  
 L’exemple suivant crée un contrôle pager, puis utilise le [CPagerCtrl::SetChild](#setchild) méthode permet d’associer un contrôle bouton très longue avec le contrôle pager. L’exemple utilise ensuite la [CPagerCtrl::SetButtonSize](#setbuttonsize) pour définir la hauteur du contrôle pager 20 pixels et le [CPagerCtrl::SetBorder](#setborder) pour définir l’épaisseur de bordure de 1 pixel.  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]  
  
##  <a name="setchild"></a>  CPagerCtrl::SetChild  
 Définit la fenêtre de relation contenant-contenue pour le contrôle pager actuel.  
  
```  
void SetChild(HWND hwndChild);
```  
  
### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|[in] *hwndChild*|Handle vers la fenêtre doit être contenu.|  
  
### <a name="remarks"></a>Notes  
 Cette méthode envoie le [PGM_SETCHILD](http://msdn.microsoft.com/library/windows/desktop/bb760884) message, ce qui est décrit dans le Kit de développement logiciel Windows.  
  
 Cette méthode ne modifie pas le parent de la fenêtre de relation contenant-contenu. Il affecte uniquement un handle de fenêtre pour le contrôle pager pour le défilement. Dans la plupart des cas, la fenêtre de contenu est une fenêtre enfant du contrôle pager.  
  
### <a name="example"></a>Exemple  
 L’exemple suivant crée un contrôle pager, puis utilise le [CPagerCtrl::SetChild](#setchild) méthode permet d’associer un contrôle bouton très longue avec le contrôle pager. L’exemple utilise ensuite la [CPagerCtrl::SetButtonSize](#setbuttonsize) pour définir la hauteur du contrôle pager 20 pixels et le [CPagerCtrl::SetBorder](#setborder) pour définir l’épaisseur de bordure de 1 pixel.  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]  
  
##  <a name="setscrollpos"></a>  CPagerCtrl::SetScrollPos  
 Définit la position de défilement du contrôle pager actuel.  
  
```  
void SetScrollPos(int iPos);
```  
  
### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|[in] *iPos*|La nouvelle position de défilement, en pixels.|  
  
### <a name="remarks"></a>Notes  
 Cette méthode envoie le [PGM_SETPOS](http://msdn.microsoft.com/library/windows/desktop/bb760886) message, ce qui est décrit dans le Kit de développement logiciel Windows.  
  
## <a name="see-also"></a>Voir aussi  
 [Classe de CPagerCtrl](../../mfc/reference/cpagerctrl-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Contrôles de récepteur de radiomessagerie](http://msdn.microsoft.com/library/windows/desktop/bb760855)



