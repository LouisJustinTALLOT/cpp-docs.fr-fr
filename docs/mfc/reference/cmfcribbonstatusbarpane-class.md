---
title: Cmfcribbonstatusbarpane, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCRibbonStatusBarPane
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::CMFCRibbonStatusBarPane
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::GetAlmostLargeText
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::GetTextAlign
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::IsAnimation
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::IsExtended
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::OnDrawBorder
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::OnFillBackground
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::SetAlmostLargeText
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::SetAnimationList
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::SetTextAlign
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::StartAnimation
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::StopAnimation
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::OnFinishAnimation
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonStatusBarPane [MFC], CMFCRibbonStatusBarPane
- CMFCRibbonStatusBarPane [MFC], GetAlmostLargeText
- CMFCRibbonStatusBarPane [MFC], GetTextAlign
- CMFCRibbonStatusBarPane [MFC], IsAnimation
- CMFCRibbonStatusBarPane [MFC], IsExtended
- CMFCRibbonStatusBarPane [MFC], OnDrawBorder
- CMFCRibbonStatusBarPane [MFC], OnFillBackground
- CMFCRibbonStatusBarPane [MFC], SetAlmostLargeText
- CMFCRibbonStatusBarPane [MFC], SetAnimationList
- CMFCRibbonStatusBarPane [MFC], SetTextAlign
- CMFCRibbonStatusBarPane [MFC], StartAnimation
- CMFCRibbonStatusBarPane [MFC], StopAnimation
- CMFCRibbonStatusBarPane [MFC], OnFinishAnimation
ms.assetid: 5d034c3c-ecca-4267-b88c-0f55a2884dd0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 55ef22eec84b4d7e5e4ea27abe611cf2d18f2a1b
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2018
ms.locfileid: "42540404"
---
# <a name="cmfcribbonstatusbarpane-class"></a>Cmfcribbonstatusbarpane, classe
Le `CMFCRibbonStatusBarPane` classe implémente un élément de ruban que vous pouvez ajouter une ruban barre d’état.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCRibbonStatusBarPane : public CMFCRibbonButton  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCRibbonStatusBarPane::CMFCRibbonStatusBarPane](#cmfcribbonstatusbarpane)|Construit et initialise un objet `CMFCRibbonStatusBarPane`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCRibbonStatusBarPane::GetAlmostLargeText](#getalmostlargetext)|Retourne la chaîne qui définit la chaîne de texte la plus longue qui peut être affichée dans le volet sans troncation.|  
|[CMFCRibbonStatusBarPane::GetTextAlign](#gettextalign)|Retourne la valeur actuelle de l’alignement du texte.|  
|[CMFCRibbonStatusBarPane::IsAnimation](#isanimation)|Détermine si l’animation est en cours d’exécution.|  
|[CMFCRibbonStatusBarPane::IsExtended](#isextended)|Détermine si le volet se trouve dans la zone étendue de la barre d’état du ruban.|  
|[CMFCRibbonStatusBarPane::OnDrawBorder](#ondrawborder)|(Substitue [CMFCRibbonButton::OnDrawBorder](../../mfc/reference/cmfcribbonbutton-class.md#ondrawborder).)|  
|[CMFCRibbonStatusBarPane::OnFillBackground](#onfillbackground)|(Substitue [CMFCRibbonButton::OnFillBackground](../../mfc/reference/cmfcribbonbutton-class.md#onfillbackground).)|  
|[CMFCRibbonStatusBarPane::SetAlmostLargeText](#setalmostlargetext)|Définit la chaîne de texte la plus longue qui peut être affichée dans le volet sans troncation.|  
|[CMFCRibbonStatusBarPane::SetAnimationList](#setanimationlist)|Assigne au volet une liste d’images qui peut être utilisée pour l’animation.|  
|[CMFCRibbonStatusBarPane::SetTextAlign](#settextalign)|Définit l’alignement du texte.|  
|[CMFCRibbonStatusBarPane::StartAnimation](#startanimation)|Démarre l’animation qui est assignée au volet.|  
|[CMFCRibbonStatusBarPane::StopAnimation](#stopanimation)|Arrête l’animation qui est assignée au volet. .|  
  
### <a name="protected-methods"></a>Méthodes protégées  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCRibbonStatusBarPane::OnFinishAnimation](#onfinishanimation)|Appelé par l’infrastructure lorsque l’animation qui est assignée au volet s’arrête.|  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment utiliser les différentes méthodes de la classe `CMFCRibbonStatusBarPane`. L’exemple montre comment construire un `CMFCRibbonStatusBarPane` d’objet, de définir l’alignement du texte de l’étiquette du volet de barre d’état, de définir le texte de la plus longs qui peut être affiché dans le volet de barre d’état sans troncation, attacher vers le volet de barre d’état d’une liste d’images qui peut être utilisée pour un nimations et démarrer l’animation.  
  
 [!code-cpp[NVC_MFC_RibbonApp#2](../../mfc/reference/codesnippet/cpp/cmfcribbonstatusbarpane-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonStatusBarPane](../../mfc/reference/cmfcribbonstatusbarpane-class.md)  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxribbonstatusbarpane.h  
  
##  <a name="cmfcribbonstatusbarpane"></a>  CMFCRibbonStatusBarPane::CMFCRibbonStatusBarPane  
 Construisez un objet de volet dans la barre d’état.  
  
```  
CMFCRibbonStatusBarPane(
    UINT nCmdID,  
    LPCTSTR lpszText,  
    BOOL bIsStatic=FALSE,  
    HICON hIcon=NULL,  
    LPCTSTR lpszAlmostLargeText=NULL);

CMFCRibbonStatusBarPane(
    UINT nCmdID,  
    LPCTSTR lpszText,  
    HBITMAP hBmpAnimationList,  
    int cxAnimation=16,  
    COLORREF clrTrnsp=RGB(192,192 1,192) 1,  
    HICON hIcon=NULL,  
    BOOL bIsStatic=FALSE);

CMFCRibbonStatusBarPane(
    UINT nCmdID,  
    LPCTSTR lpszText,  
    UINT uiAnimationListResID,  
    int cxAnimation=16,  
    COLORREF clrTrnsp=RGB(192, 192 1, 192) 1,  
    HICON hIcon=NULL,  
    BOOL bIsStatic=FALSE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *nCmdID*  
 Spécifie l’ID de commande du volet.  
  
 [in] *lpszText*  
 Spécifie la chaîne de texte à afficher sur le volet.  
  
 [in] *bIsStatic*  
 Si la valeur est TRUE, le volet d’état ne peut pas être mis en surbrillance ou sélectionné en cliquant dessus.  
  
 [in] *hIcon*  
 Spécifie un handle d’une icône à afficher dans le volet.  
  
 [in] *lpszAlmostLargeText*  
 Spécifie la chaîne de texte la plus longue qui peut être affichée par le volet.  
  
 [in] *hBmpAnimationList*  
 Spécifie un handle vers une liste d’images qui est utilisé pour l’animation.  
  
 [in] *cxAnimation*  
 Spécifie la largeur, en pixels, de l’icône dans la liste d’images qui est utilisée pour l’animation.  
  
 [in] *clrTrnsp*  
 Spécifie la couleur transparente d’images dans la liste d’images qui sont utilisées pour l’animation.  
  
 [in] *uiAnimationListResID*  
 Spécifie un ID de ressource d’une liste d’images qui est utilisé pour l’animation.  
  
##  <a name="getalmostlargetext"></a>  CMFCRibbonStatusBarPane::GetAlmostLargeText  
 Obtient la chaîne de texte la plus longue que le volet de barre d’état peut afficher.  
  
```  
LPCTSTR GetAlmostLargeText() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 La chaîne de texte la plus longue que le volet de barre d’état peut afficher.  
  
##  <a name="gettextalign"></a>  CMFCRibbonStatusBarPane::GetTextAlign  
 Obtient le paramètre actuel de l’alignement du texte de l’étiquette du volet de barre d’état.  
  
```  
int GetTextAlign() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 L’alignement du texte actuel qui peut prendre l’une des opérations suivantes :  
  
-   TA_LEFT  
  
-   TA_CENTER  
  
-   TA_RIGHT.  
  
##  <a name="isanimation"></a>  CMFCRibbonStatusBarPane::IsAnimation  
 Détermine si l’animation est en cours d’exécution.  
  
```  
BOOL IsAnimation() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si l’animation est en cours ; FALSE sinon.  
  
##  <a name="isextended"></a>  CMFCRibbonStatusBarPane::IsExtended  
 Déterminer si le volet se trouve dans la zone étendue de la barre d’état du ruban.  
  
```  
BOOL IsExtended() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si le volet se trouve sur la zone étendue de la barre d’état. FALSE sinon.  
  
##  <a name="ondrawborder"></a>  CMFCRibbonStatusBarPane::OnDrawBorder  
 Pour plus d’informations, consultez le code source situé dans le **VC\\atlmfc\\src\\mfc** dossier de votre installation de Visual Studio.  
  
```  
virtual void OnDrawBorder(CDC*);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *Capture de données modifiées**  
  
### <a name="remarks"></a>Notes  
  
##  <a name="onfillbackground"></a>  CMFCRibbonStatusBarPane::OnFillBackground  
 Pour plus d’informations, consultez le code source situé dans le **VC\\atlmfc\\src\\mfc** dossier de votre installation de Visual Studio.  
  
```  
virtual COLORREF OnFillBackground(CDC* pDC);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *pDC*  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="onfinishanimation"></a>  CMFCRibbonStatusBarPane::OnFinishAnimation  
 Infrastructure appelle cette méthode lorsque l’animation qui est assignée au volet se termine.  
  
```  
virtual void OnFinishAnimation();
```  
  
### <a name="remarks"></a>Notes  
 `StopAnimation` appels de méthode le `OnFinishAnimation` (méthode), que vous pouvez utiliser pour nettoyer les données lorsque l’animation se termine.  
  
##  <a name="setalmostlargetext"></a>  CMFCRibbonStatusBarPane::SetAlmostLargeText  
 Définir le texte de la plus longs qui peut être affiché dans le volet de barre d’état sans troncation.  
  
```  
void SetAlmostLargeText(LPCTSTR lpszAlmostLargeText);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *lpszAlmostLargeText*  
 Spécifie la chaîne la plus longue qui peut être affichée dans le volet de barre d’état sans troncation.  
  
### <a name="remarks"></a>Notes  
 La bibliothèque calcule la taille du texte qui *lpszAlmostLargeText* spécifie et redimensionne le volet en conséquence. Le texte est tronqué si elle toujours ne tient pas dans le volet.  
  
##  <a name="setanimationlist"></a>  CMFCRibbonStatusBarPane::SetAnimationList  
 Attache une liste d’images qui peut être utilisée pour l’animation dans le volet de barre d’état.  
  
```  
void SetAnimationList(
    HBITMAP hBmpAnimationList,  
    int cxAnimation=16,  
    COLORREF clrTransp=RGB(192, 192 1, 192) 1);

BOOL SetAnimationList(
    UINT uiAnimationListResID,  
    int cxAnimation=16,  
    COLORREF clrTransp=RGB(192, 192 1, 192) 1);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *hBmpAnimationList*  
 Spécifie un handle vers une liste d’images.  
  
 [in] *cxAnimation*  
 Spécifie la largeur, en pixels, de l’image dans la liste d’images.  
  
 [in] *clrTransp*  
 Spécifie la couleur transparente de la liste d’images.  
  
 [in] *uiAnimationListResID*  
 Spécifie l’ID de ressource de la liste d’images.  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si la liste d’images est attachée avec succès vers le volet de barre d’état ; FALSE sinon.  
  
##  <a name="settextalign"></a>  CMFCRibbonStatusBarPane::SetTextAlign  
 Définit l’alignement du texte de l’étiquette du volet de barre d’état.  
  
```  
void SetTextAlign(int nAlign);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *nAlign*  
 Spécifie l’alignement du texte.  
  
### <a name="remarks"></a>Notes  
 *nAlign* peut avoir l’une des valeurs suivantes :  
  
- TA_LEFT : alignement à gauche  
  
- TA_CENTER : alignement au centre  
  
- TA_RIGHT : alignement à droite  
  
##  <a name="startanimation"></a>  CMFCRibbonStatusBarPane::StartAnimation  
 Démarre l’animation que vous attribuez au volet.  
  
```  
void StartAnimation(
    UINT nFrameDelay=500,  
    UINT nDuration=-1);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *nFrameDelay*  
 Spécifie la fréquence d’images de l’animation, en millisecondes.  
  
 [in] *nDuration*  
 Spécifie la durée pendant laquelle pour lire l’animation, en millisecondes. Utilisez -1 pour une boucle infinie.  
  
### <a name="remarks"></a>Notes  
 Vous devez spécifier un handle vers une liste d’images avant d’appeler `StartAnimation` à l’aide de `SetAnimationList`.  
  
##  <a name="stopanimation"></a>  CMFCRibbonStatusBarPane::StopAnimation  
 Arrête l’animation que vous avez affecté dans le volet de barre d’état.  
  
```  
void StopAnimation();
```  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [Cmfcribbonbutton, classe](../../mfc/reference/cmfcribbonbutton-class.md)   
 [CMFCRibbonStatusBar, classe](../../mfc/reference/cmfcribbonstatusbar-class.md)
