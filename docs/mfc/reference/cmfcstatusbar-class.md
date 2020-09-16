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
ms.openlocfilehash: 004873ef2696eb9504cdd4df77e700c4a145e886
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686572"
---
# <a name="cmfcstatusbar-class"></a>CMFCStatusBar, classe

La `CMFCStatusBar` classe implémente une barre d’état similaire à la `CStatusBar` classe. Toutefois, la classe `CMFCStatusBar` a des fonctionnalités que n'offre pas la classe `CStatusBar` , telles que la capacité à afficher des images, des animations et des barres de progression et la possibilité de répondre aux doubles-clics de souris.

Pour plus d’informations, consultez le code source situé dans le dossier **VC \\ ATLMFC \\ src \\ MFC** de votre installation de Visual Studio.

## <a name="syntax"></a>Syntaxe

```
class CMFCStatusBar : public CPane
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCStatusBar :: CalcFixedLayout](#calcfixedlayout)|(Substitue [CBasePane :: CalcFixedLayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout).)|
|[CMFCStatusBar :: CommandToIndex](#commandtoindex)||
|[CMFCStatusBar :: Create](#create)|Crée une barre de contrôles et l’attache à l’objet [CPane](../../mfc/reference/cpane-class.md) . (Substitue [CPane :: Create](../../mfc/reference/cpane-class.md#create).)|
|[CMFCStatusBar :: CreateEx](#createex)|Crée une barre de contrôles et l’attache à l’objet [CPane](../../mfc/reference/cpane-class.md) . (Substitue [CPane :: CreateEx](../../mfc/reference/cpane-class.md#createex).)|
|[CMFCStatusBar ::D oesAllowDynInsertBefore](#doesallowdyninsertbefore)|Détermine si un autre volet peut être inséré dynamiquement entre ce volet et le frame parent. (Substitue [CBasePane ::D oesallowdyninsertbefore](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore).)|
|[CMFCStatusBar :: EnablePaneDoubleClick](#enablepanedoubleclick)|Active ou désactive la gestion des doubles-clics de la souris sur la barre d’État.|
|[CMFCStatusBar :: EnablePaneProgressBar](#enablepaneprogressbar)|Affiche une barre de progression sur le volet spécifié.|
|[CMFCStatusBar :: GetCount](#getcount)|Retourne le nombre de volets dans la barre d’État.|
|[CMFCStatusBar :: GetDrawExtendedArea](#getdrawextendedarea)||
|[CMFCStatusBar :: GetExtendedArea](#getextendedarea)||
|[CMFCStatusBar :: GetItemID](#getitemid)||
|[CMFCStatusBar :: GetItemRect](#getitemrect)||
|[CMFCStatusBar :: GetPaneInfo](#getpaneinfo)||
|[CMFCStatusBar :: GetPaneProgress](#getpaneprogress)||
|[CMFCStatusBar :: GetPaneStyle](#getpanestyle)|Retourne le style du volet. (Substitue [CBasePane :: GetPaneStyle](../../mfc/reference/cbasepane-class.md#getpanestyle).)|
|[CMFCStatusBar :: GetPaneText](#getpanetext)||
|[CMFCStatusBar :: GetPaneWidth](#getpanewidth)|Retourne la largeur, en pixels, du volet spécifié de la barre d’État.|
|[CMFCStatusBar :: GetTipText](#gettiptext)|Retourne le texte d’info-bulle pour le volet spécifié de la barre d’État.|
|[CMFCStatusBar :: InvalidatePaneContent](#invalidatepanecontent)|Invalide le volet spécifié et redessine son contenu.|
|[CMFCStatusBar ::P reCreateWindow](#precreatewindow)|Appelé par le Framework avant la création de la fenêtre Windows attachée à cet `CWnd` objet. (Substitue [CWnd ::P recreatewindow](../../mfc/reference/cwnd-class.md#precreatewindow).)|
|[CMFCStatusBar :: SetDrawExtendedArea](#setdrawextendedarea)||
|[CMFCStatusBar :: SetIndicators](#setindicators)||
|[CMFCStatusBar :: SetPaneAnimation](#setpaneanimation)|Assigne une animation au volet spécifié.|
|[CMFCStatusBar :: SetPaneBackgroundColor](#setpanebackgroundcolor)|Définit la couleur d’arrière-plan du volet spécifié de la barre d’État.|
|[CMFCStatusBar :: SetPaneIcon](#setpaneicon)|Définit l’icône d’indicateur pour le volet spécifié de la barre d’État.|
|[CMFCStatusBar :: SetPaneInfo](#setpaneinfo)||
|[CMFCStatusBar :: SetPaneProgress](#setpaneprogress)|Définit la progression actuelle de la barre de progression pour le volet spécifié de la barre d’État.|
|[CMFCStatusBar :: SetPaneStyle](#setpanestyle)|Définit le style du volet. (Substitue [CBasePane :: SetPaneStyle](../../mfc/reference/cbasepane-class.md#setpanestyle).)|
|[CMFCStatusBar :: SetPaneText](#setpanetext)||
|[CMFCStatusBar :: SetPaneTextColor](#setpanetextcolor)|Définit la couleur du texte pour le volet spécifié de la barre d’État.|
|[CMFCStatusBar :: SetPaneWidth](#setpanewidth)|Définit la largeur en pixels du volet spécifié de la barre d’État.|
|[CMFCStatusBar :: SetTipText](#settiptext)|Définit le texte d’info-bulle pour le volet spécifié de la barre d’État.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CMFCStatusBar :: OnDrawPane](#ondrawpane)|Appelée par le Framework lorsqu’il redessine le volet de la barre d’État.|

## <a name="remarks"></a>Notes

Le diagramme suivant illustre une figure de la barre d’État à partir de la barre d' [État exemple](../../overview/visual-cpp-samples.md) d’application de démonstration.

![Exemple de CMFCStatusBar](../../mfc/reference/media/cmfcstatusbar.png "Exemple de CMFCStatusBar")

## <a name="examples"></a>Exemples

L’exemple suivant illustre les variables locales que l’application utilise pour appeler différentes méthodes dans la `CMFCStatusBar` classe. Ces variables sont déclarées dans StatusBarDemoView. h. Le frame principal est déclaré dans MainFrm. h, le document est déclaré dans StatusBarDemoDoc. h, et la vue est déclarée dans StatusBarDemoView. h. Cet extrait de code fait partie de l’exemple de démonstration de la [barre d’État](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_StatusBarDemo#9](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_1.h)]

L’exemple suivant montre comment obtenir une référence à un `CMFCStatusBar` objet en introduisant la `GetStatusBar` méthode dans MainFrm. h, puis en appelant cette méthode à partir de la `GetStatusBar` méthode dans StatusBarDemoView. h. Cet extrait de code fait partie de l’exemple de démonstration de la [barre d’État](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_StatusBarDemo#7](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_2.h)]
[!code-cpp[NVC_MFC_StatusBarDemo#8](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_3.h)]

L’exemple suivant montre comment appeler différentes méthodes dans la `CMFCStatusBar` classe dans StatusBarDemoView. cpp. Les constantes sont déclarées dans MainFrm. h. L’exemple montre comment définir l’icône, définir le texte d’info-bulle du volet barre d’État, afficher une barre de progression dans le volet spécifié, assigner une animation au volet spécifié, définir le texte et la largeur du volet barre d’État, et définir l’indicateur de progression actuel de la barre de progression pour le volet barre d’État. Cet extrait de code fait partie de l’exemple de démonstration de la [barre d’État](../../overview/visual-cpp-samples.md).

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

**En-tête :** afxstatusbar. h

## <a name="cmfcstatusbarcalcfixedlayout"></a><a name="calcfixedlayout"></a> CMFCStatusBar :: CalcFixedLayout

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>Paramètres

dans *bStretch*<br/>
dans *bHorz*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcstatusbarcommandtoindex"></a><a name="commandtoindex"></a> CMFCStatusBar :: CommandToIndex

```
int CommandToIndex(UINT nIDFind) const;
```

### <a name="parameters"></a>Paramètres

dans *nIDFind*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcstatusbarcreate"></a><a name="create"></a> CMFCStatusBar :: Create

```
BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>Paramètres

