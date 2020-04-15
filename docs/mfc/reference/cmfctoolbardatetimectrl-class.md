---
title: CMFCToolBarDateTimeCtrl, classe
ms.date: 11/04/2016
f1_keywords:
- CMFCToolBarDateTimeCtrl
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::CMFCToolBarDateTimeCtrl
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::CanBeStretched
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::CopyFrom
- AFXTOOLBARDATETIMECTRL/CMFCToolBarButton::ExportToMenuButton
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::GetByCmd
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::GetDateTimeCtrl
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::GetHwnd
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::GetTime
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::GetTimeAll
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::HaveHotBorder
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::NotifyCommand
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnAddToCustomizePage
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnChangeParentWnd
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnClick
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnCtlColor
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnGlobalFontsChanged
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnMove
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnShow
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnUpdateToolTip
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::SetTime
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::SetTimeAll
helpviewer_keywords:
- CMFCToolBarDateTimeCtrl [MFC], CMFCToolBarDateTimeCtrl
- CMFCToolBarDateTimeCtrl [MFC], CanBeStretched
- CMFCToolBarDateTimeCtrl [MFC], CopyFrom
- CMFCToolBarButton [MFC], ExportToMenuButton
- CMFCToolBarDateTimeCtrl [MFC], GetByCmd
- CMFCToolBarDateTimeCtrl [MFC], GetDateTimeCtrl
- CMFCToolBarDateTimeCtrl [MFC], GetHwnd
- CMFCToolBarDateTimeCtrl [MFC], GetTime
- CMFCToolBarDateTimeCtrl [MFC], GetTimeAll
- CMFCToolBarDateTimeCtrl [MFC], HaveHotBorder
- CMFCToolBarDateTimeCtrl [MFC], NotifyCommand
- CMFCToolBarDateTimeCtrl [MFC], OnAddToCustomizePage
- CMFCToolBarDateTimeCtrl [MFC], OnChangeParentWnd
- CMFCToolBarDateTimeCtrl [MFC], OnClick
- CMFCToolBarDateTimeCtrl [MFC], OnCtlColor
- CMFCToolBarDateTimeCtrl [MFC], OnGlobalFontsChanged
- CMFCToolBarDateTimeCtrl [MFC], OnMove
- CMFCToolBarDateTimeCtrl [MFC], OnShow
- CMFCToolBarDateTimeCtrl [MFC], OnUpdateToolTip
- CMFCToolBarDateTimeCtrl [MFC], SetTime
- CMFCToolBarDateTimeCtrl [MFC], SetTimeAll
ms.assetid: a3853cb9-8ebc-444f-a1e4-9cf905e24c18
ms.openlocfilehash: 9aebd55f19a6687554d8d8378ef84ed5932025a2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372174"
---
# <a name="cmfctoolbardatetimectrl-class"></a>CMFCToolBarDateTimeCtrl, classe

Un bouton de barre d’outils qui contient un contrôle de la date et de l’heure du cueilleur.

## <a name="syntax"></a>Syntaxe

