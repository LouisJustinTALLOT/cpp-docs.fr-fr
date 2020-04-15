---
title: CMFCStatusBar, classe
ms.date: 11/19/2018
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
ms.openlocfilehash: 8f262d0139b6dffe54e16748ffda4938ba43fc08
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366054"
---
# <a name="cmfcstatusbar-class"></a>CMFCStatusBar, classe

La `CMFCStatusBar` classe met en œuvre une barre de statut similaire à la `CStatusBar` classe. Toutefois, la classe `CMFCStatusBar` a des fonctionnalités que n'offre pas la classe `CStatusBar` , telles que la capacité à afficher des images, des animations et des barres de progression et la possibilité de répondre aux doubles-clics de souris.

Pour plus de détails, consultez le code source situé dans le dossier **VC\\\\atlmfc src\\mfc** de votre installation Visual Studio.

## <a name="syntax"></a>Syntaxe

```
class CMFCStatusBar : public CPane
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCStatusBar::CalcFixedLayout](#calcfixedlayout)|(Overrides [CBasePane::CalcFixedLayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout).)|
|[CMFCStatusBar::CommandToIndex](#commandtoindex)||
|[CMFCStatusBar::Créer](#create)|Crée une barre de commande et la fixe à l’objet [CPane.](../../mfc/reference/cpane-class.md) (Overrides [CPane::Créer](../../mfc/reference/cpane-class.md#create).)|
|[CMFCStatusBar::CreateEx](#createex)|Crée une barre de commande et la fixe à l’objet [CPane.](../../mfc/reference/cpane-class.md) (Overrides [CPane::CreateEx](../../mfc/reference/cpane-class.md#createex).)|
|[CMFCStatusBar::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|Détermine si un autre volet peut être inséré dynamiquement entre cette vitre et le cadre parent. (Overrides [CBasePane::DoesAllowDynInsertBefore](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore).)|
|[CMFCStatusBar::EnablePaneDoubleClick](#enablepanedoubleclick)|Permet ou désactive la manipulation des doubles clics de souris sur la barre d’état.|
|[CMFCStatusBar::EnablePaneProgressBar](#enablepaneprogressbar)|Affiche une barre de progression sur la vitre spécifiée.|
|[CMFCStatusBar::GetCount](#getcount)|Retourne le nombre de vitres sur la barre d’état.|
|[CMFCStatusBar::GetDrawExtendedArea](#getdrawextendedarea)||
|[CMFCStatusBar::GetExtendedArea](#getextendedarea)||
|[CMFCStatusBar::GetItemID](#getitemid)||
|[CMFCStatusBar::GetItemRect](#getitemrect)||
|[CMFCStatusBar::GetPaneInfo](#getpaneinfo)||
|[CMFCStatusBar::GetPaneProgress](#getpaneprogress)||
|[CMFCStatusBar::GetPaneStyle](#getpanestyle)|Retourne le style de vitre. (Overrides [CBasePane::GetPaneStyle](../../mfc/reference/cbasepane-class.md#getpanestyle).)|
|[CMFCStatusBar::GetPaneText](#getpanetext)||
|[CMFCStatusBar::GetPaneWidth](#getpanewidth)|Retourne la largeur, en pixels, de la vitre spécifiée de la barre d’état.|
|[CMFCStatusBar::GetTipText](#gettiptext)|Retourne le texte de pointe de l’outil pour la vitre spécifiée de la barre d’état.|
|[CMFCStatusBar::InvalidatePaneContent](#invalidatepanecontent)|Invalide la vitre spécifiée et redessine son contenu.|
|[CMFCStatusBar::PreCreateWindow](#precreatewindow)|Appelé par le cadre avant la création `CWnd` de la fenêtre Windows attachée à cet objet. (Overrides [CWnd::PreCreateWindow](../../mfc/reference/cwnd-class.md#precreatewindow).)|
|[CMFCStatusBar::SetDrawExtendedArea](#setdrawextendedarea)||
|[CMFCStatusBar::SetIndicators](#setindicators)||
|[CMFCStatusBar:SetPaneAnimation](#setpaneanimation)|Assigne une animation à la vitre spécifiée.|
|[CMFCStatusBar::SetPaneBackgroundColor](#setpanebackgroundcolor)|Définit la couleur de fond pour la vitre spécifiée de la barre d’état.|
|[CMFCStatusBar::SetPaneIcon](#setpaneicon)|Définit l’icône d’indicateur pour la vitre spécifiée de la barre d’état.|
|[CMFCStatusBar::SetPaneInfo](#setpaneinfo)||
|[CMFCStatusBar:SetPaneProgress](#setpaneprogress)|Définit l’avancement actuel de la barre de progression pour la vitre spécifiée de la barre d’état.|
|[CMFCStatusBar::SetPaneStyle](#setpanestyle)|Définit le style de la vitre. (Overrides [CBasePane::SetPaneStyle](../../mfc/reference/cbasepane-class.md#setpanestyle).)|
|[CMFCStatusBar::SetPaneText](#setpanetext)||
|[CMFCStatusBar::SetPaneTextColor](#setpanetextcolor)|Définit la couleur du texte pour la vitre spécifiée de la barre d’état.|
|[CMFCStatusBar::SetPaneWidth](#setpanewidth)|Définit la largeur en pixels de la vitre spécifiée de la barre d’état.|
|[CMFCStatusBar::SetTipText](#settiptext)|Définit le texte de pointe de l’outil pour la vitre spécifiée de la barre d’état.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CMFCStatusBar::OnDrawPane](#ondrawpane)|Appelé par le cadre quand il redessine la vitre de la barre d’état.|

## <a name="remarks"></a>Notes

Le diagramme suivant montre une figure de la barre d’état de [l’application d’échantillon de barre de statut.](../../overview/visual-cpp-samples.md)

![Exemple de CMFCStatusBar](../../mfc/reference/media/cmfcstatusbar.png "Exemple de CMFCStatusBar")

## <a name="example"></a>Exemple

L’exemple suivant montre les variables locales que l’application utilise pour appeler diverses méthodes dans la `CMFCStatusBar` classe. Ces variables sont déclarées dans StatusBarDemoView.h. Le cadre principal est déclaré dans MainFrm.h, le document est déclaré dans StatusBarDemoDoc.h, et la vue est déclarée dans StatusBarDemoView.h. Cet extrait de code fait partie de [l’échantillon de démonstration de barre d’état.](../../overview/visual-cpp-samples.md)

[!code-cpp[NVC_MFC_StatusBarDemo#9](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_1.h)]

## <a name="example"></a>Exemple

L’exemple suivant montre comment obtenir `CMFCStatusBar` une référence `GetStatusBar` à l’objet en introduisant la méthode `GetStatusBar` dans MainFrm.h, puis en appelant cette méthode à partir de la méthode dans StatusBarDemoView.h. Cet extrait de code fait partie de [l’échantillon de démonstration de barre d’état.](../../overview/visual-cpp-samples.md)

[!code-cpp[NVC_MFC_StatusBarDemo#7](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_2.h)]
[!code-cpp[NVC_MFC_StatusBarDemo#8](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_3.h)]

## <a name="example"></a>Exemple

L’exemple suivant montre comment appeler `CMFCStatusBar` différentes méthodes dans la classe dans StatusBarDemoView.cpp. Les constantes sont déclarées dans MainFrm.h. L’exemple montre comment définir l’icône, définir le texte de la barre d’état, afficher une barre de progression sur le volet spécifié, attribuer une animation à la vitre spécifiée, définir le texte et la largeur de la vitre de barre d’état, et définir l’indicateur de progression actuel de la barre de progression pour le volet de barre d’état. Cet extrait de code fait partie de [l’échantillon de démonstration de barre d’état.](../../overview/visual-cpp-samples.md)

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

## <a name="requirements"></a>Spécifications

**En-tête:** afxstatusbar.h

## <a name="cmfcstatusbarcalcfixedlayout"></a><a name="calcfixedlayout"></a>CMFCStatusBar::CalcFixedLayout

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>Paramètres

[dans] *bStretch*<br/>
[dans] *bHorz (en)*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcstatusbarcommandtoindex"></a><a name="commandtoindex"></a>CMFCStatusBar::CommandToIndex

```
int CommandToIndex(UINT nIDFind) const;
```

### <a name="parameters"></a>Paramètres

[dans] *nIDFind (en)*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcstatusbarcreate"></a><a name="create"></a>CMFCStatusBar::Créer

```
BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>Paramètres