dans *pParentWnd*<br/>
dans *dwStyle*<br/>
dans *nid*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcstatusbarcreateex"></a><a name="createex"></a> CMFCStatusBar :: CreateEx

```
BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = 0,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>Paramètres

dans *pParentWnd*<br/>
dans *dwCtrlStyle*<br/>
dans *dwStyle*<br/>
dans *nid*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcstatusbardoesallowdyninsertbefore"></a><a name="doesallowdyninsertbefore"></a> CMFCStatusBar ::D oesAllowDynInsertBefore

```
virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcstatusbarenablepanedoubleclick"></a><a name="enablepanedoubleclick"></a> CMFCStatusBar :: EnablePaneDoubleClick

Active ou désactive la gestion des doubles-clics de la souris sur la barre d’État.

```cpp
void EnablePaneDoubleClick(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Paramètres

*bEnable*<br/>
dans Si la valeur est TRUE, active le traitement du double-clic de la souris. Sinon, désactivez le traitement du double-clic de la souris.

### <a name="remarks"></a>Notes

Si la barre d’État est activée pour traiter les doubles clics, Windows envoie la notification WM_COMMAND avec un ID de ressource au propriétaire de la barre d’état chaque fois que l’utilisateur double-clique sur le volet barre d’État.

## <a name="cmfcstatusbarenablepaneprogressbar"></a><a name="enablepaneprogressbar"></a> CMFCStatusBar :: EnablePaneProgressBar

Afficher une barre de progression sur le volet spécifié.

```cpp
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
dans Spécifie l’index du volet dont la barre de progression doit être activée.

