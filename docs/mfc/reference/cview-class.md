---
title: Classe CView | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9ccb638669712222cac2dee522bf729766a4bc93
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46402263"
---
# <a name="cview-class"></a>CView (classe)

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
|[CView::DoPreparePrinting](#doprepareprinting)|Affiche la boîte de dialogue Imprimer et crée le contexte de l’imprimante ; appeler lors de la substitution du `OnPreparePrinting` fonction membre.|
|[CView::GetDocument](#getdocument)|Retourne le document associé à la vue.|
|[CView::IsSelected](#isselected)|Teste si un élément de document est sélectionné. Requis pour la prise en charge OLE.|
|[CView::OnDragEnter](#ondragenter)|Appelé lorsqu’un élément est tout d’abord déplacé vers la zone de glisser-déplacer d’une vue.|
|[CView::OnDragLeave](#ondragleave)|Appelé lorsqu’un élément glissé quitte la zone de glisser-déplacer d’une vue.|
|[CView::OnDragOver](#ondragover)|Appelé lorsqu’un élément est glissé sur la zone de glisser-déplacer d’une vue.|
|[CView::OnDragScroll](#ondragscroll)|Appelé pour déterminer si le curseur est déplacé dans la zone de défilement de la fenêtre.|
|[CView::OnDrop](#ondrop)|Appelé lorsqu’un élément a été supprimé dans la zone de glisser-déplacer d’une vue, le gestionnaire par défaut.|
|[CView::OnDropEx](#ondropex)|Appelé lorsqu’un élément a été supprimé dans la zone de glisser-déplacer d’une vue, gestionnaire principal.|
|[CView::OnInitialUpdate](#oninitialupdate)|Appelé après que la première, une vue est attachée à un document.|
|[CView::OnPrepareDC](#onpreparedc)|Appelé avant le `OnDraw` fonction membre est appelée pour afficher l’écran ou la `OnPrint` fonction membre est appelée pour l’impression ou Aperçu avant impression.|
|[CView::OnScroll](#onscroll)|Appelé lorsque vous faites glisser des éléments OLE au-delà des frontières de la vue.|
|[CView::OnScrollBy](#onscrollby)|Appelé lorsqu’une vue qui contient les éléments OLE sur place actifs défile.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CView::OnActivateFrame](#onactivateframe)|Appelé lorsque la fenêtre frame contenant la vue est activée ou désactivée.|
|[CView::OnActivateView](#onactivateview)|Appelé lorsqu’une vue est activée.|
|[CView::OnBeginPrinting](#onbeginprinting)|Appelée lorsqu’un travail d’impression commence ; méthode override pour allouer des ressources d’interface (GDI) appareil graphics.|
|[CView::OnDraw](#ondraw)|Appelé pour restituer une image du document pour la capture d’écran, d’impression ou Aperçu avant impression. Implémentation requis.|
|[CView::OnEndPrinting](#onendprinting)|Appelée lorsqu’un travail d’impression se termine ; méthode override pour libérer des ressources GDI.|
|[CView::OnEndPrintPreview](#onendprintpreview)|Appelé lorsque le mode aperçu est fermée.|
|[Comme CView::OnPreparePrinting](#onprepareprinting)|Appelé avant qu’un document soit imprimé ou affiché en aperçu ; méthode override pour initialiser la boîte de dialogue Imprimer.|
|[CView::OnPrint](#onprint)|Appelé pour imprimer ou afficher une page du document.|
|[CView::OnUpdate](#onupdate)|Appelé pour avertir une vue de son document a été modifié.|

## <a name="remarks"></a>Notes

Une vue est attachée à un document et fait Office d’intermédiaire entre le document et l’utilisateur : la vue restitue une image du document sur l’écran ou l’imprimante et interprète les entrées utilisateur en tant qu’opérations destinées au document.

Une vue est un enfant d’une fenêtre frame. Plusieurs vues peuvent partager une fenêtre frame, comme dans le cas d’une fenêtre fractionnée. La relation entre une vue classe, une classe de fenêtre frame et une classe de document est établie par un `CDocTemplate` objet. Lorsque l’utilisateur ouvre une nouvelle fenêtre ou fractionne un existant un, le framework construit une nouvelle vue et l’attache au document.

Une vue peut être attachée à un seul document, mais un document peut avoir plusieurs vues attachées à la fois, par exemple, si le document est affiché dans une fenêtre fractionnée ou dans plusieurs fenêtres enfants dans une application d’interface (multidocument MDI) document. Votre application peut prendre en charge différents types d’affichages pour un type de document donné ; par exemple, un programme de traitement de texte peut fournir une vue de texte complet d’un document et une vue hiérarchique qui montre uniquement les titres de section. Ces différents types de vues peuvent être placés dans des fenêtres frame distinct ou dans des volets distincts d’une fenêtre frame unique si vous utilisez une fenêtre fractionnée.

Une vue peut être chargée de gérer différents types d’entrée, telles que l’entrée au clavier, les entrées de souris ou entrée par le biais de glisser-déplacer, ainsi que les commandes de menus, barres d’outils ou des barres de défilement. Une vue reçoit des commandes transmises par sa fenêtre frame. Si la vue ne gère pas une commande donnée, il transfère la commande à son document associé. Comme toutes les cibles de commande, une vue gère les messages via une table des messages.

La vue est chargée d’afficher et modifier les données du document, mais ne pas pour les conserver en mémoire. Le document fournit une vue avec les informations nécessaires sur ses données. Vous pouvez laisser l’accès de la vue directement des membres de données du document, ou vous pouvez fournir des fonctions membres dans la classe de document pour la classe d’affichage à appeler.

Lorsque les données d’un document est modifié, la vue des modifications appelle généralement la [CDocument::UpdateAllViews](../../mfc/reference/cdocument-class.md#updateallviews) (fonction) pour le document, ce qui informe toutes les autres vues en appelant le `OnUpdate` fonction membre chaque. L’implémentation par défaut de `OnUpdate` invalide la zone cliente de la vue. Vous pouvez la remplacer pour invalider les régions de la zone cliente correspondant aux parties modifiées du document.

Pour utiliser `CView`, dérivez une classe à partir de celui-ci et implémenter la `OnDraw` fonction membre pour effectuer la capture d’écran. Vous pouvez également utiliser `OnDraw` pour effectuer l’impression et Aperçu avant impression. Le framework gère la boucle d’impression pour l’impression et aperçu de votre document.

Une vue gère les messages de barre de défilement avec les [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll) et [CWnd::OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll) fonctions membres. Vous pouvez implémenter dans ces fonctions de gestion de messages de barre de défilement, ou vous pouvez utiliser la `CView` classe dérivée [CScrollView](../../mfc/reference/cscrollview-class.md) pour la gestion du défilement.

En outre `CScrollView`, la bibliothèque Microsoft Foundation Class fournit neuf autres classes dérivées de `CView`:

- [CCtrlView](../../mfc/reference/cctrlview-class.md), une vue qui permet l’utilisation de document - vue architecture en arborescence de la liste et riches contrôles d’édition.

- [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md), une vue qui affiche les enregistrements de base de données dans les contrôles de boîte de dialogue.

- [CEditView](../../mfc/reference/ceditview-class.md), un affichage qui fournit un éditeur de texte multiligne. Vous pouvez utiliser un `CEditView` objet sous la forme d’un contrôle dans une boîte de dialogue, ainsi que d’une vue sur un document.

- [CFormView](../../mfc/reference/cformview-class.md), une vue déroulante qui contient les contrôles de boîte de dialogue et est basée sur une ressource de modèle de boîte de dialogue.

- [CListView](../../mfc/reference/clistview-class.md), une vue qui permet l’utilisation de document - architecture vue avec les contrôles de liste.

- [CRecordView](../../mfc/reference/crecordview-class.md), une vue qui affiche les enregistrements de base de données dans les contrôles de boîte de dialogue.

- [CRichEditView](../../mfc/reference/cricheditview-class.md), une vue qui permet l’utilisation de document - vue architecture riches avec des contrôles d’édition.

- [CScrollView](../../mfc/reference/cscrollview-class.md), une vue qui fournit automatiquement la prise en charge de défilement.

- [CTreeView](../../mfc/reference/ctreeview-class.md), une vue qui permet l’utilisation de document - architecture vue avec les contrôles d’arborescence.

Le `CView` classe a également une classe d’implémentation dérivée nommée `CPreviewView`, qui est utilisé par l’infrastructure pour effectuer l’aperçu avant impression. Cette classe prend en charge les fonctionnalités propres à la fenêtre d’aperçu avant impression, par exemple une barre d’outils, version préliminaire page unique ou double, et le zoom, qui est, une augmentation de l’image affichée en aperçu. Vous n’avez pas besoin d’appeler ou substituer des `CPreviewView`de fonctions membres, sauf si vous souhaitez implémenter votre propre interface pour l’aperçu avant impression (par exemple, si vous souhaitez prendre en charge la modification dans le mode Aperçu avant impression). Pour plus d’informations sur l’utilisation de `CView`, consultez [Architecture Document/vue](../../mfc/document-view-architecture.md) et [l’impression](../../mfc/printing.md). En outre, consultez [30 de Note technique](../../mfc/tn030-customizing-printing-and-print-preview.md) pour plus d’informations sur la personnalisation de l’aperçu avant impression.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CView`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxwin.h

##  <a name="cview"></a>  CView::CView

Construit un objet `CView`.

```
CView();
```

### <a name="remarks"></a>Notes

Le framework appelle le constructeur lorsqu’une nouvelle fenêtre frame est créée, ou une fenêtre est fractionnée. Remplacer le [OnInitialUpdate](#oninitialupdate) fonction membre pour initialiser la vue, une fois que le document est attaché.

##  <a name="doprepareprinting"></a>  CView::DoPreparePrinting

Appelez cette fonction à partir de votre substitution de [OnPreparePrinting](#onprepareprinting) pour appeler la boîte de dialogue d’impression et de créer un contexte de périphérique.

```
BOOL DoPreparePrinting(CPrintInfo* pInfo);
```

### <a name="parameters"></a>Paramètres

*pInfo*<br/>
Pointe vers un [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) structure qui décrit le travail d’impression en cours.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’impression ou Aperçu avant impression peut commencer. 0 si l’opération a été annulée.

### <a name="remarks"></a>Notes

Comportement de cette fonction varie selon qu’il est appelé pour l’impression ou Aperçu avant impression (spécifié par le `m_bPreview` membre de la *pInfo* paramètre). Si un fichier est imprimé, cette fonction appelle la boîte de dialogue Imprimer, en utilisant les valeurs dans le [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) qui structure *pInfo* pointe vers ; une fois que l’utilisateur a fermé la boîte de dialogue, la fonction crée un contexte de l’imprimante en fonction des paramètres de l’utilisateur spécifié dans la boîte de dialogue et retourne ce contexte de périphérique via le *pInfo* paramètre. Ce contexte de périphérique est utilisé pour imprimer le document.

Si un fichier est affiché en aperçu, cette fonction crée un contexte de périphérique à l’aide des paramètres de l’imprimante actuelle ; ce contexte de périphérique est utilisé pour simuler l’imprimante pendant la version préliminaire.

##  <a name="getdocument"></a>  CView::GetDocument

Appelez cette fonction pour obtenir un pointeur vers le document de la vue.

```
CDocument* GetDocument() const;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur vers le [CDocument](../../mfc/reference/cdocument-class.md) objet associé à la vue. NULL si la vue n’est pas attachée à un document.

### <a name="remarks"></a>Notes

Cela vous permet d’appeler des fonctions de membre du document.

##  <a name="isselected"></a>  CView::IsSelected

Appelé par l’infrastructure pour vérifier si l’élément de document spécifié est sélectionné.

```
virtual BOOL IsSelected(const CObject* pDocItem) const;
```

### <a name="parameters"></a>Paramètres

*pDocItem*<br/>
Pointe vers l’élément de document en cours de test.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’élément de document spécifié est sélectionné ; sinon 0.

### <a name="remarks"></a>Notes

L’implémentation par défaut de cette fonction retourne FALSE. Remplacez cette fonction si vous implémentez à l’aide de la sélection [CDocItem](../../mfc/reference/cdocitem-class.md) objets. Vous devez substituer cette fonction si votre vue contient des éléments OLE.

##  <a name="onactivateframe"></a>  CView::OnActivateFrame

Appelé par l’infrastructure lors de la fenêtre frame contenant la vue est activée ou désactivée.

```
virtual void OnActivateFrame(
    UINT nState,
    CFrameWnd* pFrameWnd);
```

### <a name="parameters"></a>Paramètres

*nState*<br/>
Spécifie si la fenêtre frame est activée ou désactivée. Il peut prendre l’une des valeurs suivantes :

- WA_INACTIVE la fenêtre frame est en cours de désactivation.

- WA_ACTIVE la fenêtre frame est activée par une méthode autre qu’une souris cliquez sur (par exemple, à l’aide de l’interface de clavier pour sélectionner la fenêtre).

- WA_CLICKACTIVE la fenêtre frame est activé par un clic de souris

*pFrameWnd*<br/>
Pointeur vers la fenêtre frame qui doit être activé.

### <a name="remarks"></a>Notes

Remplacez cette fonction membre si vous souhaitez effectuer un traitement spécial lors de la fenêtre frame associée à la vue est activée ou désactivée. Par exemple, [CFormView](../../mfc/reference/cformview-class.md) effectue ce remplacement lorsqu’il enregistre et restaure le contrôle qui a le focus.

##  <a name="onactivateview"></a>  CView::OnActivateView

Appelé par le framework lorsqu’une vue est activée ou désactivée.

```
virtual void OnActivateView(
    BOOL bActivate,
    CView* pActivateView,
    CView* pDeactiveView);
```

### <a name="parameters"></a>Paramètres

*bActivate*<br/>
Indique si la vue est activée ou désactivée.

*pActivateView*<br/>
Pointe vers l’objet de vue qui est en cours d’activation.

*pDeactiveView*<br/>
Pointe vers l’objet de vue qui est en cours de désactivation.

### <a name="remarks"></a>Notes

L’implémentation par défaut de cette fonction définit le focus à la vue en cours d’activation. Remplacez cette fonction si vous souhaitez effectuer un traitement spécial lorsqu’une vue est activée ou désactivée. Par exemple, si vous souhaitez fournir des aides visuelles spéciales qui distinguent la vue active à partir des vues inactives, examinez le *bActivate* paramètre et mettre à jour d’apparence de la vue en conséquence.

Le *pActivateView* et *pDeactiveView* paramètres pointent vers la même vue si la fenêtre frame principale de l’application est activée sans aucun changement dans la vue active, par exemple, si le focus est en cours. transférés à partir d’une autre application à celui-ci, plutôt que d’une vue à l’autre au sein de l’application ou lors du passage entre les fenêtres enfants MDI. Cela permet une vue à nouveau de réaliser sa palette, si nécessaire.

Ces paramètres diffèrent lorsque [CFrameWnd::SetActiveView](../../mfc/reference/cframewnd-class.md#setactiveview) est appelée avec une vue qui est différente de celui que [CFrameWnd::GetActiveView](../../mfc/reference/cframewnd-class.md#getactiveview) retournerait. Cela se produit souvent avec les fenêtres fractionnées.

##  <a name="onbeginprinting"></a>  CView::OnBeginPrinting

Appelé par l’infrastructure au début d’un travail d’impression ou d’aperçu avant impression, après que `OnPreparePrinting` a été appelé.

```
virtual void OnBeginPrinting(
    CDC* pDC,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>Paramètres

*contrôleur de domaine principal*<br/>
Pointe vers le contexte de l’imprimante.

*pInfo*<br/>
Pointe vers un [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) structure qui décrit le travail d’impression en cours.

### <a name="remarks"></a>Notes

L’implémentation par défaut de cette fonction est sans effet. Remplacez cette fonction pour allouer des ressources GDI, telles que des stylets ou des polices, nécessaires précisément pour l’impression. Sélectionnez les objets GDI dans le contexte de périphérique de la [OnPrint](#onprint) fonction membre pour chaque page qui les utilise. Si vous utilisez le même objet d’affichage pour l’affichage et l’impression d’écran, utilisez des variables distinctes pour les ressources GDI nécessaires à chaque affichage ; vous pourrez ainsi mettre à jour l’écran pendant l’impression.

Vous pouvez aussi utiliser cette fonction pour exécuter des initialisations qui dépendent des propriétés du contexte de l’imprimante. Par exemple, le nombre de pages nécessaires à l’impression du document peut dépendre des paramètres que l’utilisateur a spécifiés dans la boîte de dialogue d’impression (comme la longueur de page). Dans ce cas, vous ne pouvez pas spécifier la longueur du document dans le [OnPreparePrinting](#onprepareprinting) fonction membre, où vous le feriez normalement ; vous devez attendre que le contexte de l’imprimante a été créé en fonction des paramètres de la boîte de dialogue. [OnBeginPrinting](#onbeginprinting) est la première fonction substituable qui vous donne accès à la [CDC](../../mfc/reference/cdc-class.md) objet représentant le contexte de l’imprimante, vous pouvez donc définir la longueur du document à partir de cette fonction. Notez que si la longueur du document n’est pas spécifiée à ce stade, aucune barre de défilement ne s’affiche pendant l’aperçu avant impression.

##  <a name="ondragenter"></a>  CView::OnDragEnter

Appelé par le framework lorsque la souris pénètre pour la première fois dans la région qui ne défilent pas de la fenêtre de cible de dépôt.

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
Contient l’état des touches de modification. Il s’agit d’une combinaison d’un nombre quelconque de la commande suivante : MK_CONTROL MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON et MK_RBUTTON.

*point*<br/>
La position de la souris actuelle par rapport à la zone cliente de la vue.

### <a name="return-value"></a>Valeur de retour

Une valeur à partir de la DROPEFFECT type énuméré, ce qui indique le type de dépôt qui se produirait si l’objet à supprimer de l’utilisateur à cette position. Le type de liste dépend généralement de l’état de la clé actuelle indiquée par *dwKeyState*. Un mappage standard des États clés pour les valeurs DROPEFFECT est :

- DROPEFFECT_NONE l’objet de données ne peut pas être supprimé dans cette fenêtre.

- DROPEFFECT_LINK pour MK_CONTROL &#124; MK_SHIFT crée une liaison entre l’objet et son serveur.

- DROPEFFECT_COPY pour MK_CONTROL crée une copie de l’objet déplacé.

- DROPEFFECT_MOVE pour MK_ALT crée une copie de l’objet déplacé et supprimer l’objet d’origine. Il s’agit généralement l’effet de dépôt par défaut, lorsque la vue peut accepter cet objet de données.

Pour plus d’informations, consultez l’exemple de Concepts avancés MFC [OCLIENT](../../visual-cpp-samples.md).

### <a name="remarks"></a>Notes

Implémentation par défaut consiste à ne rien faire et retourner DROPEFFECT_NONE.

Remplacez cette fonction pour vous préparer à des appels ultérieurs à la [OnDragOver](#ondragover) fonction membre. Les données requises à partir de l’objet de données doivent être récupérées pour l’instant pour une utilisation ultérieure dans le `OnDragOver` fonction membre. La vue doit également être mis à jour pour l’instant pour donner la rétroaction visuelle. Pour plus d’informations, consultez l’article [glisser- déposer : implémentation d’une cible de dépôt](../../mfc/drag-and-drop-implementing-a-drop-target.md).

##  <a name="ondragleave"></a>  CView::OnDragLeave

Appelé par l’infrastructure pendant une opération glisser lorsque la souris est déplacée en dehors de la zone de dépôt valide pour cette fenêtre.

```
virtual void OnDragLeave();
```

### <a name="remarks"></a>Notes

Substituez cette fonction si la vue actuelle doit nettoyer toutes les actions effectuées au cours de [OnDragEnter](#ondragenter) ou [OnDragOver](#ondragover) appels, tels que la suppression des commentaires utilisateur visuelle pendant que l’objet a été glisser -déplacer .

##  <a name="ondragover"></a>  CView::OnDragOver

Appelé par l’infrastructure pendant une opération glisser lorsque la souris est placée sur la fenêtre cible du déplacement.

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
Contient l’état des touches de modification. Il s’agit d’une combinaison d’un nombre quelconque de la commande suivante : MK_CONTROL MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON et MK_RBUTTON.

*point*<br/>
La position actuelle de la souris par rapport à la zone d’affichage client.

### <a name="return-value"></a>Valeur de retour

Une valeur à partir de la DROPEFFECT type énuméré, ce qui indique le type de dépôt qui se produirait si l’objet à supprimer de l’utilisateur à cette position. Le type de dépôt souvent dépend de l’état actuel de la clé comme indiqué par *dwKeyState*. Un mappage standard des États clés pour les valeurs DROPEFFECT est :

- DROPEFFECT_NONE l’objet de données ne peut pas être supprimé dans cette fenêtre.

- DROPEFFECT_LINK pour MK_CONTROL &#124; MK_SHIFT crée une liaison entre l’objet et son serveur.

- DROPEFFECT_COPY pour MK_CONTROL crée une copie de l’objet déplacé.

- DROPEFFECT_MOVE pour MK_ALT crée une copie de l’objet déplacé et supprimer l’objet d’origine. Il s’agit généralement l’effet de dépôt par défaut, lorsque la vue peut accepter l’objet de données.

Pour plus d’informations, consultez l’exemple de Concepts avancés MFC [OCLIENT](../../visual-cpp-samples.md).

### <a name="remarks"></a>Notes

L’implémentation par défaut consiste à ne rien faire et retourner DROPEFFECT_NONE.

Remplacez cette fonction pour donner la rétroaction visuelle au cours de l’opération glisser. Dans la mesure où cette fonction est appelée en permanence, n’importe quel code qu’elle contient doit être optimisé autant que possible. Pour plus d’informations, consultez l’article [glisser- déposer : implémentation d’une cible de dépôt](../../mfc/drag-and-drop-implementing-a-drop-target.md).

##  <a name="ondragscroll"></a>  CView::OnDragScroll

Appelé par le framework avant d’appeler [OnDragEnter](#ondragenter) ou [OnDragOver](#ondragover) pour déterminer si le point se trouve dans la zone de défilement.

```
virtual DROPEFFECT OnDragScroll(
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Paramètres

*dwKeyState*<br/>
Contient l’état des touches de modification. Il s’agit d’une combinaison d’un nombre quelconque de la commande suivante : MK_CONTROL MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON et MK_RBUTTON.

*point*<br/>
Contient l’emplacement du curseur, en pixels, par rapport à l’écran.

### <a name="return-value"></a>Valeur de retour

Une valeur à partir de la DROPEFFECT type énuméré, ce qui indique le type de dépôt qui se produirait si l’objet à supprimer de l’utilisateur à cette position. Le type de liste dépend généralement de l’état de la clé actuelle indiquée par *dwKeyState*. Un mappage standard des États clés pour les valeurs DROPEFFECT est :

- DROPEFFECT_NONE l’objet de données ne peut pas être supprimé dans cette fenêtre.

- DROPEFFECT_LINK pour MK_CONTROL &#124; MK_SHIFT crée une liaison entre l’objet et son serveur.

- DROPEFFECT_COPY pour MK_CONTROL crée une copie de l’objet déplacé.

- DROPEFFECT_MOVE pour MK_ALT crée une copie de l’objet déplacé et supprimer l’objet d’origine.

- DROPEFFECT_SCROLL indique qu’une opération glisser de défilement est sur le point de se produire ou se produit dans la vue cible.

Pour plus d’informations, consultez l’exemple de Concepts avancés MFC [OCLIENT](../../visual-cpp-samples.md).

### <a name="remarks"></a>Notes

Remplacez cette fonction lorsque vous souhaitez fournir un comportement spécial pour cet événement. L’implémentation par défaut fait défiler automatiquement windows lorsque le curseur est déplacé dans la zone de défilement par défaut à l’intérieur de la bordure de chaque fenêtre. Pour plus d’informations, consultez l’article [glisser- déposer : implémentation d’une cible de dépôt](../../mfc/drag-and-drop-implementing-a-drop-target.md).

##  <a name="ondraw"></a>  CView::OnDraw

Appelé par l’infrastructure pour afficher une image du document.

```
virtual void OnDraw(CDC* pDC) = 0;
```

### <a name="parameters"></a>Paramètres

*contrôleur de domaine principal*<br/>
Pointe vers le contexte de périphérique à utiliser pour le rendu d’une image du document.

### <a name="remarks"></a>Notes

L’infrastructure appelle cette fonction pour effectuer une capture d’écran, l’impression et Aperçu avant impression, et transmet un contexte de périphérique différent dans chaque cas. Il n'y a pas d'implémentation par défaut.

Vous devez substituer cette fonction pour afficher votre vue du document. Vous pouvez effectuer les appels de l’interface (GDI) périphérique graphique à l’aide de la [CDC](../../mfc/reference/cdc-class.md) objet vers lequel pointe le *pDC* paramètre. Vous pouvez sélectionner des ressources GDI, telles que des stylets ou des polices, dans le contexte de périphérique avant le dessin et les désélectionner par la suite. Fréquence à laquelle votre code de dessin peut être indépendant du périphérique ; Autrement dit, il ne nécessite pas d’informations sur le type de périphérique affiche l’image.

Pour optimiser le dessin, appelez le [RectVisible](../../mfc/reference/cdc-class.md#rectvisible) fonction membre du contexte de périphérique pour déterminer si un rectangle donné sera dessiné. Si vous avez besoin de faire la distinction entre la capture d’écran normal et l’impression, appelez le [IsPrinting](../../mfc/reference/cdc-class.md#isprinting) fonction membre du contexte de périphérique.

##  <a name="ondrop"></a>  CView::OnDrop

Appelé par l’infrastructure lorsque l’utilisateur relâche un objet de données sur une cible de dépôt valide.

```
virtual BOOL OnDrop(
    COleDataObject* pDataObject,
    DROPEFFECT dropEffect,
    CPoint point);
```

### <a name="parameters"></a>Paramètres

« pDataObject * pointe vers le [COleDataObject](../../mfc/reference/coledataobject-class.md) qui est déposé dans la cible de déplacement.

*dropEffect*<br/>
L’effet que l’utilisateur a demandé.

- DROPEFFECT_COPY crée une copie de l’objet de données en cours de suppression.

- DROPEFFECT_MOVE déplace l’objet de données à l’emplacement actuel de la souris.

- DROPEFFECT_LINK crée un lien entre un objet de données et son serveur.

*point*<br/>
La position actuelle de la souris par rapport à la zone d’affichage client.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le déplacement a réussi ; sinon 0.

### <a name="remarks"></a>Notes

L’implémentation par défaut ne fait rien et retourne FALSE.

Remplacez cette fonction pour implémenter l’effet d’un dépôt OLE dans la zone cliente de la vue. L’objet de données peut être examiné par le biais de *pDataObject* pour les données du Presse-papiers, formats et données supprimée au point spécifié.

> [!NOTE]
>  Le framework n’appelle pas cette fonction s’il existe un remplacement pour [OnDropEx](#ondropex) dans cette classe d’affichage.

##  <a name="ondropex"></a>  CView::OnDropEx

Appelé par l’infrastructure lorsque l’utilisateur relâche un objet de données sur une cible de dépôt valide.

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
L’effet que l’utilisateur a choisi pour l’opération de déplacement par défaut en fonction de l’état actuel de la clé. Il peut être DROPEFFECT_NONE. Effets de déplacement sont décrits dans la section Notes.

*liste déroulante*<br/>
Liste des effets de déplacement qui prend en charge de la source de dépôt. Valeurs d’effet de déplacement peuvent être combinées à l’aide de l’opération OR au niveau du bit ( **&#124;**) opération. Effets de déplacement sont décrits dans la section Notes.

*point*<br/>
La position actuelle de la souris par rapport à la zone d’affichage client.

### <a name="return-value"></a>Valeur de retour

L’effet résultant de la tentative de déplacement à l’emplacement spécifié par *point*. Cela doit être une des valeurs indiquées par *dropEffectList*. Effets de déplacement sont décrits dans la section Notes.

### <a name="remarks"></a>Notes

L’implémentation par défaut consiste à ne rien faire et retourner une valeur factice (-1) pour indiquer que le framework doit appeler le [OnDrop](#ondrop) gestionnaire.

Remplacez cette fonction pour implémenter l’effet d’un droit de bouton de souris glisser -déplacer. Droit de bouton de souris glisser -déplacer affiche généralement un menu de choix lorsque vous relâchez le bouton de la souris de droite.

Votre substitution de `OnDropEx` doit interroger pour le bouton de la souris de droite. Vous pouvez appeler [GetKeyState](https://msdn.microsoft.com/library/windows/desktop/ms646301) ou stocker l’état du bouton de la souris de droite à partir de votre [OnDragEnter](#ondragenter) gestionnaire.

- Si le bouton de la souris de droite est arrêté, la substitution doit afficher un menu contextuel qui offre que les effets de la liste prend en charge par la source de dépôt.

   - Examinez *liste déroulante* pour déterminer les effets de déplacement pris en charge par la source de dépôt. Autoriser uniquement ces actions sur le menu contextuel.

   - Utilisez [SetMenuDefaultItem](/windows/desktop/api/winuser/nf-winuser-setmenudefaultitem) pour définir l’action par défaut selon *dropDefault*.

   - Enfin, mettez l’action indiquée par la sélection de l’utilisateur dans le menu contextuel.

- Si le bouton de la souris de droite n’est pas hors service, votre substitution doit le traiter comme une demande de déplacement standard. Utilisez l’effet spécifié dans *dropDefault*. Vous pouvez également votre remplacement peut retourner la valeur factice (-1) pour indiquer que `OnDrop` gère cette opération de suppression.

Utilisez *pDataObject* pour examiner le `COleDataObject` pour les données du Presse-papiers, format et données supprimée au point spécifié.

Effets de déplacement décrivent l’action associée à une opération de déplacement. Consultez la liste des effets de la liste suivante :

- DROPEFFECT_NONE une chute ne serait pas autorisée.

- DROPEFFECT_COPY une opération de copie est réalisée.

- DROPEFFECT_MOVE serait exécutée une opération de déplacement.

- Lien d’un DROPEFFECT_LINK à partir de données déplacées vers les données d’origine serait être établi.

- DROPEFFECT_SCROLL indique qu’une opération glisser de défilement est sur le point de se produire ou se produit dans la cible.

Pour plus d’informations sur la définition de la commande de menu par défaut, consultez [SetMenuDefaultItem](/windows/desktop/api/winuser/nf-winuser-setmenudefaultitem) dans le SDK Windows et [CMenu::GetSafeHmenu](../../mfc/reference/cmenu-class.md#getsafehmenu) dans ce volume.

##  <a name="onendprinting"></a>  CView::OnEndPrinting

Appelé par le framework après qu’un document a été imprimé ou dès sa prévisualisation.

```
virtual void OnEndPrinting(
    CDC* pDC,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>Paramètres

*contrôleur de domaine principal*<br/>
Pointe vers le contexte de l’imprimante.

*pInfo*<br/>
Pointe vers un [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) structure qui décrit le travail d’impression en cours.

### <a name="remarks"></a>Notes

L’implémentation par défaut de cette fonction est sans effet. Remplacez cette fonction pour libérer les ressources GDI que vous avez alloué dans le [OnBeginPrinting](#onbeginprinting) fonction membre.

##  <a name="onendprintpreview"></a>  CView::OnEndPrintPreview

Appelé par le framework lorsque l’utilisateur quitte le mode Aperçu avant impression.

```
virtual void OnEndPrintPreview(
    CDC* pDC,
    CPrintInfo* pInfo,
    POINT point,
    CPreviewView* pView);
```

### <a name="parameters"></a>Paramètres

*contrôleur de domaine principal*<br/>
Pointe vers le contexte de l’imprimante.

*pInfo*<br/>
Pointe vers un [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) structure qui décrit le travail d’impression en cours.

*point*<br/>
Spécifie le point sur la page dernier affichage en mode Aperçu.

*pView*<br/>
Pointe vers l’objet d’affichage utilisé pour afficher un aperçu.

### <a name="remarks"></a>Notes

L’implémentation par défaut de cette fonction appelle le [OnEndPrinting](#onendprinting) fonction membre et des restaurations de début de la fenêtre frame principale à l’état, il se trouvait avant l’aperçu avant impression. Remplacez cette fonction pour effectuer un traitement spécial lorsque le mode aperçu est terminé. Par exemple, si vous souhaitez mettre à jour la position de l’utilisateur dans le document lors du passage du mode Aperçu en mode d’affichage normal, vous pouvez faire défiler vers la position décrite par le *point* paramètre et le `m_nCurPage` membre de la `CPrintInfo` qui structure le *pInfo* paramètre pointe vers.

Appelez toujours la version de la classe de base de `OnEndPrintPreview` à partir de votre remplacement, généralement à la fin de la fonction.

##  <a name="oninitialupdate"></a>  CView::OnInitialUpdate

Appelé par l’infrastructure une fois que la vue est d’abord attachée au document, mais avant l’affichage initial.

```
virtual void OnInitialUpdate();
```

### <a name="remarks"></a>Notes

L’implémentation par défaut de cette fonction appelle le [OnUpdate](#onupdate) fonction membre sans aucune information d’indicateur (autrement dit, en utilisant les valeurs par défaut de 0 pour le *lHint* paramètre et NULL pour le  *pHint* paramètre). Remplacez cette fonction pour effectuer toute initialisation à usage unique qui requiert des informations sur le document. Par exemple, si votre application comporte des documents de taille fixe, vous pouvez utiliser cette fonction pour initialiser les limites de défilement de l’affichage en fonction de la taille du document. Si votre application prend en charge les documents de taille variable, utilisez [OnUpdate](#onupdate) pour mettre à jour le défilement limite chaque fois que les modifications de document.

##  <a name="onpreparedc"></a>  CView::OnPrepareDC

Appelé par l’infrastructure avant le [OnDraw](#ondraw) fonction membre est appelée pour afficher l’écran et avant le [OnPrint](#onprint) fonction membre est appelée pour chaque page lors de l’impression ou Aperçu avant impression.

```
virtual void OnPrepareDC(
    CDC* pDC,
    CPrintInfo* pInfo = NULL);
```

### <a name="parameters"></a>Paramètres

*contrôleur de domaine principal*<br/>
Pointe vers le contexte de périphérique à utiliser pour le rendu d’une image du document.

*pInfo*<br/>
Pointe vers un [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) structure qui décrit le travail d’impression actuel si `OnPrepareDC` est appelée pour l’impression ou Aperçu avant impression ; le `m_nCurPage` membre spécifie la page sur le point d’être imprimée. Ce paramètre est NULL si `OnPrepareDC` est appelée pour afficher l’écran.

### <a name="remarks"></a>Notes

L’implémentation par défaut de cette fonction ne fait rien si la fonction est appelée pour afficher l’écran. Toutefois, cette fonction est substituée dans les classes dérivées, telles que [CScrollView](../../mfc/reference/cscrollview-class.md), modifier les attributs de contexte de périphérique ; par conséquent, vous devez toujours appeler l’implémentation de classe de base au début du remplacement.

Si la fonction est appelée pour l’impression, l’implémentation par défaut examine les informations de page stockées dans le *pInfo* paramètre. Si la longueur du document n’a pas été spécifiée, `OnPrepareDC` suppose que le document à une seule page et arrête la boucle d’impression après l’impression d’une page. La fonction arrête la boucle d’impression en définissant le `m_bContinuePrinting` membre de la structure sur FALSE.

Substituer `OnPrepareDC` pour une des raisons suivantes :

- Pour paramétrer les attributs du contexte de périphérique en fonction des besoins pour la page spécifiée. Par exemple, si vous devez définir le mode de mappage ou d’autres caractéristiques du contexte de périphérique, le faire dans cette fonction.

- Pour exécuter la pagination de délai d’impression. Normalement vous spécifiez la longueur du document au commencement de l’impression, à l’aide de la [OnPreparePrinting](#onprepareprinting) fonction membre. Toutefois, si vous ne connaissez pas à l’avance la durée pendant laquelle le document est (par exemple, lors de l’impression d’un nombre indéterminé d’enregistrements à partir d’une base de données), substituez `OnPrepareDC` pour tester la fin du document pendant qu’il est imprimé. Lorsqu’il existe non plus du document à imprimer, définissez le `m_bContinuePrinting` membre de la `CPrintInfo` structure sur FALSE.

- Pour envoyer des codes d’échappement à l’imprimante sur une base de page par page. Pour envoyer des codes d’échappement à partir de `OnPrepareDC`, appelez le `Escape` fonction membre de la *pDC* paramètre.

Appeler la version de la classe de base de `OnPrepareDC` au début du remplacement.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFCDocView#183](../../mfc/codesnippet/cpp/cview-class_1.cpp)]

##  <a name="onprepareprinting"></a>  Comme CView::OnPreparePrinting

Appelé par l’infrastructure avant de l’impression ou la prévisualisation d’un document.

```
virtual BOOL OnPreparePrinting(CPrintInfo* pInfo);
```

### <a name="parameters"></a>Paramètres

*pInfo*<br/>
Pointe vers un [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) structure qui décrit le travail d’impression en cours.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro pour commencer l’impression ; 0 si le travail d’impression a été annulé.

### <a name="remarks"></a>Notes

L'implémentation par défaut n'exécute aucune opération.

Vous devez substituer cette fonction pour activer l’impression et Aperçu avant impression. Appelez le [DoPreparePrinting](#doprepareprinting) fonction membre, en lui passant le *pInfo* paramètre et puis retourner sa valeur de retour ; `DoPreparePrinting` affiche la boîte de dialogue Imprimer et crée un contexte de périphérique. Si vous souhaitez initialiser la boîte de dialogue d’impression avec des valeurs autres que les valeurs par défaut, affecter des valeurs aux membres de *pInfo*. Par exemple, si vous connaissez la longueur du document, passer la valeur à la [SetMaxPage](../../mfc/reference/cprintinfo-structure.md#setmaxpage) fonction membre de *pInfo* avant d’appeler `DoPreparePrinting`. Cette valeur est affichée dans le champ à : zone dans la partie de la plage de la boîte de dialogue Imprimer.

`DoPreparePrinting` n’affiche pas la boîte de dialogue d’impression pour un travail d’aperçu. Si vous souhaitez ignorer la boîte de dialogue d’impression pour un travail d’impression, vérifiez que le `m_bPreview` membre *pInfo* a la valeur FALSE et la définir sur TRUE avant leur transmission à `DoPreparePrinting`; par la suite de le réinitialiser sur FALSE.

Si vous avez besoin exécuter des initialisations qui requièrent l’accès à la `CDC` objet représentant le contexte de périphérique (par exemple, si vous avez besoin de connaître la taille de page avant de spécifier la longueur du document), remplacer le `OnBeginPrinting` membre fonction.

Si vous souhaitez définir la valeur de la `m_nNumPreviewPages` ou `m_strPageDesc` membres de la *pInfo* paramètre, le faire après avoir appelé `DoPreparePrinting`. Le `DoPreparePrinting` jeux de la fonction membre `m_nNumPreviewPages` à la valeur trouvée dans l’application. Fichier INI et définit `m_strPageDesc` à sa valeur par défaut.

### <a name="example"></a>Exemple

  Substituer `OnPreparePrinting` et appelez `DoPreparePrinting` à partir de la substitution afin que l’infrastructure affiche une boîte de dialogue Imprimer et créer une contrôleur de domaine de l’imprimante pour vous.

[!code-cpp[NVC_MFCDocView#184](../../mfc/codesnippet/cpp/cview-class_2.cpp)]

Si vous connaissez le nombre de pages contient le document, définir la page maximale `OnPreparePrinting` avant d’appeler `DoPreparePrinting`. L’infrastructure affiche le numéro de page maximale dans la zone « to » de la boîte de dialogue Imprimer.

[!code-cpp[NVC_MFCDocView#185](../../mfc/codesnippet/cpp/cview-class_3.cpp)]

##  <a name="onprint"></a>  CView::OnPrint

Appelé par l’infrastructure d’imprimer ou de prévisualisation d’une page du document.

```
virtual void OnPrint(
    CDC* pDC,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>Paramètres

*contrôleur de domaine principal*<br/>
Pointe vers le contexte de l’imprimante.

*pInfo*<br/>
Pointe vers un `CPrintInfo` structure qui décrit le travail d’impression en cours.

### <a name="remarks"></a>Notes

Pour chaque page imprimée, l’infrastructure appelle cette fonction immédiatement après avoir appelé la [OnPrepareDC](#onpreparedc) fonction membre. La page imprimée est spécifiée par le `m_nCurPage` membre de la [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) qui structure *pInfo* pointe vers. L’implémentation par défaut appelle la [OnDraw](#ondraw) fonction membre et le transmet le contexte de périphérique d’imprimante.

Remplacez cette fonction pour une des raisons suivantes :

- Pour permettre l’impression de documents multipages. Afficher uniquement la partie du document qui correspond à la page actuellement imprimée. Si vous utilisez `OnDraw` pour effectuer le rendu, vous pouvez ajuster l’origine de la fenêtre d’affichage afin que seule la partie appropriée du document est imprimée.

- Pour rendre l’image imprimée différer de l’image de l’écran (autrement dit, si votre application n’est pas WYSIWYG). Au lieu de passer à l’imprimante contexte de périphérique à `OnDraw`, utiliser le contexte de périphérique pour restituer une image à l’aide d’attributs ne pas affichées sur l’écran.

     Si vous avez besoin de ressources GDI pour l’impression que vous n’utilisez pas pour l’écran, sélectionnez-les dans le contexte de périphérique avant le dessin et désélectionnez-les par la suite. Ces ressources GDI doivent être allouées dans [OnBeginPrinting](#onbeginprinting) et publiée en [OnEndPrinting](#onendprinting).

- Pour implémenter les en-têtes ou pieds de page. Vous pouvez toujours utiliser `OnDraw` pour effectuer le rendu en limitant la zone impression.

Notez que le `m_rectDraw` membre de la *pInfo* paramètre décrit la zone imprimable de la page en unités logiques.

N’appelez pas `OnPrepareDC` dans votre substitution de `OnPrint`; le framework appelle `OnPrepareDC` automatiquement avant d’appeler `OnPrint`.

### <a name="example"></a>Exemple

Voici un squelette pour substitué `OnPrint` fonction :

[!code-cpp[NVC_MFCDocView#186](../../mfc/codesnippet/cpp/cview-class_4.cpp)]

Pour un autre exemple, consultez [CRichEditView::PrintInsideRect](../../mfc/reference/cricheditview-class.md#printinsiderect).

##  <a name="onscroll"></a>  CView::OnScroll

Appelé par l’infrastructure pour déterminer si le défilement est possible.

```
virtual BOOL OnScroll(
    UINT nScrollCode,
    UINT nPos,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>Paramètres

*nScrollCode*<br/>
Un code de la barre de défilement qui indique que l’utilisateur du défilement de demande. Ce paramètre est composé de deux parties : un octet de poids faible, qui détermine le type de défilement se produisant horizontalement, et un octet de poids fort, qui détermine le type de défilement se produisant verticalement :

- Fait défiler les SB_BOTTOM vers le bas.

- Fait défiler SB_LINEDOWN une ligne vers le bas.

- Fait défiler SB_LINEUP jusqu'à la ligne.

- SB_PAGEDOWN défiler une page vers le bas.

- Fait défiler SB_PAGEUP une page haut.

- Fait glisser SB_THUMBTRACK faites défiler vers la zone à la position spécifiée. La position actuelle est spécifiée dans *nPos*.

- Fait défiler les SB_TOP vers le haut.

*nPos*<br/>
Contient la position actuelle de la case de défilement si le code de la barre de défilement est SB_THUMBTRACK ; Sinon, il n’est pas utilisé. En fonction de la plage de défilement initiale, *nPos* peut être négatif et doit être casté en un **int** si nécessaire.

*bDoScroll*<br/>
Détermine si vous devez réellement effectuer l’action de défilement spécifiée. Si la valeur est TRUE, puis faites défiler doit avoir lieu ; Si la valeur est FALSE, puis faites défiler ne doit pas se produire.

### <a name="return-value"></a>Valeur de retour

Si *bDoScroll* a la valeur TRUE et l’affichage a été réellement défilé, puis retour différente de zéro ; sinon 0. Si *bDoScroll* est FALSE, alors retourner la valeur qui vous aurait retourné si *bDoScroll* ont la valeur TRUE, même si vous ne le faites en fait le défilement.

### <a name="remarks"></a>Notes

Dans le premier cas, cette fonction est appelée par l’infrastructure avec *bDoScroll* la valeur TRUE lorsque la vue reçoit un message de la barre de défilement. Dans ce cas, vous devez réellement faire défiler la vue. Dans les autres cas, cette fonction est appelée avec *bDoScroll* défini sur FALSE lorsqu’un élément OLE est initialement déplacé vers la zone de défilement automatique d’une cible de dépôt avant le défilement ne se produise réellement. Dans ce cas, vous ne devez pas réellement faire défiler la vue.

##  <a name="onscrollby"></a>  CView::OnScrollBy

Appelé par le framework lorsque l’utilisateur affiche une zone au-delà de la vue actuelle du document, soit en faisant glisser un élément OLE sur les bordures de la vue actuelle ou en manipulant les barres de défilement verticale ou horizontale.

```
virtual BOOL OnScrollBy(
    CSize sizeScroll,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>Paramètres

*sizeScroll*<br/>
Nombre de pixels défile horizontalement et verticalement.

*bDoScroll*<br/>
Détermine si le défilement de la vue se produit. Si la valeur est TRUE, puis le défilement a lieu ; Si la valeur est FALSE, puis le défilement ne se produit pas.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la vue a été en mesure de faire défiler ; sinon 0.

### <a name="remarks"></a>Notes

Dans les classes dérivées cette méthode vérifie si la vue est permettant le défilement dans la direction de l’utilisateur demandé, puis met à jour de la nouvelle région si nécessaire. Cette fonction est appelée automatiquement par [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll) et [CWnd::OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll) pour effectuer la demande réelle de défilement.

L’implémentation par défaut de cette méthode ne modifie pas la vue, mais si elle n’est pas appelée, la vue défile pas dans un `CScrollView`-classe dérivée.

Si la largeur du document ou la hauteur dépasse 32767 pixels, le défilement au-delà de 32767 échouera car `OnScrollBy` est appelée avec un non valide *sizeScroll* argument.

##  <a name="onupdate"></a>  CView::OnUpdate

Appelé par l’infrastructure après que le document de la vue a été modifié ; Cette fonction est appelée par [CDocument::UpdateAllViews](../../mfc/reference/cdocument-class.md#updateallviews) et permet l’affichage pour mettre à jour son affichage afin de refléter ces modifications.

```
virtual void OnUpdate(
    CView* pSender,
    LPARAM lHint,
    CObject* pHint);
```

### <a name="parameters"></a>Paramètres

*pSender*<br/>
Pointe vers la vue qui a modifié le document, ou NULL si toutes les vues doivent être mis à jour.

*lHint*<br/>
Contient des informations sur les modifications.

*pHint*<br/>
Pointe vers un objet stockant les informations sur les modifications.

### <a name="remarks"></a>Notes

Il est également appelé par l’implémentation par défaut de [OnInitialUpdate](#oninitialupdate). L’implémentation par défaut invalide la zone cliente, en marquant pour la peinture lorsque le message WM_PAINT suivant est reçu. Remplacez cette fonction si vous souhaitez mettre à jour uniquement les régions qui mappent aux parties modifiées du document. Pour ce faire, vous devez passer d’informations sur les modifications en utilisant les paramètres de l’indicateur.

Pour utiliser *lHint*, définir des valeurs d’indicateur spécial, généralement un masque de bits ou un type énuméré, et que le document de passer d’une des valeurs suivantes. Pour utiliser *pHint*, dérivez une classe de l’indicateur de [CObject](../../mfc/reference/cobject-class.md) et que le document de passer un pointeur vers un objet de Conseil ; lors de la substitution `OnUpdate`, utilisez le [CObject::IsKindOf](../../mfc/reference/cobject-class.md#iskindof) fonction membre pour déterminer le type au moment de l’exécution de l’objet d’indicateur.

En général, vous ne devez effectuer un dessin directement à partir de `OnUpdate`. Au lieu de cela, déterminer le rectangle décrivant, en coordonnées de l’appareil, la zone qui nécessite la mise à jour ; passer ce rectangle [CWnd::InvalidateRect](../../mfc/reference/cwnd-class.md#invalidaterect). Cela entraîne la peinture au prochain un [WM_PAINT](/windows/desktop/gdi/wm-paint) message est reçu.

Si *lHint* est égal à 0 et *pHint* est NULL, le document a envoyé une notification de mise à jour générique. Si une vue reçoit une notification de mise à jour générique, ou si elle ne peut pas décoder les indicateurs, elle doit invalider sa zone cliente.

## <a name="see-also"></a>Voir aussi

[Exemple MFC MDIDOCVW](../../visual-cpp-samples.md)<br/>
[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CWnd, classe](../../mfc/reference/cwnd-class.md)<br/>
[CFrameWnd, classe](../../mfc/reference/cframewnd-class.md)<br/>
[CSplitterWnd, classe](../../mfc/reference/csplitterwnd-class.md)<br/>
[CDC, classe](../../mfc/reference/cdc-class.md)<br/>
[CDocTemplate, classe](../../mfc/reference/cdoctemplate-class.md)<br/>
[CDocument, classe](../../mfc/reference/cdocument-class.md)