```
class CMFCToolBarDateTimeCtrl : public CMFCToolBarButton
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMFCToolBarDateTimeCtrl::CMFCToolBarDateTimeCtrl](#cmfctoolbardatetimectrl)|Construit un objet `CMFCToolBarDateTimeCtrl`.|
|`CMFCToolBarDateTimeCtrl::~CMFCToolBarDateTimeCtrl`|Destructeur.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMFCToolBarDateTimeCtrl::CanBeStretched](#canbestretched)|Précise si un utilisateur peut étirer le bouton pendant la personnalisation. (Overrides [CMFCToolBarButton::CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched).)|
|[CMFCToolBarDateTimeCtrl::CopyDe](#copyfrom)|Copie les propriétés d’un autre bouton de barre d’outils sur le bouton actuel. (Overrides [CMFCToolBarButton::CopyDe](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom).)|
|`CMFCToolBarDateTimeCtrl::DuplicateData`|Réservé pour un usage futur.|
|[CMFCToolBarButton::ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)|Copies du texte du bouton de la barre d’outils à un menu.|
|`CMFCToolBarDateTimeCtrl::CreateObject`|Utilisé par l'infrastructure pour créer une instance dynamique de ce type de classe.|
|[CMFCToolBarDateTimeCtrl::GetByCmd](#getbycmd)|Récupère le `CMFCToolBarDateTimeCtrl` premier objet de l’application qui a l’ID de commande spécifié.|
|[CMFCToolBarDateTimeCtrl::GetDateTimeCtrl](#getdatetimectrl)|Retourne un pointeur à la date et le contrôle du cueilleur d’heure.|
|[CMFCToolBarDateTimeCtrl::GetHwnd](#gethwnd)|Récupère la poignée de fenêtre qui est associée au bouton de la barre d’outils. (Overrides [CMFCToolBarButton::GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd).)|
|`CMFCToolBarDateTimeCtrl::GetThisClass`|Utilisé par le cadre pour obtenir un pointeur à l’objet [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) qui est associé à ce type de classe.|
|[CMFCToolBarDateTimeCtrl::GetTime](#gettime)|Obtient l’heure choisie à partir d’un contrôle de cueilleur de date et d’heure et le met dans une structure [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) spécifiée.|
|[CMFCToolBarDateTimeCtrl::GetTimeAll](#gettimeall)|Renvoie le temps choisi à partir du bouton de commande de minuteurneur qui a une pièce d’identité de commande spécifiée.|
|[CMFCToolBarDateTimeCtrl::HaveHotBorder](#havehotborder)|Détermine si une bordure du bouton est affichée lorsqu’un utilisateur sélectionne le bouton. (Overrides [CMFCToolBarButton::HaveHotBorder](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder).)|
|[CMFCToolBarDateTimeCtrl::NotifyCommand](#notifycommand)|Précise si le bouton traite le [WM_COMMAND](/windows/win32/menurc/wm-command) message. (Overrides [CMFCToolBarButton::NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand).)|
|[CMFCToolBarDateTimeCtrl::OnAddToCustomizePage](#onaddtocustomizepage)|Appelé par le cadre lorsque le bouton est ajouté à une boîte de dialogue **Personnaliser.** (Overrides [CMFCToolBarButton::OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage).)|
|`CMFCToolBarDateTimeCtrl::OnCalculateSize`|Appelé par le cadre pour calculer la taille du bouton pour le contexte de l’appareil spécifié et l’état d’amarrage. (Overrides [CMFCToolBarButton::OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize).)|
|[CMFCToolBarDateTimeCtrl::OnChangeParentWnd](#onchangeparentwnd)|Appelé par le cadre lorsque le bouton est inséré dans une nouvelle barre d’outils. (Overrides [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd).)|
|[CMFCToolBarDateTimeCtrl::OnClick](#onclick)|Appelé par le cadre lorsque l’utilisateur clique sur le contrôle. (Overrides [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick).)|
|[CMFCToolBarDateTimeCtrl::OnCtlColor](#onctlcolor)|Appelé par le cadre lorsque le barre d’outils parent gère un message WM_CTLCOLOR. (Overrides [CMFCToolBarButton::OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor).)|
|`CMFCToolBarDateTimeCtrl::OnDraw`|Appelé par le cadre pour dessiner le bouton en utilisant les styles spécifiés et les options. (Overrides [CMFCToolBarButton::OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw).)|
|`CMFCToolBarDateTimeCtrl::OnDrawOnCustomizeList`|Appelé par le cadre pour dessiner le bouton dans le volet **Commandes** de la boîte de dialogue **Customize.** (Overrides [CMFCToolBarButton::OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist).)|
|[CMFCToolBarDateTimeCtrl::OnGlobalFontsChanged](#onglobalfontschanged)|Appelé par le cadre lorsque la police mondiale a changé. (Overrides [CMFCToolBarButton::OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged).)|
|[CMFCToolBarDateTimeCtrl::OnMove](#onmove)|Appelé par le cadre lorsque la barre d’outils parent se déplace. (Overrides [CMFCToolBarButton::OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove).)|
|[CMFCToolBarDateTimeCtrl::OnShow](#onshow)|Appelé par le cadre lorsque le bouton devient visible ou invisible. (Overrides [CMFCToolBarButton::OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow).)|
|`CMFCToolBarDateTimeCtrl::OnSize`|Appelé par le cadre lorsque la barre d’outils parente change de taille ou de position, ce changement provoque le bouton de changer de taille. (Overrides [CMFCToolBarButton::OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize).)|
|[CMFCToolBarDateTimeCtrl::OnUpdateToolTip](#onupdatetooltip)|Appelé par le cadre lorsque la barre d’outils parent met à jour son texte tooltip. (Overrides [CMFCToolBarButton::OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip).)|
|`CMFCToolBarDateTimeCtrl::Serialize`|Lit cet objet à partir d’une archive ou l’écrit à une archive, (Overrides [CMFCToolBarButton::Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize).)|
|`CMFCToolBarDateTimeCtrl::SetStyle`|Définit le style du bouton de la barre d’outils. (Overrides [CMFCToolBarButton::SetStyle](../../mfc/reference/cmfctoolbarbutton-class.md#setstyle).)|
|[CMFCToolBarDateTimeCtrl::SetTime](#settime)|Définit l’heure et la date dans le contrôle du cueilleur de temps.|
|[CMFCToolBarDateTimeCtrl::SetTimeAll](#settimeall)|Définit l’heure et la date dans tous les cas du contrôle du cueilleur de temps qui ont une pièce d’identité de commande spécifiée.|

## <a name="remarks"></a>Notes

Pour un exemple de la façon d’utiliser un contrôle de la date et de l’heure, consultez le projet d’échantillon ToolbarDateTimePicker. Pour plus d’informations sur la façon d’ajouter des boutons de contrôle aux barres d’outils, voir [Procédure pas à pas: Mettre des contrôles sur les barres d’outils](../../mfc/walkthrough-putting-controls-on-toolbars.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarDateTimeCtrl](../../mfc/reference/cmfctoolbardatetimectrl-class.md)

## <a name="requirements"></a>Spécifications

**En-tête:** afxtoolbardatetimectrl.h

## <a name="cmfctoolbardatetimectrlcanbestretched"></a><a name="canbestretched"></a>CMFCToolBarDateTimeCtrl::CanBeStretched

Précise si un utilisateur peut étirer le bouton pendant la personnalisation.

```
virtual BOOL CanBeStretched() const;
```

### <a name="return-value"></a>Valeur de retour

Cette méthode renvoie TRUE.

### <a name="remarks"></a>Notes

Par défaut, le cadre ne permet pas à l’utilisateur d’étirer un bouton de barre d’outils lors de la personnalisation. Cette méthode étend l’implémentation de la classe de base ( [CMFCToolBarButton::CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched)) en permettant à l’utilisateur d’étirer un bouton de date et de barre d’outils de temps pendant la personnalisation.

## <a name="cmfctoolbardatetimectrlcmfctoolbardatetimectrl"></a><a name="cmfctoolbardatetimectrl"></a>CMFCToolBarDateTimeCtrl::CMFCToolBarDateTimeCtrl

Crée et initialise un objet [CMFCToolBarDateTimeCtrl.](../../mfc/reference/cmfctoolbardatetimectrl-class.md)

```
CMFCToolBarDateTimeCtrl(
    UINT uiID,
    int iImage,
    DWORD dwStyle=0,
    int iWidth=0);
