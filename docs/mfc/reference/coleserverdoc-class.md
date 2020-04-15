---
title: COleServerDoc, classe
ms.date: 11/04/2016
f1_keywords:
- COleServerDoc
- AFXOLE/COleServerDoc
- AFXOLE/COleServerDoc::COleServerDoc
- AFXOLE/COleServerDoc::ActivateDocObject
- AFXOLE/COleServerDoc::ActivateInPlace
- AFXOLE/COleServerDoc::DeactivateAndUndo
- AFXOLE/COleServerDoc::DiscardUndoState
- AFXOLE/COleServerDoc::GetClientSite
- AFXOLE/COleServerDoc::GetEmbeddedItem
- AFXOLE/COleServerDoc::GetItemClipRect
- AFXOLE/COleServerDoc::GetItemPosition
- AFXOLE/COleServerDoc::GetZoomFactor
- AFXOLE/COleServerDoc::IsDocObject
- AFXOLE/COleServerDoc::IsEmbedded
- AFXOLE/COleServerDoc::IsInPlaceActive
- AFXOLE/COleServerDoc::NotifyChanged
- AFXOLE/COleServerDoc::NotifyClosed
- AFXOLE/COleServerDoc::NotifyRename
- AFXOLE/COleServerDoc::NotifySaved
- AFXOLE/COleServerDoc::OnDeactivate
- AFXOLE/COleServerDoc::OnDeactivateUI
- AFXOLE/COleServerDoc::OnDocWindowActivate
- AFXOLE/COleServerDoc::OnResizeBorder
- AFXOLE/COleServerDoc::OnShowControlBars
- AFXOLE/COleServerDoc::OnUpdateDocument
- AFXOLE/COleServerDoc::RequestPositionChange
- AFXOLE/COleServerDoc::SaveEmbedding
- AFXOLE/COleServerDoc::ScrollContainerBy
- AFXOLE/COleServerDoc::UpdateAllItems
- AFXOLE/COleServerDoc::CreateInPlaceFrame
- AFXOLE/COleServerDoc::DestroyInPlaceFrame
- AFXOLE/COleServerDoc::GetDocObjectServer
- AFXOLE/COleServerDoc::OnClose
- AFXOLE/COleServerDoc::OnExecOleCmd
- AFXOLE/COleServerDoc::OnFrameWindowActivate
- AFXOLE/COleServerDoc::OnGetEmbeddedItem
- AFXOLE/COleServerDoc::OnReactivateAndUndo
- AFXOLE/COleServerDoc::OnSetHostNames
- AFXOLE/COleServerDoc::OnSetItemRects
- AFXOLE/COleServerDoc::OnShowDocument
helpviewer_keywords:
- COleServerDoc [MFC], COleServerDoc
- COleServerDoc [MFC], ActivateDocObject
- COleServerDoc [MFC], ActivateInPlace
- COleServerDoc [MFC], DeactivateAndUndo
- COleServerDoc [MFC], DiscardUndoState
- COleServerDoc [MFC], GetClientSite
- COleServerDoc [MFC], GetEmbeddedItem
- COleServerDoc [MFC], GetItemClipRect
- COleServerDoc [MFC], GetItemPosition
- COleServerDoc [MFC], GetZoomFactor
- COleServerDoc [MFC], IsDocObject
- COleServerDoc [MFC], IsEmbedded
- COleServerDoc [MFC], IsInPlaceActive
- COleServerDoc [MFC], NotifyChanged
- COleServerDoc [MFC], NotifyClosed
- COleServerDoc [MFC], NotifyRename
- COleServerDoc [MFC], NotifySaved
- COleServerDoc [MFC], OnDeactivate
- COleServerDoc [MFC], OnDeactivateUI
- COleServerDoc [MFC], OnDocWindowActivate
- COleServerDoc [MFC], OnResizeBorder
- COleServerDoc [MFC], OnShowControlBars
- COleServerDoc [MFC], OnUpdateDocument
- COleServerDoc [MFC], RequestPositionChange
- COleServerDoc [MFC], SaveEmbedding
- COleServerDoc [MFC], ScrollContainerBy
- COleServerDoc [MFC], UpdateAllItems
- COleServerDoc [MFC], CreateInPlaceFrame
- COleServerDoc [MFC], DestroyInPlaceFrame
- COleServerDoc [MFC], GetDocObjectServer
- COleServerDoc [MFC], OnClose
- COleServerDoc [MFC], OnExecOleCmd
- COleServerDoc [MFC], OnFrameWindowActivate
- COleServerDoc [MFC], OnGetEmbeddedItem
- COleServerDoc [MFC], OnReactivateAndUndo
- COleServerDoc [MFC], OnSetHostNames
- COleServerDoc [MFC], OnSetItemRects
- COleServerDoc [MFC], OnShowDocument
ms.assetid: a9cdd96a-e0ac-43bb-9203-2c29237e965c
ms.openlocfilehash: b535cc23901ba39e4beeb66d8ca6bb18d4abe2b8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376130"
---
# <a name="coleserverdoc-class"></a>COleServerDoc, classe

Classe de base des documents serveur OLE.

## <a name="syntax"></a>Syntaxe

