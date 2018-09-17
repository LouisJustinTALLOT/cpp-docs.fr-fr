---
title: Classe CToolTipCtrl | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CToolTipCtrl
- AFXCMN/CToolTipCtrl
- AFXCMN/CToolTipCtrl::CToolTipCtrl
- AFXCMN/CToolTipCtrl::Activate
- AFXCMN/CToolTipCtrl::AddTool
- AFXCMN/CToolTipCtrl::AdjustRect
- AFXCMN/CToolTipCtrl::Create
- AFXCMN/CToolTipCtrl::CreateEx
- AFXCMN/CToolTipCtrl::DelTool
- AFXCMN/CToolTipCtrl::GetBubbleSize
- AFXCMN/CToolTipCtrl::GetCurrentTool
- AFXCMN/CToolTipCtrl::GetDelayTime
- AFXCMN/CToolTipCtrl::GetMargin
- AFXCMN/CToolTipCtrl::GetMaxTipWidth
- AFXCMN/CToolTipCtrl::GetText
- AFXCMN/CToolTipCtrl::GetTipBkColor
- AFXCMN/CToolTipCtrl::GetTipTextColor
- AFXCMN/CToolTipCtrl::GetTitle
- AFXCMN/CToolTipCtrl::GetToolCount
- AFXCMN/CToolTipCtrl::GetToolInfo
- AFXCMN/CToolTipCtrl::HitTest
- AFXCMN/CToolTipCtrl::Pop
- AFXCMN/CToolTipCtrl::Popup
- AFXCMN/CToolTipCtrl::RelayEvent
- AFXCMN/CToolTipCtrl::SetDelayTime
- AFXCMN/CToolTipCtrl::SetMargin
- AFXCMN/CToolTipCtrl::SetMaxTipWidth
- AFXCMN/CToolTipCtrl::SetTipBkColor
- AFXCMN/CToolTipCtrl::SetTipTextColor
- AFXCMN/CToolTipCtrl::SetTitle
- AFXCMN/CToolTipCtrl::SetToolInfo
- AFXCMN/CToolTipCtrl::SetToolRect
- AFXCMN/CToolTipCtrl::SetWindowTheme
- AFXCMN/CToolTipCtrl::Update
- AFXCMN/CToolTipCtrl::UpdateTipText
dev_langs:
- C++
helpviewer_keywords:
- CToolTipCtrl [MFC], CToolTipCtrl
- CToolTipCtrl [MFC], Activate
- CToolTipCtrl [MFC], AddTool
- CToolTipCtrl [MFC], AdjustRect
- CToolTipCtrl [MFC], Create
- CToolTipCtrl [MFC], CreateEx
- CToolTipCtrl [MFC], DelTool
- CToolTipCtrl [MFC], GetBubbleSize
- CToolTipCtrl [MFC], GetCurrentTool
- CToolTipCtrl [MFC], GetDelayTime
- CToolTipCtrl [MFC], GetMargin
- CToolTipCtrl [MFC], GetMaxTipWidth
- CToolTipCtrl [MFC], GetText
- CToolTipCtrl [MFC], GetTipBkColor
- CToolTipCtrl [MFC], GetTipTextColor
- CToolTipCtrl [MFC], GetTitle
- CToolTipCtrl [MFC], GetToolCount
- CToolTipCtrl [MFC], GetToolInfo
- CToolTipCtrl [MFC], HitTest
- CToolTipCtrl [MFC], Pop
- CToolTipCtrl [MFC], Popup
- CToolTipCtrl [MFC], RelayEvent
- CToolTipCtrl [MFC], SetDelayTime
- CToolTipCtrl [MFC], SetMargin
- CToolTipCtrl [MFC], SetMaxTipWidth
- CToolTipCtrl [MFC], SetTipBkColor
- CToolTipCtrl [MFC], SetTipTextColor
- CToolTipCtrl [MFC], SetTitle
- CToolTipCtrl [MFC], SetToolInfo
- CToolTipCtrl [MFC], SetToolRect
- CToolTipCtrl [MFC], SetWindowTheme
- CToolTipCtrl [MFC], Update
- CToolTipCtrl [MFC], UpdateTipText
ms.assetid: 8973f70c-b73a-46c7-908d-758f364b9a97
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4708f180a1a1f5e936a6b30650a6432d48878d53
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45726750"
---
# <a name="ctooltipctrl-class"></a>CToolTipCtrl Class
Encapsule les fonctionnalités d'un « contrôle info-bulle », une petite fenêtre contextuelle qui affiche une ligne de texte unique qui décrit le rôle d'un outil dans une application.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CToolTipCtrl : public CWnd  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CToolTipCtrl::CToolTipCtrl](#ctooltipctrl)|Construit un objet `CToolTipCtrl`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CToolTipCtrl::Activate](#activate)|Active et désactive le contrôle info-bulle.|  
|[CToolTipCtrl::AddTool](#addtool)|Inscrit un outil avec le contrôle info-bulle.|  
|[CToolTipCtrl::AdjustRect](#adjustrect)|Convertit entre du texte d’un contrôle info-bulle affiche le rectangle et son rectangle de la fenêtre.|  
|[CToolTipCtrl::Create](#create)|Crée un contrôle info-bulle et l’attache à un `CToolTipCtrl` objet.|  
|[CToolTipCtrl::CreateEx](#createex)|Crée un contrôle info-bulle avec les styles étendus Windows spécifiés et l’attache à un `CToolTipCtrl` objet.|  
|[CToolTipCtrl::DelTool](#deltool)|Supprime un outil de contrôle ToolTip.|  
|[CToolTipCtrl::GetBubbleSize](#getbubblesize)|Récupère la taille de l’info-bulle.|  
|[CToolTipCtrl::GetCurrentTool](#getcurrenttool)|Récupère des informations, telles que la taille, position et texte, de la fenêtre d’info-bulle qui affiche le contrôle d’info-bulle actuel.|  
|[CToolTipCtrl::GetDelayTime](#getdelaytime)|Récupère l’initial, fenêtre contextuelle et le délai durées qui sont actuellement définies pour un outil de contrôle ToolTip.|  
|[CToolTipCtrl::GetMargin](#getmargin)|Récupère le haut, gauche, marges inférieure et droite qui sont définies pour une fenêtre d’info-bulle outil.|  
|[CToolTipCtrl::GetMaxTipWidth](#getmaxtipwidth)|Récupère la largeur maximale d’une fenêtre d’info-bulle outil.|  
|[CToolTipCtrl::GetText](#gettext)|Récupère le texte qui tient à jour un contrôle info-bulle pour un outil.|  
|[CToolTipCtrl::GetTipBkColor](#gettipbkcolor)|Récupère la couleur d’arrière-plan dans une fenêtre d’info-bulle outil.|  
|[CToolTipCtrl::GetTipTextColor](#gettiptextcolor)|Récupère la couleur du texte dans une fenêtre d’info-bulle outil.|  
|[CToolTipCtrl::GetTitle](#gettitle)|Récupère le titre du contrôle d’info-bulle actuel.|  
|[CToolTipCtrl::GetToolCount](#gettoolcount)|Récupère le nombre d’outils gérés par un contrôle info-bulle.|  
|[CToolTipCtrl::GetToolInfo](#gettoolinfo)|Récupère les informations qui tient à jour un contrôle info-bulle sur un outil.|  
|[CToolTipCtrl::HitTest](#hittest)|Teste un point pour déterminer si elle se trouve dans le rectangle englobant de l’outil donné. Dans ce cas, récupère des informations sur l’outil.|  
|[CToolTipCtrl::Pop](#pop)|Supprime une fenêtre d’info-bulle affichée outil à partir de la vue.|  
|[CToolTipCtrl::Popup](#popup)|Force le contrôle d’info-bulle actuel à afficher aux coordonnées du dernier message de la souris.|  
|[CToolTipCtrl::RelayEvent](#relayevent)|Transmet un message de la souris à un contrôle info-bulle pour le traitement.|  
|[CToolTipCtrl::SetDelayTime](#setdelaytime)|Définit l’initiale, contextuelle, délai d’apparition et durées pour un contrôle info-bulle.|  
|[CToolTipCtrl::SetMargin](#setmargin)|Définit le haut, gauche, bas et les marges droite d’une fenêtre d’info-bulle outil.|  
|[CToolTipCtrl::SetMaxTipWidth](#setmaxtipwidth)|Définit la largeur maximale d’une fenêtre d’info-bulle outil.|  
|[CToolTipCtrl::SetTipBkColor](#settipbkcolor)|Définit la couleur d’arrière-plan dans une fenêtre d’info-bulle outil.|  
|[CToolTipCtrl::SetTipTextColor](#settiptextcolor)|Définit la couleur du texte dans une fenêtre d’info-bulle outil.|  
|[CToolTipCtrl::SetTitle](#settitle)|Ajoute une chaîne de titre et icône standard à une info-bulle.|  
|[CToolTipCtrl::SetToolInfo](#settoolinfo)|Définit les informations qui tient à jour une info-bulle pour un outil.|  
|[CToolTipCtrl::SetToolRect](#settoolrect)|Définit un nouveau rectangle englobant pour un outil.|  
|[CToolTipCtrl::SetWindowTheme](#setwindowtheme)|Définit le style visuel de la fenêtre d’info-bulle outil.|  
|[CToolTipCtrl::Update](#update)|Force l’outil actuel à être redessiné.|  
|[CToolTipCtrl::UpdateTipText](#updatetiptext)|Définit le texte info-bulle pour un outil.|  
  
## <a name="remarks"></a>Notes  
 Un « tool » peut être une fenêtre, telle qu’une fenêtre enfant ou de contrôle ou d’une zone rectangulaire définie par l’application au sein de la zone cliente d’une fenêtre. Une info-bulle est masquée à la plupart du temps, qui apparaissent uniquement lorsque l’utilisateur place le curseur sur un outil et il il quitte ensuite pendant environ une demi-seconde. L’info-bulle s’affiche près du curseur et disparaît lorsque l’utilisateur clique sur un bouton de la souris ou déplace le curseur de l’outil.  
  
 `CToolTipCtrl` fournit les fonctionnalités pour contrôler la durée initiale et la durée de l’info-bulle, les largeurs de marge qui entourent le texte info-bulle, la largeur de la fenêtre d’info-bulle outil lui-même et la couleur d’arrière-plan et le texte de l’info-bulle. Un contrôle ToolTip unique peut fournir des informations pour plusieurs outils.  
  
 Le `CToolTipCtrl` classe fournit les fonctionnalités de Windows courantes contrôle ToolTip. Ce contrôle (et par conséquent la `CToolTipCtrl` classe) est disponible uniquement pour les programmes s’exécutant sous Windows 95/98 et Windows NT versions 3.51 et ultérieures.  
  
 Pour plus d’informations sur l’activation des info-bulles, consultez [info-bulles dans Windows non dérivées de CFrameWnd](../../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md).  
  
 Pour plus d’informations sur l’utilisation de `CToolTipCtrl`, consultez [contrôles](../../mfc/controls-mfc.md) et [à l’aide de CToolTipCtrl](../../mfc/using-ctooltipctrl.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CToolTipCtrl`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxcmn.h  
  
##  <a name="activate"></a>  CToolTipCtrl::Activate  
 Appelez cette fonction pour activer ou désactiver un contrôle info-bulle.  
  
```  
void Activate(BOOL bActivate);
```  
  
### <a name="parameters"></a>Paramètres  
 *bActivate*  
 Spécifie si le contrôle info-bulle doit être activée ou désactivée.  
  
### <a name="remarks"></a>Notes  
 Si *bActivate* a la valeur TRUE, le contrôle est activé ; si FALSE elle est désactivée.  
  
 Lorsqu’un contrôle info-bulle est actif, les informations d’info-bulle outil s’affiche lorsque le curseur se trouve sur un outil qui est inscrit avec le contrôle ; Lorsqu’il est inactif, les informations d’info-bulle outil n’apparaît pas, même lorsque le curseur se trouve sur un outil.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).  
  
##  <a name="addtool"></a>  CToolTipCtrl::AddTool  
 Inscrit un outil avec le contrôle info-bulle.  
  
```  
BOOL AddTool(
    CWnd* pWnd,  
    UINT nIDText,  
    LPCRECT lpRectTool = NULL,  
    UINT_PTR nIDTool = 0);

 
BOOL AddTool(
    CWnd* pWnd,  
    LPCTSTR lpszText = LPSTR_TEXTCALLBACK,  
    LPCRECT lpRectTool = NULL,  
    UINT_PTR nIDTool = 0);
```  
  
### <a name="parameters"></a>Paramètres  
 *pWnd*  
 Pointeur vers la fenêtre qui contient l’outil.  
  
 *nIDText*  
 ID de la ressource de chaîne qui contient le texte de l’outil.  
  
 *lpRectTool*  
 Pointeur vers un [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) structure contenant les coordonnées de l’outil du rectangle englobant. Les coordonnées sont exprimées par rapport à l’angle supérieur gauche de la zone cliente de la fenêtre identifiée par *pWnd*.  
  
 *nIDTool*  
 ID de l’outil.  
  
 *lpszText*  
 Pointeur vers le texte de l’outil. Si ce paramètre contient la valeur LPSTR_TEXTCALLBACK, les messages de notification TTN_NEEDTEXT adressés au parent de la fenêtre qui *pWnd* pointe vers.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Le *lpRectTool* et *nIDTool* paramètres doivent être valides, ou si *lpRectTool* est NULL, *nIDTool* doit être 0.  
  
 Un contrôle info-bulle peut être associé à plusieurs outils. Appelez cette fonction pour enregistrer un outil avec le contrôle d’info-bulle Info, afin que les informations stockées dans l’info-bulle s’affiche lorsque le curseur se trouve sur l’outil.  
  
> [!NOTE]
>  Impossible de définir une info-bulle à un contrôle statique à l’aide `AddTool`.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).  
  
##  <a name="adjustrect"></a>  CToolTipCtrl::AdjustRect  
 Convertit entre le texte d’un contrôle d’info-bulle affiche le rectangle et son rectangle de la fenêtre.  
  
```  
BOOL AdjustRect(
    LPRECT lprc,  
    BOOL bLarger = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 *lprc*  
 Pointeur vers un [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) structure qui contient un rectangle de la fenêtre outil info-bulle ou un rectangle d’affichage de texte.  
  
 *bLarger*  
 Si la valeur est TRUE, *lprc* est utilisé pour spécifier un rectangle d’affichage de texte, et qu’il reçoit le rectangle de la fenêtre correspondante. Si la valeur est FALSE, *lprc* est utilisé pour spécifier un rectangle de la fenêtre, et qu’il reçoit le rectangle d’affichage de texte correspondante.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le rectangle est ajusté avec succès ; sinon 0.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre calcule le rectangle d’affichage de texte d’un contrôle info-bulle à partir de son rectangle de la fenêtre ou le rectangle de fenêtre d’info-bulle outil nécessaire pour afficher un rectangle d’affichage de texte spécifié.  
  
 Cette fonction membre implémente le comportement du message Win32 [TTM_ADJUSTRECT](/windows/desktop/Controls/ttm-adjustrect), comme décrit dans le SDK Windows.  
  
##  <a name="create"></a>  CToolTipCtrl::Create  
 Crée un contrôle info-bulle et l’attache à un `CToolTipCtrl` objet.  
  
```  
virtual BOOL Create(CWnd* pParentWnd, DWORD dwStyle = 0);
```  
  
### <a name="parameters"></a>Paramètres  
 *pParentWnd*  
 Spécifie l’outil fenêtre du contrôle parent, généralement un `CDialog`. Il ne doit pas être NULL.  
  
 *dwStyle*  
 Spécifie le style de l’outil du contrôle. Consultez le **notes** section pour plus d’informations.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le `CToolTipCtrl` objet est créé avec succès ; sinon 0.  
  
### <a name="remarks"></a>Notes  
 Vous construisez un `CToolTipCtrl` en deux étapes. Tout d’abord, appelez le constructeur pour construire le `CToolTipCtrl` de l’objet, puis appelez `Create` pour créer le contrôle d’info-bulle Info et l’attacher à la `CToolTipCtrl` objet.  
  
 Le *dwStyle* paramètre peut être n’importe quelle combinaison de [Styles de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles). En outre, un contrôle info-bulle a deux styles de classe spécifique : TTS_ALWAYSTIP et TTS_NOPREFIX.  
  
|Style|Signification|  
|-----------|-------------|  
|TTS_ALWAYSTIP|Spécifie que l’info-bulle s’affiche lorsque le curseur se trouve sur un outil, quelle que soit la fenêtre de propriétaire du contrôle info-bulle soit active ou inactive. Sans ce style, le contrôle info-bulle s’affiche lorsque la fenêtre propriétaire de l’outil est active, mais pas lorsqu’il est inactif.|  
|TTS_NOPREFIX|Ce style empêche le système de la suppression du caractère à partir d’une chaîne esperluette (&). Si un contrôle info-bulle n’a pas le style TTS_NOPREFIX, le système supprime automatiquement les caractères « et commercial », permettant à une application à utiliser la même chaîne en tant que les deux un élément de menu et en tant que texte dans un contrôle info-bulle.|  
  
 Un contrôle info-bulle a les styles de fenêtre WS_POPUP et WS_EX_TOOLWINDOW, quelle que soit leur lors de la création du contrôle.  
  
 Pour créer un contrôle info-bulle avec des styles étendus windows, appelez [CToolTipCtrl::CreateEx](#createex) au lieu de `Create`.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).  
  
##  <a name="createex"></a>  CToolTipCtrl::CreateEx  
 Crée un contrôle (une fenêtre enfant), puis associez-la à la `CToolTipCtrl` objet.  
  
```  
virtual BOOL CreateEx(
    CWnd* pParentWnd,  
    DWORD dwStyle = 0,  
    DWORD dwStyleEx = 0);
```  
  
### <a name="parameters"></a>Paramètres  
 *pParentWnd*  
 Pointeur vers la fenêtre qui est le parent du contrôle.  
  
 *dwStyle*  
 Spécifie le style de l’outil du contrôle. Consultez le **remarques** section de [créer](#create) pour plus d’informations.  
  
 *dwStyleEx*  
 Spécifie le style étendu du contrôle en cours de création. Pour obtenir la liste des styles étendus de Windows, consultez le *dwExStyle* paramètre pour [CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) dans le SDK Windows.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro en cas de réussite sinon 0.  
  
### <a name="remarks"></a>Notes  
 Utilisez `CreateEx` au lieu de `Create` pour appliquer des styles étendus de Windows, spécifiés par la préface de style étendu Windows **WS_EX_**.  
  
##  <a name="ctooltipctrl"></a>  CToolTipCtrl::CToolTipCtrl  
 Construit un objet `CToolTipCtrl`.  
  
```  
CToolTipCtrl();
```  
  
### <a name="remarks"></a>Notes  
 Vous devez appeler `Create` après la construction de l’objet.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCControlLadenDialog#74](../../mfc/codesnippet/cpp/ctooltipctrl-class_1.h)]  
  
##  <a name="deltool"></a>  CToolTipCtrl::DelTool  
 Supprime l’outil spécifié par *pWnd* et *nIDTool* à partir de la collection d’outils pris en charge par un contrôle info-bulle.  
  
```  
void DelTool(
    CWnd* pWnd,  
    UINT_PTR nIDTool = 0);
```  
  
### <a name="parameters"></a>Paramètres  
 *pWnd*  
 Pointeur vers la fenêtre qui contient l’outil.  
  
 *nIDTool*  
 ID de l’outil.  
  
##  <a name="getbubblesize"></a>  CToolTipCtrl::GetBubbleSize  
 Récupère la taille de l’info-bulle.  
  
```  
CSize GetBubbleSize(LPTOOLINFO lpToolInfo) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *lpToolInfo*  
 Un pointeur vers l’info-bulle [TOOLINFO](/windows/desktop/api/commctrl/ns-commctrl-tagtoolinfoa) structure.  
  
### <a name="return-value"></a>Valeur de retour  
 La taille de l’info-bulle.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre implémente le comportement du message Win32 [TTM_GETBUBBLESIZE](/windows/desktop/Controls/ttm-getbubblesize), comme décrit dans le SDK Windows.  
  
##  <a name="getcurrenttool"></a>  CToolTipCtrl::GetCurrentTool  
 Récupère des informations, telles que la taille, position et texte, de la fenêtre d’info-bulle affichée par le contrôle d’info-bulle actuel.  
  
```  
BOOL GetCurrentTool(LPTOOLINFO lpToolInfo) const;  
```  
  
### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|*lpToolInfo*|[out] Pointeur vers un [TOOLINFO](/windows/desktop/api/commctrl/ns-commctrl-tagtoolinfoa) structure qui reçoit des informations sur la fenêtre d’info-bulle actuel.|  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si les informations sont récupérées avec succès ; Sinon, FALSE.  
  
### <a name="remarks"></a>Notes  
 Cette méthode envoie le [TTM_GETCURRENTTOOL](/windows/desktop/Controls/ttm-getcurrenttool) message, qui est décrite dans le SDK Windows.  
  
### <a name="example"></a>Exemple  
 L’exemple de code suivant récupère des informations sur la fenêtre d’info-bulle actuel.  
  
 [!code-cpp[NVC_MFC_CToolBarCtrl_s1#6](../../mfc/reference/codesnippet/cpp/ctooltipctrl-class_2.cpp)]  
  
##  <a name="getdelaytime"></a>  CToolTipCtrl::GetDelayTime  
 Récupère l’initiale, contextuelle, délai d’apparition et durées actuellement définies pour un contrôle info-bulle.  
  
```  
int GetDelayTime(DWORD dwDuration) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *dwDuration*  
 Indicateur qui spécifie la valeur de durée est récupérées. Ce paramètre peut être une des valeurs suivantes :  
  
- TTDT_AUTOPOP récupérer la durée pendant laquelle l’info-bulle fenêtre reste visible si le pointeur de souris s’immobilise au sein du rectangle englobant d’un outil.  
  
- La durée pendant laquelle que le pointeur doit rester immobile dans le rectangle englobant d’un outil avant la fenêtre d’info-bulle outil TTDT_INITIAL récupérer s’affiche.  
  
- La longueur du temps de que nécessaire pour les fenêtres Outil suivantes info-bulle s’affichent lorsque le pointeur récupérer TTDT_RESHOW déplace à partir d’un seul outil à un autre.  
  
### <a name="return-value"></a>Valeur de retour  
 Le délai spécifié, en millisecondes  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre implémente le comportement du message Win32 [TTM_GETDELAYTIME](/windows/desktop/Controls/ttm-getdelaytime), comme décrit dans le SDK Windows.  
  
##  <a name="getmargin"></a>  CToolTipCtrl::GetMargin  
 Récupère le haut, gauche, marges inférieure et droite défini pour une fenêtre d’info-bulle outil.  
  
```  
void GetMargin(LPRECT lprc) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *lprc*  
 Adresse d’un `RECT` structure qui recevra les informations de marge. Les membres de la [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) structure ne définissent pas un rectangle englobant. Pour les besoins de ce message, les membres de structure sont interprétés comme suit :  
  
|Membre|Représentation sous forme de|  
|------------|--------------------|  
|`top`|Distance entre la bordure supérieure et le haut du texte info-bulle, en pixels.|  
|`left`|Distance entre la bordure gauche et l’extrémité gauche du texte d’info-bulle, en pixels.|  
|`bottom`|Distance entre la bordure inférieure et le bas du texte d’info-bulle, en pixels.|  
|`right`|Distance entre la bordure droite et l’extrémité droite du texte d’info-bulle, en pixels.|  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre implémente le comportement du message Win32 [TTM_GETMARGIN](/windows/desktop/Controls/ttm-getmargin), comme décrit dans le SDK Windows.  
  
##  <a name="getmaxtipwidth"></a>  CToolTipCtrl::GetMaxTipWidth  
 Récupère la largeur maximale d’une fenêtre d’info-bulle outil.  
  
```  
int GetMaxTipWidth() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 La largeur maximale d’une fenêtre d’info-bulle outil.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre implémente le comportement du message Win32 [TTM_GETMAXTIPWIDTH](/windows/desktop/Controls/ttm-getmaxtipwidth), comme décrit dans le SDK Windows.  
  
##  <a name="gettext"></a>  CToolTipCtrl::GetText  
 Récupère le texte qui tient à jour un contrôle info-bulle pour un outil.  
  
```  
void GetText(
    CString& str,  
    CWnd* pWnd,  
    UINT_PTR nIDTool = 0) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *str*  
 Référence à un `CString` objet qui reçoit le texte de l’outil.  
  
 *pWnd*  
 Pointeur vers la fenêtre qui contient l’outil.  
  
 *nIDTool*  
 ID de l’outil.  
  
### <a name="remarks"></a>Notes  
 Le *pWnd* et *nIDTool* paramètres identifient l’outil. Si cet outil a été précédemment inscrits avec le contrôle d’info-bulle Info via un appel précédent à `CToolTipCtrl::AddTool`, l’objet référencé par le *str* texte de l’outil est assignée au paramètre.  
  
##  <a name="gettipbkcolor"></a>  CToolTipCtrl::GetTipBkColor  
 Récupère la couleur d’arrière-plan dans une fenêtre d’info-bulle outil.  
  
```  
COLORREF GetTipBkColor() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un [COLORREF](/windows/desktop/gdi/colorref) valeur qui représente la couleur d’arrière-plan.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre implémente le comportement du message Win32 [TTM_GETTIPBKCOLOR](/windows/desktop/Controls/ttm-gettipbkcolor), comme décrit dans le SDK Windows.  
  
##  <a name="gettiptextcolor"></a>  CToolTipCtrl::GetTipTextColor  
 Récupère la couleur du texte dans une fenêtre d’info-bulle outil.  
  
```  
COLORREF GetTipTextColor() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un [COLORREF](/windows/desktop/gdi/colorref) valeur qui représente la couleur du texte.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre implémente le comportement du message Win32 [TTM_GETTIPTEXTCOLOR](/windows/desktop/Controls/ttm-gettiptextcolor), comme décrit dans le SDK Windows.  
  
##  <a name="gettitle"></a>  CToolTipCtrl::GetTitle  
 Récupère le titre du contrôle d’info-bulle actuel.  
  
```  
void GetTitle(PTTGETTITLE pttgt) const;  
```  
  
### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|*pttgt*|[out] Pointeur vers un [TTGETTITLE](/windows/desktop/api/commctrl/ns-commctrl-_ttgettitle) structure qui contient des informations sur le contrôle d’info-bulle. Lorsque cette méthode est retournée, le *pszTitle* membre de la [TTGETTITLE](/windows/desktop/api/commctrl/ns-commctrl-_ttgettitle) structure pointe vers le texte du titre.|  
  
### <a name="remarks"></a>Notes  
 Cette méthode envoie le [TTM_GETTITLE](/windows/desktop/Controls/ttm-gettitle) message, qui est décrite dans le SDK Windows.  
  
##  <a name="gettoolcount"></a>  CToolTipCtrl::GetToolCount  
 Récupère le nombre d’outils inscrit avec le contrôle info-bulle.  
  
```  
int GetToolCount() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un décompte des outils inscrit avec le contrôle info-bulle.  
  
##  <a name="gettoolinfo"></a>  CToolTipCtrl::GetToolInfo  
 Récupère les informations qui tient à jour un contrôle info-bulle sur un outil.  
  
```  
BOOL GetToolInfo(
    CToolInfo& ToolInfo,  
    CWnd* pWnd,  
    UINT_PTR nIDTool = 0) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *ToolInfo*  
 Référence à un `TOOLINFO` objet qui reçoit le texte de l’outil.  
  
 *pWnd*  
 Pointeur vers la fenêtre qui contient l’outil.  
  
 *nIDTool*  
 ID de l’outil.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Le `hwnd` et `uId` membres de la [TOOLINFO](/windows/desktop/api/commctrl/ns-commctrl-tagtoolinfoa) structure référencée par *CToolInfo* identifier l’outil. Si cet outil a été inscrit avec le contrôle d’info-bulle Info via un appel précédent à `AddTool`, le `TOOLINFO` structure est remplie avec des informations sur l’outil.  
  
##  <a name="hittest"></a>  CToolTipCtrl::HitTest  
 Teste un point pour déterminer s’il est dans le rectangle englobant de l’outil donné et, dans ce cas, récupérer des informations sur l’outil.  
  
```  
BOOL HitTest(
    CWnd* pWnd,  
    CPoint pt,  
    LPTOOLINFO lpToolInfo) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 *pWnd*  
 Pointeur vers la fenêtre qui contient l’outil.  
  
 *pt*  
 Pointeur vers un `CPoint` objet contenant les coordonnées du point à tester.  
  
 *lpToolInfo*  
 Pointeur vers [TOOLINFO](/windows/desktop/api/commctrl/ns-commctrl-tagtoolinfoa) structure qui contient des informations sur l’outil.  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si le point spécifié par les informations de test de positionnement au sein du rectangle englobant de l’outil ; sinon 0.  
  
### <a name="remarks"></a>Notes  
 Si cette fonction retourne une valeur différente de zéro, la structure vers laquelle pointe *lpToolInfo* est rempli d’informations sur l’outil dans dont le rectangle se trouve le point.  
  
 Le `TTHITTESTINFO` structure est définie comme suit :  
  
 `typedef struct _TT_HITTESTINFO { // tthti`  
  
 `HWND hwnd;   // handle of tool or window with tool`  
  
 `POINT pt;    // client coordinates of point to test`  
  
 `TOOLINFO ti; // receives information about the tool`  
  
 `} TTHITTESTINFO, FAR * LPHITTESTINFO;`  
  
 `hwnd`  
 Spécifie le handle de l’outil.  
  
 `pt`  
 Spécifie les coordonnées d’un point si le point est dans l’outil rectangle englobant.  
  
 `ti`  
 Informations sur l’outil. Pour plus d’informations sur la `TOOLINFO` structure, consultez [CToolTipCtrl::GetToolInfo](#gettoolinfo).  
  
##  <a name="pop"></a>  CToolTipCtrl::Pop  
 Supprime une fenêtre d’info-bulle affichée outil à partir de la vue.  
  
```  
void Pop();
```  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre implémente le comportement du message Win32 [TTM_POP](/windows/desktop/Controls/ttm-pop), comme décrit dans le SDK Windows.  
  
##  <a name="popup"></a>  CToolTipCtrl::Popup  
 Force le contrôle d’info-bulle actuel à afficher aux coordonnées du dernier message de la souris.  
  
```  
void Popup();
```  
  
### <a name="remarks"></a>Notes  
 Cette méthode envoie le [TTM_POPUP](/windows/desktop/Controls/ttm-popup) message, qui est décrite dans le SDK Windows.  
  
### <a name="example"></a>Exemple  
 L’exemple de code suivant affiche une fenêtre d’info-bulle.  
  
 [!code-cpp[NVC_MFC_CToolBarCtrl_s1#7](../../mfc/reference/codesnippet/cpp/ctooltipctrl-class_3.cpp)]  
  
##  <a name="relayevent"></a>  CToolTipCtrl::RelayEvent  
 Transmet un message de la souris à un contrôle info-bulle pour le traitement.  
  
```  
void RelayEvent(LPMSG lpMsg);
```  
  
### <a name="parameters"></a>Paramètres  
 *lpMsg*  
 Pointeur vers un [MSG](https://msdn.microsoft.com/library/windows/desktop/ms644958) structure qui contient le message à prendre le relais.  
  
### <a name="remarks"></a>Notes  
 Un contrôle info-bulle traite uniquement les messages suivants, qui sont envoyées par `RelayEvent`:  
  
|WM_LBUTTONDOWN|WM_MOUSEMOVE|  
|---------------------|-------------------|  
|WM_LBUTTONUP|WM_RBUTTONDOWN|  
|WM_MBUTTONDOWN|WM_RBUTTONUP|  
|WM_MBUTTONUP||  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).  
  
##  <a name="setdelaytime"></a>  CToolTipCtrl::SetDelayTime  
 Définit le temps de retard pour un contrôle info-bulle.  
  
```  
void SetDelayTime(UINT nDelay);

 
void SetDelayTime(
    DWORD dwDuration,  
    int iTime);
```  
  
### <a name="parameters"></a>Paramètres  
 *nDelay*  
 Spécifie le nouveau délai, en millisecondes.  
  
 *dwDuration*  
 Indicateur qui spécifie la valeur de durée est récupérées. Consultez [CToolTipCtrl::GetDelayTime](#getdelaytime) pour obtenir une description des valeurs valides.  
  
 *iTime*  
 La durée du délai spécifié, en millisecondes.  
  
### <a name="remarks"></a>Notes  
 Le temps de retard est la durée pendant laquelle que le curseur doit rester sur un outil avant la fenêtre info-bulle s’affiche. Le délai par défaut est 500 millisecondes.  
  
##  <a name="setmargin"></a>  CToolTipCtrl::SetMargin  
 Définit le haut, gauche, bas et les marges droite d’une fenêtre d’info-bulle outil.  
  
```  
void SetMargin(LPRECT lprc);
```  
  
### <a name="parameters"></a>Paramètres  
 *lprc*  
 Adresse d’un `RECT` structure qui contient les informations de la marge à définir. Les membres de la `RECT` structure ne définissent pas un rectangle englobant. Consultez [CToolTipCtrl::GetMargin](#getmargin) pour obtenir une description des informations de marge.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre implémente le comportement du message Win32 [TTM_SETMARGIN](/windows/desktop/Controls/ttm-setmargin), comme décrit dans le SDK Windows.  
  
##  <a name="setmaxtipwidth"></a>  CToolTipCtrl::SetMaxTipWidth  
 Définit la largeur maximale d’une fenêtre d’info-bulle outil.  
  
```  
int SetMaxTipWidth(int iWidth);
```  
  
### <a name="parameters"></a>Paramètres  
 *iLargeur Argument de type*  
 Largeur de la fenêtre d’info-bulle outil maximale à définir.  
  
### <a name="return-value"></a>Valeur de retour  
 La largeur maximale de conseil précédent.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre implémente le comportement du message Win32 [TTM_SETMAXTIPWIDTH](/windows/desktop/Controls/ttm-setmaxtipwidth), comme décrit dans le SDK Windows.  
  
##  <a name="settipbkcolor"></a>  CToolTipCtrl::SetTipBkColor  
 Définit la couleur d’arrière-plan dans une fenêtre d’info-bulle outil.  
  
```  
void SetTipBkColor(COLORREF clr);
```  
  
### <a name="parameters"></a>Paramètres  
 *CLR*  
 La nouvelle couleur d’arrière-plan.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre implémente le comportement du message Win32 [TTM_SETTIPBKCOLOR](/windows/desktop/Controls/ttm-settipbkcolor), comme décrit dans le SDK Windows.  
  
##  <a name="settiptextcolor"></a>  CToolTipCtrl::SetTipTextColor  
 Définit la couleur du texte dans une fenêtre d’info-bulle outil.  
  
```  
void SetTipTextColor(COLORREF clr);
```  
  
### <a name="parameters"></a>Paramètres  
 *CLR*  
 La nouvelle couleur de texte.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre implémente le comportement du message Win32 [TTM_SETTIPTEXTCOLOR](/windows/desktop/Controls/ttm-settiptextcolor), comme décrit dans le SDK Windows.  
  
##  <a name="settitle"></a>  CToolTipCtrl::SetTitle  
 Ajoute une chaîne de titre et icône standard à une info-bulle.  
  
```  
BOOL SetTitle(
    UINT uIcon,  
    LPCTSTR lpstrTitle);
```  
  
### <a name="parameters"></a>Paramètres  
 *uIcon*  
 Consultez *icône* dans [TTM_SETTITLE](/windows/desktop/Controls/ttm-settitle) dans le SDK Windows.  
  
 *lpstrTitle*  
 Pointeur vers la chaîne de titre.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre implémente le comportement du message Win32 [TTM_SETTITLE](/windows/desktop/Controls/ttm-settitle), comme décrit dans le SDK Windows.  
  
##  <a name="settoolinfo"></a>  CToolTipCtrl::SetToolInfo  
 Définit les informations qui tient à jour une info-bulle pour un outil.  
  
```  
void SetToolInfo(LPTOOLINFO lpToolInfo);
```  
  
### <a name="parameters"></a>Paramètres  
 *lpToolInfo*  
 Un pointeur vers un [TOOLINFO](/windows/desktop/api/commctrl/ns-commctrl-tagtoolinfoa) structure qui spécifie les informations à définir.  
  
##  <a name="settoolrect"></a>  CToolTipCtrl::SetToolRect  
 Définit un nouveau rectangle englobant pour un outil.  
  
```  
void SetToolRect(
    CWnd* pWnd,  
    UINT_PTR nIDTool,  
    LPCRECT lpRect);
```  
  
### <a name="parameters"></a>Paramètres  
 *pWnd*  
 Pointeur vers la fenêtre qui contient l’outil.  
  
 *nIDTool*  
 ID de l’outil.  
  
 *lpRect*  
 Pointeur vers un [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) structure en spécifiant le nouveau rectangle englobant.  
  
##  <a name="setwindowtheme"></a>  CToolTipCtrl::SetWindowTheme  
 Définit le style visuel de la fenêtre d’info-bulle outil.  
  
```  
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```  
  
### <a name="parameters"></a>Paramètres  
 *pszSubAppName*  
 Pointeur vers une chaîne Unicode qui contient le style visuel à définir.  
  
### <a name="return-value"></a>Valeur de retour  
 La valeur de retour n’est pas utilisée.  
  
### <a name="remarks"></a>Notes  
 Cette fonction membre émule la fonctionnalité de la [TTM_SETWINDOWTHEME](/windows/desktop/Controls/ttm-setwindowtheme) du message, comme décrit dans le SDK Windows.  
  
##  <a name="update"></a>  CToolTipCtrl::Update  
 Force l’outil actuel à être redessiné.  
  
```  
void Update();
```  
  
##  <a name="updatetiptext"></a>  CToolTipCtrl::UpdateTipText  
 Met à jour le texte info-bulle pour les outils de ce contrôle.  
  
```  
void UpdateTipText(
    LPCTSTR lpszText,  
    CWnd* pWnd,  
    UINT_PTR nIDTool = 0);

 
void UpdateTipText(
    UINT nIDText,  
    CWnd* pWnd,  
    UINT_PTR nIDTool = 0);
```  
  
### <a name="parameters"></a>Paramètres  
 *lpszText*  
 Pointeur vers le texte de l’outil.  
  
 *pWnd*  
 Pointeur vers la fenêtre qui contient l’outil.  
  
 *nIDTool*  
 ID de l’outil.  
  
 *nIDText*  
 ID de la ressource de chaîne qui contient le texte de l’outil.  
  
## <a name="see-also"></a>Voir aussi  
 [CWnd, classe](../../mfc/reference/cwnd-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [CToolBar, classe](../../mfc/reference/ctoolbar-class.md)