```

### <a name="parameters"></a>Paramètres

*uiID*<br/>
[dans] L’ID de contrôle.

*iImage (en)*<br/>
[dans] L’index de l’image dans `CMFCToolBarImages` l’objet de la barre d’outils.

*dwStyle (en)*<br/>
[dans] Le style `CMFCToolBarDateTimeCtrlImpl` de la fenêtre qui est créé lorsqu’un utilisateur clique sur le bouton.

*iWidth (en)*<br/>
[dans] La largeur du contrôle, en pixels.

### <a name="remarks"></a>Notes

Cet objet est parasé à la date et à l’heure du système. Le style de `CMFCToolBarDateTimeCtrlImpl` fenêtre de l’objet interne comprend le paramètre *dwStyle* et les styles WS_CHILD et WS_VISIBLE. Vous ne pouvez pas `CMFCToolBarDateTimeCtrl::SetStyle`changer ces styles en utilisant . Utilisez `SetStyle` pour changer le `CMFCToolBarDateTimeCtrl` style du contrôle.

### <a name="example"></a>Exemple

L’exemple suivant montre comment construire `CMFCToolBarDateTimeCtrl` un objet de la classe. Cet extrait de code fait partie de [l’échantillon Toolbar Date Time Picker](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_ToolbarDateTimePicker#1](../../mfc/reference/codesnippet/cpp/cmfctoolbardatetimectrl-class_1.cpp)]

## <a name="cmfctoolbardatetimectrlcopyfrom"></a><a name="copyfrom"></a>CMFCToolBarDateTimeCtrl::CopyDe

Copie les propriétés d’un autre bouton de barre d’outils sur le bouton actuel.

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>Paramètres

*src*<br/>
[dans] Une référence au bouton source à partir duquel copier.

### <a name="remarks"></a>Notes

Appelez cette méthode pour copier un autre bouton de barre d’outils sur ce bouton de barre d’outils. *src* doit être `CMFCToolBarDateTimeCtrl`de type .

## <a name="cmfctoolbardatetimectrlexporttomenubutton"></a><a name="exporttomenubutton"></a>CMFCToolBarDateTimeCtrl::ExportToMenuButton

Copies du texte du bouton de la barre d’outils à un menu.

```
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;
```

### <a name="parameters"></a>Paramètres

*menuButton*<br/>
[dans] Une référence au bouton du menu cible.

### <a name="return-value"></a>Valeur de retour

Cette méthode renvoie TRUE.

### <a name="remarks"></a>Notes

Cette méthode remplace la mise en œuvre de la classe de base ( [CMFCToolBarButton::ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)) en chargeant la ressource de chaîne associée à l’ID de commande du contrôle. Pour plus d’informations sur les ressources de chaîne, voir [CStringT::LoadString](../../atl-mfc-shared/reference/cstringt-class.md#loadstring).

## <a name="cmfctoolbardatetimectrlgetbycmd"></a><a name="getbycmd"></a>CMFCToolBarDateTimeCtrl::GetByCmd

Récupère le `CMFCToolBarDateTimeCtrl` premier objet de l’application qui a l’ID de commande spécifié.

```
static CMFCToolBarDateTimeCtrl* __stdcall GetByCmd(UINT uiCmd);
```

### <a name="parameters"></a>Paramètres

*uiCmd uiCmd*<br/>
[dans] L’ID de commande du bouton à récupérer.

### <a name="return-value"></a>Valeur de retour

Le `CMFCToolBarDateTimeCtrl` premier objet de l’application qui a l’ID de commande spécifié, ou NULL si aucun objet n’a `CMFCToolBarDateTimeCtrl` l’ID de commande spécifié.

### <a name="remarks"></a>Notes

Cette méthode d’utilité partagée est utilisée par des méthodes telles que [CMFCToolBarDateTimeCtrl::SetTimeAll](#settimeall) et [CMFCToolBarDateTimeCtrl::GetTimeAll](#gettimeall) pour définir ou obtenir l’heure et la date de tous les cas du contrôle du cueilleur de temps qui ont un ID de commande spécifié.

## <a name="cmfctoolbardatetimectrlgetdatetimectrl"></a><a name="getdatetimectrl"></a>CMFCToolBarDateTimeCtrl::GetDateTimeCtrl

Retourne un pointeur à la date et le contrôle du cueilleur d’heure.

```
CDateTimeCtrl* GetDateTimeCtrl() const;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur à la date et le contrôle du cueilleur d’heure; ou NULL si le contrôle n’existe pas.