```
class AFX_NOVTABLE COleServerDoc : public COleLinkingDoc
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[COleServerDoc::COleServerDoc](#coleserverdoc)|Construit un objet `COleServerDoc`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[COleServerDoc::ActivateDocObject](#activatedocobject)|Active le document DocObject associé.|
|[COleServerDoc::ActivateInPlace](#activateinplace)|Active le document pour l’édition sur place.|
|[COleServerDoc::DeactivateAndUndo](#deactivateandundo)|Désactiver l’interface utilisateur du serveur.|
|[COleServerDoc::DiscardUndoState](#discardundostate)|Jetez les informations indo-étatiques.|
|[COleServerDoc::GetClientSite](#getclientsite)|Récupère un pointeur `IOleClientSite` sur l’interface sous-jacente.|
|[COleServerDoc::GetEmbeddedItem](#getembeddeditem)|Renvoie un pointeur à un élément représentant l’ensemble du document.|
|[COleServerDoc::GetItemClipRect](#getitemcliprect)|Retourne le rectangle de coupure actuel pour l’édition en place.|
|[COleServerDoc::GetItemPosition](#getitemposition)|Renvoie le rectangle de position actuel, par rapport à la zone client de l’application de conteneur, pour l’édition sur place.|
|[COleServerDoc::GetZoomFactor](#getzoomfactor)|Retourne le facteur zoom dans les pixels.|
|[COleServerDoc::IsDocObject](#isdocobject)|Détermine si le document est un DocObject.|
|[COleServerDoc::Isembedded](#isembedded)|Indique si le document est intégré dans un document de conteneurs ou s’il est autonome.|
|[COleServerDoc::IsInPlaceActive](#isinplaceactive)|Retourne VRAI si l’élément est actuellement activé en place.|
|[COleServerDoc::NotifyChanged](#notifychanged)|Informe les conteneurs que l’utilisateur a modifié le document.|
|[COleServerDoc::NotifyClosed](#notifyclosed)|Informe les conteneurs que l’utilisateur a fermé le document.|
|[COleServerDoc::NotifyRename](#notifyrename)|Informe les conteneurs que l’utilisateur a rebaptisé le document.|
|[COleServerDoc::NotifySaved](#notifysaved)|Informe les conteneurs que l’utilisateur a enregistré le document.|
|[COleServerDoc::OnDeactivate](#ondeactivate)|Appelé par le cadre lorsque l’utilisateur désactive un élément qui a été activé en place.|
|[COleServerDoc::OnDeactivateUI](#ondeactivateui)|Appelé par le cadre pour détruire les contrôles et autres éléments d’interface utilisateur créés pour l’activation sur place.|
|[COleServerDoc::OnDocWindowActivate](#ondocwindowactivate)|Appelé par le cadre lorsque la fenêtre de cadre de document du conteneur est activée ou désactivée.|
|[COleServerDoc::OnResizeBorder](#onresizeborder)|Appelé par le cadre lorsque la fenêtre de cadre ou la fenêtre de document de l’application de conteneur est resized.|
|[COleServerDoc::OnShowControlBars](#onshowcontrolbars)|Appelé par le cadre pour montrer ou cacher des barres de contrôle pour l’édition en place.|
|[COleServerDoc::OnUpdateDocument](#onupdatedocument)|Appelé par le cadre lorsqu’un document serveur qui est un élément intégré est enregistré, la mise à jour de la copie de l’élément du conteneur.|
|[COleServerDoc::RequestPositionChange](#requestpositionchange)|Modifications de la position du cadre d’édition sur place.|
|[COleServerDoc::SaveEmbedding](#saveembedding)|Indique à l’application de conteneurs d’enregistrer le document.|
|[COleServerDoc::ScrollContainerBy](#scrollcontainerby)|Faites défiler le document de conteneur.|
|[COleServerDoc::UpdateAllItems](#updateallitems)|Informe les conteneurs que l’utilisateur a modifié le document.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[COleServerDoc::CreateInPlaceFrame](#createinplaceframe)|Appelé par le cadre pour créer une fenêtre de cadre pour l’édition en place.|
|[COleServerDoc::DestroyInPlaceFrame](#destroyinplaceframe)|Appelé par le cadre pour détruire une fenêtre de cadre pour l’édition en place.|
|[COleServerDoc::GetDocObjectServer](#getdocobjectserver)|Remplacer cette fonction pour `CDocObjectServer` créer un nouvel objet et indiquer que ce document est un conteneur DocObject.|
|[COleServerDoc::OnClose](#onclose)|Appelé par le cadre lorsqu’un conteneur demande de fermer le document.|
|[COleServerDoc::OnExecOleCmd](#onexecolecmd)|Exécute une commande spécifiée ou affiche de l’aide pour la commande.|
|[COleServerDoc::OnFrameWindowActivate](#onframewindowactivate)|Appelé par le cadre lorsque la fenêtre de cadre du conteneur est activée ou désactivée.|
|[COleServerDoc::OnGetEmbeddedItem](#ongetembeddeditem)|Appelé à `COleServerItem` obtenir un qui représente l’ensemble du document; utilisé pour obtenir un élément intégré. Mise en œuvre requise.|
|[COleServerDoc::OnReactivateAndUndo](#onreactivateandundo)|Appelé par le cadre pour annuler les modifications apportées lors de l’édition sur place.|
|[COleServerDoc::OnSetHostNames](#onsethostnames)|Appelé par le cadre quand un conteneur définit le titre de fenêtre pour un objet intégré.|
|[COleServerDoc::OnSetItemRects](#onsetitemrects)|Appelé par le cadre pour positionner la fenêtre de cadre d’édition en place dans la fenêtre de l’application de conteneur.|
|[COleServerDoc::OnShowDocument](#onshowdocument)|Appelé par le cadre pour montrer ou cacher le document.|

## <a name="remarks"></a>Notes

Un document serveur peut contenir des objets [COleServerItem,](../../mfc/reference/coleserveritem-class.md) qui représentent l’interface serveur à des éléments intégrés ou liés. Lorsqu’une application serveur est lancée par un conteneur pour modifier un élément intégré, l’élément est chargé comme son propre document serveur ; l’objet `COleServerDoc` ne `COleServerItem` contient qu’un seul objet, composé de l’ensemble du document. Lorsqu’une application serveur est lancée par un conteneur pour modifier un élément lié, un document existant est chargé à partir du disque ; une partie du contenu du document est mise en évidence pour indiquer l’élément lié.

`COleServerDoc`les objets peuvent également contenir des éléments de la classe [COleClientItem.](../../mfc/reference/coleclientitem-class.md) Cela vous permet de créer des applications de serveur de conteneurs. Le cadre fournit des fonctions `COleClientItem` pour stocker `COleServerItem` correctement les articles tout en servant les objets.

Si votre application serveur ne prend pas en charge les liens, un document serveur ne contiendra toujours qu’un seul élément serveur, qui représente l’ensemble de l’objet intégré en tant que document. Si votre application serveur prend en charge les liens, elle doit créer un élément serveur chaque fois qu’une sélection est copiée sur le Clipboard.

Pour `COleServerDoc`utiliser , en tirer une classe et implémenter la fonction membre [OnGetEmbeddedItem,](#ongetembeddeditem) qui permet à votre serveur de prendre en charge les éléments embarqués. Dérivez une `COleServerItem` classe de pour implémenter les éléments `OnGetEmbeddedItem`dans vos documents, et retourner les objets de cette classe à partir de .

Pour prendre en `COleServerDoc` charge les éléments liés, fournit la fonction membre [OnGetLinkedItem.](../../mfc/reference/colelinkingdoc-class.md#ongetlinkeditem) Vous pouvez utiliser la implémentation par défaut ou la remplacer si vous avez votre propre façon de gérer les éléments de document.

Vous avez `COleServerDoc`besoin d’une classe dérivée pour chaque type de document serveur que votre application prend en charge. Par exemple, si votre application serveur prend en `COleServerDoc`charge les feuilles de travail et les graphiques, vous avez besoin de deux classes dérivées.

Pour plus d’informations sur les serveurs, voir l’article [Serveurs: Implémenter un serveur](../../mfc/servers-implementing-a-server.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocument](../../mfc/reference/cdocument-class.md)

[COleDocument](../../mfc/reference/coledocument-class.md)

[COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)

`COleServerDoc`

## <a name="requirements"></a>Spécifications

**En-tête:** afxole.h

## <a name="coleserverdocactivatedocobject"></a><a name="activatedocobject"></a>COleServerDoc::ActivateDocObject

Active le document DocObject associé.

```
void ActivateDocObject();
```

### <a name="remarks"></a>Notes

Par défaut, `COleServerDoc` ne prend pas en charge les documents actifs (également appelés DocObjects). Pour activer ce support, voir [GetDocObjectServer](#getdocobjectserver) et classe [CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md).

## <a name="coleserverdocactivateinplace"></a><a name="activateinplace"></a>COleServerDoc::ActivateInPlace

Active l’élément pour l’édition sur place.

```
BOOL ActivateInPlace();
```

### <a name="return-value"></a>Valeur de retour

Nonzero en cas de succès; autrement 0, ce qui indique que l’élément est entièrement ouvert.

### <a name="remarks"></a>Notes

Cette fonction effectue toutes les opérations nécessaires à l’activation sur place. Il crée une fenêtre de cadre sur place, l’active et la taille à l’élément, met en place des menus partagés et d’autres contrôles, fait défiler l’élément en vue, et met l’accent sur la fenêtre de cadre en place.

Cette fonction est appelée par la mise en œuvre par défaut de [COleServerItem::OnShow](../../mfc/reference/coleserveritem-class.md#onshow). Appelez cette fonction si votre application prend en charge un autre verbe pour l’activation sur place (comme Play).

## <a name="coleserverdoccoleserverdoc"></a><a name="coleserverdoc"></a>COleServerDoc::COleServerDoc

Construit un `COleServerDoc` objet sans se connecter avec le système OLE DLLs.

```
COleServerDoc();
```

### <a name="remarks"></a>Notes

Vous devez appeler [COleLinkingDoc::Inscrivez-vous](../../mfc/reference/colelinkingdoc-class.md#register) pour ouvrir les communications avec OLE. Si vous utilisez [COleTemplateServer](../../mfc/reference/coletemplateserver-class.md) dans `COleLinkingDoc::Register` votre application, `COleLinkingDoc`est appelé `OnNewDocument` `OnOpenDocument`pour `OnSaveDocument`vous par la mise en œuvre de , , , et .

## <a name="coleserverdoccreateinplaceframe"></a><a name="createinplaceframe"></a>COleServerDoc::CreateInPlaceFrame

Le cadre appelle cette fonction pour créer une fenêtre de cadre pour l’édition en place.

```
virtual COleIPFrameWnd* CreateInPlaceFrame(CWnd* pParentWnd);
```

### <a name="parameters"></a>Paramètres

*pParentWnd*<br/>
Pointeur vers la fenêtre parente de l’application de conteneur.

### <a name="return-value"></a>Valeur de retour

Un pointeur vers la fenêtre de cadre sur place, ou NULL si elle n’est pas retenue.

### <a name="remarks"></a>Notes

La implémentation par défaut utilise les informations spécifiées dans le modèle de document pour créer le cadre. La vue utilisée est la première vue créée pour le document. Cette vue est temporairement détachée du cadre d’origine et fixée au cadre nouvellement créé.

C’est un avancé primordial.

## <a name="coleserverdocdeactivateandundo"></a><a name="deactivateandundo"></a>COleServerDoc::DeactivateAndUndo

Appelez cette fonction si votre application prend en charge Annuler et l’utilisateur choisit Annuler après avoir activé un élément, mais avant de l’éditer.

```
BOOL DeactivateAndUndo();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro en cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Si l’application de conteneur est écrite à l’aide de la Microsoft Foundation Class Library, l’appel de cette fonction provoque [COleClientItem::OnDeactivateAndUndo](../../mfc/reference/coleclientitem-class.md#ondeactivateandundo) à être appelé, ce qui désactive l’interface utilisateur du serveur.

## <a name="coleserverdocdestroyinplaceframe"></a><a name="destroyinplaceframe"></a>COleServerDoc::DestroyInPlaceFrame

Le cadre appelle cette fonction à détruire une fenêtre de cadre en place et à renvoyer la fenêtre de document de l’application serveur à son état avant l’activation sur place.

```
virtual void DestroyInPlaceFrame(COleIPFrameWnd* pFrameWnd);
```

### <a name="parameters"></a>Paramètres

*pFrameWnd*<br/>
Pointeur vers la fenêtre de cadre en place à détruire.

### <a name="remarks"></a>Notes

C’est un avancé primordial.

## <a name="coleserverdocdiscardundostate"></a><a name="discardundostate"></a>COleServerDoc::DiscardUndoState

Si l’utilisateur effectue une opération d’édition qui ne peut être annulée, appelez cette fonction pour forcer l’application de conteneur à se débarrasser de ses informations indo-étatiques.

```
BOOL DiscardUndoState();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro en cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction est fournie de sorte que les serveurs qui prennent en charge Annuler peuvent libérer des ressources qui seraient autrement consommées par des informations indo-étatiques qui ne peuvent pas être utilisées.

## <a name="coleserverdocgetclientsite"></a><a name="getclientsite"></a>COleServerDoc::GetClientSite

Récupère un pointeur `IOleClientSite` sur l’interface sous-jacente.

```
LPOLECLIENTSITE GetClientSite() const;
```

### <a name="return-value"></a>Valeur de retour

Récupère un pointeur sur l’interface sous-jacente [IOleClientSite.](/windows/win32/api/oleidl/nn-oleidl-ioleclientsite)

## <a name="coleserverdocgetdocobjectserver"></a><a name="getdocobjectserver"></a>COleServerDoc::GetDocObjectServer

Remplacer cette fonction pour `CDocObjectServer` créer un nouvel élément et y retourner un pointeur.

```
virtual CDocObjectServer* GetDocObjectServer(LPOLEDOCUMENTSITE pDocSite);
```

### <a name="parameters"></a>Paramètres

*pDocSite (en)*<br/>
Pointeur `IOleDocumentSite` vers l’interface qui connectera ce document au serveur.

### <a name="return-value"></a>Valeur de retour

Un pointeur `CDocObjectServer`à un ; NULL si l’opération a échoué.

### <a name="remarks"></a>Notes

Lorsqu’un serveur DocObject est activé, le retour d’un pointeur non NULL montre que le client peut prendre en charge DocObjects. La mise en œuvre par défaut renvoie NULL.

Une implémentation typique d’un document qui prend `CDocObjectServer` en charge DocObjects attribuera simplement un nouvel objet et le retournera à l’appelant. Par exemple :

[!code-cpp[NVC_MFCOleServer#3](../../mfc/codesnippet/cpp/coleserverdoc-class_1.cpp)]

## <a name="coleserverdocgetembeddeditem"></a><a name="getembeddeditem"></a>COleServerDoc::GetEmbeddedItem

Appelez cette fonction pour obtenir un pointeur à un élément représentant l’ensemble du document.

```
COleServerItem* GetEmbeddedItem();
```

### <a name="return-value"></a>Valeur de retour

Un pointeur à un élément représentant l’ensemble du document; NULL si l’opération a échoué.

### <a name="remarks"></a>Notes

Il appelle [COleServerDoc::OnGetEmbeddedItem](#ongetembeddeditem), une fonction virtuelle sans implémentation par défaut.

## <a name="coleserverdocgetitemcliprect"></a><a name="getitemcliprect"></a>COleServerDoc::GetItemClipRect

Appelez `GetItemClipRect` la fonction du membre pour obtenir les coordonnées de la tonte de l’élément qui est en cours de modification.

```
void GetItemClipRect(LPRECT lpClipRect) const;
```

### <a name="parameters"></a>Paramètres

*lpClipRect*<br/>
Pointeur `RECT` vers une `CRect` structure ou un objet pour recevoir les coordonnées de l’élément.

### <a name="remarks"></a>Notes

Les coordonnées sont en pixels par rapport à la zone client de la fenêtre d’application du conteneur.

Le dessin ne doit pas se produire à l’extérieur du rectangle de coupure. Habituellement, le dessin est automatiquement restreint. Utilisez cette fonction pour déterminer si l’utilisateur a fait défiler en dehors de la partie visible du document; si oui, faites défiler le document de conteneur au besoin au moyen d’un appel à [ScrollContainerBy](#scrollcontainerby).

## <a name="coleserverdocgetitemposition"></a><a name="getitemposition"></a>COleServerDoc::GetItemPosition

Appelez `GetItemPosition` la fonction membre pour obtenir les coordonnées de l’élément en cours de modification.

```
void GetItemPosition(LPRECT lpPosRect) const;
```

### <a name="parameters"></a>Paramètres

*lpPosRect*<br/>
Pointeur `RECT` vers une `CRect` structure ou un objet pour recevoir les coordonnées de l’élément.

### <a name="remarks"></a>Notes

Les coordonnées sont en pixels par rapport à la zone client de la fenêtre d’application du conteneur.

La position de l’élément peut être comparée au rectangle de coupure actuel pour déterminer dans quelle mesure l’élément est visible (ou non visible) sur l’écran.

## <a name="coleserverdocgetzoomfactor"></a><a name="getzoomfactor"></a>COleServerDoc::GetZoomFactor

La `GetZoomFactor` fonction membre détermine le « facteur de zoom » d’un élément qui a été activé pour l’édition place.

```
BOOL GetZoomFactor(
    LPSIZE lpSizeNum = NULL,
    LPSIZE lpSizeDenom = NULL,
    LPCRECT lpPosRect = NULL) const;
```

### <a name="parameters"></a>Paramètres

*lpSizeNum (en)*<br/>
Pointeur vers un `CSize` objet de classe qui tiendra le numérateur du facteur zoom. Sa valeur peut être NULL.

*lpSizeDenom (en)*<br/>
Pointeur vers un `CSize` objet de classe qui tiendra le dénominateur du facteur zoom. Sa valeur peut être NULL.

*lpPosRect*<br/>
Pointeur vers un `CRect` objet de classe qui décrit la nouvelle position de l’élément. Si cet argument est NULL, la fonction utilise la position actuelle de l’élément.

### <a name="return-value"></a>Valeur de retour

Nonzero si l’élément est activé pour l’édition sur place et son facteur de zoom est autre que 100% (1:1); sinon 0.

### <a name="remarks"></a>Notes

Le facteur zoom, en pixels, est la proportion de la taille de l’élément dans sa mesure actuelle. Si l’application de conteneur n’a pas défini l’étendue de l’article, son étendue naturelle (comme déterminé par [COleServerItem::OnGetExtent](../../mfc/reference/coleserveritem-class.md#ongetextent)) est utilisée.

La fonction fixe ses deux premiers arguments au numérateur et au dénominateur du « facteur de zoom » de l’élément. Si l’élément n’est pas en place, la fonction définit ces arguments à une valeur par défaut de 100% (ou 1:1) et renvoie zéro. Pour plus d’informations, voir Note technique 40, [MFC/OLE In-Place Resizing and Zooming](../../mfc/tn040-mfc-ole-in-place-resizing-and-zooming.md).

## <a name="coleserverdocisdocobject"></a><a name="isdocobject"></a>COleServerDoc::IsDocObject

Détermine si le document est un DocObject.

```
BOOL IsDocObject() const;
```

### <a name="return-value"></a>Valeur de retour

VRAI si le document est un DocObject; autrement FALSE.

## <a name="coleserverdocisembedded"></a><a name="isembedded"></a>COleServerDoc::Isembedded

Appelez `IsEmbedded` la fonction membre pour déterminer si le document représente un objet intégré dans un conteneur.

```
BOOL IsEmbedded() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si `COleServerDoc` l’objet est un document qui représente un objet intégré dans un conteneur; sinon 0.

### <a name="remarks"></a>Notes

Un document chargé à partir d’un fichier n’est pas intégré bien qu’il puisse être manipulé par une application de conteneur comme un lien. Un document intégré dans un document de conteneurs est considéré comme intégré.

## <a name="coleserverdocisinplaceactive"></a><a name="isinplaceactive"></a>COleServerDoc::IsInPlaceActive

Appelez `IsInPlaceActive` la fonction membre pour déterminer si l’élément est actuellement dans l’état actif sur place.

```
BOOL IsInPlaceActive() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si `COleServerDoc` l’objet est actif en place; sinon 0.

## <a name="coleserverdocnotifychanged"></a><a name="notifychanged"></a>COleServerDoc::NotifyChanged

Appelez cette fonction pour informer tous les éléments liés liés au document que le document a changé.

```
void NotifyChanged();
```

### <a name="remarks"></a>Notes

En règle générale, vous appelez cette fonction après que l’utilisateur modifie un attribut global tel que les dimensions du document serveur. Si un élément OLE est lié au document avec un lien automatique, l’élément est mis à jour pour refléter les modifications. Dans les applications de conteneurs écrites avec la `COleClientItem` Microsoft Foundation Class Library, la fonction membre [OnChange](../../mfc/reference/coleclientitem-class.md#onchange) est appelée.

> [!NOTE]
> Cette fonction est incluse pour la compatibilité avec OLE 1. Les nouvelles applications devraient utiliser [UpdateAllItems](#updateallitems).

## <a name="coleserverdocnotifyclosed"></a><a name="notifyclosed"></a>COleServerDoc::NotifyClosed

Appelez cette fonction pour informer le conteneur(s) que le document a été fermé.

```
void NotifyClosed();
```

### <a name="remarks"></a>Notes

Lorsque l’utilisateur choisit la commande Close `NotifyClosed` dans `COleServerDoc`le menu Fichier, est appelé par la mise en œuvre de la fonction [membre OnCloseDocument.](../../mfc/reference/cdocument-class.md#onclosedocument) Dans les applications de conteneurs écrites avec la `COleClientItem` Microsoft Foundation Class Library, la fonction membre [OnChange](../../mfc/reference/coleclientitem-class.md#onchange) est appelée.

## <a name="coleserverdocnotifyrename"></a><a name="notifyrename"></a>COleServerDoc::NotifyRename

Appelez cette fonction après que l’utilisateur a renommé le document serveur.

```
void NotifyRename(LPCTSTR lpszNewName);
```

### <a name="parameters"></a>Paramètres

*lpszNewName (en)*<br/>
Pointer vers une chaîne spécifiant le nouveau nom du document serveur; il s’agit généralement d’un chemin entièrement qualifié.

### <a name="remarks"></a>Notes

Lorsque l’utilisateur choisit la commande Save `NotifyRename` As dans `COleServerDoc`le menu Fichier, est appelé par la mise en œuvre de la fonction membre [OnSaveDocument.](../../mfc/reference/cdocument-class.md#onsavedocument) Cette fonction informe les DLLs du système OLE, qui à leur tour avisent les conteneurs. Dans les applications de conteneurs écrites avec la `COleClientItem` Microsoft Foundation Class Library, la fonction membre [OnChange](../../mfc/reference/coleclientitem-class.md#onchange) est appelée.

## <a name="coleserverdocnotifysaved"></a><a name="notifysaved"></a>COleServerDoc::NotifySaved

Appelez cette fonction après que l’utilisateur enregistre le document serveur.

```
void NotifySaved();
```

### <a name="remarks"></a>Notes

Lorsque l’utilisateur choisit la commande Save `NotifySaved` dans le `COleServerDoc`menu Fichier, est appelé pour vous par la mise en œuvre de [OnSaveDocument](../../mfc/reference/cdocument-class.md#onsavedocument). Cette fonction informe les DLLs du système OLE, qui à leur tour avisent les conteneurs. Dans les applications de conteneurs écrites avec la `COleClientItem` Microsoft Foundation Class Library, la fonction membre [OnChange](../../mfc/reference/coleclientitem-class.md#onchange) est appelée.

## <a name="coleserverdoconclose"></a><a name="onclose"></a>COleServerDoc::OnClose

Appelé par le cadre lorsqu’un conteneur demande la fermeture du document serveur.

```
virtual void OnClose(OLECLOSE dwCloseOption);
```

### <a name="parameters"></a>Paramètres

*dwCloseOption*<br/>
Une valeur de l’énumération OLECLOSE. Ce paramètre peut prendre l'une des valeurs suivantes :

- OLECLOSE_SAVEIFDIRTY Le fichier est enregistré s’il a été modifié.

- OLECLOSE_NOSAVE Le fichier est fermé sans être enregistré.

- OLECLOSE_PROMPTSAVE Si le fichier a été modifié, l’utilisateur est invité à l’enregistrer.

### <a name="remarks"></a>Notes

Les appels `CDocument::OnCloseDocument`de mise en œuvre par défaut .

Pour plus d’informations et des valeurs supplémentaires, voir [OLECLOSE](/windows/win32/api/oleidl/ne-oleidl-oleclose) dans le SDK Windows.

## <a name="coleserverdocondeactivate"></a><a name="ondeactivate"></a>COleServerDoc::OnDeactivate

Appelé par le cadre lorsque l’utilisateur désactive un élément intégré ou lié qui est actuellement actif sur place.

```
virtual void OnDeactivate();
```

### <a name="remarks"></a>Notes

Cette fonction restaure l’interface utilisateur de l’application de conteneur à son état d’origine et détruit tous les menus et autres contrôles qui ont été créés pour l’activation en place.

Les informations de l’État annuler devraient être communiquées sans condition à ce stade.

Pour plus d’informations, voir l’article [Activation](../../mfc/activation-cpp.md)..

## <a name="coleserverdocondeactivateui"></a><a name="ondeactivateui"></a>COleServerDoc::OnDeactivateUI

Appelé lorsque l’utilisateur désactive un élément qui a été activé en place.

```
virtual void OnDeactivateUI(BOOL bUndoable);
```

### <a name="parameters"></a>Paramètres

*bUndoable*<br/>
Précise si les modifications d’édition peuvent être annulées.

### <a name="remarks"></a>Notes

Cette fonction restaure l’interface utilisateur de l’application de conteneur à son état d’origine, cachant tous les menus et autres contrôles qui ont été créés pour l’activation en place.

Le cadre définit toujours *bUndoable* à FALSE. Si le serveur prend en charge undo et il ya une opération qui peut être annulée, appelez la mise en œuvre de la classe de base avec *bUndoable* réglé à TRUE.

## <a name="coleserverdocondocwindowactivate"></a><a name="ondocwindowactivate"></a>COleServerDoc::OnDocWindowActivate

Le cadre appelle cette fonction pour activer ou désactiver une fenêtre de document pour l’édition en place.

```
virtual void OnDocWindowActivate(BOOL bActivate);
```

### <a name="parameters"></a>Paramètres

*bActivate (en)*<br/>
Précise si la fenêtre de document doit être activée ou désactivée.

### <a name="remarks"></a>Notes

L’implémentation par défaut supprime ou ajoute les éléments d’interface utilisateur au niveau du cadre, le cas échéant. Remplacez cette fonction si vous souhaitez effectuer des actions supplémentaires lorsque le document contenant votre article est activé ou désactivé.

Pour plus d’informations, voir l’article [Activation](../../mfc/activation-cpp.md)..

## <a name="coleserverdoconexecolecmd"></a><a name="onexecolecmd"></a>COleServerDoc::OnExecOleCmd

Le cadre appelle cette fonction pour exécuter une commande ou une aide d’affichage spécifiée pour la commande.

```
virtual HRESULT OnExecOleCmd(
    const GUID* pguidCmdGroup,
    DWORD nCmdID,
    DWORD nCmdExecOpt,
    VARIANTARG* pvarargIn,
    VARIANTARG* pvarargOut);
```

### <a name="parameters"></a>Paramètres

*pguidCmdGroup*<br/>
Un pointeur à un GUID qui identifie un ensemble de commandes. Peut être NULL pour indiquer le groupe de commande par défaut.

*nCmdID (en)*<br/>
Commande à exécuter. Doit faire dans le groupe identifié par *pguidCmdGroup*.

*nCmdExecOut (en anglais)*<br/>
La façon dont l’objet doit exécuter la commande, une ou plusieurs des valeurs suivantes de l’énumération OLECMDEXECOPT :

OLECMDEXECOPT_DODEFAULT

OLECMDEXECOPT_PROMPTUSER

OLECMDEXECOPT_DONTPROMPTUSER

OLECMDEXECOPT_SHOWHELP

*pvarargIn*<br/>
Pointeur vers un VARIANTARG contenant des arguments d’entrée pour la commande. Sa valeur peut être NULL.

*pvarargOut*<br/>
Pointeur vers un VARIANTARG pour recevoir les valeurs de retour de sortie de la commande. Sa valeur peut être NULL.

### <a name="return-value"></a>Valeur de retour

Retours S_OK en cas de succès; autrement, l’un des codes d’erreur suivants :

|Valeur|Description|
|-----------|-----------------|
|E_UNEXPECTED|Erreur inattendue s’est produite|
|E_FAIL|s'est produite|
|E_NOTIMPL|Indique que MFC lui-même devrait tenter de traduire et d’envoyer la commande|
|OLECMDERR_E_UNKNOWNGROUP|*pguidCmdGroup* n’est pas NULL mais ne précise pas un groupe de commandement reconnu|
|OLECMDERR_E_NOTSUPPORTED|*nCmdID* n’est pas reconnu comme une commande valide dans le groupe *pguidCmdGroup*|
|OLECMDERR_DISABLED|La commande identifiée par *nCmdID* est désactivée et ne peut pas être exécutée|
|OLECMDERR_NOHELP|L’appelant a demandé de l’aide sur la commande identifiée par *nCmdID,* mais aucune aide n’est disponible|
|OLECMDERR_CANCELED|L’utilisateur a annulé l’exécution|

### <a name="remarks"></a>Notes

`COleCmdUI`peut être utilisé pour activer, mettre à jour et définir d’autres propriétés des commandes d’interface utilisateur DocObject. Une fois les commandes sont parasécées, vous pouvez les exécuter avec `OnExecOleCmd`.

Le cadre appelle la fonction avant de tenter de traduire et d’envoyer une commande de documents OLE. Vous n’avez pas besoin de remplacer cette fonction pour gérer les commandes de documents OLE standard, mais vous devez fournir un remplacement à cette fonction si vous souhaitez gérer vos propres commandes personnalisées ou gérer les commandes qui acceptent les paramètres ou retournent les résultats.

La plupart des commandes ne prennent pas d’arguments ou ne retournent pas les valeurs. Pour une majorité de commandes, l’appelant peut passer nulLs pour *pvarargIn* et *pvarargOut*. Pour les commandes qui s’attendent à des valeurs d’entrée, l’appelant peut déclarer et initialiser une variable VARIANTARG et passer un pointeur à la variable dans *pvarargIn*. Pour les commandes qui nécessitent une valeur unique, l’argument peut être stocké directement dans le VARIANTARG et transmis à la fonction. Plusieurs arguments doivent être emballés au sein du VARIANTARG `IDispatch` à l’aide d’un des types pris en charge (tels que safeARRAY ).

De même, si une commande renvoie des arguments, l’appelant doit déclarer un VARIANTARG, l’initialiser à VT_EMPTY et passer son adresse en *pvarargOut*. Si une commande renvoie une seule valeur, l’objet peut stocker cette valeur directement en *pvarargOut*. Les valeurs de sortie multiples doivent être emballées d’une manière ou d’une autre appropriées pour le VARIANTARG.

La mise en œuvre de cette fonction par la classe de base permettra de mettre en œuvre les structures OLE_COMMAND_MAP associées à la cible de commandement et d’essayer d’envoyer la commande à un gestionnaire approprié. La mise en œuvre de la classe de base ne fonctionne qu’avec des commandes qui n’acceptent pas les arguments ou les valeurs de retour. Si vous avez besoin de gérer les commandes qui acceptent des arguments ou des valeurs de retour, vous devez passer outre à cette fonction et travailler avec les paramètres *pvarargIn* et *pvarargOut* vous-même.

## <a name="coleserverdoconframewindowactivate"></a><a name="onframewindowactivate"></a>COleServerDoc::OnFrameWindowActivate

Le cadre appelle cette fonction lorsque la fenêtre de cadre de l’application du conteneur est activée ou désactivée.

```
virtual void OnFrameWindowActivate(BOOL bActivate);
```

### <a name="parameters"></a>Paramètres

*bActivate (en)*<br/>
Précise si la fenêtre du cadre doit être activée ou désactivée.

### <a name="remarks"></a>Notes

La implémentation par défaut annule tous les modes d’aide dans lequel la fenêtre de cadre pourrait être. Remplacer cette fonction si vous souhaitez effectuer un traitement spécial lorsque la fenêtre du cadre est activée ou désactivée.

Pour plus d’informations, voir l’article [Activation](../../mfc/activation-cpp.md)..

## <a name="coleserverdocongetembeddeditem"></a><a name="ongetembeddeditem"></a>COleServerDoc::OnGetEmbeddedItem

Appelé par le cadre lorsqu’une application de conteneur appelle l’application serveur pour créer ou modifier un élément intégré.

```
virtual COleServerItem* OnGetEmbeddedItem() = 0;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur à un élément représentant l’ensemble du document; NULL si l’opération a échoué.

### <a name="remarks"></a>Notes

Il n'y a pas d'implémentation par défaut. Vous devez remplacer cette fonction pour retourner un élément qui représente l’ensemble du document. Cette valeur de rendement doit `COleServerItem`faire l’objet d’une classe dérivée.

## <a name="coleserverdoconreactivateandundo"></a><a name="onreactivateandundo"></a>COleServerDoc::OnReactivateAndUndo

Le cadre appelle cette fonction lorsque l’utilisateur choisit de annuler les modifications apportées à un élément qui a été activé en place, modifié, puis désactivé.

```
virtual BOOL OnReactivateAndUndo();
```

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

L’implémentation par défaut ne fait rien d’autre que le retour FALSE pour indiquer l’échec.

Remplacez cette fonction si votre application prend en charge undo. Habituellement, vous effectuez l’opération annuler, `ActivateInPlace`puis activer l’élément en appelant . Si l’application de conteneur est écrite `COleClientItem::ReactivateAndUndo` avec la bibliothèque de classe microsoft Foundation, l’appel provoque l’appel de cette fonction.

## <a name="coleserverdoconresizeborder"></a><a name="onresizeborder"></a>COleServerDoc::OnResizeBorder

Le cadre appelle cette fonction lorsque les fenêtres de cadre de l’application de conteneur changent de taille.

```
virtual void OnResizeBorder(
    LPCRECT lpRectBorder,
    LPOLEINPLACEUIWINDOW lpUIWindow,
    BOOL bFrame);
```

### <a name="parameters"></a>Paramètres

*lpRectBorder*<br/>
Pointer vers `RECT` une `CRect` structure ou un objet qui spécifie les coordonnées de la bordure.

*lpUIWindow*<br/>
Pointeur vers un `IOleInPlaceUIWindow` objet de classe qui possède la session d’édition actuelle sur place.

*bFrame (en)*<br/>
VRAI si *lpUIWindow* pointe vers la fenêtre de cadre de haut niveau de l’application de conteneur, ou FALSE si *lpUIWindow* pointe vers la fenêtre de cadre de l’application de conteneurs au niveau du document.

### <a name="remarks"></a>Notes

Cette fonction redimensionne et ajuste les barres d’outils et autres éléments d’interface utilisateur en fonction de la nouvelle taille de la fenêtre.

Pour plus d’informations, voir [IOleInPlaceUIWindow](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceuiwindow) dans le SDK Windows.

C’est un avancé primordial.

## <a name="coleserverdoconsethostnames"></a><a name="onsethostnames"></a>COleServerDoc::OnSetHostNames

Appelé par le cadre lorsque le conteneur définit ou modifie les noms d’hôte pour ce document.

```
virtual void OnSetHostNames(
    LPCTSTR lpszHost,
    LPCTSTR lpszHostObj);
```

### <a name="parameters"></a>Paramètres

*lpszHost (lpszHost)*<br/>
Pointeur à une chaîne qui spécifie le nom de l’application de conteneur.

*lpszHostObj*<br/>
Pointeur à une chaîne qui spécifie le nom du conteneur pour le document.

### <a name="remarks"></a>Notes

La mise en œuvre par défaut modifie le titre du document pour tous les points de vue se référant à ce document.

Remplacez cette fonction si votre application définit les titres à travers un mécanisme différent.

## <a name="coleserverdoconsetitemrects"></a><a name="onsetitemrects"></a>COleServerDoc::OnSetItemRects

Le cadre appelle cette fonction pour positionner la fenêtre de cadre d’édition en place dans la fenêtre de cadre de l’application de conteneur.

```
virtual void OnSetItemRects(
    LPCRECT lpPosRect,
    LPCRECT lpClipRect);
```

### <a name="parameters"></a>Paramètres

*lpPosRect*<br/>
Pointeur `RECT` vers une `CRect` structure ou un objet qui spécifie la position de la fenêtre de cadre sur place par rapport à la zone client de l’application de conteneur.

*lpClipRect*<br/>
Pointeur `RECT` vers une `CRect` structure ou un objet qui spécifie le rectangle de coupe de la fenêtre du cadre en place par rapport à la zone client de l’application de conteneur.

### <a name="remarks"></a>Notes

Remplacer cette fonction pour mettre à jour le facteur de zoom de la vue, si nécessaire.

Cette fonction est généralement appelée `RequestPositionChange` en réponse à un appel, bien qu’elle puisse être appelée à tout moment par le conteneur pour demander un changement de position pour l’élément sur place.

## <a name="coleserverdoconshowcontrolbars"></a><a name="onshowcontrolbars"></a>COleServerDoc::OnShowControlBars

Le cadre appelle cette fonction pour afficher ou masquer les barres de contrôle de l’application serveur associées à la fenêtre de cadre identifiée par *pFrameWnd*.

```
virtual void OnShowControlBars(
    CFrameWnd* pFrameWnd,
    BOOL bShow);
```

### <a name="parameters"></a>Paramètres

*pFrameWnd*<br/>
Pointeur vers la fenêtre de cadre dont les barres de contrôle doivent être cachées ou affichées.

*bShow (en)*<br/>
Détermine si les barres de contrôle sont affichées ou cachées.

### <a name="remarks"></a>Notes

L’implémentation par défaut énumère toutes les barres de contrôle appartenant à cette fenêtre de cadre et les cache ou les montre.

## <a name="coleserverdoconshowdocument"></a><a name="onshowdocument"></a>COleServerDoc::OnShowDocument

Le cadre `OnShowDocument` appelle la fonction lorsque le document serveur doit être caché ou affiché.

```
virtual void OnShowDocument(BOOL bShow);
```

### <a name="parameters"></a>Paramètres

*bShow (en)*<br/>
Précise si l’interface utilisateur du document doit être affichée ou cachée.

### <a name="remarks"></a>Notes

Si *bShow* est VRAI, l’implémentation par défaut active l’application du serveur, si nécessaire, et provoque l’application de conteneur à faire défiler sa fenêtre de sorte que l’élément est visible. Si *bShow* est FALSE, la implémentation par `OnDeactivate`défaut désactive l’élément par un appel à , puis détruit ou cache toutes les fenêtres de cadre qui ont été créés pour le document, sauf le premier. S’il n’y a pas de documents visibles, la implémentation par défaut cache l’application serveur.

## <a name="coleserverdoconupdatedocument"></a><a name="onupdatedocument"></a>COleServerDoc::OnUpdateDocument

Appelé par le cadre lors de l’enregistrement d’un document qui est un élément intégré dans un document composé.

```
virtual BOOL OnUpdateDocument();
```

### <a name="return-value"></a>Valeur de retour

Nonzero si le document a été mis à jour avec succès; sinon 0.

### <a name="remarks"></a>Notes

La implémentation par défaut appelle le [COleServerDoc::NotifySaved](#notifysaved) et [COleServerDoc::SaveEmbedding](#saveembedding) fonctions membres et marque ensuite le document comme propre. Remplacer cette fonction si vous souhaitez effectuer un traitement spécial lors de la mise à jour d’un élément intégré.

## <a name="coleserverdocrequestpositionchange"></a><a name="requestpositionchange"></a>COleServerDoc::RequestPositionChange

Appelez cette fonction de membre pour que l’application de conteneur change la position de l’élément.

```
void RequestPositionChange(LPCRECT lpPosRect);
```

### <a name="parameters"></a>Paramètres

*lpPosRect*<br/>
Pointeur `RECT` vers une `CRect` structure ou un objet contenant la nouvelle position de l’élément.

### <a name="remarks"></a>Notes

Cette fonction est généralement appelée `UpdateAllItems`(en conjonction avec ) lorsque les données d’un élément actif sur place ont changé. Suite à cet appel, le conteneur peut `OnSetItemRects`ou ne peut pas effectuer le changement en appelant . La position qui en résulte peut être différente de celle demandée.

## <a name="coleserverdocsaveembedding"></a><a name="saveembedding"></a>COleServerDoc::SaveEmbedding

Appelez cette fonction pour indiquer à l’application de conteneur pour enregistrer l’objet intégré.

```
void SaveEmbedding();
```

### <a name="remarks"></a>Notes

Cette fonction est `OnUpdateDocument`appelée automatiquement à partir de . Notez que cette fonction provoque la mise à jour de l’élément sur le disque, de sorte qu’il est généralement appelé uniquement à la suite d’une action utilisateur spécifique.

## <a name="coleserverdocscrollcontainerby"></a><a name="scrollcontainerby"></a>COleServerDoc::ScrollContainerBy

Appelez `ScrollContainerBy` la fonction membre pour faire défiler le document `sizeScroll`de conteneur par la quantité, en pixels, indiqué par .

```
BOOL ScrollContainerBy(CSize sizeScroll);
```

### <a name="parameters"></a>Paramètres

*tailleScroll*<br/>
Indique jusqu’où le document de conteneur doit faire défiler.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Les valeurs positives indiquent le défilement vers le bas et vers la droite; valeurs négatives indiquent le défilement vers le haut et vers la gauche.

## <a name="coleserverdocupdateallitems"></a><a name="updateallitems"></a>COleServerDoc::UpdateAllItems

Appelez cette fonction pour informer tous les éléments liés liés au document que le document a changé.

```
void UpdateAllItems(
    COleServerItem* pSender,
    LPARAM lHint = 0L,
    CObject* pHint = NULL,
    DVASPECT nDrawAspect = DVASPECT_CONTENT);
```

### <a name="parameters"></a>Paramètres

*pSender*<br/>
Pointeur vers l’élément qui a modifié le document, ou NULL si tous les éléments doivent être mis à jour.

*lHint (en anglais)*<br/>
Contient des informations sur la modification.

*pHint*<br/>
Pointeur vers un objet stockant des informations sur la modification.

*nDrawAspect (en anglais seulement)*<br/>
Détermine comment l’élément doit être dessiné. Il s’agit d’une valeur de l’énumération DVASPECT. Ce paramètre peut prendre l'une des valeurs suivantes :

- DVASPECT_CONTENT’élément est représenté de telle sorte qu’il puisse être affiché comme un objet intégré à l’intérieur de son conteneur.

- DVASPECT_THUMBNAIL’élément est rendu dans une représentation "thumbnail" afin qu’il puisse être affiché dans un outil de navigation.

- DVASPECT_ICON’élément est représenté par une icône.

- DVASPECT_DOCPRINT’article est représenté comme s’il avait été imprimé à l’aide de la commande d’impression du menu Fichier.

### <a name="remarks"></a>Notes

Vous appelez généralement cette fonction après que l’utilisateur a changé le document serveur. Si un élément OLE est lié au document avec un lien automatique, l’élément est mis à jour pour refléter les modifications. Dans les applications de conteneurs écrites avec la `COleClientItem` Microsoft Foundation Class Library, la fonction membre [OnChange](../../mfc/reference/coleclientitem-class.md#onchange) est appelée.

Cette fonction `OnUpdate` appelle la fonction membre pour chacun des éléments du document, sauf l’élément d’envoi, *passant pHint*, *lHint*, et *nDrawAspect*. Utilisez ces paramètres pour transmettre des informations aux éléments concernant les modifications apportées au document. Vous pouvez coder des informations à *l’aide de lHint* ou vous pouvez définir une `CObject`classe dérivée pour stocker des informations sur les modifications et passer un objet de cette classe à l’aide de *pHint*. Remplacer la `OnUpdate` fonction de `COleServerItem`membre dans votre classe dérivée afin d’optimiser la mise à jour de chaque élément selon que sa présentation a changé.

## <a name="see-also"></a>Voir aussi

[MFC Échantillon HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[COleLinkingDoc, classe](../../mfc/reference/colelinkingdoc-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[COleDocument, classe](../../mfc/reference/coledocument-class.md)<br/>
[COleLinkingDoc, classe](../../mfc/reference/colelinkingdoc-class.md)<br/>
[COleTemplateServer, classe](../../mfc/reference/coletemplateserver-class.md)
