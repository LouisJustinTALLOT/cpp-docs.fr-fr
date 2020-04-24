---
title: CMFCDesktopAlertWnd Class
ms.date: 10/18/2018
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
ms.openlocfilehash: cf453b6e69f012bedaf0bd91b5eaf11f7caffa12
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752458"
---
# <a name="cmfcdesktopalertwnd-class"></a>CMFCDesktopAlertWnd Class

La `CMFCDesktopAlertWnd` classe implémente la fonctionnalité d’une boîte de dialogue sans mode qui apparaît sur l’écran pour informer l’utilisateur d’un événement.

Pour plus de détails, consultez le code source situé dans le dossier **VC\\\\atlmfc src\\mfc** de votre installation Visual Studio.

## <a name="syntax"></a>Syntaxe

```
class CMFCDesktopAlertWnd : public CWnd
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCDesktopAlertWnd::Créer](#create)|Crée et initialise la fenêtre d’alerte de bureau.|
|[CMFCDesktopAlertWnd::GetAnimationSpeed](#getanimationspeed)|Retourne la vitesse d’animation.|
|[CMFCDesktopAlertWnd::GetAnimationType](#getanimationtype)|Retourne le type d’animation.|
|[CMFCDesktopAlertWnd::GetAutoCloseTime](#getautoclosetime)|Retourne le temps d’arrêt.|
|[CMFCDesktopAlertWnd::GetCaptionHeight](#getcaptionheight)|Retourne la hauteur de la légende.|
|[CMFCDesktopAlertWnd::GetDialogSize](#getdialogsize)||
|[CMFCDesktopAlertWnd::GetLastPos](#getlastpos)|Retourne la dernière position valide de la fenêtre d’alerte de bureau sur l’écran.|
|[CMFCDesktopAlertWnd::GetTransparency](#gettransparency)|Retourne le niveau de transparence.|
|[CMFCDesktopAlertWnd::HasSmallCaption](#hassmallcaption)|Détermine si la fenêtre d’alerte de bureau est affichée avec la petite légende.|
|[CMFCDesktopAlertWnd::OnBeforeShow](#onbeforeshow)||
|[CMFCDesktopAlertWnd::OnClickLinkButton](#onclicklinkbutton)|Appelé par le cadre lorsque l’utilisateur clique sur un bouton de lien situé sur le menu d’alerte de bureau.|
|[CMFCDesktopAlertWnd::SurCommand](#oncommand)|Le cadre appelle cette fonction de membre lorsque l’utilisateur sélectionne un élément à partir d’un menu, lorsqu’un contrôle de l’enfant envoie un message de notification ou lorsqu’un coup de clé d’accélérateur est traduit. (Overrides [CWnd::OnCommand](../../mfc/reference/cwnd-class.md#oncommand).)|
|[CMFCDesktopAlertWnd::OnDraw](#ondraw)||
|[CMFCDesktopAlertWnd::ProcessCommand](#processcommand)||
|[CMFCDesktopAlertWnd::SetAnimationSpeed](#setanimationspeed)|Définit la nouvelle vitesse d’animation.|
|[CMFCDesktopAlertWnd::SetAnimationType](#setanimationtype)|Définit le type d’animation.|
|[CMFCDesktopAlertWnd::SetAutoCloseTime](#setautoclosetime)|Définit le temps d’arrêt.|
|[CMFCDesktopAlertWnd::SetSmallCaption](#setsmallcaption)|Les commutateurs entre les petites et normales légendes.|
|[CMFCDesktopAlertWnd::SetTransparency](#settransparency)|Définit le niveau de transparence.|

## <a name="remarks"></a>Notes

Une fenêtre d’alerte de bureau peut être transparente, elle peut apparaître avec des effets d’animation, et elle peut disparaître (après un délai spécifié ou lorsque l’utilisateur la rejette en cliquant sur le bouton proche).

Une fenêtre d’alerte de bureau peut également contenir un dialogue par défaut qui contient à son tour une icône, un texte de message (une étiquette) et un lien. Alternativement, une fenêtre d’alerte de bureau peut contenir un dialogue personnalisé à partir des ressources de l’application.

Vous créez une fenêtre d’alerte de bureau en deux étapes. Tout d’abord, appelez `CMFCDesktopAlertWnd` le constructeur pour construire l’objet. Deuxièmement, appelez le [CMFCDesktopAlertWnd : : Créez](#create) la fonction `CMFCDesktopAlertWnd` de membre pour créer la fenêtre et attachez-la à l’objet.

L’objet `CMFCDesktopAlertWnd` crée une boîte spéciale de dialogue pour enfants qui remplit la zone client de la fenêtre d’alerte de bureau. Le dialogue possède tous les contrôles qui sont positionnés sur elle.

Pour afficher une boîte de dialogue personnalisée sur la fenêtre popup, suivez ces étapes :

1. Dérivez une classe de `CMFCDesktopAlertDialog`.

1. Créez un modèle de boîte de dialogue pour enfants dans les ressources.

1. Appelez [CMFCDesktopAlertWnd::Créer](#create) à l’aide de l’ID de ressources du modèle de boîte de dialogue et un pointeur pour les informations de classe de temps d’exécution de la classe dérivée.

1. Programmez la boîte de dialogue personnalisée pour traiter toutes les notifications provenant des contrôles hébergés, ou programmez les commandes hébergées pour traiter ces notifications directement.

Utilisez les fonctions suivantes pour contrôler le comportement de la fenêtre d’alerte de bureau :

- Définissez le type d’animation en appelant [CMFCDesktopAlertWnd::SetAnimationType](#setanimationtype). Les options valides incluent le déplier, la diapositive et le fondu.

- Définissez la vitesse du cadre d’animation en appelant [CMFCDesktopAlertWnd::SetAnimationSpeed](#setanimationspeed).

- Définissez le niveau de transparence en appelant [CMFCDesktopAlertWnd::SetTransparency](#settransparency).

- Changez la taille de la légende à petite en appelant [CMFCDesktopAlertWnd::SetSmallCaption](#setsmallcaption). La petite légende est de 7 pixels de haut.

## <a name="example"></a>Exemple

L’exemple suivant illustre comment utiliser `CMFCDesktopAlertWnd` diverses méthodes `CMFCDesktopAlertWnd` dans la classe pour configurer un objet. L’exemple montre comment définir un type d’animation, définir la transparence de la fenêtre contextueuse, spécifier que la fenêtre d’alerte affiche une petite légende, et définir le temps qui s’écoule avant la fenêtre d’alerte se ferme automatiquement. L’exemple montre également comment créer et initialiser la fenêtre d’alerte de bureau. Cet extrait de code fait partie de [l’échantillon de démonstration d’alerte de bureau](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_DesktopAlertDemo#1](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwnd-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CMFCDesktopAlertWnd](../../mfc/reference/cmfcdesktopalertwnd-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxDesktopAlertWnd.h

## <a name="cmfcdesktopalertwndcreate"></a><a name="create"></a>CMFCDesktopAlertWnd::Créer

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

*pWndOwner (en)*<br/>
[dans, dehors] Spécifie le propriétaire de la fenêtre d’alerte. Ce propriétaire recevra alors toutes les notifications pour la fenêtre d’alerte de bureau. Cette valeur ne peut pas être NULL.

*uiDlgResID*<br/>
[dans] Spécifie l’id de ressource de la fenêtre d’alerte.

*hMenu*<br/>
[dans] Spécifie le menu qui s’affiche lorsque l’utilisateur clique sur le bouton du menu. Si NULL, le bouton menu n’est pas affiché.

*ptPos*<br/>
[dans] Précise la position initiale où la fenêtre d’alerte est affichée, à l’aide des coordonnées de l’écran. Si ce paramètre est (-1, -1), la fenêtre d’alerte est affichée dans le coin inférieur droit de l’écran.

*pRTIDlgBar*<br/>
[dans] Informations de classe runtime pour un cours de boîte de dialogue personnalisé qui couvre la zone client de la fenêtre d’alerte.

*params*<br/>
[dans] Spécifie les paramètres qui sont utilisés pour créer une fenêtre d’alerte.

### <a name="return-value"></a>Valeur de retour

VRAI si la fenêtre d’alerte a été créée avec succès; autrement, FALSE.

### <a name="remarks"></a>Notes

Appelez cette méthode pour créer une fenêtre d’alerte. La zone client de la fenêtre d’alerte contient une boîte de dialogue pour enfants qui héberge tous les contrôles qui sont affichés à l’utilisateur.

La première surcharge de méthode crée une fenêtre d’alerte qui contient une boîte de dialogue pour enfants qui est chargée à partir des ressources de l’application. La première surcharge de méthode peut également spécifier des informations de classe de temps d’exécution pour une classe de boîte de dialogue personnalisée.

La deuxième surcharge de méthode crée une fenêtre d’alerte qui contient des contrôles par défaut. Vous pouvez spécifier les contrôles à afficher en modifiant la [classe CMFCDesktopAlertWndInfo](../../mfc/reference/cmfcdesktopalertwndinfo-class.md).

## <a name="cmfcdesktopalertwndgetanimationspeed"></a><a name="getanimationspeed"></a>CMFCDesktopAlertWnd::GetAnimationSpeed

Retourne la vitesse d’animation.

```
UINT GetAnimationSpeed() const;
```

### <a name="return-value"></a>Valeur de retour

La vitesse d’animation de la fenêtre d’alerte, en millisecondes.

### <a name="remarks"></a>Notes

La vitesse d’animation décrit la vitesse à laquelle la fenêtre d’alerte s’ouvre et se ferme.

## <a name="cmfcdesktopalertwndgetanimationtype"></a><a name="getanimationtype"></a>CMFCDesktopAlertWnd::GetAnimationType

Retourne le type d’animation.

```
CMFCPopupMenu::ANIMATION_TYPE GetAnimationType();
```

### <a name="return-value"></a>Valeur de retour

L’un des types d’animation suivants :

- NO_ANIMATION

- Déplier

- Glisser

- FADE FADE

- SYSTEM_DEFAULT_ANIMATION

## <a name="cmfcdesktopalertwndgetautoclosetime"></a><a name="getautoclosetime"></a>CMFCDesktopAlertWnd::GetAutoCloseTime

Retourne le temps d’arrêt.

```
int GetAutoCloseTime() const;
```

### <a name="return-value"></a>Valeur de retour

Le temps, en millisecondes, après quoi la fenêtre d’alerte se fermera automatiquement.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour déterminer combien de temps devrait s’écouler avant que la fenêtre d’alerte se ferme automatiquement.

## <a name="cmfcdesktopalertwndgetcaptionheight"></a><a name="getcaptionheight"></a>CMFCDesktopAlertWnd::GetCaptionHeight

Retourne la hauteur de la légende.

```
virtual int GetCaptionHeight();
```

### <a name="return-value"></a>Valeur de retour

La hauteur, en pixels, de la légende.

### <a name="remarks"></a>Notes

Cette méthode peut être remplacée dans une classe dérivée. L’implémentation par défaut soit: retourne la petite valeur de hauteur de légende (7 pixels) si `GetSystemMetrics(SM_CYSMCAPTION)`la fenêtre popup doit afficher la petite légende, ou la valeur obtenue à partir de la fonction API Windows .

## <a name="cmfcdesktopalertwndgetlastpos"></a><a name="getlastpos"></a>CMFCDesktopAlertWnd::GetLastPos

Retourne la dernière position de la fenêtre d’alerte de bureau sur l’écran.

```
CPoint GetLastPos() const;
```

### <a name="return-value"></a>Valeur de retour

Un point, dans les coordonnées de l’écran.

### <a name="remarks"></a>Notes

Cette méthode renvoie la dernière position valide de la fenêtre d’alerte sur l’écran.

## <a name="cmfcdesktopalertwndgettransparency"></a><a name="gettransparency"></a>CMFCDesktopAlertWnd::GetTransparency

Retourne le niveau de transparence.

```
BYTE GetTransparency() const;
```

### <a name="return-value"></a>Valeur de retour

Un niveau de transparence compris entre 0 et 255, inclusivement. Plus la valeur est grande, plus la fenêtre est opaque.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour récupérer le niveau de transparence actuel de la fenêtre d’alerte.

## <a name="cmfcdesktopalertwndhassmallcaption"></a><a name="hassmallcaption"></a>CMFCDesktopAlertWnd::HasSmallCaption

Détermine si la fenêtre d’alerte de bureau a une petite légende ou une légende de taille normale.

```
BOOL HasSmallCaption() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si la fenêtre popup est affichée avec une petite légende; FALSE si la fenêtre popup est affichée avec une légende de taille régulière.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour déterminer si la fenêtre popup a une petite légende ou une légende de taille régulière. Par défaut, la petite légende est de 7 pixels de haut. Vous pouvez obtenir la hauteur de la légende de `GetSystemMetrics(SM_CYCAPTION)`taille normale en appelant la fonction API Windows .

