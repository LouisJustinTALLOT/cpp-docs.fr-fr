---
title: Classe CView
ms.date: 11/04/2016
f1_keywords:
- CView
- AFXWIN/CView
- AFXWIN/CView::CView
- AFXWIN/CView::DoPreparePrinting
- AFXWIN/CView::GetDocument
- AFXWIN/CView::IsSelected
- AFXWIN/CView::OnDragEnter
- AFXWIN/CView::OnDragLeave
- AFXWIN/CView::OnDragOver
- AFXWIN/CView::OnDragScroll
- AFXWIN/CView::OnDrop
- AFXWIN/CView::OnDropEx
- AFXWIN/CView::OnInitialUpdate
- AFXWIN/CView::OnPrepareDC
- AFXWIN/CView::OnScroll
- AFXWIN/CView::OnScrollBy
- AFXWIN/CView::OnActivateFrame
- AFXWIN/CView::OnActivateView
- AFXWIN/CView::OnBeginPrinting
- AFXWIN/CView::OnDraw
- AFXWIN/CView::OnEndPrinting
- AFXWIN/CView::OnEndPrintPreview
- AFXWIN/CView::OnPreparePrinting
- AFXWIN/CView::OnPrint
- AFXWIN/CView::OnUpdate
helpviewer_keywords:
- CView [MFC], CView
- CView [MFC], DoPreparePrinting
- CView [MFC], GetDocument
- CView [MFC], IsSelected
- CView [MFC], OnDragEnter
- CView [MFC], OnDragLeave
- CView [MFC], OnDragOver
- CView [MFC], OnDragScroll
- CView [MFC], OnDrop
- CView [MFC], OnDropEx
- CView [MFC], OnInitialUpdate
- CView [MFC], OnPrepareDC
- CView [MFC], OnScroll
- CView [MFC], OnScrollBy
- CView [MFC], OnActivateFrame
- CView [MFC], OnActivateView
- CView [MFC], OnBeginPrinting
- CView [MFC], OnDraw
- CView [MFC], OnEndPrinting
- CView [MFC], OnEndPrintPreview
- CView [MFC], OnPreparePrinting
- CView [MFC], OnPrint
- CView [MFC], OnUpdate
ms.assetid: 9cff3c56-7564-416b-b9a4-71a9254ed755
ms.openlocfilehash: 763e36b0736ce588e7e2aded25e50347f9e0ca70
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373199"
---
# <a name="cview-class"></a>Classe CView

Fournit les fonctionnalités de base des classes de vues définies par l'utilisateur.

## <a name="syntax"></a>Syntaxe

```
class AFX_NOVTABLE CView : public CWnd
```

## <a name="members"></a>Membres

### <a name="protected-constructors"></a>Constructeurs protégés

