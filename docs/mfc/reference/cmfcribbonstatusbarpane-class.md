---
description: 'En savoir plus sur : classe CMFCRibbonStatusBarPane'
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
ms.openlocfilehash: 4ddbee5a6c44411ef2ac34bff3e07b47c3d950a0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97264984"
---
# <a name="cmfcribbonstatusbarpane-class"></a>CMFCRibbonStatusBarPane, classe

La `CMFCRibbonStatusBarPane` classe implémente un élément de ruban que vous pouvez ajouter à une barre d’état de ruban.

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
|[CMFCRibbonStatusBarPane::GetTextAlign](#gettextalign)|Retourne le paramètre actuel de l’alignement du texte.|
|[CMFCRibbonStatusBarPane::IsAnimation](#isanimation)|Détermine si l’animation est en cours.|
|[CMFCRibbonStatusBarPane::IsExtended](#isextended)|Détermine si le volet se trouve dans la zone étendue de la barre d’État du ruban.|
|[CMFCRibbonStatusBarPane::OnDrawBorder](#ondrawborder)|(Substitue [CMFCRibbonButton :: OnDrawBorder](../../mfc/reference/cmfcribbonbutton-class.md#ondrawborder).)|
|[CMFCRibbonStatusBarPane::OnFillBackground](#onfillbackground)|(Substitue [CMFCRibbonButton :: OnFillBackground](../../mfc/reference/cmfcribbonbutton-class.md#onfillbackground).)|
|[CMFCRibbonStatusBarPane::SetAlmostLargeText](#setalmostlargetext)|Définit la chaîne de texte la plus longue qui peut être affichée dans le volet sans troncation.|
|[CMFCRibbonStatusBarPane::SetAnimationList](#setanimationlist)|Affecte au volet une liste d’images qui peut être utilisée pour l’animation.|
|[CMFCRibbonStatusBarPane::SetTextAlign](#settextalign)|Définit l’alignement du texte.|
|[CMFCRibbonStatusBarPane::StartAnimation](#startanimation)|Démarre l’animation qui est assignée au volet.|
|[CMFCRibbonStatusBarPane::StopAnimation](#stopanimation)|Arrête l’animation qui est assignée au volet. .|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CMFCRibbonStatusBarPane::OnFinishAnimation](#onfinishanimation)|Appelée par l’infrastructure lorsque l’animation qui est assignée au volet s’arrête.|

## <a name="example"></a>Exemple

L'exemple suivant montre comment utiliser les différentes méthodes de la classe `CMFCRibbonStatusBarPane`. L’exemple montre comment construire un `CMFCRibbonStatusBarPane` objet, définir l’alignement du texte de l’étiquette du volet barre d’État, définir le texte le plus long qui peut être affiché dans le volet barre d’État sans troncation, attacher au volet barre d’État une liste d’images qui peut être utilisée pour l’animation et démarrer l’animation.

[!code-cpp[NVC_MFC_RibbonApp#2](../../mfc/reference/codesnippet/cpp/cmfcribbonstatusbarpane-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonStatusBarPane](../../mfc/reference/cmfcribbonstatusbarpane-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxribbonstatusbarpane. h

## <a name="cmfcribbonstatusbarpanecmfcribbonstatusbarpane"></a><a name="cmfcribbonstatusbarpane"></a> CMFCRibbonStatusBarPane::CMFCRibbonStatusBarPane

Construisez un objet Pane dans la barre d’État.

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

*nCmdID*<br/>
dans Spécifie l’ID de commande du volet.

*lpszText*<br/>
dans Spécifie la chaîne de texte à afficher dans le volet.

*bIsStatic*<br/>
dans Si la valeur est TRUE, le volet d’État ne peut pas être mis en surbrillance ou sélectionné en cliquant dessus.

*hIcon*<br/>
dans Spécifie un handle vers une icône à afficher dans le volet.

*lpszAlmostLargeText*<br/>
dans Spécifie la chaîne de texte la plus longue pouvant être affichée par le volet.

*hBmpAnimationList*<br/>
dans Spécifie un handle vers une liste d’images utilisée pour l’animation.

*cxAnimation*<br/>
dans Spécifie la largeur, en pixels, de l’icône dans la liste d’images utilisée pour l’animation.

*clrTrnsp*<br/>
dans Spécifie la couleur transparente des images de la liste d’images utilisées pour l’animation.

*uiAnimationListResID*<br/>
dans Spécifie un ID de ressource d’une liste d’images utilisée pour l’animation.

## <a name="cmfcribbonstatusbarpanegetalmostlargetext"></a><a name="getalmostlargetext"></a> CMFCRibbonStatusBarPane::GetAlmostLargeText

Obtient la chaîne de texte la plus longue que le volet de barre d’État peut afficher.

```
LPCTSTR GetAlmostLargeText() const;
```

### <a name="return-value"></a>Valeur renvoyée

La chaîne de texte la plus longue que le volet de barre d’État peut afficher.

## <a name="cmfcribbonstatusbarpanegettextalign"></a><a name="gettextalign"></a> CMFCRibbonStatusBarPane::GetTextAlign

Obtient le paramètre actuel de l’alignement du texte de l’étiquette du volet de la barre d’État.

```
int GetTextAlign() const;
```

### <a name="return-value"></a>Valeur renvoyée

L’alignement du texte actuel qui peut être l’un des éléments suivants :

- TA_LEFT

- TA_CENTER

- TA_RIGHT.

## <a name="cmfcribbonstatusbarpaneisanimation"></a><a name="isanimation"></a> CMFCRibbonStatusBarPane::IsAnimation

Détermine si l’animation est en cours.

```
BOOL IsAnimation() const;
```

### <a name="return-value"></a>Valeur renvoyée

TRUE si l’animation est en cours ; FALSe dans le cas contraire.

## <a name="cmfcribbonstatusbarpaneisextended"></a><a name="isextended"></a> CMFCRibbonStatusBarPane::IsExtended

Déterminez si le volet se trouve dans la zone étendue de la barre d’État du ruban.

```
BOOL IsExtended() const;
```

### <a name="return-value"></a>Valeur renvoyée

TRUE si le volet est sur la zone étendue de la barre d’État. Sinon, la valeur est FALSE.

## <a name="cmfcribbonstatusbarpaneondrawborder"></a><a name="ondrawborder"></a> CMFCRibbonStatusBarPane::OnDrawBorder

Pour plus d’informations, consultez le code source situé dans le dossier **VC \\ ATLMFC \\ src \\ MFC** de votre installation de Visual Studio.

```
virtual void OnDrawBorder(CDC*);
```

### <a name="parameters"></a>Paramètres

dans *&#42;* de capture de données modifiées<br/>

### <a name="remarks"></a>Notes

## <a name="cmfcribbonstatusbarpaneonfillbackground"></a><a name="onfillbackground"></a> CMFCRibbonStatusBarPane::OnFillBackground

Pour plus d’informations, consultez le code source situé dans le dossier **VC \\ ATLMFC \\ src \\ MFC** de votre installation de Visual Studio.

```
virtual COLORREF OnFillBackground(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

dans *contrôleur de domaine principal*<br/>

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cmfcribbonstatusbarpaneonfinishanimation"></a><a name="onfinishanimation"></a> CMFCRibbonStatusBarPane::OnFinishAnimation

L’infrastructure appelle cette méthode lorsque l’animation qui est assignée au volet se termine.

```
virtual void OnFinishAnimation();
```

### <a name="remarks"></a>Notes

`StopAnimation` la méthode appelle la `OnFinishAnimation` méthode, que vous pouvez utiliser pour nettoyer les données lorsque l’animation se termine.

## <a name="cmfcribbonstatusbarpanesetalmostlargetext"></a><a name="setalmostlargetext"></a> CMFCRibbonStatusBarPane::SetAlmostLargeText

Définissez le texte le plus long qui peut être affiché dans le volet de barre d’État sans troncation.

```cpp
void SetAlmostLargeText(LPCTSTR lpszAlmostLargeText);
```

### <a name="parameters"></a>Paramètres

*lpszAlmostLargeText*<br/>
dans Spécifie la chaîne la plus longue pouvant être affichée dans le volet de barre d’État sans troncation.

### <a name="remarks"></a>Notes

La bibliothèque calcule la taille du texte que *lpszAlmostLargeText* spécifie et redimensionne le volet en conséquence. Le texte est tronqué s’il ne tient pas dans le volet.

## <a name="cmfcribbonstatusbarpanesetanimationlist"></a><a name="setanimationlist"></a> CMFCRibbonStatusBarPane::SetAnimationList

Joint au volet de la barre d’État une liste d’images qui peut être utilisée pour l’animation.

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

*hBmpAnimationList*<br/>
dans Spécifie un handle vers une liste d’images.

*cxAnimation*<br/>
dans Spécifie la largeur, en pixels, du cadre dans la liste d’images.

*clrTransp*<br/>
dans Spécifie la couleur transparente de la liste d’images.

*uiAnimationListResID*<br/>
dans Spécifie l’ID de ressource de la liste d’images.

### <a name="return-value"></a>Valeur renvoyée

TRUE si la liste d’images est correctement attachée au volet de la barre d’État ; FALSe dans le cas contraire.

## <a name="cmfcribbonstatusbarpanesettextalign"></a><a name="settextalign"></a> CMFCRibbonStatusBarPane::SetTextAlign

Définit l’alignement du texte de l’étiquette du volet de la barre d’État.

```cpp
void SetTextAlign(int nAlign);
```

### <a name="parameters"></a>Paramètres

*nAlign*<br/>
dans Spécifie l’alignement du texte.

### <a name="remarks"></a>Notes

*nAlign* peut avoir l’une des valeurs suivantes :

- TA_LEFT : alignement à gauche

- TA_CENTER : alignement centré

- TA_RIGHT : alignement à droite

## <a name="cmfcribbonstatusbarpanestartanimation"></a><a name="startanimation"></a> CMFCRibbonStatusBarPane::StartAnimation

Démarre l’animation que vous affectez au volet.

```cpp
void StartAnimation(
    UINT nFrameDelay=500,
    UINT nDuration=-1);
```

### <a name="parameters"></a>Paramètres

*nFrameDelay*<br/>
dans Spécifie la fréquence d’images d’animation, en millisecondes.

*nDuration*<br/>
dans Spécifie la durée pendant laquelle l’animation doit être lue, en millisecondes. Utilisez-1 pour une boucle infinie.

### <a name="remarks"></a>Notes

Vous devez spécifier un handle vers une liste d’images avant d’appeler `StartAnimation` à l’aide de `SetAnimationList` .

## <a name="cmfcribbonstatusbarpanestopanimation"></a><a name="stopanimation"></a> CMFCRibbonStatusBarPane::StopAnimation

Arrête l’animation que vous avez assignée au volet barre d’État.

```cpp
void StopAnimation();
```

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonButton, classe](../../mfc/reference/cmfcribbonbutton-class.md)<br/>
[CMFCRibbonStatusBar, classe](../../mfc/reference/cmfcribbonstatusbar-class.md)