*nTotal*<br/>
dans Spécifie la valeur maximale de la barre de progression.

*bDisplayText*<br/>
dans Spécifie si la barre de progression doit afficher la valeur de progression actuelle.

*clrBar*<br/>
dans Spécifie la couleur d’arrière-plan de la barre de progression.

*clrBarDest*<br/>
dans Spécifie la couleur secondaire de l’arrière-plan de la barre de progression. Utilisez une valeur différente de *clrBar* pour remplir une couleur fusionnée dans un dégradé.

*clrProgressText*<br/>
dans Spécifie la couleur du texte de la barre de progression.

### <a name="remarks"></a>Notes

Si vous souhaitez désactiver l’appel de barre de progression `EnablePaneProgressBar` avec *Ntotal* défini sur-1. Par défaut, *Ntotal* est défini sur 100. Par conséquent, vous n’avez pas besoin de calculs supplémentaires pour afficher la progression sous forme de pourcentage.

Vous devez passer différentes valeurs pour *clrBar* et *clrBarDest* afin que la couleur d’arrière-plan de la barre de progression affiche une couleur fusionnée dans un dégradé. .

Pour définir la progression actuelle, appelez la méthode [CMFCStatusBar :: SetPaneProgress](#setpaneprogress) .

## <a name="cmfcstatusbargetcount"></a><a name="getcount"></a> CMFCStatusBar :: GetCount

Récupère le nombre de volets dans la barre d’État.

```
int GetCount() const;
```

### <a name="return-value"></a>Valeur de retour

Nombre de volets dans la barre d’État.

## <a name="cmfcstatusbargetdrawextendedarea"></a><a name="getdrawextendedarea"></a> CMFCStatusBar :: GetDrawExtendedArea

```
BOOL GetDrawExtendedArea() const;
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcstatusbargetextendedarea"></a><a name="getextendedarea"></a> CMFCStatusBar :: GetExtendedArea

```
virtual BOOL GetExtendedArea(CRect& rect) const;
```

### <a name="parameters"></a>Paramètres

dans *Rect*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcstatusbargetitemid"></a><a name="getitemid"></a> CMFCStatusBar :: GetItemID

```
UINT GetItemID(int nIndex) const;
```

### <a name="parameters"></a>Paramètres

dans *nIndex*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcstatusbargetitemrect"></a><a name="getitemrect"></a> CMFCStatusBar :: GetItemRect

```cpp
void GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Paramètres

dans *nIndex*<br/>
dans *lpRect*<br/>

### <a name="remarks"></a>Notes

## <a name="cmfcstatusbargetpaneinfo"></a><a name="getpaneinfo"></a> CMFCStatusBar :: GetPaneInfo

```cpp
void GetPaneInfo(
    int nIndex,
    UINT& nID,
    UINT& nStyle,
    int& cxWidth) const;
```

### <a name="parameters"></a>Paramètres

dans *nIndex*<br/>
dans *nid*<br/>
dans *nStyle*<br/>
dans *cxWidth*<br/>

### <a name="remarks"></a>Notes

## <a name="cmfcstatusbargetpaneprogress"></a><a name="getpaneprogress"></a> CMFCStatusBar :: GetPaneProgress

```
long GetPaneProgress(int nIndex) const;
```

### <a name="parameters"></a>Paramètres

dans *nIndex*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcstatusbargetpanestyle"></a><a name="getpanestyle"></a> CMFCStatusBar :: GetPaneStyle

```
UINT GetPaneStyle(int nIndex) const;
```

### <a name="parameters"></a>Paramètres

dans *nIndex*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcstatusbargetpanetext"></a><a name="getpanetext"></a> CMFCStatusBar :: GetPaneText

```cpp
void GetPaneText(
    int nIndex,
    CString& s) const;

CString GetPaneText(int nIndex) const;
```

### <a name="parameters"></a>Paramètres

dans *nIndex*<br/>
dans *s*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcstatusbargetpanewidth"></a><a name="getpanewidth"></a> CMFCStatusBar :: GetPaneWidth

Récupère la largeur du volet d’une barre d’État.

```
int GetPaneWidth(int nIndex) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
dans Spécifie l’index du volet de la barre d’État.

### <a name="return-value"></a>Valeur de retour

Largeur du volet de la barre d’État que *nIndex* spécifie ; Sinon, zéro si un volet de barre d’État n’existe pas.

## <a name="cmfcstatusbargettiptext"></a><a name="gettiptext"></a> CMFCStatusBar :: GetTipText

Récupère le texte d’info-bulle du volet d’une barre d’État.

```
CString GetTipText(int nIndex) const;
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
dans Spécifie l’index du volet pour lequel récupérer le texte d’info-bulle.

### <a name="return-value"></a>Valeur de retour

Texte d’info-bulle du volet de la barre d’État que *nIndex* spécifie. Sinon, la chaîne vide si un volet de barre d’État n’existe pas pour le *nIndex* spécifié ou si son texte info-bulle est vide.

## <a name="cmfcstatusbarinvalidatepanecontent"></a><a name="invalidatepanecontent"></a> CMFCStatusBar :: InvalidatePaneContent

Invalidez le volet de barre d’État et redessinez son contenu.

```cpp
void InvalidatePaneContent(int nIndex);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
dans Spécifie l’index du volet dont le contenu doit être invalidé et redessiné.

### <a name="remarks"></a>Notes

Lorsque la barre d’État est invalidée, elle est marquée pour être redessinée. Windows le redessine lorsque la `UpdateWindow` méthode envoie un message WM_PAINT à la `OnPaint` méthode.

## <a name="cmfcstatusbarondrawpane"></a><a name="ondrawpane"></a> CMFCStatusBar :: OnDrawPane

Redessinez le volet de la barre d’État.

```
virtual void OnDrawPane(
    CDC* pDC,
    CMFCStatusBarPaneInfo* pPane);
```

### <a name="parameters"></a>Paramètres

*Maîtres*<br/>
dans Pointeur vers un contexte de périphérique pour le dessin.

*pPane*<br/>
dans Pointeur vers une `CMFCStatusBarPaneInfo` structure qui contient les informations relatives au volet à redessiner.

### <a name="remarks"></a>Notes

Par défaut, `OnDrawPane` redessine le volet en utilisant le contrôleur de *domaine principal* du contexte de périphérique en fonction du style et du contenu du volet.

Substituez cette méthode dans une `CMFCStatusBar` classe dérivée de pour personnaliser l’apparence d’un volet.

## <a name="cmfcstatusbarprecreatewindow"></a><a name="precreatewindow"></a> CMFCStatusBar ::P reCreateWindow

```
virtual BOOL PreCreateWindow(CREATESTRUCT& cs);
```

### <a name="parameters"></a>Paramètres

dans *CS*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcstatusbarsetdrawextendedarea"></a><a name="setdrawextendedarea"></a> CMFCStatusBar :: SetDrawExtendedArea

```cpp
void SetDrawExtendedArea(BOOL bSet = TRUE);
```

### <a name="parameters"></a>Paramètres

dans *bset*<br/>

### <a name="remarks"></a>Notes

## <a name="cmfcstatusbarsetindicators"></a><a name="setindicators"></a> CMFCStatusBar :: SetIndicators

```
BOOL SetIndicators(
    const UINT* lpIDArray,
    int nIDCount);
```

### <a name="parameters"></a>Paramètres

dans *lpIDArray*<br/>
dans *nIDCount*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcstatusbarsetpaneanimation"></a><a name="setpaneanimation"></a> CMFCStatusBar :: SetPaneAnimation

Assigne une animation au volet spécifié.

```cpp
void SetPaneAnimation(
    int nIndex,
    HIMAGELIST hImageList,
    UINT nFrameRate=500,
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
dans Spécifie l’index du volet auquel vous souhaitez assigner une animation.

*hImageList*<br/>
dans Spécifie un handle vers la liste d’images qui contient les images d’animation.

*nFrameRate*<br/>
dans Spécifie la fréquence d’images, en millisecondes, de l’animation.

*bUpdate*<br/>
dans Si la valeur est TRUE, mettez immédiatement à jour le contenu du volet. Dans le cas contraire, le contenu du volet est mis à jour lorsqu’il est invalidé.

### <a name="remarks"></a>Notes

Si vous souhaitez désactiver l’animation actuelle, appelez `SetPaneAnimation` avec la `hImageList` valeur null.

## <a name="cmfcstatusbarsetpanebackgroundcolor"></a><a name="setpanebackgroundcolor"></a> CMFCStatusBar :: SetPaneBackgroundColor

Définit la couleur d’arrière-plan du volet barre d’État.

```cpp
void SetPaneBackgroundColor(
    int nIndex,
    COLORREF clrBackground=(COLORREF)-1,
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
dans Spécifie l’index du volet pour lequel une nouvelle couleur d’arrière-plan doit être définie.

*clrBackground*<br/>
dans Spécifie la nouvelle couleur d’arrière-plan.

*bUpdate*<br/>
dans Si la valeur est TRUE, mettez immédiatement à jour le contenu du volet. Sinon, ne mettez pas à jour le contenu du volet tant que le volet n’est pas invalidé par une autre méthode.

## <a name="cmfcstatusbarsetpaneicon"></a><a name="setpaneicon"></a> CMFCStatusBar :: SetPaneIcon

Définissez l’icône du volet barre d’État.

```cpp
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
dans Spécifie l’index du volet pour lequel l’image doit être définie.

*hIcon*<br/>
dans Spécifie un handle vers l’icône à définir comme image du volet.

*bUpdate*<br/>
dans Spécifie si le contenu du volet doit être mis à jour immédiatement.

*hBmp*<br/>
dans Spécifie un handle vers l’image bitmap à définir comme image du volet.

*clrTransparent*<br/>
dans Spécifie la couleur transparente de l’image bitmap que le *hBmp* signale.

### <a name="remarks"></a>Notes

Vous pouvez transmettre HICON ou HBITMAP avec la couleur transparente pour définir l’image du volet. Si vous ne souhaitez pas afficher l’image plus tard, transmettez la valeur NULL comme handle d’image.

Si une animation en cours d’exécution [CMFCStatusBar :: SetPaneAnimation](#setpaneanimation) a été définie, l’animation sera arrêtée.

## <a name="cmfcstatusbarsetpaneinfo"></a><a name="setpaneinfo"></a> CMFCStatusBar :: SetPaneInfo

```cpp
void SetPaneInfo(
    int nIndex,
    UINT nID,
    UINT nStyle,
    int cxWidth);
```

### <a name="parameters"></a>Paramètres

dans *nIndex*<br/>
dans *nid*<br/>
dans *nStyle*<br/>
dans *cxWidth*<br/>

### <a name="remarks"></a>Notes

## <a name="cmfcstatusbarsetpaneprogress"></a><a name="setpaneprogress"></a> CMFCStatusBar :: SetPaneProgress

Définit l’indicateur de progression actuel de la barre de progression pour le volet spécifié.

```cpp
void SetPaneProgress(
    int nIndex,
    long nCurr,
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
dans Spécifie l’index du volet pour lequel mettre à jour l’indicateur de progression.

*nCurr*<br/>
dans Spécifie la valeur actuelle de l’indicateur de progression.

*bUpdate*<br/>
dans Spécifie si le volet doit être mis à jour immédiatement.

### <a name="remarks"></a>Notes

Appelez cette méthode lorsque vous souhaitez mettre à jour l’indicateur de progression de la barre de progression dans le volet spécifié.

Pour utiliser cette fonction pour le volet donné, vous devez d’abord appeler [CMFCStatusBar :: EnablePaneProgressBar](#enablepaneprogressbar) .

## <a name="cmfcstatusbarsetpanestyle"></a><a name="setpanestyle"></a> CMFCStatusBar :: SetPaneStyle

```cpp
void SetPaneStyle(
    int nIndex,
    UINT nStyle);
```

### <a name="parameters"></a>Paramètres

dans *nIndex*<br/>
dans *nStyle*<br/>

### <a name="remarks"></a>Notes

## <a name="cmfcstatusbarsetpanetext"></a><a name="setpanetext"></a> CMFCStatusBar :: SetPaneText

```
virtual BOOL SetPaneText(
    int nIndex,
    LPCTSTR lpszNewText,
    BOOL bUpdate = TRUE);
```

### <a name="parameters"></a>Paramètres

dans *nIndex*<br/>
dans *lpszNewText*<br/>
dans *bUpdate*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcstatusbarsetpanetextcolor"></a><a name="setpanetextcolor"></a> CMFCStatusBar :: SetPaneTextColor

Définit la couleur du texte du volet spécifié.

```cpp
void SetPaneTextColor(
    int nIndex,
    COLORREF clrText=(COLORREF)-1,
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
dans Spécifie l’index du volet auquel vous souhaitez assigner une nouvelle couleur de texte.

*clrText*<br/>
dans Spécifie la couleur du texte.

*bUpdate*<br/>
dans Si la valeur est TRUE, mettez immédiatement à jour le contenu du volet. Sinon, ne mettez pas à jour le contenu du volet tant que le volet n’est pas invalidé par une autre méthode.

## <a name="cmfcstatusbarsetpanewidth"></a><a name="setpanewidth"></a> CMFCStatusBar :: SetPaneWidth

Définissez la largeur du volet barre d’État.

```cpp
void SetPaneWidth(
    int nIndex,
    int cx);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
dans Index du volet de barre d’État pour lequel définir une nouvelle largeur.

*adéquat*<br/>
dans Nouvelle largeur du volet de la barre d’État, en pixels.

## <a name="cmfcstatusbarsettiptext"></a><a name="settiptext"></a> CMFCStatusBar :: SetTipText

Définit le texte d’info-bulle d’un volet de barre d’État.

```cpp
void SetTipText(
    int nIndex,
    LPCTSTR pszTipText);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
dans Index du volet auquel vous souhaitez assigner le texte d’info-bulle.

*pszTipText*<br/>
dans Nouveau texte info-bulle.

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CPane, classe](../../mfc/reference/cpane-class.md)<br/>
[CStatusBar (classe)](../../mfc/reference/cstatusbar-class.md)