|Nom|Description|
|----------|-----------------|
|[CView::CView](#cview)|Construit un objet `CView`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CView::DoPreparePrinting](#doprepareprinting)|Affiche la boîte de dialogue d’impression et crée le contexte de l’appareil d’imprimante ; appeler lorsque vous `OnPreparePrinting` dépassez la fonction de membre.|
|[CView::GetDocument](#getdocument)|Retourne le document associé à la vue.|
|[CView::IsSelected](#isselected)|Teste si un élément de document est sélectionné. Nécessaire pour le soutien OLE.|
|[CView::OnDragEnter](#ondragenter)|Appelé lorsqu’un élément est d’abord traîné dans la région de drag-and-drop d’une vue.|
|[CView::OnDragLeave](#ondragleave)|Appelé quand un objet traîné quitte la région de drag-and-drop d’une vue.|
|[CView::OnDragOver](#ondragover)|Appelé quand un élément est traîné sur la région de drag-and-drop d’une vue.|
|[CView::OnDragScroll](#ondragscroll)|Appelé pour déterminer si le curseur est traîné dans la région de défilement de la fenêtre.|
|[CView::OnDrop](#ondrop)|Appelé lorsqu’un article a été déposé dans la région de drag-and-drop d’une vue, gestionnaire par défaut.|
|[CView::OnDropEx](#ondropex)|Appelé lorsqu’un article a été déposé dans la région de drag-and-drop d’une vue, gestionnaire principal.|
|[CView::OnInitialUpdate](#oninitialupdate)|Appelé après une vue est d’abord attaché à un document.|
|[CView::OnPrepareDC](#onpreparedc)|Appelé avant `OnDraw` que la fonction de `OnPrint` membre soit appelée pour l’affichage de l’écran ou la fonction membre est appelée pour l’impression ou l’aperçu d’impression.|
|[CView::OnScroll](#onscroll)|Appelé lorsque les éléments OLE sont traînés au-delà des frontières de la vue.|
|[CView::OnScrollBy](#onscrollby)|Appelé lorsqu’une vue contenant des éléments OLE actifs sur place est défilement.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CView::OnActivateFrame](#onactivateframe)|Appelé lorsque la fenêtre de cadre contenant la vue est activée ou désactivée.|
|[CView::OnActivateView](#onactivateview)|Appelé quand une vue est activée.|
|[CView::OnBeginPrinting](#onbeginprinting)|Appelé quand un travail d’impression commence; remplacer l’attribution des ressources d’interface graphique (GDI).|
|[CView::OnDraw](#ondraw)|Appelé pour rendre une image du document pour l’affichage de l’écran, l’impression ou l’aperçu d’impression. Mise en œuvre requise.|
|[CView::OnEndPrinting](#onendprinting)|Appelé quand un travail d’impression se termine; remplacer les ressources GDI.|
|[CView::OnEndPrintPreview](#onendprintpreview)|Appelé lorsque le mode de prévisualisation est sorti.|
|[CView::OnPreparePrinting](#onprepareprinting)|Appelé avant qu’un document soit imprimé ou prévisualisé; remplacer pour initialiser la boîte de dialogue d’impression.|
|[CView::OnPrint](#onprint)|Appelé pour imprimer ou prévisualiser une page du document.|
|[CView::OnUpdate](#onupdate)|Appelé à aviser un point de vue que son document a été modifié.|

## <a name="remarks"></a>Notes

Une vue est jointe à un document et agit comme intermédiaire entre le document et l’utilisateur : la vue rend une image du document sur l’écran ou l’imprimante et interprète l’entrée de l’utilisateur comme opérations sur le document.

Une vue est un enfant d’une fenêtre de cadre. Plus d’une vue peut partager une fenêtre de cadre, comme dans le cas d’une fenêtre de splitter. La relation entre une classe de vue, une classe de `CDocTemplate` fenêtre de cadre et une classe de documents est établie par un objet. Lorsque l’utilisateur ouvre une nouvelle fenêtre ou divise une fenêtre existante, le cadre construit une nouvelle vue et l’attache au document.

Une vue peut être jointe à un seul document, mais un document peut avoir plusieurs vues qui y sont immédiatement jointes — par exemple, si le document est affiché dans une fenêtre de séparation ou dans plusieurs fenêtres pour enfants dans une application d’interface de document multiple (MDI). Votre application peut prendre en charge différents types de vues pour un type de document donné; par exemple, un programme de traitement de texte peut fournir à la fois une vue texte complète d’un document et une vue d’ensemble qui ne montre que les rubriques de section. Ces différents types de vues peuvent être placés dans des fenêtres à ossature séparées ou dans des vitres séparées d’une seule fenêtre de cadre si vous utilisez une fenêtre de splitter.

Une vue peut être responsable de la manipulation de plusieurs types d’entrées, tels que l’entrée du clavier, l’entrée de la souris ou l’entrée par le biais de drag-and-drop, ainsi que des commandes à partir de menus, barres d’outils, ou barres de défilement. Une vue reçoit des commandes transmises par sa fenêtre de cadre. Si la vue ne gère pas une commande donnée, elle transmet la commande à son document associé. Comme toutes les cibles de commande, une vue gère les messages via une carte de message.

La vue est responsable de l’affichage et de la modification des données du document, mais pas de les stocker. Le document fournit à la vue les détails nécessaires sur ses données. Vous pouvez laisser la vue accéder directement aux membres des données du document, ou vous pouvez fournir des fonctions de membre dans la classe de documents pour que la classe de vue puisse appeler.

Lorsque les données d’un document changent, la vue responsable des modifications appelle généralement le [CDocument : : Mise](../../mfc/reference/cdocument-class.md#updateallviews) `OnUpdate` à jour De la fonction AllViews pour le document, qui informe toutes les autres vues en appelant la fonction de membre pour chacun. La mise `OnUpdate` en œuvre par défaut invalide l’ensemble de la zone client de la vue. Vous pouvez le remplacer pour invalider uniquement les régions de la zone client qui cartographient les parties modifiées du document.

Pour `CView`utiliser , en tirer une `OnDraw` classe et implémenter la fonction membre pour effectuer l’affichage de l’écran. Vous pouvez `OnDraw` également utiliser pour effectuer l’impression et l’impression aperçu. Le cadre gère la boucle d’impression pour l’impression et la prévisualisation de votre document.

Une vue gère les messages scroll-bar avec le [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll) et [CWnd::OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll) fonctions membres. Vous pouvez implémenter la manipulation de messages à `CView` barres de défilement dans ces fonctions, ou vous pouvez utiliser la classe dérivée [CScrollView](../../mfc/reference/cscrollview-class.md) pour gérer le défilement pour vous.

En `CScrollView`outre, la Microsoft Foundation Class `CView`Library propose neuf autres classes dérivées de :

- [CCtrlView](../../mfc/reference/cctrlview-class.md), une vue qui permet l’utilisation du document - voir l’architecture avec arbre, liste, et les contrôles d’édition riches.

- [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md), une vue qui affiche les enregistrements de base de données dans les contrôles de boîte de dialogue.

- [CEditView](../../mfc/reference/ceditview-class.md), une vue qui fournit un simple éditeur de texte multilinqué. Vous pouvez `CEditView` utiliser un objet comme contrôle dans une boîte de dialogue ainsi qu’une vue sur un document.

- [CFormView](../../mfc/reference/cformview-class.md), une vue défilementable qui contient des contrôles de boîte de dialogue et est basée sur une ressource de modèle de dialogue.

- [CListView](../../mfc/reference/clistview-class.md), une vue qui permet l’utilisation du document - voir l’architecture avec des contrôles de liste.

- [CRecordView](../../mfc/reference/crecordview-class.md), une vue qui affiche les enregistrements de base de données dans les contrôles de boîte de dialogue.

- [CRichEditView](../../mfc/reference/cricheditview-class.md), une vue qui permet l’utilisation de documents - voir l’architecture avec de riches contrôles d’édition.

- [CScrollView](../../mfc/reference/cscrollview-class.md), une vue qui fournit automatiquement un support de défilement.

- [CTreeView](../../mfc/reference/ctreeview-class.md), une vue qui permet l’utilisation du document - voir l’architecture avec des commandes d’arbres.

La `CView` classe dispose également d’une classe de mise en œuvre dérivée nommée `CPreviewView`, qui est utilisé par le cadre pour effectuer la prévisualisation d’impression. Cette classe fournit un support pour les fonctionnalités uniques à la fenêtre d’impression-aperçu, comme une barre d’outils, un ou double aperçu de page, et le zoom, c’est-à-dire, l’élargissement de l’image prévisualisé. Vous n’avez pas besoin d’appeler ou de remplacer l’une des fonctions des `CPreviewView`membres, sauf si vous souhaitez implémenter votre propre interface pour l’aperçu d’impression (par exemple, si vous souhaitez prendre en charge l’édition en mode aperçu d’impression). Pour plus d’informations sur l’utilisation `CView`, voir Document / Afficher [l’architecture](../../mfc/document-view-architecture.md) et [l’impression](../../mfc/printing.md). En outre, voir [Note technique 30](../../mfc/tn030-customizing-printing-and-print-preview.md) pour plus de détails sur la personnalisation de l’aperçu d’impression.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CView`

## <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="cviewcview"></a><a name="cview"></a>CView::CView

Construit un objet `CView`.

```
CView();
```

### <a name="remarks"></a>Notes

Le cadre appelle le constructeur lorsqu’une nouvelle fenêtre de cadre est créée ou qu’une fenêtre est divisée. Remplacer la fonction membre [OnInitialUpdate](#oninitialupdate) pour initialiser la vue après la mise en jointe du document.

## <a name="cviewdoprepareprinting"></a><a name="doprepareprinting"></a>CView::DoPreparePrinting

Appelez cette fonction à partir de votre remplacement [d’OnPreparePrinting](#onprepareprinting) pour invoquer la boîte de dialogue d’impression et créer un contexte d’appareil d’imprimante.

```
BOOL DoPreparePrinting(CPrintInfo* pInfo);
```

### <a name="parameters"></a>Paramètres

*pInfo (en anglais)*<br/>
Pointe vers une structure [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) qui décrit le travail d’impression actif.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’impression ou l’impression aperçu peut commencer; 0 si l’opération a été annulée.

### <a name="remarks"></a>Notes

Le comportement de cette fonction dépend du fait qu’il est `m_bPreview` appelé pour l’impression ou l’impression aperçu (spécifié par le membre du paramètre *pInfo).* Si un fichier est imprimé, cette fonction invoque la boîte de dialogue d’impression, en utilisant les valeurs de la structure [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) qui *indique le pInfo* ; après que l’utilisateur a fermé la boîte de dialogue, la fonction crée un contexte d’appareil d’imprimante basé sur les paramètres spécifiés par l’utilisateur dans la boîte de dialogue et renvoie ce contexte de périphérique à travers le paramètre *pInfo.* Ce contexte de périphérique est utilisé pour imprimer le document.

Si un fichier est prévisualisé, cette fonction crée un contexte d’imprimante à l’aide des paramètres actuels de l’imprimante ; ce contexte de périphérique est utilisé pour simuler l’imprimante pendant l’aperçu.

## <a name="cviewgetdocument"></a><a name="getdocument"></a>CView::GetDocument

Appelez cette fonction pour obtenir un pointeur sur le document de la vue.

```
CDocument* GetDocument() const;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur de l’objet [CDocument](../../mfc/reference/cdocument-class.md) associé à la vue. NULL si la vue n’est pas jointe à un document.

### <a name="remarks"></a>Notes

Cela vous permet d’appeler les fonctions des membres du document.

## <a name="cviewisselected"></a><a name="isselected"></a>CView::IsSelected

Appelé par le cadre pour vérifier si l’élément de document spécifié est sélectionné.

```
virtual BOOL IsSelected(const CObject* pDocItem) const;
```

### <a name="parameters"></a>Paramètres

*pDocItem (en)*<br/>
Indique l’élément document testé.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’élément de document spécifié est sélectionné; sinon 0.

### <a name="remarks"></a>Notes

La mise en œuvre par défaut de cette fonction renvoie FALSE. Remplacez cette fonction si vous implémentez la sélection à l’aide d’objets [CDocItem.](../../mfc/reference/cdocitem-class.md) Vous devez remplacer cette fonction si votre vue contient des éléments OLE.

## <a name="cviewonactivateframe"></a><a name="onactivateframe"></a>CView::OnActivateFrame

Appelé par le cadre lorsque la fenêtre de cadre contenant la vue est activée ou désactivée.

```
virtual void OnActivateFrame(
    UINT nState,
    CFrameWnd* pFrameWnd);
```

### <a name="parameters"></a>Paramètres

*nState (États-Unis)*<br/>
Précise si la fenêtre du cadre est activée ou désactivée. Ce peut être l’une des valeurs suivantes :

- WA_INACTIVE La fenêtre du cadre est désactivée.

- WA_ACTIVE La fenêtre de cadre est activée par une méthode autre qu’un clic de souris (par exemple, par l’utilisation de l’interface du clavier pour sélectionner la fenêtre).

- WA_CLICKACTIVE La fenêtre du cadre est activée par un clic de souris

*pFrameWnd*<br/>
Pointeur vers la fenêtre de cadre qui doit être activée.

### <a name="remarks"></a>Notes

Remplacer cette fonction de membre si vous souhaitez effectuer un traitement spécial lorsque la fenêtre de cadre associée à la vue est activée ou désactivée. Par exemple, [CFormView](../../mfc/reference/cformview-class.md) effectue ce remplacement lorsqu’il enregistre et restaure le contrôle qui a mis l’accent.

## <a name="cviewonactivateview"></a><a name="onactivateview"></a>CView::OnActivateView

Appelé par le cadre lorsqu’une vue est activée ou désactivée.

```
virtual void OnActivateView(
    BOOL bActivate,
    CView* pActivateView,
    CView* pDeactiveView);
```

### <a name="parameters"></a>Paramètres

*bActivate (en)*<br/>
Indique si la vue est activée ou désactivée.

*pActivateView (en)*<br/>
Points à l’objet de vue qui est activé.

*pDeactiveView (en)*<br/>
Points à l’objet de vue qui est désactivé.

### <a name="remarks"></a>Notes

La mise en œuvre par défaut de cette fonction met l’accent sur la vue activée. Remplacer cette fonction si vous souhaitez effectuer un traitement spécial lorsqu’une vue est activée ou désactivée. Par exemple, si vous souhaitez fournir des indices visuels spéciaux qui distinguent la vue active des vues inactives, vous examineriez le *paramètre bActivate* et mettre à jour l’apparence de la vue en conséquence.

Les paramètres *pActivateView* et *pDeactiveView* indiquent la même vue si la fenêtre de cadre principale de l’application est activée sans changement dans la vue active — par exemple, si l’accent est transféré d’une autre application à celle-ci, plutôt que d’une vue à l’autre dans l’application ou lors de la commutation entre les fenêtres de l’enfant MDI. Cela permet à une vue de réaliser sa palette, si nécessaire.

Ces paramètres diffèrent lorsque [CFrameWnd::SetActiveView](../../mfc/reference/cframewnd-class.md#setactiveview) est appelé avec une vue qui est différente de ce que [CFrameWnd::GetActiveView](../../mfc/reference/cframewnd-class.md#getactiveview) reviendrait. Cela arrive le plus souvent avec des fenêtres de splitter.

## <a name="cviewonbeginprinting"></a><a name="onbeginprinting"></a>CView::OnBeginPrinting

Appelé par l’infrastructure au début d’un travail d’impression ou d’aperçu avant impression, après que `OnPreparePrinting` a été appelé.

```
virtual void OnBeginPrinting(
    CDC* pDC,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
Pointe vers le contexte de l’imprimante.

*pInfo (en anglais)*<br/>
Pointe vers une structure [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) qui décrit le travail d’impression actif.

### <a name="remarks"></a>Notes

L’implémentation par défaut de cette fonction est sans effet. Remplacez cette fonction pour allouer des ressources GDI, telles que des stylets ou des polices, nécessaires précisément pour l’impression. Sélectionnez les objets GDI dans le contexte de périphérique de la fonction membre [OnPrint](#onprint) pour chaque page qui les utilise. Si vous utilisez le même objet d’affichage pour l’affichage et l’impression d’écran, utilisez des variables distinctes pour les ressources GDI nécessaires à chaque affichage ; vous pourrez ainsi mettre à jour l’écran pendant l’impression.

Vous pouvez aussi utiliser cette fonction pour exécuter des initialisations qui dépendent des propriétés du contexte de l’imprimante. Par exemple, le nombre de pages nécessaires à l’impression du document peut dépendre des paramètres que l’utilisateur a spécifiés dans la boîte de dialogue d’impression (comme la longueur de page). En pareil cas, vous ne pouvez pas spécifier la longueur du document dans la fonction membre [OnPreparePrinting](#onprepareprinting) comme vous le feriez normalement ; vous devez attendre que le contexte de l’imprimante ait été créé en fonction des paramètres de la boîte de dialogue. [OnBeginPrinting](#onbeginprinting) est la première fonction substituable qui donne accès à l’objet [CDC](../../mfc/reference/cdc-class.md) représentant le contexte de l’imprimante. Vous pouvez donc définir la longueur du document à partir de cette fonction. Notez que si la longueur du document n’est pas spécifiée à ce stade, aucune barre de défilement ne s’affiche pendant l’aperçu avant impression.

## <a name="cviewondragenter"></a><a name="ondragenter"></a>CView::OnDragEnter

Appelé par le cadre lorsque la souris entre pour la première fois dans la région non-scrolling de la fenêtre cible de chute.

```
virtual DROPEFFECT OnDragEnter(
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Paramètres

*pDataObject*<br/>
Points à la [COleDataObject](../../mfc/reference/coledataobject-class.md) étant traîné dans la zone de chute de la vue.

*dwKeyState (en)*<br/>
Contient l’état des touches modificateur. Il s’agit d’une combinaison de n’importe quel nombre de ce qui suit: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON, et MK_RBUTTON.

*Point*<br/>
La position actuelle de la souris par rapport à la zone client de la vue.

### <a name="return-value"></a>Valeur de retour

Une valeur du type énuméré DROPEFFECT, qui indique le type de goutte qui se produirait si l’utilisateur laissait tomber l’objet à cette position. Le type de baisse dépend généralement de l’état clé actuel indiqué par *dwKeyState*. Une cartographie standard des états clés aux valeurs DROPEFFECT est :

- DROPEFFECT_NONE L’objet de données ne peut pas être laissé tomber dans cette fenêtre.

- DROPEFFECT_LINK pour MK_CONTROL &#124; MK_SHIFT crée un lien entre l’objet et son serveur.

- DROPEFFECT_COPY pour MK_CONTROL crée une copie de l’objet abandonné.

- DROPEFFECT_MOVE pour MK_ALT crée une copie de l’objet abandonné et supprime l’objet d’origine. Il s’agit généralement de l’effet de chute par défaut, lorsque la vue peut accepter cet objet de données.

Pour plus d’informations, consultez l’échantillon [OCLIENT](../../overview/visual-cpp-samples.md)de MFC Advanced Concepts .

### <a name="remarks"></a>Notes

La mise en œuvre par défaut est de ne rien faire et de retourner DROPEFFECT_NONE.

Remplacer cette fonction pour se préparer aux appels futurs à la fonction membre [OnDragOver.](#ondragover) Toutes les données requises à partir de l’objet `OnDragOver` de données doivent être récupérées à ce moment-là pour une utilisation ultérieure dans la fonction membre. La vue doit également être mise à jour à ce moment-là pour donner à l’utilisateur des commentaires visuels. Pour plus d’informations, voir l’article [OLE glisser et laisser tomber: Implémenter un objectif de baisse](../../mfc/drag-and-drop-ole.md#implement-a-drop-target).

## <a name="cviewondragleave"></a><a name="ondragleave"></a>CView::OnDragLeave

Appelé par le cadre lors d’une opération de traînée lorsque la souris est déplacée hors de la zone de chute valide pour cette fenêtre.

```
virtual void OnDragLeave();
```

### <a name="remarks"></a>Notes

Remplacer cette fonction si la vue actuelle doit nettoyer toutes les mesures prises lors des appels [OnDragEnter](#ondragenter) ou [OnDragOver,](#ondragover) telles que la suppression de toute rétroaction visuelle de l’utilisateur pendant que l’objet a été traîné et abandonné.

## <a name="cviewondragover"></a><a name="ondragover"></a>CView::OnDragOver

Appelé par le cadre lors d’une opération de traînée lorsque la souris est déplacée au-dessus de la fenêtre cible de chute.

```
virtual DROPEFFECT OnDragOver(
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Paramètres

*pDataObject*<br/>
Indique que le [COleDataObject](../../mfc/reference/coledataobject-class.md) est traîné au-dessus de la cible de chute.

*dwKeyState (en)*<br/>
Contient l’état des touches modificateur. Il s’agit d’une combinaison de n’importe quel nombre de ce qui suit: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON, et MK_RBUTTON.

*Point*<br/>
La position actuelle de la souris par rapport à la zone client de vue.

### <a name="return-value"></a>Valeur de retour

Une valeur du type énuméré DROPEFFECT, qui indique le type de goutte qui se produirait si l’utilisateur laissait tomber l’objet à cette position. Le type de baisse dépend souvent de l’état clé actuel comme indiqué par *dwKeyState*. Une cartographie standard des états clés aux valeurs DROPEFFECT est :

- DROPEFFECT_NONE L’objet de données ne peut pas être laissé tomber dans cette fenêtre.

- DROPEFFECT_LINK pour MK_CONTROL &#124; MK_SHIFT crée un lien entre l’objet et son serveur.

- DROPEFFECT_COPY pour MK_CONTROL crée une copie de l’objet abandonné.

- DROPEFFECT_MOVE pour MK_ALT crée une copie de l’objet abandonné et supprime l’objet d’origine. Il s’agit généralement de l’effet de chute par défaut, lorsque la vue peut accepter l’objet de données.

Pour plus d’informations, consultez l’échantillon [OCLIENT](../../overview/visual-cpp-samples.md)de MFC Advanced Concepts .

### <a name="remarks"></a>Notes

La mise en œuvre par défaut est de ne rien faire et de retourner DROPEFFECT_NONE.

Remplacer cette fonction pour donner à l’utilisateur une rétroaction visuelle pendant l’opération de traînée. Étant donné que cette fonction est appelée en continu, tout code contenu dans celui-ci doit être optimisé autant que possible. Pour plus d’informations, voir l’article [OLE glisser et laisser tomber: Implémenter un objectif de baisse](../../mfc/drag-and-drop-ole.md#implement-a-drop-target).

## <a name="cviewondragscroll"></a><a name="ondragscroll"></a>CView::OnDragScroll

Appelé par le cadre avant d’appeler [OnDragEnter](#ondragenter) ou [OnDragOver](#ondragover) pour déterminer si le point est dans la région de défilement.

```
virtual DROPEFFECT OnDragScroll(
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Paramètres

*dwKeyState (en)*<br/>
Contient l’état des touches modificateur. Il s’agit d’une combinaison de n’importe quel nombre de ce qui suit: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON, et MK_RBUTTON.

*Point*<br/>
Contient l’emplacement du curseur, en pixels, par rapport à l’écran.

### <a name="return-value"></a>Valeur de retour

Une valeur du type énuméré DROPEFFECT, qui indique le type de goutte qui se produirait si l’utilisateur laissait tomber l’objet à cette position. Le type de baisse dépend généralement de l’état clé actuel indiqué par *dwKeyState*. Une cartographie standard des états clés aux valeurs DROPEFFECT est :

- DROPEFFECT_NONE L’objet de données ne peut pas être laissé tomber dans cette fenêtre.

- DROPEFFECT_LINK pour MK_CONTROL &#124; MK_SHIFT crée un lien entre l’objet et son serveur.

- DROPEFFECT_COPY pour MK_CONTROL crée une copie de l’objet abandonné.

- DROPEFFECT_MOVE pour MK_ALT crée une copie de l’objet abandonné et supprime l’objet d’origine.

- DROPEFFECT_SCROLL indique qu’une opération de drag scroll est sur le point de se produire ou se produit dans la vue cible.

Pour plus d’informations, consultez l’échantillon [OCLIENT](../../overview/visual-cpp-samples.md)de MFC Advanced Concepts .

### <a name="remarks"></a>Notes

Remplacez cette fonction lorsque vous souhaitez fournir un comportement spécial pour cet événement. La mise en œuvre par défaut fait défiler automatiquement les fenêtres lorsque le curseur est traîné dans la région de défilement par défaut à l’intérieur de la bordure de chaque fenêtre. Pour plus d’informations, voir l’article [OLE glisser et laisser tomber: Implémenter un objectif de baisse](../../mfc/drag-and-drop-ole.md#implement-a-drop-target).

## <a name="cviewondraw"></a><a name="ondraw"></a>CView::OnDraw

Appelé par le cadre pour rendre une image du document.

```
virtual void OnDraw(CDC* pDC) = 0;
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
Indique le contexte de l’appareil à utiliser pour rendre une image du document.

### <a name="remarks"></a>Notes

Le cadre appelle cette fonction pour effectuer l’affichage de l’écran, l’impression et l’aperçu d’impression, et il passe un contexte d’appareil différent dans chaque cas. Il n'y a pas d'implémentation par défaut.

Vous devez remplacer cette fonction pour afficher votre vue du document. Vous pouvez faire des appels d’interface périphérique graphique (GDI) à l’aide de [l’objet CDC](../../mfc/reference/cdc-class.md) pointé par le paramètre *pDC.* Vous pouvez sélectionner les ressources GDI, telles que les stylos ou les polices, dans le contexte de l’appareil avant de les dessiner, puis les désélectionner par la suite. Souvent, votre code de dessin peut être indépendant des appareils; c’est-à-dire qu’il ne nécessite pas d’informations sur le type d’appareil affiche l’image.

Pour optimiser le dessin, appelez la fonction membre [RectVisible](../../mfc/reference/cdc-class.md#rectvisible) du contexte de l’appareil pour savoir si un rectangle donné sera dessiné. Si vous devez faire la distinction entre l’affichage normal de l’écran et l’impression, appelez la fonction membre [IsPrinting](../../mfc/reference/cdc-class.md#isprinting) du contexte de l’appareil.

## <a name="cviewondrop"></a><a name="ondrop"></a>CView::OnDrop

Appelé par le cadre lorsque l’utilisateur publie un objet de données sur une cible de drop valide.

```
virtual BOOL OnDrop(
    COleDataObject* pDataObject,
    DROPEFFECT dropEffect,
    CPoint point);
```

### <a name="parameters"></a>Paramètres

'pDataObjectMD Points à [l’object COleData](../../mfc/reference/coledataobject-class.md) qui est tombé dans la cible de chute.

*dropEffect*<br/>
L’effet de chute que l’utilisateur a demandé.

- DROPEFFECT_COPY Crée une copie de l’objet de données en cours de chute.

- DROPEFFECT_MOVE déplace l’objet de données vers l’emplacement actuel de la souris.

- DROPEFFECT_LINK crée un lien entre un objet de données et son serveur.

*Point*<br/>
La position actuelle de la souris par rapport à la zone client de vue.

### <a name="return-value"></a>Valeur de retour

Nonzero si la baisse a été réussie; sinon 0.

### <a name="remarks"></a>Notes

L’implémentation par défaut ne fait rien et renvoie FALSE.

Remplacer cette fonction pour mettre en œuvre l’effet d’une chute OLE dans la zone client de la vue. L’objet de données peut être examiné via *pDataObject* pour les formats de données Clipboard et les données supprimées au point spécifié.

> [!NOTE]
> Le cadre n’appelle pas cette fonction s’il y a un remplacement à [OnDropEx](#ondropex) dans cette classe de vue.

## <a name="cviewondropex"></a><a name="ondropex"></a>CView::OnDropEx

Appelé par le cadre lorsque l’utilisateur publie un objet de données sur une cible de drop valide.

```
virtual DROPEFFECT OnDropEx(
    COleDataObject* pDataObject,
    DROPEFFECT dropDefault,
    DROPEFFECT dropList,
    CPoint point);
```

### <a name="parameters"></a>Paramètres

*pDataObject*<br/>
Points à [l’object COleData](../../mfc/reference/coledataobject-class.md) qui est tombé dans la cible de chute.

*dropDefault*<br/>
L’effet que l’utilisateur a choisi pour l’opération de chute par défaut en fonction de l’état clé actuel. C’est peut-être DROPEFFECT_NONE. Les effets de chute sont discutés dans la section Remarques.

*dropList (en)*<br/>
Une liste des effets de chute que la source de goutte prend en charge. Les valeurs d’effet de chute peuvent être combinées à l’aide de l’opération bitwise OU ( **&#124;). ** Les effets de chute sont discutés dans la section Remarques.

*Point*<br/>
La position actuelle de la souris par rapport à la zone client de vue.

### <a name="return-value"></a>Valeur de retour

L’effet de chute résultant de la tentative de chute à l’emplacement spécifié par *point*. Cela doit être l’une des valeurs indiquées par *dropEffectList*. Les effets de chute sont discutés dans la section Remarques.

### <a name="remarks"></a>Notes

La mise en œuvre par défaut est de ne rien faire et de retourner une valeur factice ( -1 ) pour indiquer que le cadre doit appeler le gestionnaire [OnDrop.](#ondrop)

Remplacer cette fonction pour implémenter l’effet d’une traînée et d’une goutte droite de bouton de souris. La traînée et la baisse droites de bouton de souris affichent typiquement un menu de choix quand le bouton de souris droit est libéré.

Votre remplacement `OnDropEx` de requête de devrait pour le bouton de souris droite. Vous pouvez appeler [GetKeyState](/windows/win32/api/winuser/nf-winuser-getkeystate) ou stocker l’état de bouton de souris droit à partir de votre gestionnaire [OnDragEnter.](#ondragenter)

- Si le bouton de souris droit est en panne, votre remplacement doit afficher un menu popup qui offre le support d’effets de goutte par la source de goutte.

  - Examinez *dropList* pour déterminer les effets de chute soutenus par la source de goutte. Activez uniquement ces actions sur le menu popup.

  - Utilisez [SetMenuDefaultItem](/windows/win32/api/winuser/nf-winuser-setmenudefaultitem) pour définir l’action par défaut basée sur *dropDefault*.

  - Enfin, prenez l’action indiquée par la sélection de l’utilisateur à partir du menu popup.

- Si le bouton de souris droit n’est pas en panne, votre remplacement doit traiter cela comme une demande de drop standard. Utilisez l’effet de chute spécifié dans *dropDefault*. Alternativement, votre remplacement peut retourner la valeur factice ( `OnDrop` -1 ) pour indiquer qui gérera cette opération de chute.

Utilisez *pDataObject* pour `COleDataObject` examiner le format de données Clipboard et les données supprimées au point spécifié.

Les effets de chute décrivent l’action associée à une opération de chute. Voir la liste suivante des effets de chute :

- DROPEFFECT_NONE Une baisse ne serait pas autorisée.

- DROPEFFECT_COPY une opération de copie serait effectuée.

- DROPEFFECT_MOVE Une opération de déménagement serait effectuée.

- DROPEFFECT_LINK Un lien entre les données abandonnées et les données originales serait établi.

- DROPEFFECT_SCROLL indique qu’une opération de drag scroll est sur le point de se produire ou se produit dans la cible.

Pour plus d’informations sur la définition de la commande de menu par défaut, voir [SetMenuDefaultItem](/windows/win32/api/winuser/nf-winuser-setmenudefaultitem) dans windows SDK et [CMenu:GetSafeHmenu](../../mfc/reference/cmenu-class.md#getsafehmenu) dans ce volume.

## <a name="cviewonendprinting"></a><a name="onendprinting"></a>CView::OnEndPrinting

Appelé par le cadre après l’impression ou la prévisualisation d’un document.

```
virtual void OnEndPrinting(
    CDC* pDC,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
Pointe vers le contexte de l’imprimante.

*pInfo (en anglais)*<br/>
Pointe vers une structure [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) qui décrit le travail d’impression actif.

### <a name="remarks"></a>Notes

L’implémentation par défaut de cette fonction est sans effet. Remplacez cette fonction pour libérer toutes les ressources GDI que vous avez allouées dans la fonction membre [OnBeginPrinting.](#onbeginprinting)

## <a name="cviewonendprintpreview"></a><a name="onendprintpreview"></a>CView::OnEndPrintPreview

Appelé par le cadre lorsque l’utilisateur sort du mode aperçu d’impression.

```
virtual void OnEndPrintPreview(
    CDC* pDC,
    CPrintInfo* pInfo,
    POINT point,
    CPreviewView* pView);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
Pointe vers le contexte de l’imprimante.

*pInfo (en anglais)*<br/>
Pointe vers une structure [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) qui décrit le travail d’impression actif.

*Point*<br/>
Spécifie le point de la page qui a été affiché pour la dernière fois en mode aperçu.

*pView (en)*<br/>
Points à l’objet de vue utilisé pour la prévisualisation.

### <a name="remarks"></a>Notes

La mise en œuvre par défaut de cette fonction appelle la fonction membre [OnEndPrinting](#onendprinting) et restaure la fenêtre de cadre principale à l’état où il était avant le début de l’aperçu d’impression. Remplacer cette fonction pour effectuer un traitement spécial lorsque le mode de prévisualisation est terminé. Par exemple, si vous souhaitez maintenir la position de l’utilisateur dans le document lors du passage du mode de prévisualisation au mode d’affichage normal, vous pouvez faire défiler vers la position décrite par le paramètre *de point* et `m_nCurPage` le membre de la `CPrintInfo` structure que le paramètre *pInfo* indique.

Appelez toujours la version `OnEndPrintPreview` de classe de base de votre remplacement, généralement à la fin de la fonction.

## <a name="cviewoninitialupdate"></a><a name="oninitialupdate"></a>CView::OnInitialUpdate

Appelé par le cadre après la vue est d’abord attaché au document, mais avant que la vue est initialement affichée.

```
virtual void OnInitialUpdate();
```

### <a name="remarks"></a>Notes

La mise en œuvre par défaut de cette fonction appelle la fonction membre [OnUpdate](#onupdate) sans aucune information d’indice (c’est-à-dire en utilisant les valeurs par défaut de 0 pour le paramètre *lHint* et NULL pour le paramètre *pHint).* Remplacer cette fonction pour effectuer une initialisation ponctuelle qui nécessite des informations sur le document. Par exemple, si votre application a des documents de taille fixe, vous pouvez utiliser cette fonction pour initialiser les limites de défilement d’une vue en fonction de la taille du document. Si votre application prend en charge des documents de taille variable, utilisez [OnUpdate](#onupdate) pour mettre à jour les limites de défilement chaque fois que le document change.

## <a name="cviewonpreparedc"></a><a name="onpreparedc"></a>CView::OnPrepareDC

Appelé par le cadre avant la fonction membre [OnDraw](#ondraw) est appelé pour l’affichage de l’écran et avant la fonction membre [OnPrint](#onprint) est appelé pour chaque page lors de l’impression ou l’impression aperçu.

```
virtual void OnPrepareDC(
    CDC* pDC,
    CPrintInfo* pInfo = NULL);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
Indique le contexte de l’appareil à utiliser pour rendre une image du document.

*pInfo (en anglais)*<br/>
Indique une structure [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) qui décrit le `OnPrepareDC` travail d’impression actuel si elle est appelée pour l’impression ou l’impression aperçu; le `m_nCurPage` membre spécifie la page sur le point d’être imprimée. Ce paramètre `OnPrepareDC` est NULL si est appelé pour l’affichage de l’écran.

### <a name="remarks"></a>Notes

La mise en œuvre par défaut de cette fonction ne fait rien si la fonction est appelée pour l’affichage de l’écran. Cependant, cette fonction est remplacée dans les classes dérivées, telles que [CScrollView](../../mfc/reference/cscrollview-class.md), pour ajuster les attributs du contexte de l’appareil; par conséquent, vous devez toujours appeler la mise en œuvre de la classe de base au début de votre remplacement.

Si la fonction est appelée pour l’impression, l’implémentation par défaut examine les informations de page stockées dans le *paramètre pInfo.* Si la longueur du document n’a pas été spécifiée, `OnPrepareDC` suppose que le document est long d’une page et arrête la boucle d’impression après l’impression d’une page. La fonction arrête la boucle `m_bContinuePrinting` d’impression en définissant le membre de la structure à FALSE.

Remplacement `OnPrepareDC` pour l’une ou l’autre des raisons suivantes :

- Ajuster les attributs du contexte de l’appareil au besoin pour la page spécifiée. Par exemple, si vous devez définir le mode de cartographie ou d’autres caractéristiques du contexte de l’appareil, faites-le dans cette fonction.

- Pour effectuer la pagination d’impression-temps. Normalement, vous spécifiez la longueur du document lorsque l’impression commence, en utilisant la fonction membre [OnPreparePrinting.](#onprepareprinting) Toutefois, si vous ne savez pas à l’avance combien de temps le document est (par exemple, lors de l’impression d’un nombre indéterminé d’enregistrements à partir d’une base de données), remplacez-vous `OnPrepareDC` pour tester la fin du document pendant qu’il est imprimé. Lorsqu’il n’y a plus de `m_bContinuePrinting` document à `CPrintInfo` imprimer, définissez le membre de la structure en FALSE.

- Envoyer des codes d’évacuation à l’imprimante page par page. Pour envoyer des `OnPrepareDC`codes `Escape` d’évacuation à partir de , appelez la fonction membre du paramètre *pDC.*

Appelez la version `OnPrepareDC` de classe de base au début de votre remplacement.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#183](../../mfc/codesnippet/cpp/cview-class_1.cpp)]

## <a name="cviewonprepareprinting"></a><a name="onprepareprinting"></a>CView::OnPreparePrinting

Appelé par le cadre avant qu’un document soit imprimé ou prévisualisé.

```
virtual BOOL OnPreparePrinting(CPrintInfo* pInfo);
```

### <a name="parameters"></a>Paramètres

*pInfo (en anglais)*<br/>
Pointe vers une structure [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) qui décrit le travail d’impression actif.

### <a name="return-value"></a>Valeur de retour

Nonzero pour commencer l’impression; 0 si le travail d’impression a été annulé.

### <a name="remarks"></a>Notes

L'implémentation par défaut n'exécute aucune opération.

Vous devez remplacer cette fonction pour activer l’impression et l’impression aperçu. Appelez la fonction [membre DoPreparePrinting,](#doprepareprinting) en le transmettant le paramètre *pInfo,* puis retournez sa valeur de retour ; `DoPreparePrinting` affiche la boîte de dialogue d’impression et crée un contexte d’appareil d’imprimante. Si vous souhaitez paralyser la boîte de dialogue d’impression avec des valeurs autres que les défauts, attribuez des valeurs aux membres de *pInfo*. Par exemple, si vous connaissez la longueur du document, transmettez la valeur à `DoPreparePrinting`la fonction membre [SetMaxPage](../../mfc/reference/cprintinfo-structure.md#setmaxpage) de *pInfo* avant d’appeler . Cette valeur est affichée dans la boîte To: dans la partie Range de la boîte de dialogue d’impression.

`DoPreparePrinting`n’affiche pas la boîte de dialogue d’impression pour un travail d’aperçu. Si vous voulez contourner la boîte de dialogue d’impression pour un travail d’impression, vérifiez que le `m_bPreview` membre de *pInfo* est FALSE et ensuite le régler à VRAI avant de le passer à `DoPreparePrinting`; réinitialiser à FALSE par la suite.

Si vous devez effectuer des initialisations `CDC` qui nécessitent l’accès à l’objet représentant le contexte de l’appareil d’imprimante `OnBeginPrinting` (par exemple, si vous avez besoin de connaître la taille de la page avant de spécifier la longueur du document), remplacez la fonction membre.

Si vous souhaitez définir la `m_nNumPreviewPages` `m_strPageDesc` valeur du paramètre pInfo ou `DoPreparePrinting`des membres du *pInfo,* faites-le après avoir appelé . La `DoPreparePrinting` fonction `m_nNumPreviewPages` du membre établit la valeur que l’on retrouve dans l’application . Fichier INI `m_strPageDesc` et définit à sa valeur par défaut.

### <a name="example"></a>Exemple

  Remplacez `OnPreparePrinting` et `DoPreparePrinting` appelez à partir du remplacement afin que le cadre affiche une boîte de dialogue d’impression et de créer une imprimante DC pour vous.

[!code-cpp[NVC_MFCDocView#184](../../mfc/codesnippet/cpp/cview-class_2.cpp)]

Si vous savez combien de pages le document `OnPreparePrinting` contient, définissez la page maximale avant d’appeler `DoPreparePrinting`. Le cadre affichera le nombre maximum de page dans la boîte " à " de la boîte de dialogue d’impression.

[!code-cpp[NVC_MFCDocView#185](../../mfc/codesnippet/cpp/cview-class_3.cpp)]

## <a name="cviewonprint"></a><a name="onprint"></a>CView::OnPrint

Appelé par le cadre pour imprimer ou prévisualiser une page du document.

```
virtual void OnPrint(
    CDC* pDC,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
Pointe vers le contexte de l’imprimante.

*pInfo (en anglais)*<br/>
Indique une `CPrintInfo` structure qui décrit le travail d’impression actuel.

### <a name="remarks"></a>Notes

Pour chaque page imprimée, le cadre appelle cette fonction immédiatement après avoir appelé la fonction membre [OnPrepareDC.](#onpreparedc) La page imprimée est `m_nCurPage` spécifiée par le membre de la structure [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) qui *indique pInfo.* La implémentation par défaut appelle la fonction membre [OnDraw](#ondraw) et l’adopte le contexte de l’appareil d’imprimante.

Remplacer cette fonction pour l’une ou l’autre des raisons suivantes :

- Permettre l’impression de documents multipages. Ne rendre que la partie du document qui correspond à la page actuellement imprimée. Si vous utilisez `OnDraw` pour effectuer le rendu, vous pouvez ajuster l’origine du port de vue de sorte que seule la partie appropriée du document est imprimée.

- Pour que l’image imprimée soit différente de l’image de l’écran (c’est-à-dire si votre application n’est pas WYSIWYG). Au lieu de passer `OnDraw`le contexte de l’appareil d’imprimante à , utilisez le contexte de l’appareil pour rendre une image en utilisant des attributs non affichés sur l’écran.

   Si vous avez besoin de ressources GDI pour l’impression que vous n’utilisez pas pour l’affichage de l’écran, sélectionnez-les dans le contexte de l’appareil avant de les dessiner et de les désélectionner par la suite. Ces ressources GDI devraient être allouées dans [OnBeginPrinting](#onbeginprinting) et publiées dans [OnEndPrinting](#onendprinting).

- Pour mettre en œuvre des en-têtes ou des pieds. Vous pouvez `OnDraw` toujours utiliser pour faire le rendu en limitant la zone qu’il peut imprimer sur.

Notez `m_rectDraw` que le membre du paramètre *pInfo* décrit la zone imprimable de la page dans les unités logiques.

N’appelez `OnPrepareDC` pas votre `OnPrint`remplacement de ; le cadre `OnPrepareDC` appelle `OnPrint`automatiquement avant d’appeler .

### <a name="example"></a>Exemple

Ce qui suit est un `OnPrint` squelette pour une fonction dépassée :

[!code-cpp[NVC_MFCDocView#186](../../mfc/codesnippet/cpp/cview-class_4.cpp)]

Pour un autre exemple, voir [CRichEditView::PrintInsideRect](../../mfc/reference/cricheditview-class.md#printinsiderect).

## <a name="cviewonscroll"></a><a name="onscroll"></a>CView::OnScroll

Appelé par le cadre pour déterminer si le défilement est possible.

```
virtual BOOL OnScroll(
    UINT nScrollCode,
    UINT nPos,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>Paramètres

*nScrollCode (en)*<br/>
Un code à barres de défilement qui indique la demande de défilement de l’utilisateur. Ce paramètre est composé de deux parties : un byte à faible ordre, qui détermine le type de défilement se produisant horizontalement, et un byte de haut ordre, qui détermine le type de défilement se produisant verticalement :

- SB_BOTTOM Faites défiler vers le bas.

- SB_LINEDOWN Parchemine une ligne vers le bas.

- SB_LINEUP Faites défiler une ligne.

- SB_PAGEDOWN parchemine une page vers le bas.

- SB_PAGEUP parchemine une page vers le haut.

- SB_THUMBTRACK Drags faire défiler la boîte à position spécifiée. La position actuelle est spécifiée dans *nPos*.

- SB_TOP Faites défiler vers le haut.

*Osbl*<br/>
Contient la position actuelle de la boîte à défilement si le code à barres de défilement est SB_THUMBTRACK ; sinon il n’est pas utilisé. Selon la plage de défilement initiale, *nPos* peut être négatif et doit être jeté à un **int** si nécessaire.

*bDoScroll (en)*<br/>
Détermine si vous devez réellement faire l’action de défilement spécifiée. Si VRAI, alors le défilement doit avoir lieu; si FALSE, alors le défilement ne devrait pas se produire.

### <a name="return-value"></a>Valeur de retour

Si *bDoScroll* est VRAI et la vue a été effectivement défilé, puis retourner nonzero; sinon 0. Si *bDoScroll* est FALSE, puis retournez la valeur que vous auriez retournée si *bDoScroll* étaient VRAI, même si vous ne faites pas réellement le défilement.

### <a name="remarks"></a>Notes

Dans un cas, cette fonction est appelée par le cadre avec *bDoScroll* réglé à VRAI lorsque la vue reçoit un message scrollbar. Dans ce cas, vous devriez en fait faire défiler la vue. Dans l’autre cas, cette fonction est appelée avec *bDoScroll* réglé à FALSE quand un élément OLE est initialement traîné dans la région de défilement automatique d’une cible de goutte avant de défiler a effectivement lieu. Dans ce cas, vous ne devriez pas réellement faire défiler la vue.

## <a name="cviewonscrollby"></a><a name="onscrollby"></a>CView::OnScrollBy

Appelé par le cadre lorsque l’utilisateur voit une zone au-delà de la vue actuelle du document, soit en faisant glisser un élément OLE contre les frontières actuelles de la vue, soit en manipulant les barres de défilement verticales ou horizontales.

```
virtual BOOL OnScrollBy(
    CSize sizeScroll,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>Paramètres

*tailleScroll*<br/>
Nombre de pixels défilés horizontalement et verticalement.

*bDoScroll (en)*<br/>
Détermine si le défilement de la vue se produit. Si VRAI, alors le défilement a lieu; si FALSE, alors le défilement ne se produit pas.

### <a name="return-value"></a>Valeur de retour

Nonzero si la vue était en mesure d’être défilé; sinon 0.

### <a name="remarks"></a>Notes

Dans les classes dérivées, cette méthode vérifie si la vue est défilementable dans la direction demandée par l’utilisateur, puis met à jour la nouvelle région si nécessaire. Cette fonction est automatiquement appelée par [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll) et [CWnd::OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll) pour effectuer la demande de défilement réelle.

La mise en œuvre par défaut de cette méthode ne change pas `CScrollView`la vue, mais si elle n’est pas appelée, la vue ne fera pas défiler dans une classe dérivée.

Si la largeur ou la hauteur du document dépasse 32767 pixels, `OnScrollBy` le défilement passé 32767 échouera parce qu’est appelé avec un argument *de tailles invalidesScroll.*

## <a name="cviewonupdate"></a><a name="onupdate"></a>CView::OnUpdate

Appelé par le cadre après la modification du document de l’avis; cette fonction est appelée par [CDocument::UpdateAllViews](../../mfc/reference/cdocument-class.md#updateallviews) et permet à la vue de mettre à jour son affichage pour refléter ces modifications.

```
virtual void OnUpdate(
    CView* pSender,
    LPARAM lHint,
    CObject* pHint);
```

### <a name="parameters"></a>Paramètres

*pSender*<br/>
Indique l’opinion qui a modifié le document, ou NULL si toutes les vues doivent être mises à jour.

*lHint (en anglais)*<br/>
Contient des informations sur les modifications.

*pHint*<br/>
Indique un objet stockant des informations sur les modifications.

### <a name="remarks"></a>Notes

Il est également appelé par la mise en œuvre par défaut de [OnInitialUpdate](#oninitialupdate). La mise en œuvre par défaut invalide l’ensemble de la zone client, la marquant pour la peinture lorsque le prochain message WM_PAINT est reçu. Remplacez cette fonction si vous souhaitez mettre à jour uniquement les régions qui cartographient les parties modifiées du document. Pour ce faire, vous devez transmettre des informations sur les modifications en utilisant les paramètres de l’indice.

Pour utiliser *lHint*, définir des valeurs d’indice spécial, généralement un bitmask ou un type énuméré, et faire passer le document une de ces valeurs. Pour utiliser *pHint*, tirer une classe d’indice de [CObject](../../mfc/reference/cobject-class.md) et avoir le document passer un pointeur à un objet d’indice; lorsque vous `OnUpdate`l’emportez, utilisez le [CObject::IsKindOf](../../mfc/reference/cobject-class.md#iskindof) fonction membre pour déterminer le type de temps d’exécution de l’objet d’indice.

Typiquement, vous ne devriez `OnUpdate`pas effectuer tout dessin directement à partir de . Déterminez plutôt le rectangle décrivant, dans les coordonnées de l’appareil, la zone qui nécessite une mise à jour; passer ce rectangle à [CWnd::InvalidateRect](../../mfc/reference/cwnd-class.md#invalidaterect). Cela provoque la peinture de se produire la prochaine fois qu’un [message WM_PAINT](/windows/win32/gdi/wm-paint) est reçu.

Si *lHint* est 0 et *pHint* est NULL, le document a envoyé une notification de mise à jour générique. Si une vue reçoit une notification de mise à jour générique, ou si elle ne peut pas décoder les indices, elle doit invalider l’ensemble de sa zone client.

## <a name="see-also"></a>Voir aussi

[MFC Échantillon MDIDOCVW](../../overview/visual-cpp-samples.md)<br/>
[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[CFrameWnd, classe](../../mfc/reference/cframewnd-class.md)<br/>
[Classe CSplitterWnd](../../mfc/reference/csplitterwnd-class.md)<br/>
[Classe CDC](../../mfc/reference/cdc-class.md)<br/>
[Classe CDocTemplate](../../mfc/reference/cdoctemplate-class.md)<br/>
[CDocument, classe](../../mfc/reference/cdocument-class.md)
