---
description: 'En savoir plus sur : classe CMFCDesktopAlertWnd'
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
ms.openlocfilehash: 45b75bdbd24a88a7eacff124bb07ac81e7703c31
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330086"
---
# <a name="cmfcdesktopalertwnd-class"></a>CMFCDesktopAlertWnd Class

La `CMFCDesktopAlertWnd` classe implémente les fonctionnalités d’une boîte de dialogue non modale qui apparaît à l’écran pour informer l’utilisateur d’un événement.

Pour plus d’informations, consultez le code source situé dans le dossier **VC \\ ATLMFC \\ src \\ MFC** de votre installation de Visual Studio.

## <a name="syntax"></a>Syntaxe

```
class CMFCDesktopAlertWnd : public CWnd
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCDesktopAlertWnd :: Create](#create)|Crée et initialise la fenêtre d’alerte sur le bureau.|
|[CMFCDesktopAlertWnd :: GetAnimationSpeed](#getanimationspeed)|Retourne la vitesse d’animation.|
|[CMFCDesktopAlertWnd :: GetAnimationType](#getanimationtype)|Retourne le type d’animation.|
|[CMFCDesktopAlertWnd :: GetAutoCloseTime](#getautoclosetime)|Retourne le délai d’expiration de la fermeture automatique.|
|[CMFCDesktopAlertWnd :: GetCaptionHeight](#getcaptionheight)|Retourne la hauteur de la légende.|
|[CMFCDesktopAlertWnd :: GetDialogSize](#getdialogsize)||
|[CMFCDesktopAlertWnd :: GetLastPos](#getlastpos)|Retourne la dernière position valide de la fenêtre d’alerte sur le Bureau à l’écran.|
|[CMFCDesktopAlertWnd :: GetTransparency](#gettransparency)|Retourne le niveau de transparence.|
|[CMFCDesktopAlertWnd :: HasSmallCaption](#hassmallcaption)|Détermine si la fenêtre d’alerte sur le Bureau s’affiche avec la petite légende.|
|[CMFCDesktopAlertWnd :: OnBeforeShow](#onbeforeshow)||
|[CMFCDesktopAlertWnd :: OnClickLinkButton](#onclicklinkbutton)|Appelée par l’infrastructure quand l’utilisateur clique sur un bouton de lien situé dans le menu alerte du bureau.|
|[CMFCDesktopAlertWnd :: OnCommand](#oncommand)|L’infrastructure appelle cette fonction membre lorsque l’utilisateur sélectionne un élément dans un menu, lorsqu’un contrôle enfant envoie un message de notification ou lorsqu’une touche d’accès rapide est traduite. (Substitue [CWnd :: OnCommand](../../mfc/reference/cwnd-class.md#oncommand).)|
|[CMFCDesktopAlertWnd :: OnDraw](#ondraw)||
|[CMFCDesktopAlertWnd ::P rocessCommand](#processcommand)||
|[CMFCDesktopAlertWnd :: SetAnimationSpeed](#setanimationspeed)|Définit la nouvelle vitesse d’animation.|
|[CMFCDesktopAlertWnd :: SetAnimationType](#setanimationtype)|Définit le type d’animation.|
|[CMFCDesktopAlertWnd :: SetAutoCloseTime](#setautoclosetime)|Définit le délai d’expiration de la fermeture automatique.|
|[CMFCDesktopAlertWnd :: SetSmallCaption](#setsmallcaption)|Bascule entre les sous-titres petite et normale.|
|[CMFCDesktopAlertWnd :: SetTransparency](#settransparency)|Définit le niveau de transparence.|

## <a name="remarks"></a>Notes

Une fenêtre d’alerte sur le Bureau peut être transparente, elle peut apparaître avec des effets d’animation, et elle peut disparaître (après un délai spécifié ou lorsque l’utilisateur la ferme en cliquant sur le bouton Fermer).

Une fenêtre d’alerte sur le Bureau peut également contenir une boîte de dialogue par défaut qui, à son tour, contient une icône, un texte de message (une étiquette) et un lien. Une fenêtre d’alerte sur le Bureau peut également contenir une boîte de dialogue personnalisée à partir des ressources de l’application.

Vous créez une fenêtre d’alerte sur le bureau en deux étapes. Tout d’abord, appelez le constructeur pour construire l' `CMFCDesktopAlertWnd` objet. Ensuite, appelez la fonction membre [CMFCDesktopAlertWnd :: Create](#create) pour créer la fenêtre et l’attacher à l' `CMFCDesktopAlertWnd` objet.

L' `CMFCDesktopAlertWnd` objet crée une boîte de dialogue enfant spéciale qui remplit la zone cliente de la fenêtre d’alerte sur le bureau. La boîte de dialogue possède tous les contrôles qui y sont positionnés.

Pour afficher une boîte de dialogue personnalisée dans la fenêtre contextuelle, procédez comme suit :

1. Dérivez une classe de `CMFCDesktopAlertDialog`.

1. Créez un modèle de boîte de dialogue enfant dans les ressources.

1. Appelez [CMFCDesktopAlertWnd :: Create](#create) à l’aide de l’ID de ressource du modèle de boîte de dialogue et d’un pointeur vers les informations de classe d’exécution de la classe dérivée.

1. Programmez la boîte de dialogue personnalisée pour gérer toutes les notifications provenant des contrôles hébergés, ou programmez les contrôles hébergés pour gérer ces notifications directement.

Utilisez les fonctions suivantes pour contrôler le comportement de la fenêtre d’alerte sur le Bureau :

- Définissez le type d’animation en appelant [CMFCDesktopAlertWnd :: SetAnimationType](#setanimationtype). Les options valides sont les suivants : déroulement, glissement et fondu.

- Définissez la vitesse d’image de l’animation en appelant [CMFCDesktopAlertWnd :: SetAnimationSpeed](#setanimationspeed).

- Définissez le niveau de transparence en appelant [CMFCDesktopAlertWnd :: SetTransparency](#settransparency).

- Remplacez la taille de la légende par petite, en appelant [CMFCDesktopAlertWnd :: SetSmallCaption](#setsmallcaption). La petite légende est élevée à 7 pixels.

## <a name="example"></a>Exemple

L’exemple suivant illustre l’utilisation de différentes méthodes dans la `CMFCDesktopAlertWnd` classe pour configurer un `CMFCDesktopAlertWnd` objet. L’exemple montre comment définir un type d’animation, définir la transparence de la fenêtre indépendante, spécifier que la fenêtre d’alerte affiche une petite légende et définir le délai qui s’écoule avant la fermeture automatique de la fenêtre d’alerte. L’exemple montre également comment créer et initialiser la fenêtre d’alerte sur le bureau. Cet extrait de code fait partie de l' [exemple de démonstration](../../overview/visual-cpp-samples.md)de l’alerte sur le bureau.

[!code-cpp[NVC_MFC_DesktopAlertDemo#1](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwnd-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CMFCDesktopAlertWnd](../../mfc/reference/cmfcdesktopalertwnd-class.md)

## <a name="requirements"></a>Spécifications

**En-tête :** afxDesktopAlertWnd. h

## <a name="cmfcdesktopalertwndcreate"></a><a name="create"></a> CMFCDesktopAlertWnd :: Create

Crée et initialise la fenêtre d’alerte sur le bureau.

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

*pWndOwner*<br/>
[in, out] Spécifie le propriétaire de la fenêtre d’alerte. Ce propriétaire recevra alors toutes les notifications de la fenêtre d’alerte sur le bureau. Cette valeur ne peut pas être NULL.

*uiDlgResID*<br/>
dans Spécifie l’ID de ressource de la fenêtre d’alerte.

*hMenu*<br/>
dans Spécifie le menu qui s’affiche lorsque l’utilisateur clique sur le bouton de menu. Si la valeur est NULL, le bouton de menu n’est pas affiché.

*ptPos*<br/>
dans Spécifie la position initiale à laquelle la fenêtre d’alerte s’affiche, à l’aide des coordonnées d’écran. Si ce paramètre est (-1,-1), la fenêtre d’alerte s’affiche dans le coin inférieur droit de l’écran.

*pRTIDlgBar*<br/>
dans Informations de classe Runtime pour une classe de boîte de dialogue personnalisée qui couvre la zone cliente de la fenêtre d’alerte.

*params*<br/>
dans Spécifie les paramètres utilisés pour créer une fenêtre d’alerte.

### <a name="return-value"></a>Valeur renvoyée

TRUE si la fenêtre d’alerte a été créée avec succès ; Sinon, FALSe.

### <a name="remarks"></a>Notes

Appelez cette méthode pour créer une fenêtre d’alerte. La zone cliente de la fenêtre d’alerte contient une boîte de dialogue enfant qui héberge tous les contrôles affichés à l’utilisateur.

La première surcharge de méthode crée une fenêtre d’alerte qui contient une boîte de dialogue enfant qui est chargée à partir des ressources de l’application. La première surcharge de méthode peut également spécifier des informations de classe Runtime pour une classe de boîte de dialogue personnalisée.

La deuxième surcharge de méthode crée une fenêtre d’alerte qui contient des contrôles par défaut. Vous pouvez spécifier les contrôles à afficher en modifiant la [classe CMFCDesktopAlertWndInfo](../../mfc/reference/cmfcdesktopalertwndinfo-class.md).

## <a name="cmfcdesktopalertwndgetanimationspeed"></a><a name="getanimationspeed"></a> CMFCDesktopAlertWnd :: GetAnimationSpeed

Retourne la vitesse d’animation.

```
UINT GetAnimationSpeed() const;
```

### <a name="return-value"></a>Valeur renvoyée

Vitesse d’animation de la fenêtre d’alerte, en millisecondes.

### <a name="remarks"></a>Notes

La vitesse d’animation décrit la vitesse à laquelle la fenêtre d’alerte s’ouvre et se ferme.

## <a name="cmfcdesktopalertwndgetanimationtype"></a><a name="getanimationtype"></a> CMFCDesktopAlertWnd :: GetAnimationType

Retourne le type d’animation.

```
CMFCPopupMenu::ANIMATION_TYPE GetAnimationType();
```

### <a name="return-value"></a>Valeur renvoyée

L’un des types d’animation suivants :

- NO_ANIMATION

- DÉROULER

- LAME

- RETRAIT

- SYSTEM_DEFAULT_ANIMATION

## <a name="cmfcdesktopalertwndgetautoclosetime"></a><a name="getautoclosetime"></a> CMFCDesktopAlertWnd :: GetAutoCloseTime

Retourne le délai d’expiration de la fermeture automatique.

```
int GetAutoCloseTime() const;
```

### <a name="return-value"></a>Valeur renvoyée

Durée, en millisecondes, au terme de laquelle la fenêtre d’alerte se ferme automatiquement.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour déterminer le temps qui doit s’écouler avant que la fenêtre d’alerte se ferme automatiquement.

## <a name="cmfcdesktopalertwndgetcaptionheight"></a><a name="getcaptionheight"></a> CMFCDesktopAlertWnd :: GetCaptionHeight

Retourne la hauteur de la légende.

```
virtual int GetCaptionHeight();
```

### <a name="return-value"></a>Valeur renvoyée

Hauteur, en pixels, de la légende.

### <a name="remarks"></a>Notes

Cette méthode peut être substituée dans une classe dérivée. L’implémentation par défaut : retourne la petite valeur de la hauteur de la légende (7 pixels) si la fenêtre contextuelle doit afficher la petite légende ou la valeur obtenue à partir de la fonction API Windows `GetSystemMetrics(SM_CYSMCAPTION)` .

## <a name="cmfcdesktopalertwndgetlastpos"></a><a name="getlastpos"></a> CMFCDesktopAlertWnd :: GetLastPos

Retourne la dernière position de la fenêtre d’alerte sur le Bureau à l’écran.

```
CPoint GetLastPos() const;
```

### <a name="return-value"></a>Valeur renvoyée

Point, en coordonnées d’écran.

### <a name="remarks"></a>Notes

Cette méthode retourne la dernière position valide de la fenêtre d’alerte à l’écran.

## <a name="cmfcdesktopalertwndgettransparency"></a><a name="gettransparency"></a> CMFCDesktopAlertWnd :: GetTransparency

Retourne le niveau de transparence.

```
BYTE GetTransparency() const;
```

### <a name="return-value"></a>Valeur renvoyée

Un niveau de transparence compris entre 0 et 255 inclus. Plus la valeur est élevée, plus la fenêtre est opaque.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour récupérer le niveau de transparence actuel de la fenêtre d’alerte.

## <a name="cmfcdesktopalertwndhassmallcaption"></a><a name="hassmallcaption"></a> CMFCDesktopAlertWnd :: HasSmallCaption

Détermine si la fenêtre d’alerte sur le bureau comporte une petite légende ou une légende de taille normale.

```
BOOL HasSmallCaption() const;
```

### <a name="return-value"></a>Valeur renvoyée

TRUE si la fenêtre contextuelle s’affiche avec une petite légende ; FALSe si la fenêtre contextuelle s’affiche avec une légende de taille normale.

### <a name="remarks"></a>Notes

Utilisez cette méthode pour déterminer si la fenêtre contextuelle a une petite légende ou une légende de taille normale. Par défaut, la petite légende est élevée à 7 pixels. Vous pouvez obtenir la hauteur de la légende de taille normale en appelant la fonction API Windows `GetSystemMetrics(SM_CYCAPTION)` .

## <a name="cmfcdesktopalertwndonbeforeshow"></a><a name="onbeforeshow"></a> CMFCDesktopAlertWnd :: OnBeforeShow

```
virtual BOOL OnBeforeShow(CPoint&);
```

### <a name="parameters"></a>Paramètres

dans *CPoint&*<br/>

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cmfcdesktopalertwndonclicklinkbutton"></a><a name="onclicklinkbutton"></a> CMFCDesktopAlertWnd :: OnClickLinkButton

Appelée par l’infrastructure quand l’utilisateur clique sur un bouton de lien situé dans le menu alerte du bureau.

```
virtual BOOL OnClickLinkButton(UINT uiCmdID);
```

### <a name="parameters"></a>Paramètres

*uiCmdID*<br/>
dans Ce paramètre n’est pas utilisé.

### <a name="return-value"></a>Valeur renvoyée

Toujours FALSE.

### <a name="remarks"></a>Remarques

Substituez cette méthode dans une classe dérivée si vous souhaitez être averti lorsqu’un utilisateur clique sur le lien dans la fenêtre d’alerte.

## <a name="cmfcdesktopalertwndoncommand"></a><a name="oncommand"></a> CMFCDesktopAlertWnd :: OnCommand

```
virtual BOOL OnCommand(
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Paramètres

dans *wParam*<br/>

dans *lParam*<br/>

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cmfcdesktopalertwndondraw"></a><a name="ondraw"></a> CMFCDesktopAlertWnd :: OnDraw

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Paramètres

dans *contrôleur de domaine principal*<br/>

### <a name="remarks"></a>Notes

## <a name="cmfcdesktopalertwndprocesscommand"></a><a name="processcommand"></a> CMFCDesktopAlertWnd ::P rocessCommand

```
BOOL ProcessCommand(HWND hwnd);
```

### <a name="parameters"></a>Paramètres

dans *HWND*<br/>

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="cmfcdesktopalertwndsetanimationspeed"></a><a name="setanimationspeed"></a> CMFCDesktopAlertWnd :: SetAnimationSpeed

Définit la nouvelle vitesse d’animation.

```cpp
void SetAnimationSpeed(UINT nSpeed);
```

### <a name="parameters"></a>Paramètres

*nSpeed*<br/>
dans Spécifie la nouvelle vitesse d’animation, en millisecondes.

### <a name="remarks"></a>Notes

Appelez cette méthode pour définir la vitesse d’animation de la fenêtre d’alerte. La vitesse d’animation par défaut est de 30 millisecondes.

## <a name="cmfcdesktopalertwndsetanimationtype"></a><a name="setanimationtype"></a> CMFCDesktopAlertWnd :: SetAnimationType

Définit le type d’animation.

```cpp
void SetAnimationType(CMFCPopupMenu::ANIMATION_TYPE type);
```

### <a name="parameters"></a>Paramètres

*type*<br/>
dans Spécifie le type d’animation.

### <a name="remarks"></a>Notes

Appelez cette méthode pour définir le type d’animation. Vous pouvez spécifier l'une des valeurs suivantes :

- NO_ANIMATION

- DÉROULER

- LAME

- RETRAIT

- SYSTEM_DEFAULT_ANIMATION

## <a name="cmfcdesktopalertwndsetautoclosetime"></a><a name="setautoclosetime"></a> CMFCDesktopAlertWnd :: SetAutoCloseTime

Définit le délai d’expiration de la fermeture automatique.

```cpp
void SetAutoCloseTime(int nTime);
```

### <a name="parameters"></a>Paramètres

*Nintervalle*<br/>
dans Durée, en millisecondes, qui s’écoule avant la fermeture automatique de la fenêtre d’alerte.

### <a name="remarks"></a>Notes

La fenêtre d’alerte est fermée automatiquement après l’heure spécifiée si l’utilisateur n’interagit pas avec la fenêtre.

## <a name="cmfcdesktopalertwndsetsmallcaption"></a><a name="setsmallcaption"></a> CMFCDesktopAlertWnd :: SetSmallCaption

Bascule entre les légendes de petite taille et de taille normale.

```cpp
void SetSmallCaption(BOOL bSmallCaption = TRUE);
```

### <a name="parameters"></a>Paramètres

*bSmallCaption*<br/>
dans TRUE pour spécifier que la fenêtre d’alerte affiche une petite légende ; Sinon, FALSe pour indiquer que la fenêtre d’alerte affiche une légende de taille normale.

### <a name="remarks"></a>Notes

Appelez cette méthode pour afficher la légende de taille petite ou normale. Par défaut, la petite légende est élevée à 7 pixels. Vous pouvez obtenir la taille de la légende normale en appelant la fonction de l’API Windows `GetSystemMetrics(SM_CYCAPTION)` .

## <a name="cmfcdesktopalertwndsettransparency"></a><a name="settransparency"></a> CMFCDesktopAlertWnd :: SetTransparency

Définit le niveau de transparence de la fenêtre contextuelle.

```cpp
void SetTransparency(BYTE nTransparency);
```

### <a name="parameters"></a>Paramètres

*nTransparency*<br/>
dans Spécifie le niveau de transparence. Cette valeur doit être comprise entre 0 et 255 inclus. Plus la valeur est élevée, plus la fenêtre est opaque.

### <a name="remarks"></a>Notes

Appelez cette fonction pour définir le niveau de transparence de la fenêtre contextuelle.

## <a name="cmfcdesktopalertwndgetdialogsize"></a><a name="getdialogsize"></a> CMFCDesktopAlertWnd :: GetDialogSize

```
virtual CSize GetDialogSize();
```

### <a name="return-value"></a>Valeur renvoyée

### <a name="remarks"></a>Notes

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCDesktopAlertWndInfo, classe](../../mfc/reference/cmfcdesktopalertwndinfo-class.md)<br/>
[CMFCDesktopAlertDialog, classe](../../mfc/reference/cmfcdesktopalertdialog-class.md)<br/>
[CWnd, classe](../../mfc/reference/cwnd-class.md)