### <a name="remarks"></a>Notes

La `CMFCToolBarDateTimeCtrl` classe initialise `m_pWndDateTime` le membre de `CMFCToolBarDateTimeCtrl` données lorsque vous insérez un objet dans une barre d’outils.

## <a name="cmfctoolbardatetimectrlgethwnd"></a><a name="gethwnd"></a>CMFCToolBarDateTimeCtrl::GetHwnd

Récupère la poignée de fenêtre qui est associée au bouton de la barre d’outils.

```
virtual HWND GetHwnd();
```

### <a name="return-value"></a>Valeur de retour

La poignée de fenêtre qui est associée au bouton date et heure de la barre d’outils.

### <a name="remarks"></a>Notes

Cette méthode remplace la [méthode CMFCToolBarButton::GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd) méthode.

## <a name="cmfctoolbardatetimectrlgettime"></a><a name="gettime"></a>CMFCToolBarDateTimeCtrl::GetTime

Obtient le temps choisi à partir du contrôle de la date et du chronométreur associé et le met dans une structure [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) spécifiée

```
BOOL GetTime(COleDateTime& timeDest) const;
DWORD GetTime(CTime& timeDest) const;
DWORD GetTime(LPSYSTEMTIME pTimeDest) const;
```

### <a name="parameters"></a>Paramètres