[dans] *pParentWnd*<br/>
[dans] *dwStyle (en)*<br/>
[dans] *nID (en)*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcstatusbarcreateex"></a><a name="createex"></a>CMFCStatusBar::CreateEx

```
BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = 0,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>Paramètres

[dans] *pParentWnd*<br/>
[dans] *dwCtrlStyle (en)*<br/>
[dans] *dwStyle (en)*<br/>
[dans] *nID (en)*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcstatusbardoesallowdyninsertbefore"></a><a name="doesallowdyninsertbefore"></a>CMFCStatusBar::DoesAllowDynInsertBefore

```
virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcstatusbarenablepanedoubleclick"></a><a name="enablepanedoubleclick"></a>CMFCStatusBar::EnablePaneDoubleClick

Permet ou désactive la manipulation des doubles clics de souris sur la barre d’état.

```
void EnablePaneDoubleClick(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Paramètres

*bEnable*<br/>
[dans] Si VRAI, activez le traitement de la souris en double clic. Sinon désactiver le traitement de la souris double-clic.

### <a name="remarks"></a>Notes

Si la barre d’état est activée pour traiter les doubles clics, Windows envoie la notification WM_COMMAND ainsi qu’un identifiant de ressource au propriétaire de la barre d’état chaque fois que l’utilisateur double clics sur la carte de barre d’état.

## <a name="cmfcstatusbarenablepaneprogressbar"></a><a name="enablepaneprogressbar"></a>CMFCStatusBar::EnablePaneProgressBar

Affichez une barre de progression sur la vitre spécifiée.

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
[dans] Spécifie l’index de la vitre dont la barre de progression pour permettre.

*nTotal (en)*<br/>
[dans] Spécifie la valeur maximale pour la barre de progression.

*bDisplayText (en)*<br/>
[dans] Précise si la barre de progression doit afficher la valeur de progression actuelle.

*clrBar*<br/>
[dans] Spécifie la couleur de fond de la barre de progression.

*clrBarDest*<br/>
[dans] Spécifie la couleur secondaire de l’arrière-plan de la barre de progression. Utilisez une valeur différente de *celle de clrBar* pour remplir par une couleur mélangée à un gradient.

*clrProgressText*<br/>
[dans] Spécifie la couleur du texte de la barre de progression.

### <a name="remarks"></a>Notes

Si vous voulez désactiver l’appel `EnablePaneProgressBar` de barre de progression avec *nTotal* réglé à -1. Par défaut *nTotal* est réglé à 100. Par conséquent, vous n’avez pas besoin de calculs supplémentaires pour afficher les progrès en pourcentage.

Vous devez passer différentes valeurs pour *clrBar* et *clrBarDest* de sorte que la couleur de fond de la barre de progression affiche une couleur mélangée dans un gradient. .

Pour définir les progrès actuels, appelez la méthode [CMFCStatusBar::SetPaneProgress.](#setpaneprogress)

## <a name="cmfcstatusbargetcount"></a><a name="getcount"></a>CMFCStatusBar::GetCount

Récupère le nombre de vitres dans la barre d’état.

```
int GetCount() const;
```

### <a name="return-value"></a>Valeur de retour

Le nombre de vitres dans la barre d’état.

## <a name="cmfcstatusbargetdrawextendedarea"></a><a name="getdrawextendedarea"></a>CMFCStatusBar::GetDrawExtendedArea

```
BOOL GetDrawExtendedArea() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcstatusbargetextendedarea"></a><a name="getextendedarea"></a>CMFCStatusBar::GetExtendedArea

