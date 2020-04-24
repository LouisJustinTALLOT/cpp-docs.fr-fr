---
title: CMFCRibbonStatusBarPane, classe
ms.date: 11/04/2016
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
ms.openlocfilehash: bb4e09eabab17061812ed22b2739d06accd57fee
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753501"
---
# <a name="cmfcribbonstatusbarpane-class"></a>CMFCRibbonStatusBarPane, classe

La `CMFCRibbonStatusBarPane` classe implémente un élément ruban que vous pouvez ajouter à une barre d’état de ruban.

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
|[CMFCRibbonStatusBarPane::GetAlmostLargeText](#getalmostlargetext)|Retourne la chaîne qui définit la plus longue chaîne de texte qui peut être affichée dans la vitre sans troncation.|
|[CMFCRibbonStatusBarPane::GetTextAlign](#gettextalign)|Retourne le paramètre actuel de l’alignement du texte.|
|[CMFCRibbonStatusBarPane::IsAnimation](#isanimation)|Détermine si l’animation est en cours.|
|[CMFCRibbonStatusBarPane::IsExtended](#isextended)|Détermine si la vitre est située dans la zone étendue de la barre d’état du ruban.|
|[CMFCRibbonStatusBarPane::OnDrawBorder](#ondrawborder)|(Overrides [CMFCRibbonButton::OnDrawBorder](../../mfc/reference/cmfcribbonbutton-class.md#ondrawborder).)|
|[CMFCRibbonStatusBarPane::OnFillBackground](#onfillbackground)|(Overrides [CMFCRibbonButton::OnFillBackground](../../mfc/reference/cmfcribbonbutton-class.md#onfillbackground).)|
|[CMFCRibbonStatusBarPane::SetAlmostLargeText](#setalmostlargetext)|Définit la plus longue chaîne de texte qui peut être affichée dans le volet sans troncation.|
|[CMFCRibbonStatusBarPane::SetAnimationList](#setanimationlist)|Assigne à la vitre une liste d’images qui peut être utilisée pour l’animation.|
|[CMFCRibbonStatusBarPane::SetTextAlign](#settextalign)|Définit l’alignement du texte.|
|[CMFCRibbonStatusBarPane::StartAnimation](#startanimation)|Démarre l’animation qui est assignée à la vitre.|
|[CMFCRibbonStatusBarPane::StopAnimation](#stopanimation)|Arrête l’animation qui est assignée à la vitre. .|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CMFCRibbonStatusBarPane::OnFinishAnimation](#onfinishanimation)|Appelé par le cadre lorsque l’animation qui est attribuée à la vitre s’arrête.|

## <a name="example"></a>Exemple

L'exemple suivant montre comment utiliser les différentes méthodes de la classe `CMFCRibbonStatusBarPane`. L’exemple montre comment `CMFCRibbonStatusBarPane` construire un objet, définir l’alignement du texte de l’étiquette du volet de barre d’état, définir le texte le plus long qui peut être affiché dans le volet de barre d’état sans troncation, attacher à la barre d’état une liste d’image qui peut être utilisée pour l’animation, et commencer l’animation.

[!code-cpp[NVC_MFC_RibbonApp#2](../../mfc/reference/codesnippet/cpp/cmfcribbonstatusbarpane-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonStatusBarPane](../../mfc/reference/cmfcribbonstatusbarpane-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxribbonstatusbarpane.h

## <a name="cmfcribbonstatusbarpanecmfcribbonstatusbarpane"></a><a name="cmfcribbonstatusbarpane"></a>CMFCRibbonStatusBarPane::CMFCRibbonStatusBarPane

Construire un objet de vitre dans la barre d’état.

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

*nCmdID (en)*<br/>
[dans] Spécifie l’id de commande de la vitre.

*lpszText*<br/>
[dans] Spécifie la chaîne de texte à afficher sur le volet.

*bIsStatic (Enstatique)*<br/>
[dans] Si VRAI, le volet d’état ne peut pas être mis en surbrillance ou sélectionné en cliquant dessus.

*hIcon (en)*<br/>
[dans] Spécifie une poignée à une icône à afficher sur la vitre.

*lpszAlmostLargeText*<br/>
[dans] Spécifie la plus longue chaîne de texte qui peut être affichée par la vitre.

*hBmpAnimationList (en)*<br/>
[dans] Spécifie une poignée à une liste d’images qui est utilisée pour l’animation.

*cxAnimation*<br/>
[dans] Spécifie la largeur, en pixels, de l’icône dans la liste d’images qui est utilisée pour l’animation.

*clrTrnsp*<br/>
[dans] Spécifie la couleur transparente des images dans la liste d’images qui sont utilisées pour l’animation.

*uiAnimationListResID*<br/>
[dans] Spécifie une pièce d’identité de ressource d’une liste d’images qui est utilisée pour l’animation.

## <a name="cmfcribbonstatusbarpanegetalmostlargetext"></a><a name="getalmostlargetext"></a>CMFCRibbonStatusBarPane::GetAlmostLargeText

Obtient la chaîne de texte la plus longue que la vitre de barre d’état peut afficher.

```
LPCTSTR GetAlmostLargeText() const;
```

### <a name="return-value"></a>Valeur de retour

La plus longue chaîne de texte que la vitre de barre d’état peut afficher.

## <a name="cmfcribbonstatusbarpanegettextalign"></a><a name="gettextalign"></a>CMFCRibbonStatusBarPane::GetTextAlign

Obtient le réglage actuel de l’alignement de texte de l’étiquette de la barre d’état.

```
int GetTextAlign() const;
```

### <a name="return-value"></a>Valeur de retour

L’alignement de texte actuel qui peut être l’un des éléments suivants:

- TA_LEFT

- TA_CENTER

- TA_RIGHT.

## <a name="cmfcribbonstatusbarpaneisanimation"></a><a name="isanimation"></a>CMFCRibbonStatusBarPane::IsAnimation

Détermine si l’animation est en cours.

```
BOOL IsAnimation() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si l’animation est en cours; FALSE autrement.

## <a name="cmfcribbonstatusbarpaneisextended"></a><a name="isextended"></a>CMFCRibbonStatusBarPane::IsExtended

Déterminez si la vitre est située dans la zone étendue de la barre d’état du ruban.

```
BOOL IsExtended() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si la vitre est sur la zone étendue de barre d’état. Sinon, la valeur est FALSE.

## <a name="cmfcribbonstatusbarpaneondrawborder"></a><a name="ondrawborder"></a>CMFCRibbonStatusBarPane::OnDrawBorder

Pour plus de détails, consultez le code source situé dans le dossier **VC\\\\atlmfc src\\mfc** de votre installation Visual Studio.

```
virtual void OnDrawBorder(CDC*);
```

### <a name="parameters"></a>Paramètres

[dans] *&#42;des CDC*<br/>

### <a name="remarks"></a>Notes

## <a name="cmfcribbonstatusbarpaneonfillbackground"></a><a name="onfillbackground"></a>CMFCRibbonStatusBarPane::OnFillBackground

Pour plus de détails, consultez le code source situé dans le dossier **VC\\\\atlmfc src\\mfc** de votre installation Visual Studio.

```
virtual COLORREF OnFillBackground(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

[dans] *pDC (pDC)*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcribbonstatusbarpaneonfinishanimation"></a><a name="onfinishanimation"></a>CMFCRibbonStatusBarPane::OnFinishAnimation

Framework appelle cette méthode lorsque l’animation qui est attribuée à la vitre se termine.

```
virtual void OnFinishAnimation();
```

### <a name="remarks"></a>Notes

`StopAnimation`méthode appelle `OnFinishAnimation` la méthode, que vous pouvez utiliser pour nettoyer les données lorsque l’animation se termine.

## <a name="cmfcribbonstatusbarpanesetalmostlargetext"></a><a name="setalmostlargetext"></a>CMFCRibbonStatusBarPane::SetAlmostLargeText

Définissez le texte le plus long qui peut être affiché dans le volet de barre d’état sans troncation.

```cpp
void SetAlmostLargeText(LPCTSTR lpszAlmostLargeText);
```

### <a name="parameters"></a>Paramètres

*lpszAlmostLargeText*<br/>
[dans] Spécifie la plus longue chaîne qui peut être affichée sur le volet de barre d’état sans troncation.

### <a name="remarks"></a>Notes

La bibliothèque calcule la taille du texte qui *lpszAlmostLargeText* spécifie et resize le volet en conséquence. Le texte sera tronqué s’il ne rentre toujours pas dans la vitre.

## <a name="cmfcribbonstatusbarpanesetanimationlist"></a><a name="setanimationlist"></a>CMFCRibbonStatusBarPane::SetAnimationList

Attache à la barre d’état une liste d’images qui peut être utilisée pour l’animation.

```cpp
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

*hBmpAnimationList (en)*<br/>
[dans] Spécifie une poignée à une liste d’images.

*cxAnimation*<br/>
[dans] Spécifie la largeur, en pixels, du cadre dans la liste d’images.

*clrTransp*<br/>
[dans] Spécifie la couleur transparente de la liste d’images.

*uiAnimationListResID*<br/>
[dans] Spécifie l’ID de ressources de la liste d’images.

### <a name="return-value"></a>Valeur de retour

VRAI si la liste d’images est jointe avec succès à la barre d’état; FALSE autrement.

## <a name="cmfcribbonstatusbarpanesettextalign"></a><a name="settextalign"></a>CMFCRibbonStatusBarPane::SetTextAlign

Définit l’alignement de texte de l’étiquette de la barre d’état.

```cpp
void SetTextAlign(int nAlign);
```

### <a name="parameters"></a>Paramètres

*nAlign*<br/>
[dans] Spécifie l’alignement du texte.

### <a name="remarks"></a>Notes

*nAlign* peut avoir l’une des valeurs suivantes :

- TA_LEFT : alignement gauche

- TA_CENTER : alignement central

- TA_RIGHT : alignement droit

## <a name="cmfcribbonstatusbarpanestartanimation"></a><a name="startanimation"></a>CMFCRibbonStatusBarPane::StartAnimation

Démarre l’animation que vous attribuez à la vitre.

```cpp
void StartAnimation(
    UINT nFrameDelay=500,
    UINT nDuration=-1);
```

### <a name="parameters"></a>Paramètres

*nFrameDelay (en)*<br/>
[dans] Spécifie le taux d’image d’animation, en millisecondes.

*nDuration*<br/>
[dans] Précise combien de temps pour jouer de l’animation, en millisecondes. Utilisez -1 pour une boucle infinie.

### <a name="remarks"></a>Notes

Vous devez spécifier une poignée `StartAnimation` à `SetAnimationList`une liste d’images avant d’appeler en utilisant .

## <a name="cmfcribbonstatusbarpanestopanimation"></a><a name="stopanimation"></a>CMFCRibbonStatusBarPane::StopAnimation

Arrête l’animation que vous avez assignée à la vitre de barre d’état.

```cpp
void StopAnimation();
```

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonButton, classe](../../mfc/reference/cmfcribbonbutton-class.md)<br/>
[CMFCRibbonStatusBar, classe](../../mfc/reference/cmfcribbonstatusbar-class.md)
