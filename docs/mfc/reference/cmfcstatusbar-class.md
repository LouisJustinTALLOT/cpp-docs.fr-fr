---
title: Cmfcstatusbar, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCStatusBar
- AFXSTATUSBAR/CMFCStatusBar
- AFXSTATUSBAR/CMFCStatusBar::CalcFixedLayout
- AFXSTATUSBAR/CMFCStatusBar::CommandToIndex
- AFXSTATUSBAR/CMFCStatusBar::Create
- AFXSTATUSBAR/CMFCStatusBar::CreateEx
- AFXSTATUSBAR/CMFCStatusBar::DoesAllowDynInsertBefore
- AFXSTATUSBAR/CMFCStatusBar::EnablePaneDoubleClick
- AFXSTATUSBAR/CMFCStatusBar::EnablePaneProgressBar
- AFXSTATUSBAR/CMFCStatusBar::GetCount
- AFXSTATUSBAR/CMFCStatusBar::GetDrawExtendedArea
- AFXSTATUSBAR/CMFCStatusBar::GetExtendedArea
- AFXSTATUSBAR/CMFCStatusBar::GetItemID
- AFXSTATUSBAR/CMFCStatusBar::GetItemRect
- AFXSTATUSBAR/CMFCStatusBar::GetPaneInfo
- AFXSTATUSBAR/CMFCStatusBar::GetPaneProgress
- AFXSTATUSBAR/CMFCStatusBar::GetPaneStyle
- AFXSTATUSBAR/CMFCStatusBar::GetPaneText
- AFXSTATUSBAR/CMFCStatusBar::GetPaneWidth
- AFXSTATUSBAR/CMFCStatusBar::GetTipText
- AFXSTATUSBAR/CMFCStatusBar::InvalidatePaneContent
- AFXSTATUSBAR/CMFCStatusBar::PreCreateWindow
- AFXSTATUSBAR/CMFCStatusBar::SetDrawExtendedArea
- AFXSTATUSBAR/CMFCStatusBar::SetIndicators
- AFXSTATUSBAR/CMFCStatusBar::SetPaneAnimation
- AFXSTATUSBAR/CMFCStatusBar::SetPaneBackgroundColor
- AFXSTATUSBAR/CMFCStatusBar::SetPaneIcon
- AFXSTATUSBAR/CMFCStatusBar::SetPaneInfo
- AFXSTATUSBAR/CMFCStatusBar::SetPaneProgress
- AFXSTATUSBAR/CMFCStatusBar::SetPaneStyle
- AFXSTATUSBAR/CMFCStatusBar::SetPaneText
- AFXSTATUSBAR/CMFCStatusBar::SetPaneTextColor
- AFXSTATUSBAR/CMFCStatusBar::SetPaneWidth
- AFXSTATUSBAR/CMFCStatusBar::SetTipText
- AFXSTATUSBAR/CMFCStatusBar::OnDrawPane
dev_langs:
- C++
helpviewer_keywords:
- CMFCStatusBar [MFC], CalcFixedLayout
- CMFCStatusBar [MFC], CommandToIndex
- CMFCStatusBar [MFC], Create
- CMFCStatusBar [MFC], CreateEx
- CMFCStatusBar [MFC], DoesAllowDynInsertBefore
- CMFCStatusBar [MFC], EnablePaneDoubleClick
- CMFCStatusBar [MFC], EnablePaneProgressBar
- CMFCStatusBar [MFC], GetCount
- CMFCStatusBar [MFC], GetDrawExtendedArea
- CMFCStatusBar [MFC], GetExtendedArea
- CMFCStatusBar [MFC], GetItemID
- CMFCStatusBar [MFC], GetItemRect
- CMFCStatusBar [MFC], GetPaneInfo
- CMFCStatusBar [MFC], GetPaneProgress
- CMFCStatusBar [MFC], GetPaneStyle
- CMFCStatusBar [MFC], GetPaneText
- CMFCStatusBar [MFC], GetPaneWidth
- CMFCStatusBar [MFC], GetTipText
- CMFCStatusBar [MFC], InvalidatePaneContent
- CMFCStatusBar [MFC], PreCreateWindow
- CMFCStatusBar [MFC], SetDrawExtendedArea
- CMFCStatusBar [MFC], SetIndicators
- CMFCStatusBar [MFC], SetPaneAnimation
- CMFCStatusBar [MFC], SetPaneBackgroundColor
- CMFCStatusBar [MFC], SetPaneIcon
- CMFCStatusBar [MFC], SetPaneInfo
- CMFCStatusBar [MFC], SetPaneProgress
- CMFCStatusBar [MFC], SetPaneStyle
- CMFCStatusBar [MFC], SetPaneText
- CMFCStatusBar [MFC], SetPaneTextColor
- CMFCStatusBar [MFC], SetPaneWidth
- CMFCStatusBar [MFC], SetTipText
- CMFCStatusBar [MFC], OnDrawPane
ms.assetid: f2960d1d-f4ed-41e8-bd99-0382b2f8d88e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7150789756273f9d70b3dd6e156c63d0649d0957
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45708185"
---
# <a name="cmfcstatusbar-class"></a>Cmfcstatusbar, classe
Le `CMFCStatusBar` classe implémente une barre d’état semblable à la `CStatusBar` classe. Toutefois, la classe `CMFCStatusBar` a des fonctionnalités que n'offre pas la classe `CStatusBar` , telles que la capacité à afficher des images, des animations et des barres de progression et la possibilité de répondre aux doubles-clics de souris. 

 Pour plus d’informations, consultez le code source situé dans le **VC\\atlmfc\\src\\mfc** dossier de votre installation de Visual Studio.   
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCStatusBar : public CPane  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCStatusBar::CalcFixedLayout](#calcfixedlayout)|(Substitue [CBasePane::CalcFixedLayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout).)|  
|[CMFCStatusBar::CommandToIndex](#commandtoindex)||  
|[CMFCStatusBar::Create](#create)|Crée une barre de contrôle et l’attache à la [CPane](../../mfc/reference/cpane-class.md) objet. (Substitue [CPane::Create](../../mfc/reference/cpane-class.md#create).)|  
|[CMFCStatusBar::CreateEx](#createex)|Crée une barre de contrôle et l’attache à la [CPane](../../mfc/reference/cpane-class.md) objet. (Substitue [CPane::CreateEx](../../mfc/reference/cpane-class.md#createex).)|  
|[CMFCStatusBar::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|Détermine si un autre volet peut être inséré dynamiquement entre ce volet et le frame parent. (Substitue [CBasePane::DoesAllowDynInsertBefore](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore).)|  
|[CMFCStatusBar::EnablePaneDoubleClick](#enablepanedoubleclick)|Active ou désactive la gestion de la souris double-clique sur la barre d’état.|  
|[CMFCStatusBar::EnablePaneProgressBar](#enablepaneprogressbar)|Affiche une barre de progression dans le volet spécifié.|  
|[CMFCStatusBar::GetCount](#getcount)|Retourne le nombre de volets dans la barre d’état.|  
|[CMFCStatusBar::GetDrawExtendedArea](#getdrawextendedarea)||  
|[CMFCStatusBar::GetExtendedArea](#getextendedarea)||  
|[CMFCStatusBar::GetItemID](#getitemid)||  
|[CMFCStatusBar::GetItemRect](#getitemrect)||  
|[CMFCStatusBar::GetPaneInfo](#getpaneinfo)||  
|[CMFCStatusBar::GetPaneProgress](#getpaneprogress)||  
|[CMFCStatusBar::GetPaneStyle](#getpanestyle)|Retourne le style du volet. (Substitue [CBasePane::GetPaneStyle](../../mfc/reference/cbasepane-class.md#getpanestyle).)|  
|[CMFCStatusBar::GetPaneText](#getpanetext)||  
|[CMFCStatusBar::GetPaneWidth](#getpanewidth)|Retourne la largeur, en pixels, du volet de la barre d’état spécifié.|  
|[CMFCStatusBar::GetTipText](#gettiptext)|Retourne le texte info-bulle pour le volet de la barre d’état spécifié.|  
|[CMFCStatusBar::InvalidatePaneContent](#invalidatepanecontent)|Invalide le volet spécifié, puis le redessine son contenu.|  
|[CMFCStatusBar::PreCreateWindow](#precreatewindow)|Appelé par l’infrastructure avant la création de la fenêtre Windows attachée à cet `CWnd` objet. (Substitue [CWnd::PreCreateWindow](../../mfc/reference/cwnd-class.md#precreatewindow).)|  
|[CMFCStatusBar::SetDrawExtendedArea](#setdrawextendedarea)||  
|[CMFCStatusBar::SetIndicators](#setindicators)||  
|[CMFCStatusBar::SetPaneAnimation](#setpaneanimation)|Assigne une animation vers le volet spécifié.|  
|[CMFCStatusBar::SetPaneBackgroundColor](#setpanebackgroundcolor)|Définit la couleur d’arrière-plan du volet de la barre d’état spécifié.|  
|[CMFCStatusBar::SetPaneIcon](#setpaneicon)|Définit l’icône d’indicateur pour le volet de la barre d’état spécifié.|  
|[CMFCStatusBar::SetPaneInfo](#setpaneinfo)||  
|[CMFCStatusBar::SetPaneProgress](#setpaneprogress)|Définit la progression actuelle de la barre de progression pour le volet de la barre d’état spécifié.|  
|[CMFCStatusBar::SetPaneStyle](#setpanestyle)|Définit le style du volet. (Substitue [CBasePane::SetPaneStyle](../../mfc/reference/cbasepane-class.md#setpanestyle).)|  
|[CMFCStatusBar::SetPaneText](#setpanetext)||  
|[CMFCStatusBar::SetPaneTextColor](#setpanetextcolor)|Définit la couleur du texte du volet de la barre d’état spécifié.|  
|[CMFCStatusBar::SetPaneWidth](#setpanewidth)|Définit la largeur en pixels du volet de la barre d’état spécifié.|  
|[CMFCStatusBar::SetTipText](#settiptext)|Définit le texte info-bulle pour le volet de la barre d’état spécifié.|  
  
### <a name="protected-methods"></a>Méthodes protégées  
  
|Nom|Description|  
|----------|-----------------|  
|[CMFCStatusBar::OnDrawPane](#ondrawpane)|Appelé par l’infrastructure quand il redessine le volet de la barre d’état.|  
  
## <a name="remarks"></a>Notes  
 Le diagramme suivant illustre une figure de la barre d’état à partir de [exemple de démonstration de barre d’état](../../visual-cpp-samples.md) application.  
  
 ![Exemple de CMFCStatusBar](../../mfc/reference/media/cmfcstatusbar.png "cmfcstatusbar")  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre les variables locales que l’application utilise pour appeler les différentes méthodes la `CMFCStatusBar` classe. Ces variables sont déclarées dans StatusBarDemoView.h. Frame principal est déclaré dans MainFrm.h, le document est déclaré dans StatusBarDemoDoc.h, et la vue est déclarée dans StatusBarDemoView.h. Cet extrait de code fait partie de la [exemple de démonstration de barre d’état](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_StatusBarDemo#9](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_1.h)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment obtenir une référence à `CMFCStatusBar` objet en introduisant le `GetStatusBar` méthode dans MainFrm.h, puis en appelant cette méthode à partir de la `GetStatusBar` dans StatusBarDemoView.h (méthode). Cet extrait de code fait partie de la [exemple de démonstration de barre d’état](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_StatusBarDemo#7](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_2.h)]  
[!code-cpp[NVC_MFC_StatusBarDemo#8](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_3.h)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment appeler les différentes méthodes la `CMFCStatusBar` classe dans StatusBarDemoView.cpp. Les constantes sont déclarées dans MainFrm.h. L’exemple montre comment définir l’icône de définir le texte d’info-bulle du volet de barre d’état, afficher une barre de progression dans le volet spécifié, affecter une animation vers le volet spécifié, définir le texte et la largeur du volet de barre d’état et définir l’indicateur de progression actuelle du progr. barre ESS pour le volet de barre d’état. Cet extrait de code fait partie de la [exemple de démonstration de barre d’état](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_StatusBarDemo#6](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_4.h)]  
[!code-cpp[NVC_MFC_StatusBarDemo#1](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_5.cpp)]  
[!code-cpp[NVC_MFC_StatusBarDemo#2](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_6.cpp)]  
[!code-cpp[NVC_MFC_StatusBarDemo#3](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_7.cpp)]  
[!code-cpp[NVC_MFC_StatusBarDemo#4](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_8.cpp)]  
[!code-cpp[NVC_MFC_StatusBarDemo#5](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_9.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCStatusBar](../../mfc/reference/cmfcstatusbar-class.md)  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxstatusbar.h  
  
##  <a name="calcfixedlayout"></a>  CMFCStatusBar::CalcFixedLayout  

  
```  
virtual CSize CalcFixedLayout(
    BOOL bStretch,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>Paramètres  
*bStretch*<br/>
[in] [in] *bHorz*  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="commandtoindex"></a>  CMFCStatusBar::CommandToIndex  

  
```  
int CommandToIndex(UINT nIDFind) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *nIDFind*  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="create"></a>  CMFCStatusBar::Create  

  
```  
BOOL Create(
    CWnd* pParentWnd,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,  
    UINT nID = AFX_IDW_STATUS_BAR);
```  
  
### <a name="parameters"></a>Paramètres  
*pParentWnd*<br/>
[in] [in] *dwStyle*  
 [in] *nID*  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="createex"></a>  CMFCStatusBar::CreateEx  

  
```  
BOOL CreateEx(
    CWnd* pParentWnd,  
    DWORD dwCtrlStyle = 0,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,  
    UINT nID = AFX_IDW_STATUS_BAR);
```  
  
### <a name="parameters"></a>Paramètres  
*pParentWnd*<br/>
[in] [in] *dwCtrlStyle*  
*dwStyle*<br/>
[in] [in] *nID*  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="doesallowdyninsertbefore"></a>  CMFCStatusBar::DoesAllowDynInsertBefore  

  
```  
virtual BOOL DoesAllowDynInsertBefore() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="enablepanedoubleclick"></a>  CMFCStatusBar::EnablePaneDoubleClick  
 Active ou désactive la gestion de la souris double-clique sur la barre d’état.  
  
```  
void EnablePaneDoubleClick(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
*bActivez*<br/>
[in] Si la valeur est TRUE, activer le traitement du double-clic de souris. Dans le cas contraire désactiver le traitement du double-clic de souris.  
  
### <a name="remarks"></a>Notes  
 Si la barre d’état est activée pour traiter des double-clics, Windows envoie la notification WM_COMMAND avec un ID de ressource au propriétaire de l’état de la barre chaque fois que l’utilisateur double-clique sur le volet de barre d’état.  
  
##  <a name="enablepaneprogressbar"></a>  CMFCStatusBar::EnablePaneProgressBar  
 Afficher une barre de progression dans le volet spécifié.  
  
```  
void EnablePaneProgressBar(
    int nIndex,  
    long nTotal=100,  
    BOOL bDisplayText=FALSE,  
    COLORREF clrBar=-1,  
    COLORREF clrBarDest=-1,  
    COLORREF clrProgressText=-1);
```  
  
### <a name="parameters"></a>Paramètres  
*nIndex*<br/>
[in] Spécifie l’index du volet dont barre de progression à activer.  
  
*nLa*<br/>
[in] Spécifie la valeur maximale de la barre de progression.  
  
*bDisplayText*<br/>
[in] Spécifie si la barre de progression doit afficher la valeur de progression actuel.  
  
*clrBar*<br/>
[in] Spécifie la couleur d’arrière-plan de la barre de progression.  
  
*clrBarDest*<br/>
[in] Spécifie la couleur secondaire de l’arrière-plan de barre de progression. Utilisez une valeur autre que *clrBar* à remplir par une couleur fusionnée dans un dégradé.  
  
*clrProgressText*<br/>
[in] Spécifie la couleur du texte de la barre de progression.  
  
### <a name="remarks"></a>Notes  
 Si vous souhaitez désactiver l’appel de barre de progression `EnablePaneProgressBar` avec *NLA* définie sur -1. Par défaut *NLA* est défini à 100. Par conséquent, il est inutile des calculs supplémentaires pour afficher la progression en pourcentage.  
  
 Vous devez passer des valeurs différentes *clrBar* et *clrBarDest* afin que la couleur d’arrière-plan de la barre de progression affiche une couleur fusionnée dans un dégradé. .  
  
 Pour définir l’état d’avancement, appelez le [CMFCStatusBar::SetPaneProgress](#setpaneprogress) (méthode).  
  
##  <a name="getcount"></a>  CMFCStatusBar::GetCount  
 Récupère le nombre de volets dans la barre d’état.  
  
```  
int GetCount() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre de volets dans la barre d’état.  
  
##  <a name="getdrawextendedarea"></a>  CMFCStatusBar::GetDrawExtendedArea  

  
```  
BOOL GetDrawExtendedArea() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getextendedarea"></a>  CMFCStatusBar::GetExtendedArea  

  
```  
virtual BOOL GetExtendedArea(CRect& rect) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *rect*  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getitemid"></a>  CMFCStatusBar::GetItemID  

  
```  
UINT GetItemID(int nIndex) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *nIndex*  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getitemrect"></a>  CMFCStatusBar::GetItemRect  

  
```  
void GetItemRect(
    int nIndex,  
    LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>Paramètres  
*nIndex*<br/>
[in] [in] *lpRect*  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getpaneinfo"></a>  CMFCStatusBar::GetPaneInfo  

  
```  
void GetPaneInfo(
    int nIndex,  
    UINT& nID,  
    UINT& nStyle,  
    int& cxWidth) const;  
```  
  
### <a name="parameters"></a>Paramètres  
*nIndex*<br/>
[in] [in] *nID*  
*nStyle*<br/>
[in] [in] *cxWidth*  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getpaneprogress"></a>  CMFCStatusBar::GetPaneProgress  

  
```  
long GetPaneProgress(int nIndex) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *nIndex*  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getpanestyle"></a>  CMFCStatusBar::GetPaneStyle  

  
```  
UINT GetPaneStyle(int nIndex) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *nIndex*  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getpanetext"></a>  CMFCStatusBar::GetPaneText  

  
```  
void GetPaneText(
    int nIndex,  
    CString& s) const;  
  
CString GetPaneText(int nIndex) const;  
```  
  
### <a name="parameters"></a>Paramètres  
*nIndex*<br/>
[in] [in] *s*  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="getpanewidth"></a>  CMFCStatusBar::GetPaneWidth  
 Récupère la largeur du volet d’une barre d’état.  
  
```  
int GetPaneWidth(int nIndex) const;  
```  
  
### <a name="parameters"></a>Paramètres  
*nIndex*<br/>
[in] Spécifie l’index du volet de barre d’état.  
  
### <a name="return-value"></a>Valeur de retour  
 La largeur du volet de barre d’état qui *nIndex* spécifie ; sinon, zéro si un volet de barre d’état n’existe pas.  
  
##  <a name="gettiptext"></a>  CMFCStatusBar::GetTipText  
 Récupérer le texte d’info-bulle du volet d’une barre état.  
  
```  
CString GetTipText(int nIndex) const;  
```  
  
### <a name="parameters"></a>Paramètres  
*nIndex*<br/>
[in] Spécifie l’index du volet pour lequel récupérer le texte info-bulle.  
  
### <a name="return-value"></a>Valeur de retour  
 Le texte d’info-bulle du volet barre d’état qui *nIndex* spécifie. Sinon, la chaîne vide si un volet de barre d’état n’existe pas pour le texte spécifié *nIndex* ou si son texte d’info-bulle est vide.  
  
##  <a name="invalidatepanecontent"></a>  CMFCStatusBar::InvalidatePaneContent  
 Invalider le volet de barre d’état et redessiner son contenu.  
  
```  
void InvalidatePaneContent(int nIndex);
```  
  
### <a name="parameters"></a>Paramètres  
*nIndex*<br/>
[in] Spécifie l’index du volet dont le contenu doit être invalidé et redessiné.  
  
### <a name="remarks"></a>Notes  
 Lors de la barre d’état est invalidée, il est marqué pour être redessiné. Windows redessine lorsque le `UpdateWindow` méthode envoie un message WM_PAINT à la `OnPaint` (méthode).  
  
##  <a name="ondrawpane"></a>  CMFCStatusBar::OnDrawPane  
 Redessiner le volet de la barre d’état.  
  
```  
virtual void OnDrawPane(
    CDC* pDC,  
    CMFCStatusBarPaneInfo* pPane);
```  
  
### <a name="parameters"></a>Paramètres  
*contrôleur de domaine principal*<br/>
[in] Pointeur vers un contexte de périphérique pour le dessin.  
  
*pPane*<br/>
[in] Un pointeur vers un `CMFCStatusBarPaneInfo` structure qui contient des informations sur le volet à être redessiné.  
  
### <a name="remarks"></a>Notes  
 Par défaut, `OnDrawPane` redessine le volet à l’aide du contexte de périphérique *pDC* en fonction de style et le contenu du volet.  
  
 Substituez cette méthode dans un `CMFCStatusBar`-classe pour personnaliser l’apparence d’un volet dérivée.  
  
##  <a name="precreatewindow"></a>  CMFCStatusBar::PreCreateWindow  

  
```  
virtual BOOL PreCreateWindow(CREATESTRUCT& cs);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *cs*  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="setdrawextendedarea"></a>  CMFCStatusBar::SetDrawExtendedArea  

  
```  
void SetDrawExtendedArea(BOOL bSet = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 [in] *bSet*  
  
### <a name="remarks"></a>Notes  
  
##  <a name="setindicators"></a>  CMFCStatusBar::SetIndicators  

  
```  
BOOL SetIndicators(
    const UINT* lpIDArray,  
    int nIDCount);
```  
  
### <a name="parameters"></a>Paramètres  
*lpIDArray*<br/>
[in] [in] *nIDCount*  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="setpaneanimation"></a>  CMFCStatusBar::SetPaneAnimation  
 Assigne une animation vers le volet spécifié.  
  
```  
void SetPaneAnimation(
    int nIndex,  
    HIMAGELIST hImageList,  
    UINT nFrameRate=500,  
    BOOL bUpdate=TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
*nIndex*<br/>
[in] Spécifie l’index du volet auquel vous souhaitez lui affecter une animation.  
  
*hImageList*<br/>
[in] Spécifie un handle vers la liste d’images contenant les images d’animation.  
  
*nFrameRate*<br/>
[in] Spécifie la fréquence d’images, en millisecondes, pour l’animation.  
  
*bUpdate*<br/>
[in] Si la valeur est TRUE, à jour le volet de contenu. Sinon, le volet de contenu est mis à jour lorsqu’elle est invalidée.  
  
### <a name="remarks"></a>Notes  
 Si vous souhaitez désactiver l’animation actuelle, appelez `SetPaneAnimation` avec `hImageList` la valeur NULL.  
  
##  <a name="setpanebackgroundcolor"></a>  CMFCStatusBar::SetPaneBackgroundColor  
 Définit la couleur d’arrière-plan du volet de barre d’état.  
  
```  
void SetPaneBackgroundColor(
    int nIndex,  
    COLORREF clrBackground=(COLORREF)-1,  
    BOOL bUpdate=TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
*nIndex*<br/>
[in] Spécifie l’index du volet pour lequel définir une couleur d’arrière-plan.  
  
*clrBackground*<br/>
[in] Spécifie la nouvelle couleur d’arrière-plan.  
  
*bUpdate*<br/>
[in] Si la valeur est TRUE, à jour le volet de contenu. Dans le cas contraire, ne modifiez pas le volet de contenu jusqu'à ce que le volet est invalidé par une autre méthode.  
  
##  <a name="setpaneicon"></a>  CMFCStatusBar::SetPaneIcon  
 Définir l’icône du volet de barre d’état.  
  
```  
void SetPaneIcon(
    int nIndex,  
    HICON hIcon,  
    BOOL bUpdate=TRUE);

 
void SetPaneIcon(
    int nIndex,  
    HBITMAP hBmp,  
    COLORREF clrTransparent=RGB(255, 0, 255),  
    BOOL bUpdate=TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
*nIndex*<br/>
[in] Spécifie l’index du volet pour lequel définir l’image.  
  
*hIcon*<br/>
[in] Spécifie un handle de l’icône à définir en tant que l’image du volet.  
  
*bUpdate*<br/>
[in] Spécifie s’il faut mettre à jour le volet de contenu immédiatement.  
  
*hBmp*<br/>
[in] Spécifie un handle vers la bitmap à définir en tant que l’image du volet.  
  
*clrTransparent*<br/>
[in] Spécifie la couleur transparente de l’image bitmap qui le *hBmp* indique.  
  
### <a name="remarks"></a>Notes  
 Vous pouvez passer HICON ou HBITMAP avec la couleur transparente pour définir image du volet. Si vous ne souhaitez pas afficher l’image de plus, passez la valeur NULL en tant que handle de l’image.  
  
 S’il existe une animation en cours d’exécution qui [CMFCStatusBar::SetPaneAnimation](#setpaneanimation) a la valeur, l’animation va être arrêtée.  
  
##  <a name="setpaneinfo"></a>  CMFCStatusBar::SetPaneInfo  

  
```  
void SetPaneInfo(
    int nIndex,  
    UINT nID,  
    UINT nStyle,  
    int cxWidth);
```  
  
### <a name="parameters"></a>Paramètres  
*nIndex*<br/>
[in] [in] *nID*  
*nStyle*<br/>
[in] [in] *cxWidth*  
  
### <a name="remarks"></a>Notes  
  
##  <a name="setpaneprogress"></a>  CMFCStatusBar::SetPaneProgress  
 Définissez l’indicateur de progression actuelle de la barre de progression pour le volet spécifié.  
  
```  
void SetPaneProgress(
    int nIndex,  
    long nCurr,  
    BOOL bUpdate=TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
*nIndex*<br/>
[in] Spécifie l’index du volet pour laquelle mettre à jour l’indicateur de progression.  
  
*nCurr*<br/>
[in] Spécifie la valeur actuelle de l’indicateur de progression.  
  
*bUpdate*<br/>
[in] Spécifie si le volet doit être mis à jour immédiatement.  
  
### <a name="remarks"></a>Notes  
 Appelez cette méthode lorsque vous souhaitez mettre à jour de l’indicateur de progression de la barre de progression dans le volet spécifié.  
  
 Pour utiliser cette fonction pour le volet donné, vous devez appeler [CMFCStatusBar::EnablePaneProgressBar](#enablepaneprogressbar) premier.  
  
##  <a name="setpanestyle"></a>  CMFCStatusBar::SetPaneStyle  

  
```  
void SetPaneStyle(
    int nIndex,  
    UINT nStyle);
```  
  
### <a name="parameters"></a>Paramètres  
*nIndex*<br/>
[in] [in] *nStyle*  
  
### <a name="remarks"></a>Notes  
  
##  <a name="setpanetext"></a>  CMFCStatusBar::SetPaneText  

  
```  
virtual BOOL SetPaneText(
    int nIndex,  
    LPCTSTR lpszNewText,  
    BOOL bUpdate = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
*nIndex*<br/>
[in] [in] *lpszNewText*  
 [in] *bUpdate*  
  
### <a name="return-value"></a>Valeur de retour  
  
### <a name="remarks"></a>Notes  
  
##  <a name="setpanetextcolor"></a>  CMFCStatusBar::SetPaneTextColor  
 Définit la couleur du texte du volet spécifié.  
  
```  
void SetPaneTextColor(
    int nIndex,  
    COLORREF clrText=(COLORREF)-1,  
    BOOL bUpdate=TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
*nIndex*<br/>
[in] Spécifie l’index du volet auquel vous souhaitez affecter une nouvelle couleur de texte.  
  
*clrText*<br/>
[in] Spécifie la couleur du texte.  
  
*bUpdate*<br/>
[in] Si la valeur est TRUE, à jour le volet de contenu. Dans le cas contraire, ne modifiez pas le volet de contenu jusqu'à ce que le volet est invalidé par une autre méthode.  
  
##  <a name="setpanewidth"></a>  CMFCStatusBar::SetPaneWidth  
 Définissez la largeur du volet de barre d’état.  
  
```  
void SetPaneWidth(
    int nIndex,  
    int cx);
```  
  
### <a name="parameters"></a>Paramètres  
*nIndex*<br/>
[in] L’index du volet de barre d’état pour lequel définir une nouvelle largeur.  
  
*CX*<br/>
[in] La nouvelle largeur du volet de barre d’état, en pixels.  
  
##  <a name="settiptext"></a>  CMFCStatusBar::SetTipText  
 Définir le texte d’info-bulle d’un volet de barre d’état.  
  
```  
void SetTipText(
    int nIndex,  
    LPCTSTR pszTipText);
```  
  
### <a name="parameters"></a>Paramètres  
*nIndex*<br/>
[in] L’index du volet auquel vous souhaitez affecter le texte d’info-bulle.  
  
*pszTipText*<br/>
[in] Le nouveau texte info-bulle.  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [CPANE, classe](../../mfc/reference/cpane-class.md)   
 [CStatusBar, classe](../../mfc/reference/cstatusbar-class.md)