```
virtual BOOL GetExtendedArea(CRect& rect) const;
```

### <a name="parameters"></a>Paramètres

[dans] *rect*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcstatusbargetitemid"></a><a name="getitemid"></a>CMFCStatusBar::GetItemID

```
UINT GetItemID(int nIndex) const;
```

### <a name="parameters"></a>Paramètres

[dans] *nIndex*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcstatusbargetitemrect"></a><a name="getitemrect"></a>CMFCStatusBar::GetItemRect

```
void GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Paramètres

[dans] *nIndex*<br/>
[dans] *lpRect*<br/>

### <a name="remarks"></a>Notes

## <a name="cmfcstatusbargetpaneinfo"></a><a name="getpaneinfo"></a>CMFCStatusBar::GetPaneInfo

```
void GetPaneInfo(
    int nIndex,
    UINT& nID,
    UINT& nStyle,
    int& cxWidth) const;
```

### <a name="parameters"></a>Paramètres

[dans] *nIndex*<br/>
[dans] *nID (en)*<br/>
[dans] *nStyle (en)*<br/>
[dans] *cxWidth (en)*<br/>

### <a name="remarks"></a>Notes

## <a name="cmfcstatusbargetpaneprogress"></a><a name="getpaneprogress"></a>CMFCStatusBar::GetPaneProgress

```
long GetPaneProgress(int nIndex) const;
```

### <a name="parameters"></a>Paramètres

[dans] *nIndex*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcstatusbargetpanestyle"></a><a name="getpanestyle"></a>CMFCStatusBar::GetPaneStyle

```
UINT GetPaneStyle(int nIndex) const;
```

### <a name="parameters"></a>Paramètres

[dans] *nIndex*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcstatusbargetpanetext"></a><a name="getpanetext"></a>CMFCStatusBar::GetPaneText

```
void GetPaneText(
    int nIndex,
    CString& s) const;