*timeDest*<br/>
[out] Dans la première surcharge, un objet [COleDateTime Class](../../atl-mfc-shared/reference/coledatetime-class.md) qui recevra les informations de temps du système. Dans la deuxième surcharge, un objet [CTime](../../atl-mfc-shared/reference/ctime-class.md) qui recevra les informations de temps du système.

*pTimeDest*<br/>
[out] Un pointeur à la structure [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) pour recevoir les informations de temps du système. Ne doit pas être NULL.

### <a name="return-value"></a>Valeur de retour

Dans la première surcharge, nonzero si le temps est écrit avec succès à [l’objet COleDateTime Class;](../../atl-mfc-shared/reference/coledatetime-class.md) sinon 0. Dans les deuxième et troisième surcharges, la valeur de retour est un DWORD qui est égal au membre dwFlag qui a été fixé dans la structure [NMDATETIMECHANGE.](/windows/win32/api/commctrl/ns-commctrl-nmdatetimechange)

### <a name="remarks"></a>Notes

La méthode définit le membre de la structure [NMDATETIMECHANGE](/windows/win32/api/commctrl/ns-commctrl-nmdatetimechange) dwFlags pour indiquer si la date et l’heure de ramassage est fixée à une date et à une heure. Si la valeur est égale GDT_NONE, le `no date` contrôle est réglé sur le statut, et utilise le style DTS_SHOWNONE. Si la valeur retournée équivaut à GDT_VALID, le temps du système est stocké avec succès dans l’emplacement de destination.

## <a name="cmfctoolbardatetimectrlgettimeall"></a><a name="gettimeall"></a>CMFCToolBarDateTimeCtrl::GetTimeAll

Retourne le temps choisi par l’utilisateur à partir du bouton de commande du sélectionneur de temps qui a un ID de commande spécifié.

```
static BOOL GetTimeAll(
    UINT uiCmd,
    COleDateTime& timeDest);

static DWORD GetTimeAll(
    UINT uiCmd,
    CTime& timeDest);

static DWORD GetTimeAll(
    UINT uiCmd,
    LPSYSTEMTIME pTimeDest);
```

### <a name="parameters"></a>Paramètres

*uiCmd uiCmd*<br/>
[dans] Spécifie l’ID de commande d’un bouton de barre d’outils.

*timeDest*<br/>
[out] Dans la première surcharge, un objet [COleDateTime Class](../../atl-mfc-shared/reference/coledatetime-class.md) qui recevra les informations de temps du système. Dans la deuxième surcharge, un objet [CTime](../../atl-mfc-shared/reference/ctime-class.md) qui recevra les informations de temps du système.

*pTimeDest*<br/>
[out] Un pointeur à la structure [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) pour recevoir les informations de temps du système. Ne doit pas être NULL.

### <a name="return-value"></a>Valeur de retour