## <a name="cmfcdesktopalertwndonbeforeshow"></a><a name="onbeforeshow"></a>CMFCDesktopAlertWnd::OnBeforeShow

```
virtual BOOL OnBeforeShow(CPoint&);
```

### <a name="parameters"></a>Paramètres

[dans] *&CPoint*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcdesktopalertwndonclicklinkbutton"></a><a name="onclicklinkbutton"></a>CMFCDesktopAlertWnd::OnClickLinkButton

Appelé par le cadre lorsque l’utilisateur clique sur un bouton de lien situé sur le menu d’alerte de bureau.

```
virtual BOOL OnClickLinkButton(UINT uiCmdID);
```

### <a name="parameters"></a>Paramètres

*uiCmdID*<br/>
[dans] Ce paramètre n’est pas utilisé.

### <a name="return-value"></a>Valeur de retour

Toujours FALSE.

### <a name="remarks"></a>Notes

Remplacer cette méthode dans une classe dérivée si vous souhaitez être averti lorsqu’un utilisateur clique sur le lien sur la fenêtre d’alerte.

## <a name="cmfcdesktopalertwndoncommand"></a><a name="oncommand"></a>CMFCDesktopAlertWnd::SurCommand

```
virtual BOOL OnCommand(
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Paramètres

[dans] *wParam (en)*<br/>

[dans] *lParam (en)*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcdesktopalertwndondraw"></a><a name="ondraw"></a>CMFCDesktopAlertWnd::OnDraw

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

[dans] *pDC (pDC)*<br/>

### <a name="remarks"></a>Notes

## <a name="cmfcdesktopalertwndprocesscommand"></a><a name="processcommand"></a>CMFCDesktopAlertWnd::ProcessCommand

```
BOOL ProcessCommand(HWND hwnd);
```

### <a name="parameters"></a>Paramètres

[dans] *hwnd hwnd*<br/>

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="cmfcdesktopalertwndsetanimationspeed"></a><a name="setanimationspeed"></a>CMFCDesktopAlertWnd::SetAnimationSpeed

Définit la nouvelle vitesse d’animation.

```cpp
void SetAnimationSpeed(UINT nSpeed);
```

### <a name="parameters"></a>Paramètres

*nSpeed*<br/>
[dans] Spécifie la nouvelle vitesse d’animation, en millisecondes.

### <a name="remarks"></a>Notes

Appelez cette méthode pour définir la vitesse d’animation pour la fenêtre d’alerte. La vitesse d’animation par défaut est de 30 millisecondes.

## <a name="cmfcdesktopalertwndsetanimationtype"></a><a name="setanimationtype"></a>CMFCDesktopAlertWnd::SetAnimationType

Définit le type d’animation.

```cpp
void SetAnimationType(CMFCPopupMenu::ANIMATION_TYPE type);
```

### <a name="parameters"></a>Paramètres

*type*<br/>
[dans] Spécifie le type d’animation.

### <a name="remarks"></a>Notes

Appelez cette méthode pour définir le type d’animation. Vous pouvez spécifier l'une des valeurs suivantes :

- NO_ANIMATION

- Déplier

- Glisser

- FADE FADE

- SYSTEM_DEFAULT_ANIMATION

## <a name="cmfcdesktopalertwndsetautoclosetime"></a><a name="setautoclosetime"></a>CMFCDesktopAlertWnd::SetAutoCloseTime

Définit le temps d’arrêt.

```cpp
void SetAutoCloseTime(int nTime);
```

### <a name="parameters"></a>Paramètres

*n Temps*<br/>
[dans] Le temps, en millisecondes, qui s’écoule avant la fenêtre d’alerte se ferme automatiquement.

### <a name="remarks"></a>Notes

La fenêtre d’alerte est automatiquement fermée après l’heure spécifiée si l’utilisateur n’interagit pas avec la fenêtre.

## <a name="cmfcdesktopalertwndsetsmallcaption"></a><a name="setsmallcaption"></a>CMFCDesktopAlertWnd::SetSmallCaption

Commutateurs entre les petites légendes et les légendes de taille régulière.

```cpp
void SetSmallCaption(BOOL bSmallCaption = TRUE);
```

### <a name="parameters"></a>Paramètres

*bSmallCaption*<br/>
[dans] VRAI pour spécifier que la fenêtre d’alerte affiche une petite légende; autrement, FALSE pour spécifier que la fenêtre d’alerte affiche une légende de taille régulière.

### <a name="remarks"></a>Notes

Appelez cette méthode pour afficher la légende de petite taille ou régulière. Par défaut, la petite légende est de 7 pixels de haut. Vous pouvez obtenir la taille de la légende `GetSystemMetrics(SM_CYCAPTION)`régulière en appelant la fonction API Windows .

## <a name="cmfcdesktopalertwndsettransparency"></a><a name="settransparency"></a>CMFCDesktopAlertWnd::SetTransparency

Définit le niveau de transparence de la fenêtre popup.

```cpp
void SetTransparency(BYTE nTransparency);
```

### <a name="parameters"></a>Paramètres

*nTransparency (en)*<br/>
[dans] Spécifie le niveau de transparence. Cette valeur doit être comprise entre 0 et 255, inclusivement. Plus la valeur est grande, plus la fenêtre est opaque.

### <a name="remarks"></a>Notes

Appelez cette fonction pour définir le niveau de transparence de la fenêtre popup.

## <a name="cmfcdesktopalertwndgetdialogsize"></a><a name="getdialogsize"></a>CMFCDesktopAlertWnd::GetDialogSize

```
virtual CSize GetDialogSize();
```

### <a name="return-value"></a>Valeur de retour

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[Classe CMFCDesktopAlertWndInfo](../../mfc/reference/cmfcdesktopalertwndinfo-class.md)<br/>
[CMFCDesktopAlertDialog, classe](../../mfc/reference/cmfcdesktopalertdialog-class.md)<br/>
[CWnd, classe](../../mfc/reference/cwnd-class.md)