CString GetPaneText(int nIndex) const;
```

### <a name="parameters"></a>Paramètres

[dans] *nIndex*<br/>
[dans] *s*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcstatusbargetpanewidth"></a><a name="getpanewidth"></a>CMFCStatusBar::GetPaneWidth

Récupère la largeur de la vitre d’une barre d’état.

```
int GetPaneWidth(int nIndex) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
[dans] Spécifie l’index du volet de barre d’état.

### <a name="return-value"></a>Valeur de retour

La largeur de la vitre de barre d’état qui *nIndex* spécifie; autrement, zéro si une vitre de barre de statut n’existe pas.

## <a name="cmfcstatusbargettiptext"></a><a name="gettiptext"></a>CMFCStatusBar::GetTipText

Récupérez le texte de pointe d’une barre d’état.

```
CString GetTipText(int nIndex) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
[dans] Spécifie l’index de la vitre pour laquelle récupérer le texte de pointe de l’outil.

### <a name="return-value"></a>Valeur de retour

Le texte de bout d’outils du volet de barre d’état que *nIndex* spécifie. Sinon, la chaîne vide si un volet de barre d’état n’existe pas pour le *nIndex* spécifié ou si son texte de pointe d’outil est vide.

## <a name="cmfcstatusbarinvalidatepanecontent"></a><a name="invalidatepanecontent"></a>CMFCStatusBar::InvalidatePaneContent

Invalider le volet de barre d’état et redessiner son contenu.

```
void InvalidatePaneContent(int nIndex);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
[dans] Spécifie l’index de la vitre dont le contenu doit être invalidé et redessiné.

### <a name="remarks"></a>Notes

Lorsque la barre d’état est invalidée, elle est marquée pour le redessinage. Windows le redessiner `UpdateWindow` lorsque la méthode envoie `OnPaint` un message WM_PAINT à la méthode.

## <a name="cmfcstatusbarondrawpane"></a><a name="ondrawpane"></a>CMFCStatusBar::OnDrawPane

Redessiner la vitre de la barre d’état.

