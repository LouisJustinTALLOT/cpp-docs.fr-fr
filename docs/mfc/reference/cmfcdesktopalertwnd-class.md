---
title: Classe CMFCDesktopAlertWnd | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCDesktopAlertWnd
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::Create
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetAnimationSpeed
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetAnimationType
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetAutoCloseTime
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetCaptionHeight
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetDialogSize
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetLastPos
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetTransparency
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::HasSmallCaption
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::OnBeforeShow
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::OnClickLinkButton
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::OnCommand
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::OnDraw
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::ProcessCommand
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::SetAnimationSpeed
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::SetAnimationType
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::SetAutoCloseTime
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::SetSmallCaption
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::SetTransparency
dev_langs:
- C++
helpviewer_keywords:
- CMFCDesktopAlertWnd [MFC], Create
- CMFCDesktopAlertWnd [MFC], GetAnimationSpeed
- CMFCDesktopAlertWnd [MFC], GetAnimationType
- CMFCDesktopAlertWnd [MFC], GetAutoCloseTime
- CMFCDesktopAlertWnd [MFC], GetCaptionHeight
- CMFCDesktopAlertWnd [MFC], GetDialogSize
- CMFCDesktopAlertWnd [MFC], GetLastPos
- CMFCDesktopAlertWnd [MFC], GetTransparency
- CMFCDesktopAlertWnd [MFC], HasSmallCaption
- CMFCDesktopAlertWnd [MFC], OnBeforeShow
- CMFCDesktopAlertWnd [MFC], OnClickLinkButton
- CMFCDesktopAlertWnd [MFC], OnCommand
- CMFCDesktopAlertWnd [MFC], OnDraw
- CMFCDesktopAlertWnd [MFC], ProcessCommand
- CMFCDesktopAlertWnd [MFC], SetAnimationSpeed
- CMFCDesktopAlertWnd [MFC], SetAnimationType
- CMFCDesktopAlertWnd [MFC], SetAutoCloseTime
- CMFCDesktopAlertWnd [MFC], SetSmallCaption
- CMFCDesktopAlertWnd [MFC], SetTransparency
ms.assetid: 73a2dd7b-ea84-4ae2-9830-7cf6e8dd2425
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1947f93e65126df403feee658ade15648b081076
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37039984"
---
# <a name="cmfcdesktopalertwnd-class"></a>CMFCDesktopAlertWnd Class
La `CMFCDesktopAlertWnd` classe implémente les fonctionnalités d’une boîte de dialogue non modale qui apparaît à l’écran pour informer l’utilisateur sur un événement.  

 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]    
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCDesktopAlertWnd : public CWnd  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCDesktopAlertWnd::Create](#create)|Crée et initialise la fenêtre d’alerte de bureau.|  
|[CMFCDesktopAlertWnd::GetAnimationSpeed](#getanimationspeed)|Retourne la vitesse d’animation.|  
|[CMFCDesktopAlertWnd::GetAnimationType](#getanimationtype)|Retourne le type de l’animation.|  
|[CMFCDesktopAlertWnd::GetAutoCloseTime](#getautoclosetime)|Retourne le délai d’attente de fermeture automatique.|  
|[CMFCDesktopAlertWnd::GetCaptionHeight](#getcaptionheight)|Retourne la hauteur de la légende.|  
|[CMFCDesktopAlertWnd::GetDialogSize](#getdialogsize)||  
|[CMFCDesktopAlertWnd::GetLastPos](#getlastpos)|Retourne la dernière position valide de la fenêtre d’alerte bureau sur l’écran.|  
|[CMFCDesktopAlertWnd::GetTransparency](#gettransparency)|Retourne le niveau de transparence.|  
|[CMFCDesktopAlertWnd::HasSmallCaption](#hassmallcaption)|Détermine si la fenêtre d’alerte de bureau est affichée avec la petite légende.|  
|[CMFCDesktopAlertWnd::OnBeforeShow](#onbeforeshow)||  
|[CMFCDesktopAlertWnd::OnClickLinkButton](#onclicklinkbutton)|Appelé par le framework lorsque l’utilisateur clique sur un bouton de lien situé dans le menu alerte bureau.|  
|[CMFCDesktopAlertWnd::OnCommand](#oncommand)|L’infrastructure appelle cette fonction membre quand l’utilisateur sélectionne un élément dans un menu, lorsqu’un contrôle enfant envoie un message de notification, ou lors de la traduction d’une séquence de touches accélérateur. (Substitue [fonction membre CWnd::OnCommand](../../mfc/reference/cwnd-class.md#oncommand).)|  
|[CMFCDesktopAlertWnd::OnDraw](#ondraw)||  
|[CMFCDesktopAlertWnd::ProcessCommand](#processcommand)||  
|[CMFCDesktopAlertWnd::SetAnimationSpeed](#setanimationspeed)|Définit la vitesse d’animation.|  
|[CMFCDesktopAlertWnd::SetAnimationType](#setanimationtype)|Définit le type de l’animation.|  
|[CMFCDesktopAlertWnd::SetAutoCloseTime](#setautoclosetime)|Définit le délai d’attente de fermeture automatique.|  
|[CMFCDesktopAlertWnd::SetSmallCaption](#setsmallcaption)|Bascule entre les légendes normales et de petite taille.|  
|[CMFCDesktopAlertWnd::SetTransparency](#settransparency)|Définit le niveau de transparence.|  
  
## <a name="remarks"></a>Notes  
 Une fenêtre du bureau alerte peut être transparente, il peut être affichée avec des effets d’animation, et il peut disparaître (après un délai spécifié ou lors de l’action de l’utilisateur en cliquant sur le bouton Fermer).  
  
 Une fenêtre d’alerte bureau peut également contenir une boîte de dialogue par défaut qui à son tour contient une icône, texte du message (étiquette) et un lien. Sinon, une fenêtre du bureau alerte peut contenir une boîte de dialogue personnalisée à partir des ressources de l’application.  
  
 Vous créez une fenêtre d’alerte bureau en deux étapes. Tout d’abord, appelez le constructeur pour construire le `CMFCDesktopAlertWnd` objet. Ensuite, appelez le [CMFCDesktopAlertWnd::Create](#create) fonction membre pour créer la fenêtre et l’attacher à la `CMFCDesktopAlertWnd` objet.  
  
 Le `CMFCDesktopAlertWnd` objet crée une boîte de dialogue enfants spéciaux qui remplit la zone cliente de la fenêtre d’alerte de bureau. Tous les contrôles qui sont placés sur ce dernier est propriétaire de la boîte de dialogue.  
  
 Pour afficher une boîte de dialogue personnalisée dans la fenêtre contextuelle, procédez comme suit :  
  
1.  Dérivez une classe de `CMFCDesktopAlertDialog`.  
  
2.  Créer un modèle de boîte de dialogue enfant dans les ressources.  
  
3.  Appelez [CMFCDesktopAlertWnd::Create](#create) à l’aide de l’ID de ressource de modèle de boîte de dialogue et un pointeur vers les informations de classe runtime de la classe dérivée.  
  
4.  Programmer la boîte de dialogue personnalisée pour gérer toutes les communications en provenance des contrôles hébergés ou programmez les contrôles hébergés de gérer ces notifications directement.  
  
 Pour contrôler le comportement de la fenêtre d’alerte de bureau, utilisez les fonctions suivantes :  
  
-   Définir le type de l’animation en appelant [CMFCDesktopAlertWnd::SetAnimationType](#setanimationtype). Les options valides incluent dérouler, faites glisser et en fondu.  
  
-   Définir la vitesse de frame d’animation en appelant [CMFCDesktopAlertWnd::SetAnimationSpeed](#setanimationspeed).  
  
-   Définir le niveau de transparence en appelant [CMFCDesktopAlertWnd::SetTransparency](#settransparency).  
  
-   Modifier la taille de la légende à petite en appelant [CMFCDesktopAlertWnd::SetSmallCaption](#setsmallcaption). La petite légende est 7 pixels de haut.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser différentes méthodes de la `CMFCDesktopAlertWnd` classe permettant de configurer un `CMFCDesktopAlertWnd` objet. L’exemple montre comment définir un type d’animation, la transparence de la fenêtre indépendante, spécifiez que la fenêtre d’alerte affiche une barre de titre réduite et le temps qui s’écoule avant que la fenêtre d’alerte se ferme automatiquement. L’exemple montre également comment créer et initialiser la fenêtre d’alerte de bureau. Cet extrait de code fait partie de la [exemple de démonstration d’alerte bureau](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_DesktopAlertDemo#1](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwnd-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CMFCDesktopAlertWnd](../../mfc/reference/cmfcdesktopalertwnd-class.md)  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxDesktopAlertWnd.h  
  
##  <a name="create"></a>  CMFCDesktopAlertWnd::Create  
 Crée et initialise la fenêtre d’alerte de bureau.  
  
```  
virtual BOOL Create(
    CWnd* pWndOwner,  
    UINT uiDlgResID,  
    HMENU hMenu = NULL,  
    CPoint ptPos = CPoint(-1,-1),  
    CRuntimeClass* pRTIDlgBar = RUNTIME_CLASS(CMFCDesktopAlertDialog));

 
virtual BOOL Create(
    CWnd* pWndOwner,  
    CMFCDesktopAlertWndInfo& params,  
    HMENU hMenu = NULL,  
    CPoint ptPos = CPoint(-1,-1));
```  
  
### <a name="parameters"></a>Paramètres  
 [in] [out] *pWndOwner*  
 Spécifie le propriétaire de la fenêtre d’alerte. Ce propriétaire reçoit ensuite toutes les notifications de la fenêtre d’alerte de bureau. Cette valeur ne peut pas être `NULL`.  
  
 [in] *uiDlgResID*  
 Spécifie l’ID de ressource de la fenêtre d’alerte.  
  
 [in] *hMenu*  
 Spécifie le menu qui s’affiche lorsque l’utilisateur clique sur le bouton de menu. Si `NULL`, le bouton de menu n’est pas affiché.  
  
 [in] *ptPos*  
 Spécifie la position initiale, où la fenêtre d’alerte s’affiche, à l’aide des coordonnées d’écran. Si ce paramètre est (-1, -1), la fenêtre d’alerte s’affiche dans le coin inférieur droit de l’écran.  
  
 [in] *pRTIDlgBar*  
 Informations de classe runtime pour une classe de boîte de dialogue personnalisée qui couvre la zone cliente de la fenêtre alerte.  
  
 [in] *params*  
 Spécifie les paramètres qui sont utilisés pour créer une fenêtre d’alerte.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` Si la fenêtre d’alerte a été créée avec succès ; dans le cas contraire, `FALSE`.  
  
### <a name="remarks"></a>Notes  
 Appelez cette méthode pour créer une fenêtre d’alerte. La zone cliente de la fenêtre d’alerte contient une boîte de dialogue enfant qui héberge tous les contrôles qui sont affichés à l’utilisateur.  
  
 La première surcharge de méthode crée une fenêtre qui contient une boîte de dialogue enfant qui est chargée à partir des ressources de l’application. La première surcharge de méthode peut également spécifier des informations de classe runtime pour une classe de boîte de dialogue personnalisées.  
  
 La deuxième surcharge de méthode crée une fenêtre qui contient les contrôles par défaut. Vous pouvez spécifier les contrôles à afficher en modifiant le [cmfcdesktopalertwndinfo, classe](../../mfc/reference/cmfcdesktopalertwndinfo-class.md).  
  
##  <a name="getanimationspeed"></a>  CMFCDesktopAlertWnd::GetAnimationSpeed  
 Retourne la vitesse d’animation.  
  
```  
UINT GetAnimationSpeed() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 La vitesse d’animation de la fenêtre d’alerte, en millisecondes.  
  
### <a name="remarks"></a>Notes  
 La vitesse d’animation décrit la vitesse à laquelle la fenêtre d’alerte s’ouvre et se ferme.  
  
##  <a name="getanimationtype"></a>  CMFCDesktopAlertWnd::GetAnimationType  
 Retourne le type de l’animation.  
  
```  
CMFCPopupMenu::ANIMATION_TYPE GetAnimationType();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un des types d’animation suivants :  
  
- `NO_ANIMATION`  
  
- `UNFOLD`  
  
- `SLIDE`  
  
- `FADE`  
  
- `SYSTEM_DEFAULT_ANIMATION`  
  
##  <a name="getautoclosetime"></a>  CMFCDesktopAlertWnd::GetAutoCloseTime  
 Retourne le délai d’attente de fermeture automatique.  
  
```  
int GetAutoCloseTime() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 La durée, en millisecondes, après laquelle l’alerte fenêtre se fermera automatiquement.  
  
### <a name="remarks"></a>Notes  
 Utilisez cette méthode pour déterminer combien de temps qui doit s’écouler avant que la fenêtre se fermera automatiquement.  
  
##  <a name="getcaptionheight"></a>  CMFCDesktopAlertWnd::GetCaptionHeight  
 Retourne la hauteur de la légende.  
  
```  
virtual int GetCaptionHeight();
```  
  
### <a name="return-value"></a>Valeur de retour  
 La hauteur, en pixels, de la légende.  
  
### <a name="remarks"></a>Notes  
 Cette méthode peut être substituée dans une classe dérivée. L’implémentation par défaut soit : retourne la valeur de hauteur de petite légende (7 pixels) si la fenêtre contextuelle doit afficher la barre de titre réduite, ou la valeur obtenue à partir de la fonction API Windows `GetSystemMetrics(SM_CYSMCAPTION)`.  
  
##  <a name="getlastpos"></a>  CMFCDesktopAlertWnd::GetLastPos  
 Retourne la dernière position de la fenêtre d’alerte de bureau sur l’écran.  
  
```  
CPoint GetLastPos() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un point, en coordonnées d’écran.  
  
### <a name="remarks"></a>Notes  
 Cette méthode retourne la dernière position valide de la fenêtre d’alerte sur l’écran.  
  
##  <a name="gettransparency"></a>  CMFCDesktopAlertWnd::GetTransparency  
 Retourne le niveau de transparence.  
  
```  
BYTE GetTransparency() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un niveau de transparence comprise entre 0 et 255, inclus. Plus la valeur, la partie la plus opaque la fenêtre.  
  
### <a name="remarks"></a>Notes  
 Utilisez cette méthode pour récupérer le niveau actuel de la transparence de la fenêtre d’alerte.  
  
##  <a name="hassmallcaption"></a>  CMFCDesktopAlertWnd::HasSmallCaption  
 Détermine si la fenêtre d’alerte bureau a une barre de titre réduite ou d’une légende de la taille normale.  
  
```  
BOOL HasSmallCaption() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` Si la fenêtre contextuelle s’affiche avec une barre de titre réduite ; `FALSE` si la fenêtre contextuelle s’affiche avec une légende de la taille normale.  
  
### <a name="remarks"></a>Notes  
 Utilisez cette méthode pour déterminer si la fenêtre contextuelle a une barre de titre réduite ou d’une légende de la taille normale. Par défaut, la petite légende est 7 pixels de haut. Vous pouvez obtenir la hauteur de la légende de la taille standard en appelant la fonction API Windows `GetSystemMetrics(SM_CYCAPTION)`.  
  
##  <a name="onbeforeshow"></a>  CMFCDesktopAlertWnd::OnBeforeShow  

  
```  
virtual BOOL OnBeforeShow(CPoint&);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *CPoint &*  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="onclicklinkbutton"></a>  CMFCDesktopAlertWnd::OnClickLinkButton  
 Appelé par le framework lorsque l’utilisateur clique sur un bouton de lien situé dans le menu alerte bureau.  
  
```  
virtual BOOL OnClickLinkButton(UINT uiCmdID);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *uiCmdID*  
 Ce paramètre n'est pas utilisé.  
  
### <a name="return-value"></a>Valeur de retour  
 Toujours `FALSE`.  
  
### <a name="remarks"></a>Notes  
 Substituez cette méthode dans une classe dérivée si vous souhaitez être averti lorsqu’un utilisateur clique sur le lien dans la fenêtre d’alerte.  
  
##  <a name="oncommand"></a>  CMFCDesktopAlertWnd::OnCommand  

  
```  
virtual BOOL OnCommand(
    WPARAM wParam,  
    LPARAM lParam);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *wParam*  
 [in] *lParam*  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="ondraw"></a>  CMFCDesktopAlertWnd::OnDraw  

  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *contrôleur de domaine principal*  
  
### <a name="remarks"></a>Notes  
  
##  <a name="processcommand"></a>  CMFCDesktopAlertWnd::ProcessCommand  

  
```  
BOOL ProcessCommand(HWND hwnd);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *hwnd*  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="setanimationspeed"></a>  CMFCDesktopAlertWnd::SetAnimationSpeed  
 Définit la vitesse d’animation.  
  
```  
void SetAnimationSpeed(UINT nSpeed);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *nSpeed*  
 Spécifie la vitesse d’animation nouvelle, en millisecondes.  
  
### <a name="remarks"></a>Notes  
 Appelez cette méthode pour définir la vitesse d’animation de la fenêtre d’alerte. La vitesse d’animation par défaut est de 30 millisecondes.  
  
##  <a name="setanimationtype"></a>  CMFCDesktopAlertWnd::SetAnimationType  
 Définit le type de l’animation.  
  
```  
void SetAnimationType(CMFCPopupMenu::ANIMATION_TYPE type);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *type*  
 Spécifie le type de l’animation.  
  
### <a name="remarks"></a>Notes  
 Appelez cette méthode pour définir le type d’animation. Vous pouvez spécifier l'une des valeurs suivantes :  
  
- `NO_ANIMATION`  
  
- `UNFOLD`  
  
- `SLIDE`  
  
- `FADE`  
  
- `SYSTEM_DEFAULT_ANIMATION`  
  
##  <a name="setautoclosetime"></a>  CMFCDesktopAlertWnd::SetAutoCloseTime  
 Définit le délai d’attente de fermeture automatique.  
  
```  
void SetAutoCloseTime(int nTime);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *nTime*  
 La durée, en millisecondes, qui s’écoule avant que la fenêtre d’alerte se ferme automatiquement.  
  
### <a name="remarks"></a>Notes  
 Si l’utilisateur n’interagit pas avec la fenêtre, la fenêtre d’alerte est fermée automatiquement après l’heure spécifiée.  
  
##  <a name="setsmallcaption"></a>  CMFCDesktopAlertWnd::SetSmallCaption  
 Bascule entre les légendes de taille normale et de petite taille.  
  
```  
void SetSmallCaption(BOOL bSmallCaption = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *bSmallCaption*  
 `TRUE` Pour spécifier que la fenêtre d’alerte affiche une barre de titre réduite ; dans le cas contraire, `FALSE` pour spécifier que la fenêtre d’alerte affiche une légende de la taille normale.  
  
### <a name="remarks"></a>Notes  
 Appelez cette méthode pour afficher la légende de petite taille ou de taille normale. Par défaut, la petite légende est 7 pixels de haut. Vous pouvez obtenir la taille de la légende régulière en appelant la fonction API Windows `GetSystemMetrics(SM_CYCAPTION)`.  
  
##  <a name="settransparency"></a>  CMFCDesktopAlertWnd::SetTransparency  
 Définit le niveau de transparence de la fenêtre contextuelle.  
  
```  
void SetTransparency(BYTE nTransparency);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *nTransparency*  
 Spécifie le niveau de transparence. Cette valeur doit être comprise entre 0 et 255, inclus. Plus la valeur, la partie la plus opaque la fenêtre.  
  
### <a name="remarks"></a>Notes  
 Appelez cette fonction pour définir le niveau de transparence de la fenêtre contextuelle.  
  
##  <a name="getdialogsize"></a>  CMFCDesktopAlertWnd::GetDialogSize  

  
```  
virtual CSize GetDialogSize();
```  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [Cmfcdesktopalertwndinfo, classe](../../mfc/reference/cmfcdesktopalertwndinfo-class.md)   
 [Classe de CMFCDesktopAlertDialog](../../mfc/reference/cmfcdesktopalertdialog-class.md)   
 [CWnd, classe](../../mfc/reference/cwnd-class.md)