Si le cadre ne peut pas trouver un bouton de barre d’outils qui correspond à l’id de commande *uiCmd*, la valeur de retour est nulle dans la première surcharge, et GDT_NONE dans les autres surcharges. Si le bouton de la barre d’outils est trouvé, la valeur de retour est la même que la valeur de retour d’un appel à [CMFCToolBarDateTimeCtrl:GetTime](#gettime) sur ce bouton. Une valeur de retour de zéro ou de GDT_NONE peut se produire `GetTime` lorsque le bouton est trouvé, ce qui indique que l’appel à n’a pas retourné une date valide pour une autre raison.

### <a name="remarks"></a>Notes

Cette méthode recherche un bouton de barre d’outils qui a l’ID de commande spécifié et appelle [CMFCToolBarDateTimeCtrl::GetTime](#gettime) méthode sur ce bouton.

## <a name="cmfctoolbardatetimectrlhavehotborder"></a><a name="havehotborder"></a>CMFCToolBarDateTimeCtrl::HaveHotBorder

Détermine si une bordure du bouton est affichée lorsqu’un utilisateur sélectionne le bouton.

```
virtual BOOL HaveHotBorder() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si un bouton affiche sa bordure lorsqu’il est sélectionné; sinon 0.

### <a name="remarks"></a>Notes

Cette méthode renvoie une valeur non zéro si le contrôle est visible.

## <a name="cmfctoolbardatetimectrlnotifycommand"></a><a name="notifycommand"></a>CMFCToolBarDateTimeCtrl::NotifyCommand

Précise si le bouton traite le [WM_COMMAND](/windows/win32/menurc/wm-command) message.

```
virtual BOOL NotifyCommand(int iNotifyCode);
```

### <a name="parameters"></a>Paramètres

*iNotifyCode (en)*<br/>
[dans] Le message de notification associé à la commande.

### <a name="return-value"></a>Valeur de retour

VRAI si le bouton traite le WM_COMMAND message, ou FALSE pour indiquer que le message doit être manipulé par la barre d’outils parent.

### <a name="remarks"></a>Notes

Le cadre appelle cette méthode lorsqu’elle est sur le point d’envoyer un [message WM_COMMAND](/windows/win32/menurc/wm-command) à la fenêtre parente.

Cette méthode étend la mise en œuvre de la classe de base ( [CMFCToolBarButton::NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand)) en traitant la notification [DTN_DATETIMECHANGE.](/windows/win32/Controls/dtn-datetimechange) Il met à jour l’état du `CMFCToolBarDateTimeCtrl` temps interne et met à jour la propriété temporelle de tous les objets avec le même ID de commande.

## <a name="cmfctoolbardatetimectrlonaddtocustomizepage"></a><a name="onaddtocustomizepage"></a>CMFCToolBarDateTimeCtrl::OnAddToCustomizePage

Appelé par le cadre lorsque le bouton est ajouté à une boîte de dialogue **Personnaliser.**

```
virtual void OnAddToCustomizePage();
```

### <a name="remarks"></a>Notes

Cette méthode étend la mise en œuvre de la classe de base, [CMFCToolBarButton::OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage), en copiant les propriétés à partir de la première date et le contrôle de temps dans n’importe quelle barre d’outils qui a le même ID de commande que cet objet. Cette méthode ne fait rien si aucune barre d’outils n’a un contrôle de date et d’heure qui a le même ID de commande que cet objet.

Pour plus d’informations sur la boîte de dialogue **Customize,** voir [CMFCToolBarsCustomizeDialog Class](../../mfc/reference/cmfctoolbarscustomizedialog-class.md).

## <a name="cmfctoolbardatetimectrlonchangeparentwnd"></a><a name="onchangeparentwnd"></a>CMFCToolBarDateTimeCtrl::OnChangeParentWnd

Appelé par le cadre lorsque le bouton est inséré dans une nouvelle barre d’outils.

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>Paramètres

*pWndParent*<br/>
[dans] La nouvelle fenêtre parente.

### <a name="remarks"></a>Notes

Cette méthode remplace la mise en œuvre de la classe de base ( [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)) en recréant l’objet interne. `CMFCToolBarDateTimeCtrlImpl`

## <a name="cmfctoolbardatetimectrlonclick"></a><a name="onclick"></a>CMFCToolBarDateTimeCtrl::OnClick

Appelé par le cadre lorsque l’utilisateur clique sur le contrôle.

```
virtual BOOL OnClick(
    CWnd* pWnd,
    BOOL bDelay = TRUE);
```

### <a name="parameters"></a>Paramètres

*Pwnd*<br/>
[in] Inutilisé.

*bDelay (en)*<br/>
[in] Inutilisé.

### <a name="return-value"></a>Valeur de retour

Nonzero si le bouton traite le message de clic; sinon 0.

### <a name="remarks"></a>Notes

Cette méthode remplace la mise en œuvre de la classe de base, [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick), en retournant une valeur non zéro si l’objet interne `CMFCToolBarDateTimeCtrlImpl` est visible.

## <a name="cmfctoolbardatetimectrlonctlcolor"></a><a name="onctlcolor"></a>CMFCToolBarDateTimeCtrl::OnCtlColor

Appelé par le cadre lorsque le barre d’outils parent gère un message WM_CTLCOLOR.

```
virtual HBRUSH OnCtlColor(
    CDC* pDC,
    UINT nCtlColor);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
[dans] Le contexte de l’appareil qui affiche le bouton.

*nCtlColor (en anglais)*<br/>
[in] Inutilisé.

### <a name="return-value"></a>Valeur de retour

Une poignée à la brosse globale que le cadre utilise pour peindre l’arrière-plan du bouton.

### <a name="remarks"></a>Notes

Cette méthode remplace la mise en œuvre de la classe de base, [CMFCToolBarButton::OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor), en définissant le texte et les couleurs de fond du contexte fourni de l’appareil au texte global et aux couleurs de fond, respectivement.

Pour plus d’informations sur les options globales qui sont disponibles à votre application, voir [AFX_GLOBAL_DATA Structure](../../mfc/reference/afx-global-data-structure.md).

## <a name="cmfctoolbardatetimectrlonglobalfontschanged"></a><a name="onglobalfontschanged"></a>CMFCToolBarDateTimeCtrl::OnGlobalFontsChanged

Appelé par le cadre lorsque la police mondiale a changé.

```
virtual void OnGlobalFontsChanged();
```

### <a name="remarks"></a>Notes

Cette méthode étend la mise en œuvre de la classe de base ( [CMFCToolBarButton::OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged)) en changeant la police du contrôle à celle de la police globale.

Pour plus d’informations sur les options globales qui sont disponibles à votre application, voir [AFX_GLOBAL_DATA Structure](../../mfc/reference/afx-global-data-structure.md).

## <a name="cmfctoolbardatetimectrlonmove"></a><a name="onmove"></a>CMFCToolBarDateTimeCtrl::OnMove

Appelé par le cadre lorsque la barre d’outils parent se déplace.

```
virtual void OnMove();
```

### <a name="remarks"></a>Notes

Cette méthode remplace l’implémentation de la classe par défaut ( [CMFCToolBarButton::OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove)) en mettant à jour la position de l’objet interne. `CMFCToolBarDateTimeCtrlImpl`

## <a name="cmfctoolbardatetimectrlonshow"></a><a name="onshow"></a>CMFCToolBarDateTimeCtrl::OnShow

Appelé par le cadre lorsque le bouton devient visible ou invisible.

```
virtual void OnShow(BOOL bShow);
```

### <a name="parameters"></a>Paramètres

*bShow (en)*<br/>
[dans] Précise si le bouton est visible. Si ce paramètre est VRAI, le bouton est visible. Sinon, le bouton n’est pas visible.

### <a name="remarks"></a>Notes

Cette méthode étend la mise en œuvre de la classe de base ( [CMFCToolBarButton::OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow)) en affichant le bouton si *bShow* est VRAI. Sinon, cette méthode cache le bouton.

## <a name="cmfctoolbardatetimectrlonsize"></a><a name="onsize"></a>CMFCToolBarDateTimeCtrl::OnSize

Appelé par le cadre lorsque la barre d’outils parente change de taille ou de position, ce changement provoque le bouton de changer de taille.

```
virtual void OnSize(int iSize);
```

### <a name="parameters"></a>Paramètres

*iSize (en)*<br/>
[dans] La nouvelle largeur du bouton, en pixels.

### <a name="remarks"></a>Notes

Cette méthode remplace l’implémentation par défaut de classe ( [CMFCToolBarButton::OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize)) en mettant à jour la taille et la position de l’objet interne. `CMFCToolBarDateTimeCtrlImpl`

## <a name="cmfctoolbardatetimectrlonupdatetooltip"></a><a name="onupdatetooltip"></a>CMFCToolBarDateTimeCtrl::OnUpdateToolTip

Appelé par le cadre lorsque la barre d’outils parent met à jour son texte tooltip.

```
virtual BOOL OnUpdateToolTip(
    CWnd* pWndParent,
    int iButtonIndex,
    CToolTipCtrl& wndToolTip,
    CString& str);
```

### <a name="parameters"></a>Paramètres

*pWndParent*<br/>
[dans] La fenêtre parent.

*iButtonIndex*<br/>
[dans] L’index zéro du bouton dans la collection de boutons parent.

*wndToolTip*<br/>
[dans] Le contrôle qui affiche le texte de l’outiltip.

*Str*<br/>
[out] Un `CString` objet qui reçoit le texte de pointe d’outil mis à jour.

### <a name="return-value"></a>Valeur de retour

Nonzero si la méthode met à jour le texte tooltip; sinon 0.

### <a name="remarks"></a>Notes

Cette méthode étend la mise en œuvre de la classe de base ( [CMFCToolBarButton::OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip)) en affichant le texte de pointe d’outil qui est associé au bouton. Si le bouton n’est pas amarré horizontalement, cette méthode ne fait rien et renvoie FALSE.

## <a name="cmfctoolbardatetimectrlsettime"></a><a name="settime"></a>CMFCToolBarDateTimeCtrl::SetTime

Définit l’heure et la date dans le contrôle du cueilleur de temps.

```
BOOL SetTime(const COleDateTime& timeNew);
BOOL SetTime(const CTime* timeNew);
BOOL SetTime(LPSYSTEMTIME pTimeNew=NULL);
```

### <a name="parameters"></a>Paramètres

*timeNew*<br/>
[dans] Dans la première version, une référence à un objet [COleDateTime Class](../../atl-mfc-shared/reference/coledatetime-class.md) qui contient l’heure à laquelle le contrôle sera défini. Dans la deuxième version, un pointeur vers un objet [CTime](../../atl-mfc-shared/reference/ctime-class.md) qui contient l’heure à laquelle le contrôle sera réglé.

*pTimeNew*<br/>
[dans] Un pointeur vers la structure [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) qui contient le temps auquel le contrôle sera réglé.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Définit l’heure dans un contrôle de cueilleur de date et d’heure en appelant [CDateTimeCtrl: :SetTime](../../mfc/reference/cdatetimectrl-class.md#settime).

## <a name="cmfctoolbardatetimectrlsettimeall"></a><a name="settimeall"></a>CMFCToolBarDateTimeCtrl::SetTimeAll

Définit l’heure et la date dans tous les cas du contrôle du cueilleur de temps qui ont une pièce d’identité de commande spécifiée.

```
static BOOL SetTimeAll(
    UINT uiCmd,
    const COleDateTime& timeNew);

static BOOL SetTimeAll(
    UINT uiCmd,
    const CTime* pTimeNew);

static BOOL SetTimeAll(
    UINT uiCmd,
    LPSYSTEMTIME pTimeNew=NULL);
```

### <a name="parameters"></a>Paramètres

*uiCmd uiCmd*<br/>
[dans] Spécifie l’ID de commande d’un bouton de barre d’outils.

*timeNew*<br/>
[dans] Dans la première version, un objet [COleDateTime Class](../../atl-mfc-shared/reference/coledatetime-class.md) qui contient l’heure à laquelle le contrôle sera défini. Dans la deuxième version, un pointeur vers un objet [CTime](../../atl-mfc-shared/reference/ctime-class.md) qui contient l’heure à laquelle le contrôle sera réglé.

*pTimeNew*<br/>
[dans] Un pointeur vers la structure [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) qui contient le temps auquel le contrôle sera réglé.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Recherche un bouton de barre d’outils avec l’ID de commande spécifié et définit l’heure dans un contrôle de cueilleur de date et d’heure en appelant [CMFCToolBarDateTimeCtrl:SetTime](#settime).

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarButton, classe](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[Procédure pas à pas : placement de contrôles dans les barres d'outils](../../mfc/walkthrough-putting-controls-on-toolbars.md)