```
virtual void OnDrawPane(
    CDC* pDC,
    CMFCStatusBarPaneInfo* pPane);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[dans] Un pointeur vers un contexte d’appareil pour le dessin.

*pPane (en anglais)*<br/>
[dans] Un pointeur `CMFCStatusBarPaneInfo` vers une structure qui contient les informations sur le volet à redessiner.

### <a name="remarks"></a>Notes

Par défaut, `OnDrawPane` redessiner la vitre en utilisant le contexte de l’appareil *pDC* selon le style et le contenu du volet.

Remplacer cette méthode `CMFCStatusBar`dans une classe dérivée pour personnaliser l’apparence d’une vitre.

## <a name="cmfcstatusbarprecreatewindow"></a><a name="precreatewindow"></a>CMFCStatusBar::PreCreateWindow

```
virtual BOOL PreCreateWindow(CREATESTRUCT& cs);
```

### <a name="parameters"></a>Paramètres

[dans] *cs*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcstatusbarsetdrawextendedarea"></a><a name="setdrawextendedarea"></a>CMFCStatusBar::SetDrawExtendedArea

```
void SetDrawExtendedArea(BOOL bSet = TRUE);
```

### <a name="parameters"></a>Paramètres

[dans] *bSet (en anglais)*<br/>

### <a name="remarks"></a>Notes

## <a name="cmfcstatusbarsetindicators"></a><a name="setindicators"></a>CMFCStatusBar::SetIndicators

```
BOOL SetIndicators(
    const UINT* lpIDArray,
    int nIDCount);
