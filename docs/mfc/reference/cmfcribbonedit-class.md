---
title: Classe de CMFCRibbonEdit | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonEdit
- AFXRIBBONEDIT/CMFCRibbonEdit
- AFXRIBBONEDIT/CMFCRibbonEdit::CMFCRibbonEdit
- AFXRIBBONEDIT/CMFCRibbonEdit::CanBeStretched
- AFXRIBBONEDIT/CMFCRibbonEdit::CMFCRibbonEdit
- AFXRIBBONEDIT/CMFCRibbonEdit::CopyFrom
- AFXRIBBONEDIT/CMFCRibbonEdit::CreateEdit
- AFXRIBBONEDIT/CMFCRibbonEdit::DestroyCtrl
- AFXRIBBONEDIT/CMFCRibbonEdit::DropDownList
- AFXRIBBONEDIT/CMFCRibbonEdit::EnableSpinButtons
- AFXRIBBONEDIT/CMFCRibbonEdit::GetCompactSize
- AFXRIBBONEDIT/CMFCRibbonEdit::GetEditText
- AFXRIBBONEDIT/CMFCRibbonEdit::GetIntermediateSize
- AFXRIBBONEDIT/CMFCRibbonEdit::GetTextAlign
- AFXRIBBONEDIT/CMFCRibbonEdit::GetWidth
- AFXRIBBONEDIT/CMFCRibbonEdit::HasCompactMode
- AFXRIBBONEDIT/CMFCRibbonEdit::HasFocus
- AFXRIBBONEDIT/CMFCRibbonEdit::HasLargeMode
- AFXRIBBONEDIT/CMFCRibbonEdit::HasSpinButtons
- AFXRIBBONEDIT/CMFCRibbonEdit::IsHighlighted
- AFXRIBBONEDIT/CMFCRibbonEdit::OnAfterChangeRect
- AFXRIBBONEDIT/CMFCRibbonEdit::OnDraw
- AFXRIBBONEDIT/CMFCRibbonEdit::OnDrawLabelAndImage
- AFXRIBBONEDIT/CMFCRibbonEdit::OnDrawOnList
- AFXRIBBONEDIT/CMFCRibbonEdit::OnEnable
- AFXRIBBONEDIT/CMFCRibbonEdit::OnHighlight
- AFXRIBBONEDIT/CMFCRibbonEdit::OnKey
- AFXRIBBONEDIT/CMFCRibbonEdit::OnLButtonDown
- AFXRIBBONEDIT/CMFCRibbonEdit::OnLButtonUp
- AFXRIBBONEDIT/CMFCRibbonEdit::OnRTLChanged
- AFXRIBBONEDIT/CMFCRibbonEdit::OnShow
- AFXRIBBONEDIT/CMFCRibbonEdit::Redraw
- AFXRIBBONEDIT/CMFCRibbonEdit::SetACCData
- AFXRIBBONEDIT/CMFCRibbonEdit::SetEditText
- AFXRIBBONEDIT/CMFCRibbonEdit::SetTextAlign
- AFXRIBBONEDIT/CMFCRibbonEdit::SetWidth
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonEdit class
ms.assetid: 9b85f1f2-446b-454e-9af9-104fdad8a897
caps.latest.revision: 25
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 03eb96bf971b53a2100e6f93bac2f0641f0298e1
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcribbonedit-class"></a>CMFCRibbonEdit (classe)
Implémente un contrôle d’édition qui se trouve sur une barre de ruban.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCRibbonEdit : public CMFCRibbonButton  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCRibbonEdit::CMFCRibbonEdit](#cmfcribbonedit)|Construit un objet `CMFCRibbonEdit`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCRibbonEdit::CanBeStretched](#canbestretched)|Indique si la hauteur de la `CMFCRibbonEdit` contrôle peut augmenter verticalement à la hauteur d’une ligne de ruban.|  
|[CMFCRibbonEdit::CMFCRibbonEdit](#cmfcribbonedit)|Construit un objet `CMFCRibbonEdit`.|  
|[CMFCRibbonEdit::CopyFrom](#copyfrom)|Copie de l’état de l’objet `CMFCRibbonEdit` objet actuel `CMFCRibbonEdit` objet.|  
|[CMFCRibbonEdit::CreateEdit](#createedit)|Crée une nouvelle zone de texte pour le `CMFCRibbonEdit` objet.|  
|[CMFCRibbonEdit::DestroyCtrl](#destroyctrl)|Détruit le `CMFCRibbonEdit` objet.|  
|[CMFCRibbonEdit::DropDownList](#dropdownlist)|Une zone de liste se déroule.|  
|[CMFCRibbonEdit::EnableSpinButtons](#enablespinbuttons)|Active et définit la plage de la toupie pour la zone de texte.|  
|[CMFCRibbonEdit::GetCompactSize](#getcompactsize)|Récupère la taille compacte de le `CFMCRibbonEdit` objet.|  
|[CMFCRibbonEdit::GetEditText](#getedittext)|Récupère le texte dans la zone de texte.|  
|[CMFCRibbonEdit::GetIntermediateSize](#getintermediatesize)|Récupère la taille intermédiaire de la `CMFCRibbonEdit` objet.|  
|[CMFCRibbonEdit::GetTextAlign](#gettextalign)|Récupère l’alignement du texte dans la zone de texte.|  
|[CMFCRibbonEdit::GetWidth](#getwidth)|Récupère la largeur, en pixels, de la `CMFCRibbonEdit` contrôle.|  
|[CMFCRibbonEdit::HasCompactMode](#hascompactmode)|Indique si l’affichage de la taille de la `CMFCRibbonEdit` contrôle peut être compact.|  
|[CMFCRibbonEdit::HasFocus](#hasfocus)|Indique si le `CMFCRIbbonEdit` contrôle a le focus.|  
|[CMFCRibbonEdit::HasLargeMode](#haslargemode)|Indique si l’affichage de la taille de la `CMFCRibbonEdit` contrôle peut être volumineux.|  
|[CMFCRibbonEdit::HasSpinButtons](#hasspinbuttons)|Indique si la zone de texte a un bouton de sélection numérique.|  
|[CMFCRibbonEdit::IsHighlighted](#ishighlighted)|Indique si le `CMFCRibbonEdit` contrôle est mis en surbrillance.|  
|[CMFCRibbonEdit::OnAfterChangeRect](#onafterchangerect)|Appelé par l’infrastructure lorsque les dimensions du rectangle d’affichage du `CMFCRibbonEdit` contrôle change.|  
|[CMFCRibbonEdit::OnDraw](#ondraw)|Appelé par l’infrastructure pour dessiner le `CMFCRibbonEdit` contrôle.|  
|[CMFCRibbonEdit::OnDrawLabelAndImage](#ondrawlabelandimage)|Appelée par l’infrastructure pour dessiner l’étiquette et de l’image pour le `CMFCRibbonEdit` contrôle.|  
|[CMFCRibbonEdit::OnDrawOnList](#ondrawonlist)|Appelé par l’infrastructure pour dessiner le `CMFCRibbonEdit` contrôle dans une zone de liste de commandes.|  
|[CMFCRibbonEdit::OnEnable](#onenable)|Appelé par l’infrastructure pour activer ou désactiver la `CMFCRibbonEdit` contrôle.|  
|[CMFCRibbonEdit::OnHighlight](#onhighlight)|Appelé par l’infrastructure lorsque le pointeur entre ou quitte les limites de la `CMFCRibbonEdit` contrôle.|  
|[CMFCRibbonEdit::OnKey](#onkey)|Appelé par l’infrastructure lorsque l’utilisateur appuie sur une touche d’accès et le `CMFCRibbonEdit` contrôle a le focus.|  
|[CMFCRibbonEdit::OnLButtonDown](#onlbuttondown)|Appelé par l’infrastructure pour mettre à jour la `CMFCRibbonEdit` contrôle lorsque l’utilisateur appuie sur le bouton gauche de la souris sur le contrôle.|  
|[CMFCRibbonEdit::OnLButtonUp](#onlbuttonup)|Appelé par l’infrastructure lorsque l’utilisateur relâche le bouton gauche de la souris.|  
|[CMFCRibbonEdit::OnRTLChanged](#onrtlchanged)|Appelé par l’infrastructure pour mettre à jour la `CMFCRibbonEdit` contrôle lorsque la disposition change de direction.|  
|[CMFCRibbonEdit::OnShow](#onshow)|Appelé par l’infrastructure pour afficher ou masquer la `CMFCRibbonEdit` contrôle.|  
|[CMFCRibbonEdit::Redraw](#redraw)|Met à jour l’affichage de la `CMFCRibbonEdit` contrôle.|  
|[CMFCRibbonEdit::SetACCData](#setaccdata)|Définit les données d’accessibilité pour les `CMFCRibbonEdit` objet.|  
|[CMFCRibbonEdit::SetEditText](#setedittext)|Définit le texte dans la zone de texte.|  
|[CMFCRibbonEdit::SetTextAlign](#settextalign)|Définit l’alignement du texte de la zone de texte.|  
|[CMFCRibbonEdit::SetWidth](#setwidth)|Définit la largeur de la zone de texte pour le `CMFCRibbonEdit` contrôle.|  
  
## <a name="remarks"></a>Remarques  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment construire un `CMFCRibbonEdit` de l’objet, afficher les boutons de sélection numérique en regard du contrôle d’édition et définir le texte du contrôle d’édition. Cet extrait de code fait partie de la [exemple de démonstration de MS Office 2007](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_MSOffice2007Demo&#7;](../../mfc/reference/codesnippet/cpp/cmfcribbonedit-class_1.cpp)]  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxRibbonEdit.h  
  
##  <a name="canbestretched"></a>CMFCRibbonEdit::CanBeStretched  
 Indique si la hauteur de la [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) contrôle peut augmenter verticalement à la hauteur d’une ligne de ruban.  
  
```  
virtual BOOL CanBeStretched();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne toujours `FALSE`.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="cmfcribbonedit"></a>CMFCRibbonEdit::CMFCRibbonEdit  
 Construit un [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) objet.  
  
```  
CMFCRibbonEdit(
    UINT nID,  
    int nWidth,  
    LPCTSTR lpszLabel = NULL,  
    int nImage = -1);

CMFCRibbonEdit();
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nID`  
 ID de commande du `CMFCRibbonEdit` contrôle.  
  
 [in] `nWidth`  
 La largeur, en pixels, de la zone de texte pour le `CMFCRibbonEdit` contrôle.  
  
 [in] `lpszLabel`  
 L’étiquette de la `CMFCRibbonEdit` contrôle.  
  
 [in] `nImage`  
 Index de l’image à utiliser pour la `CMFCRibbonEdit` contrôle. La collection de petites images est gérée par la catégorie de ruban parent.  
  
### <a name="remarks"></a>Notes  
 Le `CMFCRibbonEdit` contrôle n’utilise pas une grande image.  
  
##  <a name="copyfrom"></a>CMFCRibbonEdit::CopyFrom  
 Copie de l’état de l’objet [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) objet actuel [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) objet.  
  
```  
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `src`  
 Objet `CMFCRibbonEdit` source.  
  
### <a name="remarks"></a>Notes  
 Le `src` paramètre doit être de type `CMFCRibbonEdit`.  
  
##  <a name="createedit"></a>CMFCRibbonEdit::CreateEdit  
 Crée une nouvelle zone de texte pour le [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) objet.  
  
```  
virtual CMFCRibbonRichEditCtrl* CreateEdit(
    CWnd* pWndParent,  
    DWORD dwEditStyle);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pWndParent`  
 Un pointeur vers la fenêtre parente de la `CMFCRibbonEdit` objet.  
  
 [in] `dwEditStyle`  
 Spécifie le style de la zone de texte. Vous pouvez combiner les styles de fenêtre répertoriés dans la section Notes avec le [modifier les styles de contrôle](http://msdn.microsoft.com/library/windows/desktop/bb775464) qui sont décrites dans le SDK Windows.  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers la nouvelle zone de texte si la méthode a réussi ; dans le cas contraire, `NULL`.  
  
### <a name="remarks"></a>Notes  
 Substituez cette méthode dans une classe dérivée pour créer une zone de texte personnalisé.  
  
 Vous pouvez appliquer ce qui suit [Styles de fenêtre](../../mfc/reference/window-styles.md) pour une zone de texte :  
  
- **WS_CHILD**  
  
- **WS_VISIBLE**  
  
- **WS_DISABLED**  
  
- **WS_GROUP**  
  
- **WS_TABSTOP**  
  
##  <a name="destroyctrl"></a>CMFCRibbonEdit::DestroyCtrl  
 Détruit le [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) objet.  
  
```  
virtual void DestroyCtrl();
```  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="dropdownlist"></a>CMFCRibbonEdit::DropDownList  
 Une zone de liste se déroule.  
  
```  
virtual void DropDownList();
```  
  
### <a name="remarks"></a>Remarques  
 Par défaut, cette méthode ne fait rien. Substituez cette méthode pour une zone de liste déroulante.  
  
##  <a name="enablespinbuttons"></a>CMFCRibbonEdit::EnableSpinButtons  
 Active et définit la plage de la toupie pour la zone de texte.  
  
```  
void EnableSpinButtons(
    int nMin,  
    int nMax);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nMin`  
 La valeur minimale de la toupie.  
  
 [in] `nMax`  
 La valeur maximale de la toupie.  
  
### <a name="remarks"></a>Remarques  
 Boutons de sélection numérique affichent le haut et flèche vers le bas et permettent aux utilisateurs de parcourir un ensemble fixe de valeurs.  
  
##  <a name="getcompactsize"></a>CMFCRibbonEdit::GetCompactSize  
 Récupère la taille compacte de le [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) objet.  
  
```  
virtual CSize GetCompactSize(CDC* pDC);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pDC`  
 Pointeur vers un contexte de périphérique pour le `CMFCRibbonEdit` objet.  
  
### <a name="return-value"></a>Valeur de retour  
 La taille compacte de le `CMFCRibbonEdit` objet.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getedittext"></a>CMFCRibbonEdit::GetEditText  
 Récupère le texte dans la zone de texte.  
  
```  
CString GetEditText() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le texte dans la zone de texte.  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="getintermediatesize"></a>CMFCRibbonEdit::GetIntermediateSize  
 Récupère la taille intermédiaire de la [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) objet.  
  
```  
virtual CSize GetIntermediateSize(CDC* pDC);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pDC`  
 Pointeur vers un contexte de périphérique pour le `CMFCRibbonEdit` objet.  
  
### <a name="return-value"></a>Valeur de retour  
 La taille des intermédiaire du `CMFCRibbonEdit` objet.  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="gettextalign"></a>CMFCRibbonEdit::GetTextAlign  
 Récupère l’alignement du texte dans la zone de texte.  
  
```  
int GetTextAlign() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un alignement de texte de valeur énumérée. Consultez la section Notes pour les valeurs possibles.  
  
### <a name="remarks"></a>Remarques  
 La valeur renvoyée est un des styles de contrôle d’édition suivants :  
  
- **ES_LEFT** pour l’alignement à gauche  
  
- **ES_CENTER** pour alignement au centre  
  
- **ES_RIGHT** d’alignement à droite  
  
 Pour plus d’informations sur ces styles, consultez [modifier les Styles de contrôle](http://msdn.microsoft.com/library/windows/desktop/bb775464).  
  
##  <a name="getwidth"></a>CMFCRibbonEdit::GetWidth  
 Récupère la largeur, en pixels, de la [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) contrôle.  
  
```  
int GetWidth(BOOL bInFloatyMode = FALSE) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `bInFloatyMode`  
 `TRUE`Si le `CMFCRibbonEdit` contrôle est en mode flottant ; sinon, `FALSE`.  
  
### <a name="return-value"></a>Valeur de retour  
 La largeur, en pixels, de la `CMFCRibbonEdit` contrôle.  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="hascompactmode"></a>CMFCRibbonEdit::HasCompactMode  
 Indique si l’affichage de la taille de la [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) contrôle peut être compact.  
  
```  
virtual BOOL HasCompactMode() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne toujours `TRUE`.  
  
### <a name="remarks"></a>Remarques  
 Par défaut cette méthode retourne toujours `TRUE`. Substituez cette méthode pour indiquer si la taille d’affichage peut être compacte.  
  
##  <a name="hasfocus"></a>CMFCRibbonEdit::HasFocus  
 Indique si le [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) contrôle a le focus.  
  
```  
virtual BOOL HasFocus() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si le `CMFCRibbonEdit` contrôle a le focus ; sinon `FALSE`.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="haslargemode"></a>CMFCRibbonEdit::HasLargeMode  
 Indique si l’affichage de la taille de la [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) contrôle peut être volumineux.  
  
```  
virtual BOOL HasLargeMode() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne toujours `FALSE`.  
  
### <a name="remarks"></a>Remarques  
 Par défaut cette méthode retourne toujours `FALSE`. Substituez cette méthode pour indiquer si la taille d’affichage peut être volumineux.  
  
##  <a name="hasspinbuttons"></a>CMFCRibbonEdit::HasSpinButtons  
 Indique si la zone de texte a un bouton de sélection numérique.  
  
```  
virtual BOOL HasSpinButtons() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si la zone de texte comporte un bouton toupie (spin) ; dans le cas contraire `FALSE`.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="ishighlighted"></a>CMFCRibbonEdit::IsHighlighted  
 Indique si le [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) contrôle est mis en surbrillance.  
  
```  
virtual BOOL IsHighlighted() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si le `CMFCRibbonEdit` contrôle est mis en surbrillance ; sinon `FALSE`.  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="onafterchangerect"></a>CMFCRibbonEdit::OnAfterChangeRect  
 Appelé par l’infrastructure lorsque les dimensions du rectangle d’affichage du [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) contrôle le changement.  
  
```  
virtual void OnAfterChangeRect(CDC* pDC);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pDC`  
 Pointeur vers un contexte de périphérique pour le `CMFCRibbonEdit` contrôle.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="ondraw"></a>CMFCRibbonEdit::OnDraw  
 Appelé par l’infrastructure pour dessiner le [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) contrôle.  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pDC`  
 Pointeur vers un contexte de périphérique pour le `CMFCRibbonEdit` contrôle.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="ondrawlabelandimage"></a>CMFCRibbonEdit::OnDrawLabelAndImage  
 Appelée par l’infrastructure pour dessiner l’étiquette et de l’image pour le [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) contrôle.  
  
```  
virtual void OnDrawLabelAndImage(CDC* pDC);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pDC`  
 Pointeur vers un contexte de périphérique pour le `CMFCRibbonEdit` contrôle.  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="ondrawonlist"></a>CMFCRibbonEdit::OnDrawOnList  
 Appelé par l’infrastructure pour dessiner le [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) contrôle dans une zone de liste de commandes.  
  
```  
virtual void OnDrawOnList(
    CDC* pDC,  
    CString strText,  
    int nTextOffset,  
    CRect rect,  
    BOOL bIsSelected,  
    BOOL bHighlighted);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `pDC`  
 Pointeur vers un contexte de périphérique pour le `CMFCRibbonEdit` contrôle.  
  
 [in] `strText`  
 Le texte d’affichage [ ](../../mfc/reference/cmfcribbonedit-class.md "cmfcribbonedit class").  
  
 [in] `nTextOffset`  
 Distance, en pixels, du côté gauche de la zone de liste pour afficher du texte.  
  
 [in] `rect`  
 Le rectangle d’affichage pour le `CMFCRibbonEdit` contrôle.  
  
 [in] `bIsSelected`  
 Ce paramètre n'est pas utilisé.  
  
 [in] `bHighlighted`  
 Ce paramètre n'est pas utilisé.  
  
### <a name="remarks"></a>Notes  
 La zone de liste de commandes affiche les contrôles de ruban pour permettre aux utilisateurs de personnaliser la barre d’outils Accès rapide.  
  
##  <a name="onenable"></a>CMFCRibbonEdit::OnEnable  
 Appelé par l’infrastructure pour activer ou désactiver la [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) contrôle.  
  
```  
virtual void OnEnable(BOOL bEnable);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `bEnable`  
 `TRUE`Pour activer le contrôle ; `FALSE` pour désactiver le contrôle.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="onhighlight"></a>CMFCRibbonEdit::OnHighlight  
 Appelé par l’infrastructure lorsque le pointeur entre ou quitte les limites de la [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) contrôle.  
  
```  
virtual void OnHighlight(BOOL bHighlight);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `bHighlight`  
 `TRUE`Si le pointeur se trouve dans les limites de la `CMFCRibbonEdit` contrôle ; sinon, `FALSE`.  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="onkey"></a>CMFCRibbonEdit::OnKey  
 Appelé par l’infrastructure lorsque l’utilisateur appuie sur une touche d’accès et le [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) contrôle a le focus.  
  
```  
virtual BOOL OnKey(BOOL bIsMenuKey);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `bIsMenuKey`  
 `TRUE`Si la touche d’accès affiche un menu contextuel. dans le cas contraire, `FALSE`.  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE` si l’événement a été géré ; sinon, `FALSE`.  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="onlbuttondown"></a>CMFCRibbonEdit::OnLButtonDown  
 Appelé par l’infrastructure pour mettre à jour la [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) contrôle lorsque l’utilisateur appuie sur le bouton gauche de la souris sur le contrôle.  
  
```  
virtual void OnLButtonDown(CPoint point);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `point`  
 Ce paramètre n'est pas utilisé.  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="onlbuttonup"></a>CMFCRibbonEdit::OnLButtonUp  
 Appelé par l’infrastructure lorsque l’utilisateur relâche le bouton gauche de la souris.  
  
```  
virtual void OnLButtonUp(CPoint point);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `point`  
 Ce paramètre n'est pas utilisé.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="onrtlchanged"></a>CMFCRibbonEdit::OnRTLChanged  
 Appelé par l’infrastructure pour mettre à jour la [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) contrôle lorsque la disposition change de direction.  
  
```  
virtual void OnRTLChanged(BOOL bIsRTL);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `bIsRTL`  
 `TRUE`Si la disposition est de droite à gauche ; `FALSE` si la disposition est de gauche à droite.  
  
### <a name="remarks"></a>Remarques  
  
##  <a name="onshow"></a>CMFCRibbonEdit::OnShow  
 Appelé par l’infrastructure pour afficher ou masquer la [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) contrôle.  
  
```  
virtual void OnShow(BOOL bShow);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `bShow`  
 `TRUE`Pour afficher le contrôle ; `FALSE` pour masquer le contrôle.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="redraw"></a>CMFCRibbonEdit::Redraw  
 Met à jour l’affichage de la [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) contrôle.  
  
```  
virtual void Redraw();
```  
  
### <a name="remarks"></a>Remarques  
 Cette méthode redessine le rectangle d’affichage pour le `CMFCRibbonEdit` objet en appelant indirectement [CWnd::RedrawWindow](http://msdn.microsoft.com/library/windows/desktop/dd162911) avec la `RDW_INVALIDATE`, `RDW_ERASE`, et `RDW_UPDATENOW` indicateurs définis.  
  
##  <a name="setaccdata"></a>CMFCRibbonEdit::SetACCData  
 Définit les données d’accessibilité pour les [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) objet.  
  
```  
virtual BOOL SetACCData(
    CWnd* pParent,  
    CAccessibilityData& data);
```  
  
### <a name="parameters"></a>Paramètres  
 `pParent`  
 Pointeur vers la fenêtre parente de la `CMFCRibbonEdit` objet.  
  
 `data`  
 Les données d’accessibilité pour les `CMFCRibbonEdit` objet.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne toujours `TRUE`.  
  
### <a name="remarks"></a>Notes  
  
##  <a name="setedittext"></a>CMFCRibbonEdit::SetEditText  
 Définit le texte dans la zone de texte.  
  
```  
void SetEditText(CString strText);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `strText`  
 Le texte de la zone de texte.  
  
##  <a name="settextalign"></a>CMFCRibbonEdit::SetTextAlign  
 Définit l’alignement du texte de la zone de texte.  
  
```  
void SetTextAlign(int nAlign);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nAlign`  
 Un alignement de texte de valeur énumérée. Consultez la section Notes pour les valeurs possibles.  
  
### <a name="remarks"></a>Notes  
 Le paramètre `nAlign` est un de la modification suivante des styles de contrôle :  
  
- **ES_LEFT** pour l’alignement à gauche  
  
- **ES_CENTER** pour alignement au centre  
  
- **ES_RIGHT** d’alignement à droite  
  
 Pour plus d’informations sur ces styles, consultez [modifier les Styles de contrôle](http://msdn.microsoft.com/library/windows/desktop/bb775464).  
  
##  <a name="setwidth"></a>CMFCRibbonEdit::SetWidth  
 Définit la largeur de la zone de texte pour le [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) contrôle.  
  
```  
void SetWidth(
    int nWidth,  
    BOOL bInFloatyMode = FALSE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] `nWidth`  
 La largeur, en pixels, de la zone de texte.  
  
 `bInFloatyMode`  
 `TRUE`Pour définir la largeur en mode flottant ; `FALSE` pour définir la largeur pour le mode normal.  
  
### <a name="remarks"></a>Remarques  
 Le `CMFCRibbonEdit` contrôle possède deux largeurs en fonction de son mode d’affichage : flottante mode et le mode normal.  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique de la hiérarchie](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonButton (classe)](../../mfc/reference/cmfcribbonbutton-class.md)   
 [CMFCRibbonBar (classe)](../../mfc/reference/cmfcribbonbar-class.md)
