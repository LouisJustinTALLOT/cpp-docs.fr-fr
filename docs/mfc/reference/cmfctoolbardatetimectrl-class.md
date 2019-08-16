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
ms.openlocfilehash: 7ab6a240a403e70446ebc1860474f6cb9e1d71e3
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504765"
---
# <a name="cmfctoolbardatetimectrl-class"></a>CMFCToolBarDateTimeCtrl, classe

Bouton de barre d’outils qui contient un contrôle de sélecteur de date et d’heure.

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
|[CMFCToolBarDateTimeCtrl::CanBeStretched](#canbestretched)|Spécifie si un utilisateur peut étirer le bouton pendant la personnalisation. (Substitue [CMFCToolBarButton:: CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched).)|
|[CMFCToolBarDateTimeCtrl::CopyFrom](#copyfrom)|Copie les propriétés d’un autre bouton de barre d’outils sur le bouton actuel. (Substitue [CMFCToolBarButton:: CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom).)|
|`CMFCToolBarDateTimeCtrl::DuplicateData`|Réservé à un usage ultérieur.|
|[CMFCToolBarButton::ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)|Copie le texte du bouton de barre d’outils dans un menu.|
|`CMFCToolBarDateTimeCtrl::CreateObject`|Utilisé par l'infrastructure pour créer une instance dynamique de ce type de classe.|
|[CMFCToolBarDateTimeCtrl::GetByCmd](#getbycmd)|Récupère le premier `CMFCToolBarDateTimeCtrl` objet de l’application qui a l’ID de commande spécifié.|
|[CMFCToolBarDateTimeCtrl::GetDateTimeCtrl](#getdatetimectrl)|Retourne un pointeur vers le contrôle de sélecteur de date et d’heure.|
|[CMFCToolBarDateTimeCtrl::GetHwnd](#gethwnd)|Récupère le handle de fenêtre associé au bouton de barre d’outils. (Substitue [CMFCToolBarButton:: GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd).)|
|`CMFCToolBarDateTimeCtrl::GetThisClass`|Utilisé par l’infrastructure pour obtenir un pointeur vers l’objet [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) associé à ce type de classe.|
|[CMFCToolBarDateTimeCtrl::GetTime](#gettime)|Obtient l’heure sélectionnée à partir d’un contrôle de sélecteur de date et d’heure et la place dans une structure [SystemTime](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) spécifiée.|
|[CMFCToolBarDateTimeCtrl::GetTimeAll](#gettimeall)|Retourne l’heure sélectionnée à partir du bouton de contrôle de sélecteur d’heure qui a un ID de commande spécifié.|
|[CMFCToolBarDateTimeCtrl::HaveHotBorder](#havehotborder)|Détermine si une bordure du bouton s’affiche lorsqu’un utilisateur sélectionne le bouton. (Substitue [CMFCToolBarButton:: HaveHotBorder](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder).)|
|[CMFCToolBarDateTimeCtrl::NotifyCommand](#notifycommand)|Spécifie si le bouton traite le message [WM_COMMAND](/windows/win32/menurc/wm-command) . (Substitue [CMFCToolBarButton:: NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand).)|
|[CMFCToolBarDateTimeCtrl::OnAddToCustomizePage](#onaddtocustomizepage)|Appelée par l’infrastructure quand le bouton est ajouté à une boîte de dialogue **personnaliser** . (Substitue [CMFCToolBarButton:: OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage).)|
|`CMFCToolBarDateTimeCtrl::OnCalculateSize`|Appelé par l’infrastructure pour calculer la taille du bouton pour le contexte de périphérique et l’état d’ancrage spécifiés. (Substitue [CMFCToolBarButton:: OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize).)|
|[CMFCToolBarDateTimeCtrl::OnChangeParentWnd](#onchangeparentwnd)|Appelée par l’infrastructure quand le bouton est inséré dans une nouvelle barre d’outils. (Substitue [CMFCToolBarButton:: OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd).)|
|[CMFCToolBarDateTimeCtrl::OnClick](#onclick)|Appelée par l’infrastructure quand l’utilisateur clique sur le contrôle. (Substitue [CMFCToolBarButton:: OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick).)|
|[CMFCToolBarDateTimeCtrl::OnCtlColor](#onctlcolor)|Appelé par le Framework lorsque la barre d’outils parente gère un message WM_CTLCOLOR. (Substitue [CMFCToolBarButton:: OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor).)|
|`CMFCToolBarDateTimeCtrl::OnDraw`|Appelé par l’infrastructure pour dessiner le bouton à l’aide des styles et options spécifiés. (Substitue [CMFCToolBarButton:: OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw).)|
|`CMFCToolBarDateTimeCtrl::OnDrawOnCustomizeList`|Appelée par l’infrastructure pour dessiner le bouton dans le volet **commandes** de la boîte de dialogue **personnaliser** . (Substitue [CMFCToolBarButton:: OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist).)|
|[CMFCToolBarDateTimeCtrl::OnGlobalFontsChanged](#onglobalfontschanged)|Appelé par le Framework lorsque la police globale a changé. (Substitue [CMFCToolBarButton:: OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged).)|
|[CMFCToolBarDateTimeCtrl::OnMove](#onmove)|Appelé par le Framework lorsque la barre d’outils parente se déplace. (Substitue [CMFCToolBarButton:: OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove).)|
|[CMFCToolBarDateTimeCtrl::OnShow](#onshow)|Appelé par le Framework lorsque le bouton devient visible ou invisible. (Substitue [CMFCToolBarButton:: onshow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow).)|
|`CMFCToolBarDateTimeCtrl::OnSize`|Appelé par l’infrastructure quand la barre d’outils parente modifie sa taille ou sa position et que cette modification entraîne la modification de la taille du bouton. (Substitue [CMFCToolBarButton:: OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize).)|
|[CMFCToolBarDateTimeCtrl::OnUpdateToolTip](#onupdatetooltip)|Appelé par le Framework lorsque la barre d’outils parente met à jour son texte d’info-bulle. (Substitue [CMFCToolBarButton:: OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip).)|
|`CMFCToolBarDateTimeCtrl::Serialize`|Lit cet objet à partir d’une archive ou l’écrit dans une archive, (Substitue [CMFCToolBarButton:: Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize).)|
|`CMFCToolBarDateTimeCtrl::SetStyle`|Définit le style du bouton de la barre d’outils. (Substitue [CMFCToolBarButton:: SetStyle](../../mfc/reference/cmfctoolbarbutton-class.md#setstyle).)|
|[CMFCToolBarDateTimeCtrl::SetTime](#settime)|Définit la date et l’heure dans le contrôle de sélecteur d’heure.|
|[CMFCToolBarDateTimeCtrl::SetTimeAll](#settimeall)|Définit la date et l’heure dans toutes les instances du contrôle de sélecteur d’heure qui ont un ID de commande spécifié.|

## <a name="remarks"></a>Notes

Pour obtenir un exemple d’utilisation d’un contrôle de sélecteur de date et d’heure, consultez l’exemple de projet ToolbarDateTimePicker. Pour plus d’informations sur l’ajout de boutons de contrôle à des [barres d’outils, consultez Procédure pas à pas: Placer des contrôles sur des](../../mfc/walkthrough-putting-controls-on-toolbars.md)barres d’outils.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarDateTimeCtrl](../../mfc/reference/cmfctoolbardatetimectrl-class.md)

## <a name="requirements"></a>Configuration requise

**En-tête:** afxtoolbardatetimectrl. h

##  <a name="canbestretched"></a>  CMFCToolBarDateTimeCtrl::CanBeStretched

Spécifie si un utilisateur peut étirer le bouton pendant la personnalisation.

```
virtual BOOL CanBeStretched() const;
```

### <a name="return-value"></a>Valeur de retour

Cette méthode retourne TRUE.

### <a name="remarks"></a>Notes

Par défaut, l’infrastructure ne permet pas à l’utilisateur d’étirer un bouton de barre d’outils pendant la personnalisation. Cette méthode étend l’implémentation de la classe de base ( [CMFCToolBarButton:: CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched)) en permettant à l’utilisateur d’étirer un bouton de barre d’outils de date et d’heure pendant la personnalisation.

##  <a name="cmfctoolbardatetimectrl"></a>  CMFCToolBarDateTimeCtrl::CMFCToolBarDateTimeCtrl

Crée et initialise un objet [CMFCToolBarDateTimeCtrl](../../mfc/reference/cmfctoolbardatetimectrl-class.md) .

```
CMFCToolBarDateTimeCtrl(
    UINT uiID,
    int iImage,
    DWORD dwStyle=0,
    int iWidth=0);
```

### <a name="parameters"></a>Paramètres

*uiID*<br/>
dans ID du contrôle.

*iImage*<br/>
dans Index de l’image dans l' `CMFCToolBarImages` objet de la barre d’outils.

*dwStyle*<br/>
dans Style de la `CMFCToolBarDateTimeCtrlImpl` fenêtre créée lorsqu’un utilisateur clique sur le bouton.

*iWidth*<br/>
dans Largeur du contrôle, en pixels.

### <a name="remarks"></a>Notes

Cet objet est initialisé à la date et à l’heure système. Le style de fenêtre de l' `CMFCToolBarDateTimeCtrlImpl` objet interne comprend le paramètre *dwStyle* et les styles WS_CHILD et WS_VISIBLE. Vous ne pouvez pas modifier ces styles `CMFCToolBarDateTimeCtrl::SetStyle`à l’aide de. Utilisez `SetStyle` pour modifier le style `CMFCToolBarDateTimeCtrl` du contrôle.

### <a name="example"></a>Exemples

L’exemple suivant montre comment construire un objet de la `CMFCToolBarDateTimeCtrl` classe. Cet extrait de code fait partie de l' [exemple de sélecteur de date et d’heure de la barre d’outils](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_ToolbarDateTimePicker#1](../../mfc/reference/codesnippet/cpp/cmfctoolbardatetimectrl-class_1.cpp)]

##  <a name="copyfrom"></a>  CMFCToolBarDateTimeCtrl::CopyFrom

Copie les propriétés d’un autre bouton de barre d’outils sur le bouton actuel.

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>Paramètres

*src*<br/>
dans Référence au bouton source à partir duquel effectuer la copie.

### <a name="remarks"></a>Notes

Appelez cette méthode pour copier un autre bouton de barre d’outils sur ce bouton de barre d’outils. *src* doit être de type `CMFCToolBarDateTimeCtrl`.

##  <a name="exporttomenubutton"></a>  CMFCToolBarDateTimeCtrl::ExportToMenuButton

Copie le texte du bouton de barre d’outils dans un menu.

```
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;
```

### <a name="parameters"></a>Paramètres

*menuButton*<br/>
dans Référence au bouton de menu cible.

### <a name="return-value"></a>Valeur de retour

Cette méthode retourne TRUE.

### <a name="remarks"></a>Notes

Cette méthode remplace l’implémentation de la classe de base ( [CMFCToolBarButton:: ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)) en chargeant la ressource de chaîne associée à l’ID de commande du contrôle. Pour plus d’informations sur les ressources de type chaîne, consultez [CStringT:: LoadString](../../atl-mfc-shared/reference/cstringt-class.md#loadstring).

##  <a name="getbycmd"></a>  CMFCToolBarDateTimeCtrl::GetByCmd

Récupère le premier `CMFCToolBarDateTimeCtrl` objet de l’application qui a l’ID de commande spécifié.

```
static CMFCToolBarDateTimeCtrl* __stdcall GetByCmd(UINT uiCmd);
```

### <a name="parameters"></a>Paramètres

*uiCmd*<br/>
dans ID de commande du bouton à récupérer.

### <a name="return-value"></a>Valeur de retour

Premier `CMFCToolBarDateTimeCtrl` objet de l’application qui a l’ID de commande spécifié, ou null si aucun `CMFCToolBarDateTimeCtrl` objet n’a l’ID de commande spécifié.

### <a name="remarks"></a>Notes

Cette méthode utilitaire partagée est utilisée par les méthodes telles que [CMFCToolBarDateTimeCtrl:: SetTimeAll](#settimeall) et [CMFCToolBarDateTimeCtrl:: GetTimeAll](#gettimeall) pour définir ou obtenir la date et l’heure de toutes les instances du contrôle de sélecteur d’heure qui ont un ID de commande spécifié.

##  <a name="getdatetimectrl"></a>  CMFCToolBarDateTimeCtrl::GetDateTimeCtrl

Retourne un pointeur vers le contrôle de sélecteur de date et d’heure.

```
CDateTimeCtrl* GetDateTimeCtrl() const;
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers le contrôle de sélecteur de date et d’heure; ou NULL si le contrôle n’existe pas.

### <a name="remarks"></a>Notes

La `CMFCToolBarDateTimeCtrl` classe initialise les `m_pWndDateTime` données membres lorsque vous insérez un `CMFCToolBarDateTimeCtrl` objet dans une barre d’outils.

##  <a name="gethwnd"></a>  CMFCToolBarDateTimeCtrl::GetHwnd

Récupère le handle de fenêtre associé au bouton de barre d’outils.

```
virtual HWND GetHwnd();
```

### <a name="return-value"></a>Valeur de retour

Handle de fenêtre associé au bouton de la barre d’outils date et heure.

### <a name="remarks"></a>Notes

Cette méthode remplace la méthode [CMFCToolBarButton:: GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd) .

##  <a name="gettime"></a>  CMFCToolBarDateTimeCtrl::GetTime

Obtient l’heure sélectionnée à partir du contrôle de sélecteur de date et d’heure associé et la place dans une structure [SystemTime](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) spécifiée.

```
BOOL GetTime(COleDateTime& timeDest) const;
DWORD GetTime(CTime& timeDest) const;
DWORD GetTime(LPSYSTEMTIME pTimeDest) const;
```

### <a name="parameters"></a>Paramètres

*timeDest*<br/>
à Dans la première surcharge, objet de [classe COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) qui recevra les informations d’heure système. Dans la deuxième surcharge, objet [ctime](../../atl-mfc-shared/reference/ctime-class.md) qui recevra les informations d’heure système.

*pTimeDest*<br/>
à Pointeur vers la structure [SystemTime](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) pour recevoir les informations d’heure système. Ne doit pas avoir la valeur NULL.

### <a name="return-value"></a>Valeur de retour

Dans la première surcharge, différente de zéro si l’heure est correctement écrite dans l’objet de [classe COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) ; Sinon, 0. Dans les deuxième et troisième surcharges, la valeur de retour est une valeur DWORD qui est égale au membre dwFlag défini dans la structure [NMDATETIMECHANGE](/windows/win32/api/commctrl/ns-commctrl-nmdatetimechange) .

### <a name="remarks"></a>Notes

La méthode définit le membre de structure [NMDATETIMECHANGE](/windows/win32/api/commctrl/ns-commctrl-nmdatetimechange) dwFlags pour indiquer si le sélecteur de date et d’heure est défini sur une date et une heure. Si la valeur est égale à `no date` GDT_NONE, le contrôle a la valeur Status et utilise le style DTS_SHOWNONE. Si la valeur retournée est égale à GDT_VALID, l’heure système est stockée dans l’emplacement de destination.

##  <a name="gettimeall"></a>  CMFCToolBarDateTimeCtrl::GetTimeAll

Retourne l’heure sélectionnée par l’utilisateur à partir du bouton de contrôle de sélecteur d’heure qui a un ID de commande spécifié.

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

*uiCmd*<br/>
dans Spécifie l’ID de commande d’un bouton de barre d’outils.

*timeDest*<br/>
à Dans la première surcharge, objet de [classe COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) qui recevra les informations d’heure système. Dans la deuxième surcharge, objet [ctime](../../atl-mfc-shared/reference/ctime-class.md) qui recevra les informations d’heure système.

*pTimeDest*<br/>
à Pointeur vers la structure [SystemTime](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) pour recevoir les informations d’heure système. Ne doit pas avoir la valeur NULL.

### <a name="return-value"></a>Valeur de retour

Si le Framework ne trouve pas de bouton de barre d’outils correspondant à l’ID de commande *uiCmd*, la valeur de retour est égale à zéro dans la première surcharge et GDT_NONE dans les autres surcharges. Si le bouton de barre d’outils est trouvé, la valeur de retour est la même que la valeur de retour d’un appel à [CMFCToolBarDateTimeCtrl:: getTime](#gettime) sur ce bouton. Une valeur de retour de zéro ou de GDT_NONE peut se produire lorsque le bouton est trouvé, ce qui indique `GetTime` que l’appel à n’a pas retourné de date valide pour une autre raison.

### <a name="remarks"></a>Notes

Cette méthode recherche un bouton de barre d’outils avec l’ID de commande spécifié et appelle la méthode [CMFCToolBarDateTimeCtrl:: getTime](#gettime) sur ce bouton.

##  <a name="havehotborder"></a>  CMFCToolBarDateTimeCtrl::HaveHotBorder

Détermine si une bordure du bouton s’affiche lorsqu’un utilisateur sélectionne le bouton.

```
virtual BOOL HaveHotBorder() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si un bouton affiche sa bordure lorsqu’il est sélectionné; Sinon, 0.

### <a name="remarks"></a>Notes

Cette méthode retourne une valeur différente de zéro si le contrôle est visible.

##  <a name="notifycommand"></a>  CMFCToolBarDateTimeCtrl::NotifyCommand

Spécifie si le bouton traite le message [WM_COMMAND](/windows/win32/menurc/wm-command) .

```
virtual BOOL NotifyCommand(int iNotifyCode);
```

### <a name="parameters"></a>Paramètres

*iNotifyCode*<br/>
dans Message de notification associé à la commande.

### <a name="return-value"></a>Valeur de retour

TRUE si le bouton traite le message WM_COMMAND, ou FALSe pour indiquer que le message doit être géré par la barre d’outils parente.

### <a name="remarks"></a>Notes

L’infrastructure appelle cette méthode lorsqu’il est sur le paragraphe d’envoyer un message [WM_COMMAND](/windows/win32/menurc/wm-command) à la fenêtre parente.

Cette méthode étend l’implémentation de la classe de base ( [CMFCToolBarButton:: NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand)) en traitant la notification [DTN_DATETIMECHANGE](/windows/win32/Controls/dtn-datetimechange) . Il met à jour l’état de temps interne et met à jour la propriété Time de `CMFCToolBarDateTimeCtrl` tous les objets avec le même ID de commande.

##  <a name="onaddtocustomizepage"></a>  CMFCToolBarDateTimeCtrl::OnAddToCustomizePage

Appelée par l’infrastructure quand le bouton est ajouté à une boîte de dialogue **personnaliser** .

```
virtual void OnAddToCustomizePage();
```

### <a name="remarks"></a>Notes

Cette méthode étend l’implémentation de la classe de base, [CMFCToolBarButton:: OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage), en copiant les propriétés à partir du premier contrôle de date et d’heure dans une barre d’outils qui a le même ID de commande que cet objet. Cette méthode ne fait rien si aucune barre d’outils n’a de contrôle de date et d’heure qui a le même ID de commande que cet objet.

Pour plus d’informations sur la boîte de dialogue **personnaliser** , consultez [CMFCToolBarsCustomizeDialog, classe](../../mfc/reference/cmfctoolbarscustomizedialog-class.md).

##  <a name="onchangeparentwnd"></a>  CMFCToolBarDateTimeCtrl::OnChangeParentWnd

Appelée par l’infrastructure quand le bouton est inséré dans une nouvelle barre d’outils.

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>Paramètres

*pWndParent*<br/>
dans Nouvelle fenêtre parente.

### <a name="remarks"></a>Notes

Cette méthode remplace l’implémentation de la classe de base ( [CMFCToolBarButton:: OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)) en recréant l' `CMFCToolBarDateTimeCtrlImpl` objet interne.

##  <a name="onclick"></a>  CMFCToolBarDateTimeCtrl::OnClick

Appelée par l’infrastructure quand l’utilisateur clique sur le contrôle.

```
virtual BOOL OnClick(
    CWnd* pWnd,
    BOOL bDelay = TRUE);
```

### <a name="parameters"></a>Paramètres

*pWnd*<br/>
dans Inutilisé.

*bDelay*<br/>
dans Inutilisé.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le bouton traite le message Click; Sinon, 0.

### <a name="remarks"></a>Notes

Cette méthode remplace l’implémentation de la classe de base, [CMFCToolBarButton:: OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick), en retournant une valeur différente de zéro `CMFCToolBarDateTimeCtrlImpl` si l’objet interne est visible.

##  <a name="onctlcolor"></a>  CMFCToolBarDateTimeCtrl::OnCtlColor

Appelé par le Framework lorsque la barre d’outils parente gère un message WM_CTLCOLOR.

```
virtual HBRUSH OnCtlColor(
    CDC* pDC,
    UINT nCtlColor);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
dans Contexte de périphérique qui affiche le bouton.

*nCtlColor*<br/>
dans Inutilisé.

### <a name="return-value"></a>Valeur de retour

Handle du pinceau global utilisé par l’infrastructure pour peindre l’arrière-plan du bouton.

### <a name="remarks"></a>Notes

Cette méthode remplace l’implémentation de la classe de base, [CMFCToolBarButton:: OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor), en définissant les couleurs de texte et d’arrière-plan du contexte de périphérique fourni sur le texte global et les couleurs d’arrière-plan, respectivement.

Pour plus d’informations sur les options globales qui sont disponibles pour votre application, consultez [structure AFX_GLOBAL_DATA](../../mfc/reference/afx-global-data-structure.md).

##  <a name="onglobalfontschanged"></a>  CMFCToolBarDateTimeCtrl::OnGlobalFontsChanged

Appelé par le Framework lorsque la police globale a changé.

```
virtual void OnGlobalFontsChanged();
```

### <a name="remarks"></a>Notes

Cette méthode étend l’implémentation de la classe de base ( [CMFCToolBarButton:: OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged)) en remplaçant la police du contrôle par celle de la police globale.

Pour plus d’informations sur les options globales qui sont disponibles pour votre application, consultez [structure AFX_GLOBAL_DATA](../../mfc/reference/afx-global-data-structure.md).

##  <a name="onmove"></a>  CMFCToolBarDateTimeCtrl::OnMove

Appelé par le Framework lorsque la barre d’outils parente se déplace.

```
virtual void OnMove();
```

### <a name="remarks"></a>Notes

Cette méthode remplace l’implémentation de classe par défaut ( [CMFCToolBarButton:: OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove)) en mettant à jour la position de l' `CMFCToolBarDateTimeCtrlImpl` objet interne.

##  <a name="onshow"></a>  CMFCToolBarDateTimeCtrl::OnShow

Appelé par le Framework lorsque le bouton devient visible ou invisible.

```
virtual void OnShow(BOOL bShow);
```

### <a name="parameters"></a>Paramètres

*bShow*<br/>
dans Spécifie si le bouton est visible. Si ce paramètre a la valeur TRUE, le bouton est visible. Dans le cas contraire, le bouton n’est pas visible.

### <a name="remarks"></a>Notes

Cette méthode étend l’implémentation de la classe de base ( [CMFCToolBarButton:: onshow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow)) en affichant le bouton si *bShow* a la valeur true. Sinon, cette méthode masque le bouton.

##  <a name="onsize"></a>  CMFCToolBarDateTimeCtrl::OnSize

Appelé par l’infrastructure quand la barre d’outils parente modifie sa taille ou sa position et que cette modification entraîne la modification de la taille du bouton.

```
virtual void OnSize(int iSize);
```

### <a name="parameters"></a>Paramètres

*iSize*<br/>
dans Nouvelle largeur du bouton, en pixels.

### <a name="remarks"></a>Notes

Cette méthode remplace l’implémentation de classe par défaut ( [CMFCToolBarButton:: OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize)) en mettant à jour la taille et la position de `CMFCToolBarDateTimeCtrlImpl` l’objet interne.

##  <a name="onupdatetooltip"></a>  CMFCToolBarDateTimeCtrl::OnUpdateToolTip

Appelé par le Framework lorsque la barre d’outils parente met à jour son texte d’info-bulle.

```
virtual BOOL OnUpdateToolTip(
    CWnd* pWndParent,
    int iButtonIndex,
    CToolTipCtrl& wndToolTip,
    CString& str);
```

### <a name="parameters"></a>Paramètres

*pWndParent*<br/>
dans Fenêtre parente.

*iButtonIndex*<br/>
dans Index de base zéro du bouton dans la collection de boutons parents.

*wndToolTip*<br/>
dans Contrôle qui affiche le texte d’info-bulle.

*str*<br/>
à `CString` Objet qui reçoit le texte info-bulle mis à jour.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la méthode met à jour le texte de l’info-bulle; Sinon, 0.

### <a name="remarks"></a>Notes

Cette méthode étend l’implémentation de la classe de base ( [CMFCToolBarButton:: OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip)) en affichant le texte d’info-bulle associé au bouton. Si le bouton n’est pas ancré horizontalement, cette méthode ne fait rien et retourne FALSe.

##  <a name="settime"></a>  CMFCToolBarDateTimeCtrl::SetTime

Définit la date et l’heure dans le contrôle de sélecteur d’heure.

```
BOOL SetTime(const COleDateTime& timeNew);
BOOL SetTime(const CTime* timeNew);
BOOL SetTime(LPSYSTEMTIME pTimeNew=NULL);
```

### <a name="parameters"></a>Paramètres

*timeNew*<br/>
dans Dans la première version, référence à un objet de [classe COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) qui contient l’heure à laquelle le contrôle sera défini. Dans la deuxième version, pointeur vers un objet [ctime](../../atl-mfc-shared/reference/ctime-class.md) qui contient l’heure à laquelle le contrôle sera défini.

*pTimeNew*<br/>
dans Pointeur vers la structure [SystemTime](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) qui contient l’heure à laquelle le contrôle doit être défini.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Définit l’heure dans un contrôle de sélecteur de date et d’heure en appelant [CDateTimeCtrl:: setTime](../../mfc/reference/cdatetimectrl-class.md#settime).

##  <a name="settimeall"></a>  CMFCToolBarDateTimeCtrl::SetTimeAll

Définit la date et l’heure dans toutes les instances du contrôle de sélecteur d’heure qui ont un ID de commande spécifié.

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

*uiCmd*<br/>
dans Spécifie l’ID de commande d’un bouton de barre d’outils.

*timeNew*<br/>
dans Dans la première version, objet de [classe COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) qui contient l’heure à laquelle le contrôle sera défini. Dans la deuxième version, pointeur vers un objet [ctime](../../atl-mfc-shared/reference/ctime-class.md) qui contient l’heure à laquelle le contrôle sera défini.

*pTimeNew*<br/>
dans Pointeur vers la structure [SystemTime](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) qui contient l’heure à laquelle le contrôle doit être défini.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Recherche un bouton de barre d’outils avec l’ID de commande spécifié et définit l’heure dans un contrôle de sélecteur de date et d’heure en appelant [CMFCToolBarDateTimeCtrl:: setTime](#settime).

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarButton, classe](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[Procédure pas à pas : Placement de contrôles dans les barres d’outils](../../mfc/walkthrough-putting-controls-on-toolbars.md)
