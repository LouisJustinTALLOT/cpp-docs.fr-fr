---
title: CView, classe
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
ms.openlocfilehash: f6be846e80209ce94c84222d61c37a7964baad03
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127507"
---
# <a name="cview-class"></a>CView, classe

Fournit les fonctionnalités de base des classes de vues définies par l'utilisateur.

## <a name="syntax"></a>Syntaxe

```
class AFX_NOVTABLE CView : public CWnd
```

## <a name="members"></a>Membres

### <a name="protected-constructors"></a>Constructeurs prot&#233;g&#233;s

|Name|Description|
|----------|-----------------|
|[CView :: CView](#cview)|Construit un objet `CView`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[CView ::D oPreparePrinting](#doprepareprinting)|Affiche la boîte de dialogue Imprimer et crée un contexte de périphérique d’impression. Appelez lors de la substitution de la fonction membre `OnPreparePrinting`.|
|[CView :: GetDocument](#getdocument)|Retourne le document associé à la vue.|
|[CView :: IsSelected](#isselected)|Teste si un élément de document est sélectionné. Requis pour la prise en charge OLE.|
|[CView :: OnDragEnter](#ondragenter)|Appelé lors du premier déplacement d’un élément dans la zone de glisser-déplacer d’une vue.|
|[CView :: OnDragLeave](#ondragleave)|Appelée lorsqu’un élément déplacé quitte la zone de glisser-déplacer d’une vue.|
|[CView :: OnDragOver](#ondragover)|Appelée lorsqu’un élément est glissé sur la zone de glisser-déplacer d’une vue.|
|[CView :: OnDragScroll](#ondragscroll)|Appelé pour déterminer si le curseur est déplacé dans la zone de défilement de la fenêtre.|
|[CView :: OnDrop](#ondrop)|Appelé lorsqu’un élément a été déplacé dans la zone de glisser-déplacer d’une vue, le gestionnaire par défaut.|
|[CView :: OnDropEx](#ondropex)|Appelé lorsqu’un élément a été déplacé dans la zone de glisser-déplacer d’une vue, gestionnaire principal.|
|[CView :: OnInitialUpdate](#oninitialupdate)|Appelé après qu’une vue a été attachée pour la première fois à un document.|
|[CView :: OnPrepareDC](#onpreparedc)|Appelé avant que la fonction membre `OnDraw` soit appelée pour l’affichage à l’écran ou que la fonction membre `OnPrint` soit appelée pour l’impression ou l’aperçu avant impression.|
|[CView :: OnScroll](#onscroll)|Appelé lorsque des éléments OLE sont glissés au-delà des bordures de la vue.|
|[CView :: OnScrollBy](#onscrollby)|Appelée lorsqu’une vue contenant des éléments OLE actifs sur place est défilant.|

### <a name="protected-methods"></a>Méthodes protégées

|Name|Description|
|----------|-----------------|
|[CView :: OnActivateFrame](#onactivateframe)|Appelé lorsque la fenêtre frame contenant la vue est activée ou désactivée.|
|[CView :: OnActivateView](#onactivateview)|Appelée lorsqu’une vue est activée.|
|[CView :: OnBeginPrinting](#onbeginprinting)|Appelé lorsqu’un travail d’impression commence ; Substituez pour allouer des ressources GDI (Graphics Device Interface).|
|[CView :: OnDraw](#ondraw)|Appelé pour restituer une image du document pour l’affichage, l’impression ou l’aperçu avant impression de l’écran. Implémentation requise.|
|[CView :: OnEndPrinting](#onendprinting)|Appelé lorsqu’un travail d’impression se termine ; Substituez pour libérer des ressources GDI.|
|[CView :: OnEndPrintPreview](#onendprintpreview)|Appelé lorsque le mode aperçu est fermé.|
|[CView :: OnPreparePrinting](#onprepareprinting)|Appelé avant l’impression ou l’aperçu d’un document ; Substituez pour initialiser la boîte de dialogue Imprimer.|
|[CView :: OnPrint](#onprint)|Appelé pour imprimer ou afficher un aperçu d’une page du document.|
|[CView :: OnUpdate](#onupdate)|Appelé pour avertir une vue que son document a été modifié.|

## <a name="remarks"></a>Notes

Une vue est attachée à un document et agit en tant qu’intermédiaire entre le document et l’utilisateur : la vue affiche une image du document sur l’écran ou l’imprimante et interprète les entrées utilisateur comme des opérations sur le document.

Une vue est un enfant d’une fenêtre frame. Plusieurs vues peuvent partager une fenêtre frame, comme dans le cas d’une fenêtre fractionnée. La relation entre une classe de vue, une classe de fenêtre frame et une classe de document est établie par un objet `CDocTemplate`. Lorsque l’utilisateur ouvre une nouvelle fenêtre ou fractionne une fenêtre existante, le Framework construit une nouvelle vue et l’attache au document.

Une vue peut être jointe à un seul document, mais plusieurs vues peuvent être attachées à un document à la fois, par exemple, si le document est affiché dans une fenêtre fractionnée ou dans plusieurs fenêtres enfants dans une application d’interface multidocument (MDI, multiple document interface). Votre application peut prendre en charge différents types de vues pour un type de document donné. par exemple, un programme de traitement de texte peut fournir une vue de texte complète d’un document et un mode plan qui affiche uniquement les en-têtes de section. Ces différents types d’affichages peuvent être placés dans des fenêtres Frame distinctes ou dans des volets séparés d’une même fenêtre frame si vous utilisez une fenêtre fractionnée.

Une vue peut être responsable de la gestion de différents types d’entrée, tels que l’entrée au clavier, l’entrée ou l’entrée de la souris par le biais du glisser-déplacer, ainsi que des commandes de menus, de barres d’outils ou de barres de défilement. Une vue reçoit les commandes transférées par sa fenêtre frame. Si la vue ne gère pas une commande donnée, elle transfère la commande vers son document associé. Comme toutes les cibles de commande, une vue gère les messages via une table des messages.

La vue est chargée d’afficher et de modifier les données du document, mais pas de les stocker. Le document fournit la vue avec les détails nécessaires sur ses données. Vous pouvez laisser la vue accéder directement aux membres de données du document, ou vous pouvez fournir des fonctions membres dans la classe de document pour la classe d’affichage à appeler.

Lorsque les données d’un document sont modifiées, la vue responsable des modifications appelle généralement la fonction [CDocument :: UpdateAllViews](../../mfc/reference/cdocument-class.md#updateallviews) pour le document, qui avertit toutes les autres vues en appelant la fonction membre `OnUpdate` pour chaque. L’implémentation par défaut de `OnUpdate` invalide la zone cliente entière de la vue. Vous pouvez la remplacer pour invalider uniquement les régions de la zone cliente qui mappent aux parties modifiées du document.

Pour utiliser `CView`, dérivez une classe de celle-ci et implémentez la fonction membre `OnDraw` pour effectuer l’affichage de l’écran. Vous pouvez également utiliser `OnDraw` pour effectuer l’impression et l’aperçu avant impression. Le Framework gère la boucle d’impression pour l’impression et l’aperçu de votre document.

Une vue gère les messages de la barre de défilement avec les fonctions membres [CWnd :: OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll) et [CWnd :: OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll) . Vous pouvez implémenter la gestion des messages de la barre de défilement dans ces fonctions, ou vous pouvez utiliser la `CView` classe dérivée [CScrollView](../../mfc/reference/cscrollview-class.md) pour gérer le défilement pour vous.

Outre `CScrollView`, le bibliothèque MFC (Microsoft Foundation Class) fournit neuf autres classes dérivées de `CView`:

- [CCtrlView](../../mfc/reference/cctrlview-class.md), une vue qui permet l’utilisation de l’architecture document/vue avec des contrôles d’arborescence, de liste et RichEdit.

- [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md), vue qui affiche des enregistrements de base de données dans des contrôles de boîte de dialogue.

- [CEditView](../../mfc/reference/ceditview-class.md), vue qui fournit un éditeur de texte multiligne simple. Vous pouvez utiliser un objet `CEditView` en tant que contrôle dans une boîte de dialogue, ainsi qu’une vue sur un document.

- [CFormView](../../mfc/reference/cformview-class.md), une vue à défilement qui contient des contrôles de boîte de dialogue et est basée sur une ressource de modèle de boîte de dialogue.

- [CListView](../../mfc/reference/clistview-class.md), vue qui permet l’utilisation de l’architecture document/vue avec des contrôles de liste.

- [CRecordView](../../mfc/reference/crecordview-class.md), vue qui affiche des enregistrements de base de données dans des contrôles de boîte de dialogue.

- [CRichEditView](../../mfc/reference/cricheditview-class.md), vue qui permet l’utilisation de l’architecture document-vue avec des contrôles RichEdit.

- [CScrollView](../../mfc/reference/cscrollview-class.md), vue qui fournit automatiquement la prise en charge du défilement.

- [CTreeView](../../mfc/reference/ctreeview-class.md), vue qui permet l’utilisation de l’architecture document-vue avec des contrôles d’arborescence.

La classe `CView` a également une classe d’implémentation dérivée nommée `CPreviewView`, qui est utilisée par l’infrastructure pour effectuer un aperçu avant impression. Cette classe assure la prise en charge des fonctionnalités propres à la fenêtre d’aperçu avant impression, telles qu’une barre d’outils, un aperçu d’une seule page ou d’une seule page, ainsi que le zoom, c’est-à-dire l’agrandissement de l’image prévisualisée. Vous n’avez pas besoin d’appeler ou de substituer les fonctions membres de `CPreviewView`, sauf si vous souhaitez implémenter votre propre interface pour l’aperçu avant impression (par exemple, si vous souhaitez prendre en charge la modification en mode aperçu avant impression). Pour plus d’informations sur l’utilisation de `CView`, consultez [architecture de document/vue](../../mfc/document-view-architecture.md) et [impression](../../mfc/printing.md). En outre, consultez la [note technique 30](../../mfc/tn030-customizing-printing-and-print-preview.md) pour plus d’informations sur la personnalisation de l’aperçu avant impression.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CView`

## <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

##  <a name="cview"></a>CView :: CView

Construit un objet `CView`.

```
CView();
```

### <a name="remarks"></a>Notes

L’infrastructure appelle le constructeur lors de la création d’une nouvelle fenêtre frame ou lors du fractionnement d’une fenêtre. Substituez la fonction membre [OnInitialUpdate](#oninitialupdate) pour initialiser la vue une fois que le document est attaché.

##  <a name="doprepareprinting"></a>CView ::D oPreparePrinting

Appelez cette fonction à partir de votre remplacement de [OnPreparePrinting](#onprepareprinting) pour appeler la boîte de dialogue Imprimer et créer un contexte de périphérique d’impression.

```
BOOL DoPreparePrinting(CPrintInfo* pInfo);
```

### <a name="parameters"></a>Paramètres

*pInfo*<br/>
Pointe vers une structure [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) qui décrit le travail d’impression actif.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’impression ou l’aperçu avant impression peuvent commencer ; 0 si l’opération a été annulée.

### <a name="remarks"></a>Notes

Le comportement de cette fonction varie selon qu’elle est appelée pour l’impression ou l’aperçu avant impression (spécifié par le membre `m_bPreview` du paramètre *pinfo* ). Si un fichier est en cours d’impression, cette fonction appelle la boîte de dialogue Imprimer, en utilisant les valeurs de la structure [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) vers laquelle *pinfo* pointe ; une fois que l’utilisateur a fermé la boîte de dialogue, la fonction crée un contexte de périphérique d’impression en fonction des paramètres spécifiés par l’utilisateur dans la boîte de dialogue et retourne ce contexte de périphérique par le biais du paramètre *pinfo* . Ce contexte de périphérique est utilisé pour imprimer le document.

Si un fichier est en cours d’aperçu, cette fonction crée un contexte de périphérique d’impression à l’aide des paramètres actuels de l’imprimante ; ce contexte de périphérique est utilisé pour simuler l’imprimante pendant la version préliminaire.

##  <a name="getdocument"></a>CView :: GetDocument

Appelez cette fonction pour obtenir un pointeur vers le document de la vue.

```
CDocument* GetDocument() const;
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers l’objet [CDocument](../../mfc/reference/cdocument-class.md) associé à la vue. NULL si la vue n’est pas attachée à un document.

### <a name="remarks"></a>Notes

Cela vous permet d’appeler les fonctions membres du document.

##  <a name="isselected"></a>CView :: IsSelected

Appelé par l’infrastructure pour vérifier si l’élément de document spécifié est sélectionné.

```
virtual BOOL IsSelected(const CObject* pDocItem) const;
```

### <a name="parameters"></a>Paramètres

*pDocItem*<br/>
Pointe vers l’élément de document en cours de test.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’élément de document spécifié est sélectionné ; Sinon, 0.

### <a name="remarks"></a>Notes

L’implémentation par défaut de cette fonction retourne FALSe. Substituez cette fonction si vous implémentez la sélection à l’aide d’objets [CDocItem](../../mfc/reference/cdocitem-class.md) . Vous devez remplacer cette fonction si votre vue contient des éléments OLE.

##  <a name="onactivateframe"></a>CView :: OnActivateFrame

Appelé par le Framework lorsque la fenêtre frame contenant la vue est activée ou désactivée.

```
virtual void OnActivateFrame(
    UINT nState,
    CFrameWnd* pFrameWnd);
```

### <a name="parameters"></a>Paramètres

*nState*<br/>
Spécifie si la fenêtre frame est en cours d’activation ou de désactivation. Ce peut être l’une des valeurs suivantes :

- WA_INACTIVE la fenêtre frame est désactivée.

- WA_ACTIVE la fenêtre frame est activée à l’aide d’une méthode autre qu’un clic de souris (par exemple, à l’aide de l’interface clavier pour sélectionner la fenêtre).

- WA_CLICKACTIVE la fenêtre frame est activée par un clic de souris

*pFrameWnd*<br/>
Pointeur vers la fenêtre frame à activer.

### <a name="remarks"></a>Notes

Substituez cette fonction membre si vous souhaitez effectuer un traitement spécial lorsque la fenêtre frame associée à la vue est activée ou désactivée. Par exemple, [CFormView](../../mfc/reference/cformview-class.md) effectue cette substitution lorsqu’il enregistre et restaure le contrôle qui a le focus.

##  <a name="onactivateview"></a>CView :: OnActivateView

Appelé par le Framework lorsqu’une vue est activée ou désactivée.

```
virtual void OnActivateView(
    BOOL bActivate,
    CView* pActivateView,
    CView* pDeactiveView);
```

### <a name="parameters"></a>Paramètres

*bActivate*<br/>
Indique si la vue est en cours d’activation ou de désactivation.

*pActivateView*<br/>
Pointe vers l’objet de vue en cours d’activation.

*pDeactiveView*<br/>
Pointe vers l’objet de vue qui est désactivé.

### <a name="remarks"></a>Notes

L’implémentation par défaut de cette fonction définit le focus sur la vue en cours d’activation. Remplacez cette fonction si vous souhaitez effectuer un traitement spécial lorsqu’une vue est activée ou désactivée. Par exemple, si vous souhaitez fournir des signaux visuels spéciaux qui distinguent la vue active des vues inactives, vous devez examiner le paramètre *bActivate* et mettre à jour l’apparence de la vue en conséquence.

Les paramètres *pActivateView* et *pDeactiveView* pointent vers la même vue si la fenêtre frame principale de l’application est activée sans modification dans la vue active (par exemple, si le focus est transféré d’une autre application à celle-ci, et non d’une vue à l’autre au sein de l’application ou lors du basculement entre des fenêtres enfants MDI). Cela permet à une vue de rétablir sa palette, si nécessaire.

Ces paramètres diffèrent lorsque [CFrameWnd :: SetActiveView](../../mfc/reference/cframewnd-class.md#setactiveview) est appelé avec une vue différente de celle que [CFrameWnd :: GetActiveView](../../mfc/reference/cframewnd-class.md#getactiveview) retournerait. Cela se produit le plus souvent avec des fenêtres fractionnées.

##  <a name="onbeginprinting"></a>CView :: OnBeginPrinting

Appelé par l’infrastructure au début d’un travail d’impression ou d’aperçu avant impression, après que `OnPreparePrinting` a été appelé.

```
virtual void OnBeginPrinting(
    CDC* pDC,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
Pointe vers le contexte de l’imprimante.

*pInfo*<br/>
Pointe vers une structure [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) qui décrit le travail d’impression actif.

### <a name="remarks"></a>Notes

L’implémentation par défaut de cette fonction est sans effet. Remplacez cette fonction pour allouer des ressources GDI, telles que des stylets ou des polices, nécessaires précisément pour l’impression. Sélectionnez les objets GDI dans le contexte de périphérique de la fonction membre [OnPrint](#onprint) pour chaque page qui les utilise. Si vous utilisez le même objet d’affichage pour l’affichage et l’impression d’écran, utilisez des variables distinctes pour les ressources GDI nécessaires à chaque affichage ; vous pourrez ainsi mettre à jour l’écran pendant l’impression.

Vous pouvez aussi utiliser cette fonction pour exécuter des initialisations qui dépendent des propriétés du contexte de l’imprimante. Par exemple, le nombre de pages nécessaires à l’impression du document peut dépendre des paramètres que l’utilisateur a spécifiés dans la boîte de dialogue d’impression (comme la longueur de page). En pareil cas, vous ne pouvez pas spécifier la longueur du document dans la fonction membre [OnPreparePrinting](#onprepareprinting) comme vous le feriez normalement ; vous devez attendre que le contexte de l’imprimante ait été créé en fonction des paramètres de la boîte de dialogue. [OnBeginPrinting](#onbeginprinting) est la première fonction substituable qui donne accès à l’objet [CDC](../../mfc/reference/cdc-class.md) représentant le contexte de l’imprimante. Vous pouvez donc définir la longueur du document à partir de cette fonction. Notez que si la longueur du document n’est pas spécifiée à ce stade, aucune barre de défilement ne s’affiche pendant l’aperçu avant impression.

##  <a name="ondragenter"></a>CView :: OnDragEnter

Appelé par le Framework lorsque la souris entre pour la première fois dans la zone sans défilement de la fenêtre cible du déplacement.

```
virtual DROPEFFECT OnDragEnter(
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Paramètres

*pDataObject*<br/>
Pointe vers le [COleDataObject](../../mfc/reference/coledataobject-class.md) déplacé dans la zone de dépôt de la vue.

*dwKeyState*<br/>
Contient l’état des touches de modification. Il s’agit d’une combinaison de n’importe quel nombre de ce qui suit : MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON et MK_RBUTTON.

*point*<br/>
Position actuelle de la souris par rapport à la zone cliente de la vue.

### <a name="return-value"></a>Valeur de retour

Valeur du type énuméré DROPEFFECT, qui indique le type de déplacement qui se produit si l’utilisateur a supprimé l’objet à cette position. Le type de déplacement dépend généralement de l’état de clé actuel indiqué par *dwKeyState*. Un mappage standard des KeyStates aux valeurs DROPEFFECT est le suivant :

- DROPEFFECT_NONE l’objet de données ne peut pas être supprimé dans cette fenêtre.

- DROPEFFECT_LINK pour MK_CONTROL &#124; MK_SHIFT crée une liaison entre l’objet et son serveur.

- DROPEFFECT_COPY pour MK_CONTROL crée une copie de l’objet supprimé.

- DROPEFFECT_MOVE pour MK_ALT crée une copie de l’objet supprimé et supprime l’objet d’origine. Il s’agit généralement de l’effet de déplacement par défaut, lorsque la vue peut accepter cet objet de données.

Pour plus d’informations, consultez l’exemple de concepts avancés MFC [OCLIENT](../../overview/visual-cpp-samples.md).

### <a name="remarks"></a>Notes

L’implémentation par défaut consiste à ne rien faire et à retourner DROPEFFECT_NONE.

Substituez cette fonction pour préparer les appels futurs à la fonction membre [OnDragOver](#ondragover) . Toutes les données requises à partir de l’objet de données doivent être récupérées à ce stade pour une utilisation ultérieure dans la fonction membre `OnDragOver`. La vue doit également être mise à jour à ce stade pour fournir des commentaires visuels à l’utilisateur. Pour plus d’informations, consultez l’article [glisser-déplacer OLE : implémenter une cible de déplacement](../../mfc/drag-and-drop-ole.md#implement-a-drop-target).

##  <a name="ondragleave"></a>CView :: OnDragLeave

Appelée par l’infrastructure pendant une opération glisser lorsque la souris est déplacée hors de la zone de dépôt valide pour cette fenêtre.

```
virtual void OnDragLeave();
```

### <a name="remarks"></a>Notes

Substituez cette fonction si la vue actuelle doit nettoyer les actions effectuées pendant les appels [OnDragEnter](#ondragenter) ou [OnDragOver](#ondragover) , par exemple la suppression des commentaires des utilisateurs visuels pendant que l’objet a été glissé et déposé.

##  <a name="ondragover"></a>CView :: OnDragOver

Appelée par l’infrastructure pendant une opération glisser lorsque la souris est déplacée sur la fenêtre cible du déplacement.

```
virtual DROPEFFECT OnDragOver(
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Paramètres

*pDataObject*<br/>
Pointe vers le [COleDataObject](../../mfc/reference/coledataobject-class.md) glissé sur la cible de déplacement.

*dwKeyState*<br/>
Contient l’état des touches de modification. Il s’agit d’une combinaison de n’importe quel nombre de ce qui suit : MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON et MK_RBUTTON.

*point*<br/>
Position actuelle de la souris par rapport à la zone cliente de la vue.

### <a name="return-value"></a>Valeur de retour

Valeur du type énuméré DROPEFFECT, qui indique le type de déplacement qui se produit si l’utilisateur a supprimé l’objet à cette position. Le type de déplacement dépend souvent de l’état de la clé actuelle, comme indiqué par *dwKeyState*. Un mappage standard des KeyStates aux valeurs DROPEFFECT est le suivant :

- DROPEFFECT_NONE l’objet de données ne peut pas être supprimé dans cette fenêtre.

- DROPEFFECT_LINK pour MK_CONTROL &#124; MK_SHIFT crée une liaison entre l’objet et son serveur.

- DROPEFFECT_COPY pour MK_CONTROL crée une copie de l’objet supprimé.

- DROPEFFECT_MOVE pour MK_ALT crée une copie de l’objet supprimé et supprime l’objet d’origine. Il s’agit généralement de l’effet de dépôt par défaut, lorsque la vue peut accepter l’objet de données.

Pour plus d’informations, consultez l’exemple de concepts avancés MFC [OCLIENT](../../overview/visual-cpp-samples.md).

### <a name="remarks"></a>Notes

L’implémentation par défaut consiste à ne rien faire et à retourner DROPEFFECT_NONE.

Substituez cette fonction pour fournir des commentaires visuels à l’utilisateur pendant l’opération glisser. Étant donné que cette fonction est appelée en continu, tout code contenu dans celle-ci doit être optimisé autant que possible. Pour plus d’informations, consultez l’article [glisser-déplacer OLE : implémenter une cible de déplacement](../../mfc/drag-and-drop-ole.md#implement-a-drop-target).

##  <a name="ondragscroll"></a>CView :: OnDragScroll

Appelée par l’infrastructure avant d’appeler [OnDragEnter](#ondragenter) ou [OnDragOver](#ondragover) pour déterminer si le point se trouve dans la zone de défilement.

```
virtual DROPEFFECT OnDragScroll(
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Paramètres

*dwKeyState*<br/>
Contient l’état des touches de modification. Il s’agit d’une combinaison de n’importe quel nombre de ce qui suit : MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON et MK_RBUTTON.

*point*<br/>
Contient l’emplacement du curseur, en pixels, par rapport à l’écran.

### <a name="return-value"></a>Valeur de retour

Valeur du type énuméré DROPEFFECT, qui indique le type de déplacement qui se produit si l’utilisateur a supprimé l’objet à cette position. Le type de déplacement dépend généralement de l’état de clé actuel indiqué par *dwKeyState*. Un mappage standard des KeyStates aux valeurs DROPEFFECT est le suivant :

- DROPEFFECT_NONE l’objet de données ne peut pas être supprimé dans cette fenêtre.

- DROPEFFECT_LINK pour MK_CONTROL &#124; MK_SHIFT crée une liaison entre l’objet et son serveur.

- DROPEFFECT_COPY pour MK_CONTROL crée une copie de l’objet supprimé.

- DROPEFFECT_MOVE pour MK_ALT crée une copie de l’objet supprimé et supprime l’objet d’origine.

- DROPEFFECT_SCROLL indique qu’une opération de défilement de glissement est sur le ou se produit dans la vue cible.

Pour plus d’informations, consultez l’exemple de concepts avancés MFC [OCLIENT](../../overview/visual-cpp-samples.md).

### <a name="remarks"></a>Notes

Substituez cette fonction lorsque vous souhaitez fournir un comportement spécial pour cet événement. L’implémentation par défaut fait défiler automatiquement les fenêtres lorsque le curseur est déplacé dans la zone de défilement par défaut à l’intérieur de la bordure de chaque fenêtre. Pour plus d’informations, consultez l’article [glisser-déplacer OLE : implémenter une cible de déplacement](../../mfc/drag-and-drop-ole.md#implement-a-drop-target).

##  <a name="ondraw"></a>CView :: OnDraw

Appelé par l’infrastructure pour restituer une image du document.

```
virtual void OnDraw(CDC* pDC) = 0;
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
Pointe vers le contexte de périphérique à utiliser pour afficher une image du document.

### <a name="remarks"></a>Notes

L’infrastructure appelle cette fonction pour effectuer l’affichage de l’écran, l’impression et l’aperçu avant impression, et elle passe un autre contexte de périphérique dans chaque cas. Il n'y a pas d'implémentation par défaut.

Vous devez substituer cette fonction pour afficher la vue du document. Vous pouvez effectuer des appels GDI (Graphics Device Interface) à l’aide de l’objet [CDC](../../mfc/reference/cdc-class.md) pointé par le paramètre *PDC* . Vous pouvez sélectionner des ressources GDI, telles que des stylets ou des polices, dans le contexte de périphérique avant de les dessiner, puis les désélectionner ultérieurement. Souvent, votre code de dessin peut être indépendant de l’appareil ; autrement dit, il ne requiert pas d’informations sur le type d’appareil qui affiche l’image.

Pour optimiser le dessin, appelez la fonction membre [RectVisible](../../mfc/reference/cdc-class.md#rectvisible) du contexte de périphérique pour savoir si un rectangle donné sera dessiné. Si vous avez besoin de faire la distinction entre l’affichage normal et l’impression, appelez la fonction membre [IsPrinting](../../mfc/reference/cdc-class.md#isprinting) du contexte de périphérique.

##  <a name="ondrop"></a>CView :: OnDrop

Appelée par l’infrastructure quand l’utilisateur relâche un objet de données sur une cible de déplacement valide.

```
virtual BOOL OnDrop(
    COleDataObject* pDataObject,
    DROPEFFECT dropEffect,
    CPoint point);
```

### <a name="parameters"></a>Paramètres

'pDataObject * pointe vers le [COleDataObject](../../mfc/reference/coledataobject-class.md) qui est déposé dans la cible de déplacement.

*dropEffect*<br/>
L’effet de dépôt que l’utilisateur a demandé.

- DROPEFFECT_COPY crée une copie de l’objet de données qui est supprimé.

- DROPEFFECT_MOVE déplace l’objet de données vers l’emplacement actuel de la souris.

- DROPEFFECT_LINK crée un lien entre un objet de données et son serveur.

*point*<br/>
Position actuelle de la souris par rapport à la zone cliente de la vue.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la suppression a réussi ; Sinon, 0.

### <a name="remarks"></a>Notes

L’implémentation par défaut ne fait rien et retourne FALSe.

Substituez cette fonction pour implémenter l’effet d’une instruction DROP OLE dans la zone cliente de la vue. L’objet de données peut être examiné via *pDataObject* pour les formats de données du presse-papiers et les données déposées au point spécifié.

> [!NOTE]
>  L’infrastructure n’appelle pas cette fonction s’il existe une substitution à [OnDropEx](#ondropex) dans cette classe d’affichage.

##  <a name="ondropex"></a>CView :: OnDropEx

Appelée par l’infrastructure quand l’utilisateur relâche un objet de données sur une cible de déplacement valide.

```
virtual DROPEFFECT OnDropEx(
    COleDataObject* pDataObject,
    DROPEFFECT dropDefault,
    DROPEFFECT dropList,
    CPoint point);
```

### <a name="parameters"></a>Paramètres

*pDataObject*<br/>
Pointe vers le [COleDataObject](../../mfc/reference/coledataobject-class.md) qui est déposé dans la cible de déplacement.

*dropDefault*<br/>
Effet choisi par l’utilisateur pour l’opération de suppression par défaut en fonction de l’état de la clé actuelle. Il peut être DROPEFFECT_NONE. Les effets de la suppression sont décrits dans la section Notes.

*Roulant*<br/>
Liste des effets de suppression pris en charge par la source de déplacement. Les valeurs d’effet de dépôt peuvent être combinées à **&#124;** l’aide de l’opération or au niveau du bit. Les effets de la suppression sont décrits dans la section Notes.

*point*<br/>
Position actuelle de la souris par rapport à la zone cliente de la vue.

### <a name="return-value"></a>Valeur de retour

Effet de déplacement résultant de la tentative de suppression à l’emplacement spécifié par *point*. Il doit s’agir de l’une des valeurs indiquées par *dropEffectList*. Les effets de la suppression sont décrits dans la section Notes.

### <a name="remarks"></a>Notes

L’implémentation par défaut consiste à ne rien faire et à retourner une valeur factice (-1) pour indiquer que l’infrastructure doit appeler le gestionnaire [OnDrop](#ondrop) .

Substituez cette fonction pour implémenter l’effet d’un glisser-déplacer avec le bouton droit de la souris. Le glissement-déplacement du bouton droit affiche généralement un menu de choix lorsque le bouton droit de la souris est relâché.

Votre remplacement de `OnDropEx` doit rechercher le bouton droit de la souris. Vous pouvez appeler [GetKeyState](/windows/win32/api/winuser/nf-winuser-getkeystate) ou stocker l’état du bouton droit de la souris à partir de votre gestionnaire [OnDragEnter](#ondragenter) .

- Si le bouton droit de la souris est enfoncé, votre remplacement doit afficher un menu contextuel qui offre la prise en charge des effets de déplacement par la source de déplacement.

   - Examinez la liste déroulante pour déterminer les *effets de suppression* pris en charge par la source de déplacement. Activez uniquement ces actions dans le menu contextuel.

   - Utilisez [SetMenuDefaultItem](/windows/win32/api/winuser/nf-winuser-setmenudefaultitem) pour définir l’action par défaut en fonction de *dropDefault*.

   - Enfin, prenez l’action indiquée par la sélection de l’utilisateur dans le menu contextuel.

- Si le bouton droit de la souris n’est pas enfoncé, votre remplacement doit le traiter en tant que requête de suppression standard. Utilisez l’effet de déplacement spécifié dans *dropDefault*. Votre remplacement peut également retourner la valeur factice (-1) pour indiquer que `OnDrop` va gérer cette opération de suppression.

Utilisez *pDataObject* pour examiner la `COleDataObject` pour le format de données du presse-papiers et les données supprimées au point spécifié.

Drop Effects décrit l’action associée à une opération de déplacement. Consultez la liste des effets de dépôt suivante :

- DROPEFFECT_NONE une suppression n’est pas autorisée.

- DROPEFFECT_COPY une opération de copie est effectuée.

- DROPEFFECT_MOVE une opération de déplacement est effectuée.

- DROPEFFECT_LINK un lien des données déplacées vers les données d’origine serait établi.

- DROPEFFECT_SCROLL indique qu’une opération de défilement de glissement est sur le ou se produit dans la cible.

Pour plus d’informations sur la définition de la commande de menu par défaut, consultez [SetMenuDefaultItem](/windows/win32/api/winuser/nf-winuser-setmenudefaultitem) dans le SDK Windows et [CMenu :: GetSafeHmenu](../../mfc/reference/cmenu-class.md#getsafehmenu) dans ce volume.

##  <a name="onendprinting"></a>CView :: OnEndPrinting

Appelé par le Framework après qu’un document a été imprimé ou affiché en aperçu.

```
virtual void OnEndPrinting(
    CDC* pDC,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
Pointe vers le contexte de l’imprimante.

*pInfo*<br/>
Pointe vers une structure [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) qui décrit le travail d’impression actif.

### <a name="remarks"></a>Notes

L’implémentation par défaut de cette fonction est sans effet. Substituez cette fonction pour libérer toutes les ressources GDI que vous avez allouées dans la fonction membre [OnBeginPrinting](#onbeginprinting) .

##  <a name="onendprintpreview"></a>CView :: OnEndPrintPreview

Appelé par le Framework lorsque l’utilisateur quitte le mode aperçu avant impression.

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

*pInfo*<br/>
Pointe vers une structure [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) qui décrit le travail d’impression actif.

*point*<br/>
Spécifie le point sur la page qui a été affiché pour la dernière fois en mode aperçu.

*pView*<br/>
Pointe vers l’objet de vue utilisé pour l’aperçu.

### <a name="remarks"></a>Notes

L’implémentation par défaut de cette fonction appelle la fonction membre [OnEndPrinting](#onendprinting) et restaure la fenêtre frame principale à l’État dans lequel elle se trouvait avant le début de l’aperçu avant impression. Substituez cette fonction pour effectuer un traitement spécial lorsque le mode aperçu est terminé. Par exemple, si vous souhaitez conserver la position de l’utilisateur dans le document lors du passage du mode aperçu au mode d’affichage normal, vous pouvez faire défiler jusqu’à l’emplacement décrit par le paramètre *point* et le membre `m_nCurPage` de la structure `CPrintInfo` vers laquelle pointe le paramètre *pinfo* .

Appelez toujours la version de la classe de base de `OnEndPrintPreview` à partir de votre substitution, en général à la fin de la fonction.

##  <a name="oninitialupdate"></a>CView :: OnInitialUpdate

Appelée par l’infrastructure après que la vue a été attachée pour la première fois au document, mais avant l’affichage initial de la vue.

```
virtual void OnInitialUpdate();
```

### <a name="remarks"></a>Notes

L’implémentation par défaut de cette fonction appelle la fonction membre [OnUpdate](#onupdate) sans informations d’indication (autrement dit, en utilisant les valeurs par défaut 0 pour le paramètre *lHint* et null pour le paramètre *pHint* ). Substituez cette fonction pour exécuter une initialisation unique qui nécessite des informations sur le document. Par exemple, si votre application comporte des documents de taille fixe, vous pouvez utiliser cette fonction pour initialiser les limites de défilement d’une vue en fonction de la taille du document. Si votre application prend en charge les documents de taille variable, utilisez [OnUpdate](#onupdate) pour mettre à jour les limites de défilement chaque fois que le document change.

##  <a name="onpreparedc"></a>CView :: OnPrepareDC

Appelée par l’infrastructure avant que la fonction membre [OnDraw](#ondraw) soit appelée pour l’affichage à l’écran et avant que la fonction membre [OnPrint](#onprint) soit appelée pour chaque page lors de l’impression ou de l’aperçu avant impression.

```
virtual void OnPrepareDC(
    CDC* pDC,
    CPrintInfo* pInfo = NULL);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
Pointe vers le contexte de périphérique à utiliser pour afficher une image du document.

*pInfo*<br/>
Pointe vers une structure [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) qui décrit le travail d’impression en cours si `OnPrepareDC` est appelé pour l’impression ou l’aperçu avant impression ; le membre `m_nCurPage` spécifie la page à imprimer. Ce paramètre a la valeur NULL si `OnPrepareDC` est appelé pour l’affichage à l’écran.

### <a name="remarks"></a>Notes

L’implémentation par défaut de cette fonction ne fait rien si la fonction est appelée pour l’affichage à l’écran. Toutefois, cette fonction est substituée dans les classes dérivées, telles que [CScrollView](../../mfc/reference/cscrollview-class.md), pour ajuster les attributs du contexte de périphérique (Device Context); par conséquent, vous devez toujours appeler l’implémentation de la classe de base au début de votre remplacement.

Si la fonction est appelée pour l’impression, l’implémentation par défaut examine les informations de page stockées dans le paramètre *pinfo* . Si la longueur du document n’a pas été spécifiée, `OnPrepareDC` suppose que le document est long d’une page et arrête la boucle d’impression après l’impression d’une page. La fonction arrête la boucle d’impression en affectant à la `m_bContinuePrinting` membre de la structure la valeur FALSe.

Remplacez `OnPrepareDC` pour l’une des raisons suivantes :

- Pour ajuster les attributs du contexte de périphérique en fonction des besoins de la page spécifiée. Par exemple, si vous devez définir le mode de mappage ou d’autres caractéristiques du contexte de périphérique, faites-le dans cette fonction.

- Pour effectuer une pagination au moment de l’impression. Normalement, vous spécifiez la longueur du document lorsque l’impression commence, à l’aide de la fonction membre [OnPreparePrinting](#onprepareprinting) . Toutefois, si vous ne connaissez pas à l’avance la durée du document (par exemple, lors de l’impression d’un nombre indéterminé d’enregistrements à partir d’une base de données), remplacez `OnPrepareDC` pour tester la fin du document lors de son impression. Lorsqu’il n’y a plus de document à imprimer, affectez la valeur FALSe au membre `m_bContinuePrinting` de la structure `CPrintInfo`.

- Pour envoyer des codes d’échappement à l’imprimante page par page. Pour envoyer des codes d’échappement à partir de `OnPrepareDC`, appelez la fonction membre `Escape` du paramètre *PDC* .

Appelez la version de la classe de base de `OnPrepareDC` au début de votre remplacement.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#183](../../mfc/codesnippet/cpp/cview-class_1.cpp)]

##  <a name="onprepareprinting"></a>CView :: OnPreparePrinting

Appelé par le Framework avant qu’un document soit imprimé ou affiché en aperçu.

```
virtual BOOL OnPreparePrinting(CPrintInfo* pInfo);
```

### <a name="parameters"></a>Paramètres

*pInfo*<br/>
Pointe vers une structure [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) qui décrit le travail d’impression actif.

### <a name="return-value"></a>Valeur de retour

Différent de zéro pour commencer l’impression ; 0 si le travail d’impression a été annulé.

### <a name="remarks"></a>Notes

L'implémentation par défaut n'exécute aucune opération.

Vous devez remplacer cette fonction pour activer l’impression et l’aperçu avant impression. Appelez la fonction membre [DoPreparePrinting](#doprepareprinting) , en lui transmettant le paramètre *pinfo* , puis retournez sa valeur de retour ; `DoPreparePrinting` affiche la boîte de dialogue Imprimer et crée un contexte de périphérique d’impression. Si vous souhaitez initialiser la boîte de dialogue Imprimer avec des valeurs autres que les valeurs par défaut, affectez des valeurs aux membres de *pinfo*. Par exemple, si vous connaissez la longueur du document, transmettez la valeur à la fonction membre [SetMaxPage](../../mfc/reference/cprintinfo-structure.md#setmaxpage) de *pinfo* avant d’appeler `DoPreparePrinting`. Cette valeur est affichée dans la zone à : de la partie plage de la boîte de dialogue Imprimer.

`DoPreparePrinting` n’affiche pas la boîte de dialogue Imprimer pour un travail en version préliminaire. Si vous souhaitez contourner la boîte de dialogue Imprimer pour un travail d’impression, vérifiez que le membre `m_bPreview` de *pinfo* a la valeur false, puis affectez-lui la valeur true avant de le passer à `DoPreparePrinting`; Réinitialisez-la sur FALSe par la suite.

Si vous devez effectuer des initialisations qui requièrent l’accès à l’objet `CDC` représentant le contexte de périphérique d’impression (par exemple, si vous avez besoin de connaître la taille de la page avant de spécifier la longueur du document), substituez la fonction membre `OnBeginPrinting`.

Si vous souhaitez définir la valeur des membres `m_nNumPreviewPages` ou `m_strPageDesc` du paramètre *pinfo* , faites-le après l’appel de `DoPreparePrinting`. La fonction membre `DoPreparePrinting` définit `m_nNumPreviewPages` sur la valeur trouvée dans le de l’application. Fichier INI et définit `m_strPageDesc` à sa valeur par défaut.

### <a name="example"></a>Exemple

  Substituez `OnPreparePrinting` et appelez `DoPreparePrinting` à partir de la substitution afin que l’infrastructure affiche une boîte de dialogue Imprimer et crée un contrôleur de périphérique d’imprimante pour vous.

[!code-cpp[NVC_MFCDocView#184](../../mfc/codesnippet/cpp/cview-class_2.cpp)]

Si vous connaissez le nombre de pages contenues dans le document, définissez la page maximum dans `OnPreparePrinting` avant d’appeler `DoPreparePrinting`. L’infrastructure affiche le nombre de pages maximal dans la zone « à » de la boîte de dialogue Imprimer.

[!code-cpp[NVC_MFCDocView#185](../../mfc/codesnippet/cpp/cview-class_3.cpp)]

##  <a name="onprint"></a>CView :: OnPrint

Appelé par le Framework pour imprimer ou afficher un aperçu d’une page du document.

```
virtual void OnPrint(
    CDC* pDC,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>Paramètres

*pDC*<br/>
Pointe vers le contexte de l’imprimante.

*pInfo*<br/>
Pointe vers une structure de `CPrintInfo` qui décrit le travail d’impression en cours.

### <a name="remarks"></a>Notes

Pour chaque page imprimée, l’infrastructure appelle cette fonction immédiatement après avoir appelé la fonction membre [OnPrepareDC](#onpreparedc) . La page en cours d’impression est spécifiée par le membre `m_nCurPage` de la structure [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) vers laquelle *pinfo* pointe. L’implémentation par défaut appelle la fonction membre [OnDraw](#ondraw) et lui passe le contexte de périphérique d’impression.

Remplacez cette fonction pour l’une des raisons suivantes :

- Pour autoriser l’impression des documents multipages. Affiche uniquement la partie du document qui correspond à la page actuellement imprimée. Si vous utilisez `OnDraw` pour effectuer le rendu, vous pouvez ajuster l’origine de la fenêtre d’affichage afin que seule la partie appropriée du document soit imprimée.

- Pour donner à l’image imprimée une apparence différente de celle de l’image d’écran (autrement dit, si votre application n’est pas WYSIWYG). Au lieu de passer le contexte de périphérique d’impression à `OnDraw`, utilisez le contexte de périphérique pour afficher une image à l’aide des attributs non affichés à l’écran.

   Si vous avez besoin de ressources GDI pour l’impression que vous n’utilisez pas pour l’affichage à l’écran, sélectionnez-les dans le contexte de périphérique avant de les dessiner et désélectionnez-les par la suite. Ces ressources GDI doivent être allouées dans [OnBeginPrinting](#onbeginprinting) et libérées dans [OnEndPrinting](#onendprinting).

- Pour implémenter des en-têtes ou des pieds de page. Vous pouvez toujours utiliser `OnDraw` pour effectuer le rendu en restreignant la zone sur laquelle il peut imprimer.

Notez que le `m_rectDraw` membre du paramètre *pinfo* décrit la zone imprimable de la page en unités logiques.

N’appelez pas `OnPrepareDC` dans votre remplacement de `OnPrint`; le Framework appelle `OnPrepareDC` automatiquement avant d’appeler `OnPrint`.

### <a name="example"></a>Exemple

Voici un squelette pour une fonction de `OnPrint` substituée :

[!code-cpp[NVC_MFCDocView#186](../../mfc/codesnippet/cpp/cview-class_4.cpp)]

Pour un autre exemple, consultez [CRichEditView ::P rintinsiderect](../../mfc/reference/cricheditview-class.md#printinsiderect).

##  <a name="onscroll"></a>CView :: OnScroll

Appelé par l’infrastructure pour déterminer si le défilement est possible.

```
virtual BOOL OnScroll(
    UINT nScrollCode,
    UINT nPos,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>Paramètres

*nScrollCode*<br/>
Code-barres de défilement qui indique la requête de défilement de l’utilisateur. Ce paramètre est composé de deux parties : un octet de poids faible, qui détermine le type de défilement horizontalement et un octet de poids fort, qui détermine le type de défilement qui se produit verticalement :

- SB_BOTTOM fait défiler vers le bas.

- SB_LINEDOWN fait défiler d’une ligne vers le dessous.

- SB_LINEUP fait défiler d’une ligne vers le haut.

- SB_PAGEDOWN fait défiler une page vers le dessous.

- SB_PAGEUP fait défiler d’une page vers le haut.

- SB_THUMBTRACK fait glisser la case de défilement à la position spécifiée. La position actuelle est spécifiée dans *nPos*.

- SB_TOP fait défiler vers le haut.

*nPos*<br/>
Contient la position de la zone de défilement en cours si le code de la barre de défilement est SB_THUMBTRACK ; dans le cas contraire, il n’est pas utilisé. Selon la plage de défilement initiale, *nPos* peut être négatif et doit être casté en **int** si nécessaire.

*bDoScroll*<br/>
Détermine si vous devez réellement effectuer l’action de défilement spécifiée. Si la valeur est TRUE, le défilement doit avoir lieu ; Si la valeur est FALSe, le défilement ne doit pas se produire.

### <a name="return-value"></a>Valeur de retour

Si *bDoScroll* a la valeur true et que la vue a fait l’effet d’un défilement, puis retourne une valeur différente de zéro ; Sinon, 0. Si *bDoScroll* a la valeur false, retourne la valeur que vous auriez renvoyée si *bDoScroll* était true, même si vous n’effectuez pas réellement le défilement.

### <a name="remarks"></a>Notes

Dans un cas, cette fonction est appelée par l’infrastructure avec *bDoScroll* défini sur true lorsque la vue reçoit un message de barre de défilement. Dans ce cas, vous devez faire défiler la vue. Dans le cas contraire, cette fonction est appelée avec *bDoScroll* défini sur false lorsqu’un élément OLE est déplacé initialement dans la zone de défilement automatique d’une cible de déplacement avant que le défilement ait lieu. Dans ce cas, vous ne devez pas faire défiler la vue.

##  <a name="onscrollby"></a>CView :: OnScrollBy

Appelée par l’infrastructure quand l’utilisateur affiche une zone au-delà de la vue actuelle du document, soit en faisant glisser un élément OLE sur les bordures actuelles de la vue, soit en manipulant les barres de défilement verticales ou horizontales.

```
virtual BOOL OnScrollBy(
    CSize sizeScroll,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>Paramètres

*sizeScroll*<br/>
Nombre de pixels défilant horizontalement et verticalement.

*bDoScroll*<br/>
Détermine si le défilement de la vue se produit. Si la valeur est TRUE, le défilement a lieu ; Si la valeur est FALSe, le défilement n’a pas lieu.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la vue a pu être défilée ; Sinon, 0.

### <a name="remarks"></a>Notes

Dans les classes dérivées, cette méthode vérifie si la vue est défilante dans la direction demandée par l’utilisateur, puis met à jour la nouvelle région si nécessaire. Cette fonction est appelée automatiquement par [CWnd :: OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll) et [CWnd :: OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll) pour effectuer la requête de défilement proprement dite.

L’implémentation par défaut de cette méthode ne modifie pas la vue, mais si elle n’est pas appelée, la vue ne défile pas dans une classe dérivée de `CScrollView`.

Si la largeur ou la hauteur du document dépasse 32767 pixels, le défilement au-delà de 32767 échouera, car `OnScrollBy` est appelé avec un argument *sizeScroll* non valide.

##  <a name="onupdate"></a>CView :: OnUpdate

Appelé par le Framework après la modification du document de la vue ; Cette fonction est appelée par [CDocument :: UpdateAllViews](../../mfc/reference/cdocument-class.md#updateallviews) et permet à la vue de mettre à jour son affichage pour refléter ces modifications.

```
virtual void OnUpdate(
    CView* pSender,
    LPARAM lHint,
    CObject* pHint);
```

### <a name="parameters"></a>Paramètres

*pSender*<br/>
Pointe vers la vue qui a modifié le document, ou NULL si toutes les vues doivent être mises à jour.

*lHint*<br/>
Contient des informations sur les modifications.

*pHint*<br/>
Pointe vers un objet qui stocke des informations sur les modifications.

### <a name="remarks"></a>Notes

Elle est également appelée par l’implémentation par défaut de [OnInitialUpdate](#oninitialupdate). L’implémentation par défaut invalide la totalité de la zone client, en la marquant pour la peinture lors de la réception du message de WM_PAINT suivant. Remplacez cette fonction si vous souhaitez mettre à jour uniquement les régions qui mappent aux parties modifiées du document. Pour ce faire, vous devez transmettre des informations sur les modifications à l’aide des paramètres de l’indicateur.

Pour utiliser *lHint*, définissez des valeurs d’indication spéciales, en général un masque de masque ou un type énuméré, et faites en sorte que le document passe l’une de ces valeurs. Pour utiliser *pHint*, dérivez une classe hint de [CObject](../../mfc/reference/cobject-class.md) et faites en sorte que le document passe un pointeur vers un objet Hint ; lors du remplacement d' `OnUpdate`, utilisez la fonction membre [CObject :: IsKindOf](../../mfc/reference/cobject-class.md#iskindof) pour déterminer le type d’exécution de l’objet hint.

En général, vous ne devez effectuer aucun dessin directement à partir de `OnUpdate`. Au lieu de cela, déterminez le rectangle qui décrit, dans les coordonnées de l’appareil, la zone qui nécessite une mise à jour ; transmettez ce rectangle à [CWnd :: InvalidateRect](../../mfc/reference/cwnd-class.md#invalidaterect). La peinture se produit lors de la prochaine réception d’un message de [WM_PAINT](/windows/win32/gdi/wm-paint) .

Si *lHint* a la valeur 0 et que *pHint* a la valeur null, le document a envoyé une notification de mise à jour générique. Si une vue reçoit une notification de mise à jour générique, ou si elle ne peut pas décoder les indicateurs, elle doit invalider sa zone cliente entière.

## <a name="see-also"></a>Voir aussi

[Exemple MFC MDIDOCVW](../../overview/visual-cpp-samples.md)<br/>
[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[CFrameWnd, classe](../../mfc/reference/cframewnd-class.md)<br/>
[CSplitterWnd, classe](../../mfc/reference/csplitterwnd-class.md)<br/>
[CDC, classe](../../mfc/reference/cdc-class.md)<br/>
[CDocTemplate, classe](../../mfc/reference/cdoctemplate-class.md)<br/>
[CDocument, classe](../../mfc/reference/cdocument-class.md)