```

### <a name="parameters"></a>Paramètres

[dans] *lpIDArray*<br/>
[dans] *nIDCompte*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcstatusbarsetpaneanimation"></a><a name="setpaneanimation"></a>CMFCStatusBar:SetPaneAnimation

Assigne une animation à la vitre spécifiée.

```
void SetPaneAnimation(
    int nIndex,
    HIMAGELIST hImageList,
    UINT nFrameRate=500,
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
[dans] Spécifie l’index de la vitre à laquelle vous souhaitez lui assigner une animation.

*hImageList*<br/>
[dans] Spécifie une poignée à la liste d’images qui détient les cadres d’animation.

*nFrameRate (en)*<br/>
[dans] Spécifie le taux d’image, en millisecondes, pour l’animation.

*bUpdate (en)*<br/>
[dans] Si VRAI, mettez à jour immédiatement le contenu du volet. Dans le cas contraire, le contenu de la vitre est mis à jour lorsqu’il est invalidé.

### <a name="remarks"></a>Notes

Si vous souhaitez désactiver l’animation `SetPaneAnimation` `hImageList` en cours, appelez avec définissez NULL.

## <a name="cmfcstatusbarsetpanebackgroundcolor"></a><a name="setpanebackgroundcolor"></a>CMFCStatusBar::SetPaneBackgroundColor

Définit la couleur de fond de la vitre de barre d’état.

```
void SetPaneBackgroundColor(
    int nIndex,
    COLORREF clrBackground=(COLORREF)-1,
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
[dans] Spécifie l’index de la vitre pour laquelle définir une nouvelle couleur de fond.

*clrBackground*<br/>
[dans] Spécifie la nouvelle couleur de fond.

*bUpdate (en)*<br/>
[dans] Si VRAI, mettez à jour immédiatement le contenu du volet. Sinon, ne mettez pas à jour le contenu de la vitre jusqu’à ce que le volet soit invalidé par une autre méthode.

## <a name="cmfcstatusbarsetpaneicon"></a><a name="setpaneicon"></a>CMFCStatusBar::SetPaneIcon

Réglez l’icône du volet de barre d’état.

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
[dans] Spécifie l’index de la vitre pour lequel définir l’image.

*hIcon (en)*<br/>
[dans] Spécifie une poignée à l’icône à définir comme image de volet.

*bUpdate (en)*<br/>
[dans] Précise s’il faut mettre à jour immédiatement le contenu du volet.

*hBmp (en)*<br/>
[dans] Spécifie une poignée à la bitmap à régler comme image de volet.

*clrTransparent*<br/>
[dans] Spécifie la couleur transparente de la bitmap que le *hBmp* indique.

### <a name="remarks"></a>Notes

Vous pouvez passer hiCON ou HBITMAP avec la couleur transparente pour définir l’image du volet. Si vous ne voulez plus afficher l’image, passez la valeur NULL comme poignée d’image.

S’il y a une animation en cours d’exécution que [CMFCStatusBar::SetPaneAnimation](#setpaneanimation) a définie, l’animation sera arrêtée.

## <a name="cmfcstatusbarsetpaneinfo"></a><a name="setpaneinfo"></a>CMFCStatusBar::SetPaneInfo

```
void SetPaneInfo(
    int nIndex,
    UINT nID,
    UINT nStyle,
    int cxWidth);
```

### <a name="parameters"></a>Paramètres

[dans] *nIndex*<br/>
[dans] *nID (en)*<br/>
[dans] *nStyle (en)*<br/>
[dans] *cxWidth (en)*<br/>

### <a name="remarks"></a>Notes

## <a name="cmfcstatusbarsetpaneprogress"></a><a name="setpaneprogress"></a>CMFCStatusBar:SetPaneProgress

Définissez l’indicateur de progression actuel de la barre de progression pour le volet spécifié.

```
void SetPaneProgress(
    int nIndex,
    long nCurr,
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
[dans] Spécifie l’indice de la vitre pour laquelle mettre à jour l’indicateur de progression.

*nCurr (en)*<br/>
[dans] Spécifie la valeur actuelle de l’indicateur de progression.

*bUpdate (en)*<br/>
[dans] Précise si le volet doit être mis à jour immédiatement.

### <a name="remarks"></a>Notes

Appelez cette méthode lorsque vous souhaitez mettre à jour l’indicateur de progression de la barre de progression dans le volet spécifié.

Pour utiliser cette fonction pour le volet donné, vous devez appeler [CMFCStatusBar::EnablePaneProgressBar](#enablepaneprogressbar) d’abord.

## <a name="cmfcstatusbarsetpanestyle"></a><a name="setpanestyle"></a>CMFCStatusBar::SetPaneStyle

```
void SetPaneStyle(
    int nIndex,
    UINT nStyle);
```

### <a name="parameters"></a>Paramètres

[dans] *nIndex*<br/>
[dans] *nStyle (en)*<br/>

### <a name="remarks"></a>Notes

## <a name="cmfcstatusbarsetpanetext"></a><a name="setpanetext"></a>CMFCStatusBar::SetPaneText

```
virtual BOOL SetPaneText(
    int nIndex,
    LPCTSTR lpszNewText,
    BOOL bUpdate = TRUE);
```

### <a name="parameters"></a>Paramètres

[dans] *nIndex*<br/>
[dans] *lpszNewText*<br/>
[dans] *bUpdate (en)*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcstatusbarsetpanetextcolor"></a><a name="setpanetextcolor"></a>CMFCStatusBar::SetPaneTextColor

Définit la couleur du texte de la vitre spécifiée.

```
void SetPaneTextColor(
    int nIndex,
    COLORREF clrText=(COLORREF)-1,
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
[dans] Spécifie l’index de la vitre à laquelle vous souhaitez attribuer une nouvelle couleur de texte.

*clrText*<br/>
[dans] Spécifie la couleur du texte.

*bUpdate (en)*<br/>
[dans] Si VRAI, mettez à jour immédiatement le contenu du volet. Sinon, ne mettez pas à jour le contenu de la vitre jusqu’à ce que le volet soit invalidé par une autre méthode.

## <a name="cmfcstatusbarsetpanewidth"></a><a name="setpanewidth"></a>CMFCStatusBar::SetPaneWidth

Réglez la largeur de la vitre de la barre d’état.

```
void SetPaneWidth(
    int nIndex,
    int cx);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
[dans] L’index de la barre d’état pour lequel définir une nouvelle largeur.

*Cx*<br/>
[dans] La nouvelle largeur de la vitre de barre d’état, en pixels.

## <a name="cmfcstatusbarsettiptext"></a><a name="settiptext"></a>CMFCStatusBar::SetTipText

Réglez le texte de l’outil d’un volet de barre d’état.

```
void SetTipText(
    int nIndex,
    LPCTSTR pszTipText);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
[dans] L’index de la vitre à laquelle vous souhaitez attribuer le texte de pointe d’outil.

*pszTipText*<br/>
[dans] Le nouveau texte de l’outiltip.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CPane Class](../../mfc/reference/cpane-class.md)<br/>
[Classe CStatusBar](../../mfc/reference/cstatusbar-class.md)
