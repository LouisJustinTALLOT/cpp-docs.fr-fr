---
title: CMFCCaptionBar, classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCCaptionBar
- AFXCAPTIONBAR/CMFCCaptionBar
- AFXCAPTIONBAR/CMFCCaptionBar::Create
- AFXCAPTIONBAR/CMFCCaptionBar::DoesAllowDynInsertBefore
- AFXCAPTIONBAR/CMFCCaptionBar::EnableButton
- AFXCAPTIONBAR/CMFCCaptionBar::GetAlignment
- AFXCAPTIONBAR/CMFCCaptionBar::GetBorderSize
- AFXCAPTIONBAR/CMFCCaptionBar::GetButtonRect
- AFXCAPTIONBAR/CMFCCaptionBar::GetMargin
- AFXCAPTIONBAR/CMFCCaptionBar::IsMessageBarMode
- AFXCAPTIONBAR/CMFCCaptionBar::RemoveBitmap
- AFXCAPTIONBAR/CMFCCaptionBar::RemoveButton
- AFXCAPTIONBAR/CMFCCaptionBar::RemoveIcon
- AFXCAPTIONBAR/CMFCCaptionBar::RemoveText
- AFXCAPTIONBAR/CMFCCaptionBar::SetBitmap
- AFXCAPTIONBAR/CMFCCaptionBar::SetBorderSize
- AFXCAPTIONBAR/CMFCCaptionBar::SetButton
- AFXCAPTIONBAR/CMFCCaptionBar::SetButtonPressed
- AFXCAPTIONBAR/CMFCCaptionBar::SetButtonToolTip
- AFXCAPTIONBAR/CMFCCaptionBar::SetFlatBorder
- AFXCAPTIONBAR/CMFCCaptionBar::SetIcon
- AFXCAPTIONBAR/CMFCCaptionBar::SetImageToolTip
- AFXCAPTIONBAR/CMFCCaptionBar::SetMargin
- AFXCAPTIONBAR/CMFCCaptionBar::SetText
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawBackground
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawBorder
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawButton
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawImage
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawText
- AFXCAPTIONBAR/CMFCCaptionBar::m_clrBarBackground
- AFXCAPTIONBAR/CMFCCaptionBar::m_clrBarBorder
- AFXCAPTIONBAR/CMFCCaptionBar::m_clrBarText
dev_langs:
- C++
helpviewer_keywords:
- CMFCCaptionBar [MFC], Create
- CMFCCaptionBar [MFC], DoesAllowDynInsertBefore
- CMFCCaptionBar [MFC], EnableButton
- CMFCCaptionBar [MFC], GetAlignment
- CMFCCaptionBar [MFC], GetBorderSize
- CMFCCaptionBar [MFC], GetButtonRect
- CMFCCaptionBar [MFC], GetMargin
- CMFCCaptionBar [MFC], IsMessageBarMode
- CMFCCaptionBar [MFC], RemoveBitmap
- CMFCCaptionBar [MFC], RemoveButton
- CMFCCaptionBar [MFC], RemoveIcon
- CMFCCaptionBar [MFC], RemoveText
- CMFCCaptionBar [MFC], SetBitmap
- CMFCCaptionBar [MFC], SetBorderSize
- CMFCCaptionBar [MFC], SetButton
- CMFCCaptionBar [MFC], SetButtonPressed
- CMFCCaptionBar [MFC], SetButtonToolTip
- CMFCCaptionBar [MFC], SetFlatBorder
- CMFCCaptionBar [MFC], SetIcon
- CMFCCaptionBar [MFC], SetImageToolTip
- CMFCCaptionBar [MFC], SetMargin
- CMFCCaptionBar [MFC], SetText
- CMFCCaptionBar [MFC], OnDrawBackground
- CMFCCaptionBar [MFC], OnDrawBorder
- CMFCCaptionBar [MFC], OnDrawButton
- CMFCCaptionBar [MFC], OnDrawImage
- CMFCCaptionBar [MFC], OnDrawText
- CMFCCaptionBar [MFC], m_clrBarBackground
- CMFCCaptionBar [MFC], m_clrBarBorder
- CMFCCaptionBar [MFC], m_clrBarText
ms.assetid: acb54d5f-14ff-4c96-aeb3-7717cf566d9a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5f655d8bd6fbfd19182bbaeed21eaa95739ff33d
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37038970"
---
# <a name="cmfccaptionbar-class"></a>CMFCCaptionBar, classe
A `CMFCCaptionBar` objet est une barre de contrôle qui peut afficher trois éléments : un bouton, une étiquette de texte et une image bitmap. Elle ne peut afficher qu'un élément de chaque type à la fois. Vous pouvez aligner chaque élément sur le bord gauche ou droit du contrôle ou le centrer. Vous pouvez également appliquer un style 2D ou 3D aux bordures supérieure et inférieure de la barre de légende.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCCaptionBar : public CPane  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCCaptionBar::Create](#create)|Crée le contrôle de barre de légende et l’attache à le `CMFCCaptionBar` objet.|  
|[CMFCCaptionBar::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|Indique si un autre volet peut être inséré dynamiquement entre la barre de légende et le cadre de son parent. (Substitue [CBasePane::DoesAllowDynInsertBefore](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore).)|  
|[CMFCCaptionBar::EnableButton](#enablebutton)|Active ou désactive le bouton de la barre de légende.|  
|[CMFCCaptionBar::GetAlignment](#getalignment)|Retourne l’alignement de l’élément spécifié.|  
|[CMFCCaptionBar::GetBorderSize](#getbordersize)|Retourne la taille de bordure de la barre de légende.|  
|[CMFCCaptionBar::GetButtonRect](#getbuttonrect)|Récupère le rectangle englobant du bouton sur la barre de légende.|  
|[CMFCCaptionBar::GetMargin](#getmargin)|Retourne la distance entre le bord des éléments de barre de légende et le bord du contrôle de barre de légende.|  
|[CMFCCaptionBar::IsMessageBarMode](#ismessagebarmode)|Spécifie si la barre de légende est en mode d’affichage du message.|  
|[CMFCCaptionBar::RemoveBitmap](#removebitmap)|Supprime l’image bitmap de la barre de légende.|  
|[CMFCCaptionBar::RemoveButton](#removebutton)|Supprime le bouton de la barre de légende.|  
|[CMFCCaptionBar::RemoveIcon](#removeicon)|Supprime l’icône de la barre de légende.|  
|[CMFCCaptionBar::RemoveText](#removetext)|Supprime l’étiquette de texte de la barre de légende.|  
|[CMFCCaptionBar::SetBitmap](#setbitmap)|Définit l’image bitmap de la barre de légende.|  
|[CMFCCaptionBar::SetBorderSize](#setbordersize)|Définit la taille de bordure de la barre de légende.|  
|[CMFCCaptionBar::SetButton](#setbutton)|Définit le bouton de la barre de légende.|  
|[CMFCCaptionBar::SetButtonPressed](#setbuttonpressed)|Spécifie si le bouton reste enfoncé.|  
|[CMFCCaptionBar::SetButtonToolTip](#setbuttontooltip)|Définit l’info-bulle du bouton.|  
|[CMFCCaptionBar::SetFlatBorder](#setflatborder)|Définit le style de bordure de la barre de légende.|  
|[CMFCCaptionBar::SetIcon](#seticon)|Définit l’icône de barre de légende.|  
|[CMFCCaptionBar::SetImageToolTip](#setimagetooltip)|Définit l’info-bulle de l’image de la barre de légende.|  
|[CMFCCaptionBar::SetMargin](#setmargin)|Définit la distance entre le bord de l’élément de barre de légende et le bord du contrôle de barre de légende.|  
|[CMFCCaptionBar::SetText](#settext)|Définit l’étiquette de texte de la barre de légende.|  
  
### <a name="protected-methods"></a>Méthodes protégées  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCCaptionBar::OnDrawBackground](#ondrawbackground)|Appelé par l’infrastructure pour remplir l’arrière-plan de la barre de légende.|  
|[CMFCCaptionBar::OnDrawBorder](#ondrawborder)|Appelé par l’infrastructure pour dessiner la bordure de la barre de légende.|  
|[CMFCCaptionBar::OnDrawButton](#ondrawbutton)|Appelé par l’infrastructure pour dessiner le bouton de barre de légende.|  
|[CMFCCaptionBar::OnDrawImage](#ondrawimage)|Appelé par l’infrastructure pour dessiner l’image de barre de légende.|  
|[CMFCCaptionBar::OnDrawText](#ondrawtext)|Appelé par l’infrastructure pour dessiner le texte de barre de légende.|  
  
### <a name="data-members"></a>Membres de données  
  
|Name|Description|  
|----------|-----------------|  
|[CMFCCaptionBar::m_clrBarBackground](#m_clrbarbackground)|La couleur d’arrière-plan de la barre de légende.|  
|[CMFCCaptionBar::m_clrBarBorder](#m_clrbarborder)|La couleur de la bordure de la barre de légende.|  
|[CMFCCaptionBar::m_clrBarText](#m_clrbartext)|Couleur de texte de la barre de légende.|  
  
## <a name="remarks"></a>Notes  
 Pour créer une barre de légende, procédez comme suit :  
  
1.  Construire la `CMFCCaptionBar` objet. En règle générale, vous devez ajouter la barre de légende à une classe de fenêtre frame.  
  
2.  Appelez le [CMFCCaptionBar::Create](#create) méthode pour créer le contrôle de barre de légende et l’attacher à la `CMFCCaptionBar` objet.  
  
3.  Appelez [CMFCCaptionBar::SetButton](#setbutton), [CMFCCaptionBar::SetText](#settext), [CMFCCaptionBar::SetIcon](#seticon), et [CMFCCaptionBar::SetBitmap](#setbitmap)de définir les éléments de barre de légende.  
  
 Lorsque vous définissez l’élément de bouton, vous devez affecter un ID de commande pour le bouton. Lorsque l’utilisateur clique sur le bouton, les itinéraires de barre de légende du `WM_COMMAND` messages avec ce code à la fenêtre frame parente.  
  
 La barre de légende peut également fonctionner en mode d’affichage du message qui émule la barre de message qui s’affiche dans les applications Microsoft Office 2007. En mode d’affichage de message, la barre de légende affiche une image, un message et un bouton (en général, ouvre une boîte de dialogue) Vous pouvez affecter une info-bulle pour l’image bitmap.  
  
 Pour activer le mode d’affichage des messages, appelez [CMFCCaptionBar::Create](#create) et le quatrième paramètre (bIsMessageBarMode) la valeur `TRUE`.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser différentes méthodes de la `CMFCCaptionBar` classe. L’exemple montre comment créer le contrôle de barre de légende, définissez une bordure 3D de la barre de légende, définit la distance, en pixels, entre le bord de la légende des éléments de la barre et le bord du contrôle de barre de légende, définissez le bouton de la barre de légende , définir l’info-bulle pour le bouton, affectez à l’étiquette de texte de la barre de légende, définir l’image bitmap de la barre de légende et définir l’info-bulle pour l’image dans la barre de légende. Cet extrait de code fait partie de la [exemple de démonstration de MS Office 2007](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_MSOffice2007Demo#1](../../mfc/reference/codesnippet/cpp/cmfccaptionbar-class_1.h)]  
[!code-cpp[NVC_MFC_MSOffice2007Demo#2](../../mfc/reference/codesnippet/cpp/cmfccaptionbar-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCCaptionBar](../../mfc/reference/cmfccaptionbar-class.md)  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxcaptionbar.h  
  
##  <a name="create"></a>  CMFCCaptionBar::Create  
 Crée le contrôle de barre de légende et l’attache à le `CMFCCaptionBar` objet.  
  
```  
BOOL Create(
    DWORD dwStyle,  
    CWnd* pParentWnd,  
    UINT uID,  
    int nHeight=-1,  
    BOOL bIsMessageBarMode=FALSE);
```  
  
### <a name="parameters"></a>Paramètres  
 *dwStyle*  
 La combinaison OR logique des styles de barre de légende.  
  
 *pParentWnd*  
 La fenêtre parente du contrôle de barre de légende.  
  
 *UID*  
 L’ID du contrôle de barre de légende.  
  
 *nHeight*  
 La hauteur, en pixels, du contrôle de barre de légende. S’il est -1, la hauteur est calculée en fonction de la hauteur de l’icône, le texte et le bouton affichant le contrôle de barre de légende.  
  
 *bIsMessageBarMode*  
 `TRUE` Si la barre de légende est en mode de la barre de message ; `FALSE` dans le cas contraire.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` Si le contrôle de barre de légende est créé avec succès ; `FALSE` dans le cas contraire.  
  
### <a name="remarks"></a>Notes  
 Vous construisez un `CMFCCaptionBar` objet en deux étapes. Tout d’abord, vous appelez le constructeur, et que vous appelez ensuite la `Create` méthode, ce qui crée le contrôle Windows et l’attache à le `CMFCCaptionBar` objet.  
  
##  <a name="doesallowdyninsertbefore"></a>  CMFCCaptionBar::DoesAllowDynInsertBefore  
 Indique si un autre volet peut être inséré dynamiquement entre la barre de légende et le cadre de son parent.  
  
```  
virtual BOOL DoesAllowDynInsertBefore() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne `FALSE` , sauf si la substitution.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="enablebutton"></a>  CMFCCaptionBar::EnableButton  
 Active ou désactive le bouton de la barre de légende.  
  
```  
void EnableButton(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *bActivez*  
 `TRUE` Pour activer le bouton, `FALSE` pour désactiver le bouton.  
  
##  <a name="getalignment"></a>  CMFCCaptionBar::GetAlignment  
 Retourne l’alignement de l’élément spécifié.  
  
```  
BarElementAlignment GetAlignment(BarElement elem);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *elem*  
 Un élément de barre de légende pour lequel récupérer l’alignement.  
  
### <a name="return-value"></a>Valeur de retour  
 L’alignement d’un élément, comme un bouton, une image bitmap, texte ou une icône.  
  
### <a name="remarks"></a>Notes  
 L’alignement de l’élément peut être une des valeurs suivantes :  
  
-   ALIGN_INVALID  
  
-   ALIGN_LEFT  
  
-   ALIGN_RIGHT  
  
-   ALIGN_CENTER  
  
##  <a name="getbordersize"></a>  CMFCCaptionBar::GetBorderSize  
 Retourne la taille de bordure de la barre de légende.  
  
```  
int GetBorderSize() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 La taille, en pixels, de la bordure.  
  
##  <a name="getbuttonrect"></a>  CMFCCaptionBar::GetButtonRect  
 Récupère le rectangle englobant du bouton sur la barre de légende.  
  
```  
CRect GetButtonRect() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 A `CRect` objet qui contient les coordonnées du rectangle englobant du bouton sur la barre de légende.  
  
##  <a name="getmargin"></a>  CMFCCaptionBar::GetMargin  
 Retourne la distance entre le bord des éléments de barre de légende et le bord du contrôle de barre de légende.  
  
```  
int GetMargin() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 La distance, en pixels, entre le bord des éléments de barre de légende et le bord du contrôle de barre de légende.  
  
##  <a name="ismessagebarmode"></a>  CMFCCaptionBar::IsMessageBarMode  
 Spécifie si la barre de légende est en mode d’affichage du message.  
  
```  
BOOL IsMessageBarMode() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` Si la barre de légende est en mode de la barre de message ; `FALSE` dans le cas contraire.  
  
### <a name="remarks"></a>Notes  
 En mode de la barre de message, la barre de légende affiche une image avec une info-bulle, un message texte et un bouton.  
  
##  <a name="m_clrbarbackground"></a>  CMFCCaptionBar::m_clrBarBackground  
 La couleur d’arrière-plan de la barre de légende.  
  
```  
COLORREF m_clrBarBackground  
```  
  
##  <a name="m_clrbarborder"></a>  CMFCCaptionBar::m_clrBarBorder  
 La couleur de la bordure de la barre de légende.  
  
```  
COLORREF m_clrBarBorder  
```  
  
##  <a name="m_clrbartext"></a>  CMFCCaptionBar::m_clrBarText  
 Couleur de texte de la barre de légende.  
  
```  
COLORREF m_clrBarText  
```  
  
##  <a name="ondrawbackground"></a>  CMFCCaptionBar::OnDrawBackground  
 Appelé par l’infrastructure pour remplir l’arrière-plan de la barre de légende.  
  
```  
virtual void OnDrawBackground(
    CDC* pDC,  
    CRect rect);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *contrôleur de domaine principal*  
 Pointeur vers le contexte de périphérique de la barre de légende.  
  
 [in] *rect*  
 Le rectangle à remplir.  
  
### <a name="remarks"></a>Notes  
 Le `OnDrawBackground` méthode est appelée lorsque l’arrière-plan de la barre de légende est sur le point d’être rempli. L’implémentation par défaut remplit l’arrière-plan à l’aide de la [CMFCCaptionBar::m_clrBarBackground](#m_clrbarbackground) couleur.  
  
 Substituez cette méthode dans un `CMFCCaptionBar` dérivée de la classe pour personnaliser l’apparence de la barre de légende.  
  
##  <a name="ondrawborder"></a>  CMFCCaptionBar::OnDrawBorder  
 Appelé par l’infrastructure pour dessiner la bordure de la barre de légende.  
  
```  
virtual void OnDrawBorder(
    CDC* pDC,  
    CRect rect);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *contrôleur de domaine principal*  
 Un contexte de périphérique qui est utilisé pour afficher les bordures.  
  
 [in] *rect*  
 Rectangle englobant.  
  
### <a name="remarks"></a>Notes  
 Par défaut, les bordures ont le style à deux dimensions.  
  
 Substituez cette méthode dans un `CMFCCaptionBar` dérivée de la classe pour personnaliser l’apparence des bordures de la barre de légende.  
  
##  <a name="ondrawbutton"></a>  CMFCCaptionBar::OnDrawButton  
 Appelé par l’infrastructure pour dessiner le bouton de barre de légende.  
  
```  
virtual void OnDrawButton(
    CDC* pDC,  
    CRect rect,  
    const CString& strButton,  
    BOOL bEnabled);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *contrôleur de domaine principal*  
 Pointeur vers un contexte de périphérique qui est utilisé pour afficher le bouton.  
  
 [in] *rect*  
 Le rectangle englobant du bouton.  
  
 [in] *strButton*  
 Étiquette de texte du bouton.  
  
 [in] *case d’option bActivé*  
 `TRUE` Si le bouton est activé ; `FALSE` dans le cas contraire.  
  
### <a name="remarks"></a>Notes  
 Substituez cette méthode dans un `CMFCCaptionBar` dérivée de la classe pour personnaliser l’apparence du bouton de la barre de légende.  
  
##  <a name="ondrawimage"></a>  CMFCCaptionBar::OnDrawImage  
 Appelé par l’infrastructure pour dessiner l’image de barre de légende.  
  
```  
virtual void OnDrawImage(
    CDC* pDC,  
    CRect rect);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *contrôleur de domaine principal*  
 Pointeur vers un contexte de périphérique qui est utilisé pour afficher l’image.  
  
 [in] *rect*  
 Spécifie le rectangle englobant de l’image.  
  
### <a name="remarks"></a>Notes  
 Substituez cette méthode dans un `CMFCCaptionBar` dérivée de la classe pour personnaliser l’apparence de l’image.  
  
##  <a name="ondrawtext"></a>  CMFCCaptionBar::OnDrawText  
 Appelé par l’infrastructure pour dessiner le texte de barre de légende.  
  
```  
virtual void OnDrawText(
    CDC* pDC,  
    CRect rect,  
    const CString& strText);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *contrôleur de domaine principal*  
 Pointeur vers un contexte de périphérique qui est utilisé pour afficher le bouton.  
  
 [in] *rect*  
 Le rectangle englobant du texte.  
  
 [in] *%{strText/}*  
 La chaîne de texte à afficher.  
  
### <a name="remarks"></a>Notes  
 L’implémentation par défaut affiche le texte à l’aide de `CDC::DrawText` et [CMFCCaptionBar::m_clrBarText](#m_clrbartext) couleur.  
  
 Substituez cette méthode dans un `CMFCCaptionBar` dérivée de la classe pour personnaliser l’apparence du texte de la barre de légende.  
  
##  <a name="removebitmap"></a>  CMFCCaptionBar::RemoveBitmap  
 Supprime l’image bitmap de la barre de légende.  
  
```  
void RemoveBitmap();
```  
  
##  <a name="removebutton"></a>  CMFCCaptionBar::RemoveButton  
 Supprime le bouton de la barre de légende.  
  
```  
void RemoveButton();
```  
  
### <a name="remarks"></a>Notes  
 La disposition des éléments de barre de légende sont ajustés automatiquement.  
  
##  <a name="removeicon"></a>  CMFCCaptionBar::RemoveIcon  
 Supprime l’icône de la barre de légende.  
  
```  
void RemoveIcon();
```  
  
##  <a name="removetext"></a>  CMFCCaptionBar::RemoveText  
 Supprime l’étiquette de texte de la barre de légende.  
  
```  
void RemoveText();
```  
  
##  <a name="setbitmap"></a>  CMFCCaptionBar::SetBitmap  
 Définit l’image bitmap de la barre de légende.  
  
```  
void SetBitmap(
    HBITMAP hBitmap,  
    COLORREF clrTransparent,  
    BOOL bStretch=FALSE,  
    BarElementAlignment bmpAlignment=ALIGN_RIGHT);

 
void SetBitmap(
    UINT uiBmpResID,  
    COLORREF clrTransparent,  
    BOOL bStretch=FALSE,  
    BarElementAlignment bmpAlignment=ALIGN_RIGHT);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *hBitmap*  
 Handle de l’image bitmap à définir.  
  
 [in] *clrTransparent*  
 Une valeur RVB qui spécifie la couleur transparente de l’image bitmap.  
  
 [in] *bStretch*  
 Si `TRUE`, la bitmap est étendue si elle ne tient pas à l’image du rectangle englobant. Dans le cas contraire, l’image bitmap n’est pas étendue.  
  
 [in] *bmpAlignment*  
 L’alignement de l’image bitmap.  
  
### <a name="remarks"></a>Notes  
 Utilisez cette méthode pour définir une image bitmap sur une barre de légende.  
  
 L’image bitmap précédent est supprimé automatiquement. Si la barre de légende affiche une icône, car vous avez appelé la [CMFCCaptionBar::SetIcon](#seticon) (méthode), l’image bitmap ne s’affichera pas sauf si vous supprimez l’icône en appelant [CMFCCaptionBar::RemoveIcon](#removeicon).  
  
 L’image bitmap est aligné comme spécifié par le *bmpAlignment* paramètre.  Ce paramètre peut avoir l'une des valeurs `BarElementAlignment` suivantes :  
  
-   ALIGN_INVALID  
  
-   ALIGN_LEFT  
  
-   ALIGN_RIGHT  
  
-   ALIGN_CENTER  
  
##  <a name="setbordersize"></a>  CMFCCaptionBar::SetBorderSize  
 Définit la taille de bordure de la barre de légende.  
  
```  
void SetBorderSize(int nSize);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *nSize*  
 La nouvelle taille, en pixels, de la bordure de barre de légende.  
  
##  <a name="setbutton"></a>  CMFCCaptionBar::SetButton  
 Définit le bouton de la barre de légende.  
  
```  
void SetButton(
    LPCTSTR lpszLabel,  
    UINT uiCmdUI,  
    BarElementAlignment btnAlignmnet=ALIGN_LEFT,  
    BOOL bHasDropDownArrow=TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 *lpszLabel*  
 L’étiquette du bouton commande.  
  
 *uiCmdUI*  
 ID de commande. du bouton  
  
 *btnAlignmnet*  
 Alignement du bouton.  
  
 *bHasDropDownArrow*  
 `TRUE` Si le bouton affiche une liste déroulante flèche, `FALSE` dans le cas contraire.  
  
##  <a name="setbuttonpressed"></a>  CMFCCaptionBar::SetButtonPressed  
 Spécifie si le bouton reste enfoncé.  
  
```  
void SetButtonPressed(BOOL bPresed=TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 *bPresed*  
 `TRUE` Si le bouton conserve son état enfoncé, `FALSE` dans le cas contraire.  
  
##  <a name="setbuttontooltip"></a>  CMFCCaptionBar::SetButtonToolTip  
 Définit l’info-bulle du bouton.  
  
```  
void SetButtonToolTip(
    LPCTSTR lpszToolTip,  
    LPCTSTR lpszDescription=NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *lpszToolTip*  
 La légende de l’info-bulle.  
  
 [in] *lpszDescription*  
 Description de l’info-bulle.  
  
##  <a name="setflatborder"></a>  CMFCCaptionBar::SetFlatBorder  
 Définit le style de bordure de la barre de légende.  
  
```  
void SetFlatBorder(BOOL bFlat=TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *bFlat*  
 `TRUE` Si la bordure d’une barre de légende est en deux dimensions. `FALSE` Si la bordure est 3D.  
  
##  <a name="seticon"></a>  CMFCCaptionBar::SetIcon  
 Définit l’icône de barre de légende.  
  
```  
void SetIcon(
    HICON hIcon,  
    BarElementAlignment iconAlignment=ALIGN_RIGHT);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *hIcon*  
 Le handle de l’icône à définir.  
  
 [in] *iconAlignment*  
 L’alignement de l’icône.  
  
### <a name="remarks"></a>Notes  
 Barres de légende peuvent afficher des icônes ou bitmaps. Consultez [CMFCCaptionBar::SetBitmap](#setbitmap) pour savoir comment afficher une image bitmap. Si vous définissez une icône et une image bitmap, l’icône est toujours affichée. Appelez [CMFCCaptionBar::RemoveIcon](#removeicon) pour supprimer une icône de la barre de légende.  
  
 L’icône est aligné en fonction de la *iconAlignment* paramètre. Il peut être une de ces `BarElementAlignment` valeurs :  
  
-   ALIGN_INVALID  
  
-   ALIGN_LEFT  
  
-   ALIGN_RIGHT  
  
-   ALIGN_CENTER  
  
##  <a name="setimagetooltip"></a>  CMFCCaptionBar::SetImageToolTip  
 Définit l’info-bulle pour l’image dans la barre de légende.  
  
```  
void SetImageToolTip(
    LPCTSTR lpszToolTip,  
    LPCTSTR lpszDescription=NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *lpszToolTip*  
 Le texte de l’info-bulle.  
  
 [in] *lpszDescription*  
 Description de l’info-bulle.  
  
##  <a name="setmargin"></a>  CMFCCaptionBar::SetMargin  
 Définit la distance entre le bord de l’élément de barre de légende et le bord du contrôle de barre de légende.  
  
```  
void SetMargin(int nMargin);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *nMargin*  
 La distance, en pixels, entre le bord des éléments de barre de légende et le bord du contrôle de barre de légende.  
  
##  <a name="settext"></a>  CMFCCaptionBar::SetText  
 Définit l’étiquette de texte de la barre de légende.  
  
```  
void SetText(
    const CString& strText,  
    BarElementAlignment textAlignment=ALIGN_RIGHT);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *%{strText/}*  
 La chaîne de texte à définir.  
  
 [in] *textAlignment*  
 L’alignement du texte.  
  
### <a name="remarks"></a>Notes  
 L’étiquette de texte est aligné comme spécifié par le *textAlignment* paramètre. Il peut être une de ces `BarElementAlignment` valeurs :  
  
-   ALIGN_INVALID  
  
-   ALIGN_LEFT  
  
-   ALIGN_RIGHT  
  
-   ALIGN_CENTER  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)
