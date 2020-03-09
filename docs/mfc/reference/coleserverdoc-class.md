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
ms.openlocfilehash: eec94a32fa0963d4cf2eccae0fb9e2423e75ffdc
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855502"
---
# <a name="coleserverdoc-class"></a>COleServerDoc, classe

Classe de base des documents serveur OLE.

## <a name="syntax"></a>Syntaxe

```
class AFX_NOVTABLE COleServerDoc : public COleLinkingDoc
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[COleServerDoc :: COleServerDoc](#coleserverdoc)|Construit un objet `COleServerDoc`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Name|Description|
|----------|-----------------|
|[COleServerDoc :: ActivateDocObject](#activatedocobject)|Active le document DocObject associé.|
|[COleServerDoc :: ActivateInPlace](#activateinplace)|Active le document pour la modification sur place.|
|[COleServerDoc ::D eactivateAndUndo](#deactivateandundo)|Désactive l’interface utilisateur du serveur.|
|[COleServerDoc ::D iscardUndoState](#discardundostate)|Ignore les informations d’état d’annulation.|
|[COleServerDoc :: GetClientSite](#getclientsite)|Récupère un pointeur vers l’interface de `IOleClientSite` sous-jacente.|
|[COleServerDoc :: GetEmbeddedItem](#getembeddeditem)|Retourne un pointeur vers un élément représentant le document entier.|
|[COleServerDoc :: GetItemClipRect](#getitemcliprect)|Retourne le rectangle de découpage actuel pour la modification sur place.|
|[COleServerDoc :: GetItemPosition](#getitemposition)|Retourne le rectangle de position actuel, relatif à la zone cliente de l’application conteneur, pour la modification sur place.|
|[COleServerDoc :: GetZoomFactor](#getzoomfactor)|Retourne le facteur de zoom en pixels.|
|[COleServerDoc :: IsDocObject](#isdocobject)|Détermine si le document est un DocObject.|
|[COleServerDoc :: IsEmbedded](#isembedded)|Indique si le document est incorporé dans un document conteneur ou en cours d’exécution autonome.|
|[COleServerDoc :: IsInPlaceActive](#isinplaceactive)|Retourne la valeur TRUE si l’élément est actuellement activé sur place.|
|[COleServerDoc :: NotifyChanged](#notifychanged)|Notifie les conteneurs que l’utilisateur a modifié le document.|
|[COleServerDoc :: NotifyClosed](#notifyclosed)|Notifie les conteneurs que l’utilisateur a fermé le document.|
|[COleServerDoc :: NotifyRename](#notifyrename)|Notifie les conteneurs que l’utilisateur a renommé le document.|
|[COleServerDoc :: NotifySaved](#notifysaved)|Avertit les conteneurs que l’utilisateur a enregistré le document.|
|[COleServerDoc :: OnDeactivate](#ondeactivate)|Appelé par le Framework lorsque l’utilisateur désactive un élément qui a été activé sur place.|
|[COleServerDoc :: OnDeactivateUI](#ondeactivateui)|Appelé par l’infrastructure pour détruire des contrôles et d’autres éléments d’interface utilisateur créés pour l’activation sur place.|
|[COleServerDoc :: OnDocWindowActivate](#ondocwindowactivate)|Appelé par le Framework lorsque la fenêtre frame de document du conteneur est activée ou désactivée.|
|[COleServerDoc :: OnResizeBorder](#onresizeborder)|Appelé par le Framework lorsque la fenêtre frame ou la fenêtre de document de l’application conteneur est redimensionnée.|
|[COleServerDoc :: OnShowControlBars](#onshowcontrolbars)|Appelé par l’infrastructure pour afficher ou masquer les barres de contrôles pour la modification sur place.|
|[COleServerDoc :: OnUpdateDocument](#onupdatedocument)|Appelé par le Framework lorsqu’un document serveur qui est un élément incorporé est enregistré, en mettant à jour la copie du conteneur de l’élément.|
|[COleServerDoc :: RequestPositionChange](#requestpositionchange)|Modifie la position du frame de modification sur place.|
|[COleServerDoc :: SaveEmbedding](#saveembedding)|Indique à l’application conteneur d’enregistrer le document.|
|[COleServerDoc :: ScrollContainerBy](#scrollcontainerby)|Fait défiler le document conteneur.|
|[COleServerDoc :: UpdateAllItems](#updateallitems)|Notifie les conteneurs que l’utilisateur a modifié le document.|

### <a name="protected-methods"></a>Méthodes protégées

|Name|Description|
|----------|-----------------|
|[COleServerDoc :: CreateInPlaceFrame](#createinplaceframe)|Appelé par l’infrastructure pour créer une fenêtre frame pour la modification sur place.|
|[COleServerDoc ::D estroyInPlaceFrame](#destroyinplaceframe)|Appelé par l’infrastructure pour détruire une fenêtre frame pour la modification sur place.|
|[COleServerDoc :: GetDocObjectServer](#getdocobjectserver)|Substituez cette fonction pour créer un nouvel `CDocObjectServer` objet et indiquez que ce document est un conteneur DocObject.|
|[COleServerDoc :: OnClose](#onclose)|Appelé par le Framework lorsqu’un conteneur demande de fermer le document.|
|[COleServerDoc :: OnExecOleCmd](#onexecolecmd)|Exécute une commande spécifiée ou affiche l’aide de la commande.|
|[COleServerDoc :: OnFrameWindowActivate](#onframewindowactivate)|Appelé par le Framework lorsque la fenêtre frame du conteneur est activée ou désactivée.|
|[COleServerDoc :: OnGetEmbeddedItem](#ongetembeddeditem)|Appelé pour obtenir un `COleServerItem` qui représente le document entier ; utilisé pour récupérer un élément incorporé. Implémentation requise.|
|[COleServerDoc :: OnReactivateAndUndo](#onreactivateandundo)|Appelé par l’infrastructure pour annuler les modifications apportées pendant la modification sur place.|
|[COleServerDoc :: OnSetHostNames](#onsethostnames)|Appelé par le Framework lorsqu’un conteneur définit le titre de la fenêtre pour un objet incorporé.|
|[COleServerDoc :: OnSetItemRects](#onsetitemrects)|Appelé par l’infrastructure pour positionner la fenêtre frame de modification sur place dans la fenêtre de l’application conteneur.|
|[COleServerDoc :: OnShowDocument](#onshowdocument)|Appelé par le Framework pour afficher ou masquer le document.|

## <a name="remarks"></a>Notes

Un document serveur peut contenir des objets [COleServerItem](../../mfc/reference/coleserveritem-class.md) , qui représentent l’interface de serveur pour les éléments incorporés ou liés. Quand une application serveur est lancée par un conteneur pour modifier un élément incorporé, l’élément est chargé comme son propre document serveur ; l’objet `COleServerDoc` contient un seul objet `COleServerItem`, constitué du document entier. Quand une application serveur est lancée par un conteneur pour modifier un élément lié, un document existant est chargé à partir du disque ; une partie du contenu du document est mise en surbrillance pour indiquer l’élément lié.

les objets `COleServerDoc` peuvent également contenir des éléments de la classe [COleClientItem](../../mfc/reference/coleclientitem-class.md) . Cela vous permet de créer des applications de serveur de conteneur. L’infrastructure fournit des fonctions permettant de stocker correctement les éléments de `COleClientItem` lors du traitement des objets `COleServerItem`.

Si votre application serveur ne prend pas en charge les liaisons, un document serveur ne contient toujours qu’un seul élément de serveur, qui représente la totalité de l’objet incorporé en tant que document. Si votre application serveur prend en charge les liens, elle doit créer un élément de serveur chaque fois qu’une sélection est copiée dans le presse-papiers.

Pour utiliser `COleServerDoc`, dérivez une classe de celle-ci et implémentez la fonction membre [OnGetEmbeddedItem](#ongetembeddeditem) , qui permet à votre serveur de prendre en charge les éléments incorporés. Dérivez une classe de `COleServerItem` pour implémenter les éléments de vos documents, et retournez les objets de cette classe à partir de `OnGetEmbeddedItem`.

Pour prendre en charge les éléments liés, `COleServerDoc` fournit la fonction membre [OnGetLinkedItem](../../mfc/reference/colelinkingdoc-class.md#ongetlinkeditem) . Vous pouvez utiliser l’implémentation par défaut ou la remplacer si vous disposez de votre propre méthode de gestion des éléments de document.

Vous avez besoin d’une classe dérivée de `COleServerDoc`pour chaque type de document serveur que votre application prend en charge. Par exemple, si votre application serveur prend en charge les feuilles de calcul et les graphiques, vous avez besoin de deux classes dérivées de `COleServerDoc`.

Pour plus d’informations sur les serveurs, consultez l’article [serveurs : implémentation d’un serveur](../../mfc/servers-implementing-a-server.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocument](../../mfc/reference/cdocument-class.md)

[COleDocument](../../mfc/reference/coledocument-class.md)

[COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)

`COleServerDoc`

## <a name="requirements"></a>Spécifications

**En-tête :** AFXOLE. h

##  <a name="activatedocobject"></a>COleServerDoc :: ActivateDocObject

Active le document DocObject associé.

```
void ActivateDocObject();
```

### <a name="remarks"></a>Notes

Par défaut, `COleServerDoc` ne prend pas en charge les documents actifs (également appelés DocObjects). Pour activer cette prise en charge, consultez [GetDocObjectServer](#getdocobjectserver) et Class [CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md).

##  <a name="activateinplace"></a>COleServerDoc :: ActivateInPlace

Active l’élément pour la modification sur place.

```
BOOL ActivateInPlace();
```

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite ; Sinon, 0, ce qui indique que l’élément est entièrement ouvert.

### <a name="remarks"></a>Notes

Cette fonction effectue toutes les opérations nécessaires pour l’activation sur place. Il crée une fenêtre frame sur place, l’active et la dimensionne à l’élément, configure des menus partagés et d’autres contrôles, fait défiler l’élément dans l’affichage et définit le focus sur la fenêtre frame sur place.

Cette fonction est appelée par l’implémentation par défaut de [COleServerItem :: onshow](../../mfc/reference/coleserveritem-class.md#onshow). Appelez cette fonction si votre application prend en charge un autre verbe pour l’activation sur place (par exemple, la lecture).

##  <a name="coleserverdoc"></a>COleServerDoc :: COleServerDoc

Construit un objet `COleServerDoc` sans se connecter à l’aide des DLL système OLE.

```
COleServerDoc();
```

### <a name="remarks"></a>Notes

Vous devez appeler [COleLinkingDoc :: Register](../../mfc/reference/colelinkingdoc-class.md#register) pour ouvrir communications avec OLE. Si vous utilisez [COleTemplateServer](../../mfc/reference/coletemplateserver-class.md) dans votre application, `COleLinkingDoc::Register` est appelé pour vous par `COleLinkingDoc`l’implémentation de `OnNewDocument`, `OnOpenDocument`et `OnSaveDocument`.

##  <a name="createinplaceframe"></a>COleServerDoc :: CreateInPlaceFrame

L’infrastructure appelle cette fonction pour créer une fenêtre frame pour la modification sur place.

```
virtual COleIPFrameWnd* CreateInPlaceFrame(CWnd* pParentWnd);
```

### <a name="parameters"></a>Paramètres

*pParentWnd*<br/>
Pointeur vers la fenêtre parente de l’application conteneur.

### <a name="return-value"></a>Valeur de retour

Pointeur vers la fenêtre frame sur place, ou NULL en cas d’échec.

### <a name="remarks"></a>Notes

L’implémentation par défaut utilise les informations spécifiées dans le modèle de document pour créer le frame. La vue utilisée est la première vue créée pour le document. Cette vue est détachée temporairement du frame d’origine et attachée au frame nouvellement créé.

Il s’agit d’un substituable avancé.

##  <a name="deactivateandundo"></a>COleServerDoc ::D eactivateAndUndo

Appelez cette fonction si votre application prend en charge l’annulation et que l’utilisateur choisit annuler après avoir activé un élément, mais avant de le modifier.

```
BOOL DeactivateAndUndo();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro en cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Si l’application conteneur est écrite à l’aide de la bibliothèque MFC (Microsoft Foundation Class), l’appel de cette fonction entraîne l’appel de [COleClientItem :: OnDeactivateAndUndo](../../mfc/reference/coleclientitem-class.md#ondeactivateandundo) , qui désactive l’interface utilisateur du serveur.

##  <a name="destroyinplaceframe"></a>COleServerDoc ::D estroyInPlaceFrame

L’infrastructure appelle cette fonction pour détruire une fenêtre frame sur place et retourner la fenêtre de document de l’application serveur à son état avant l’activation sur place.

```
virtual void DestroyInPlaceFrame(COleIPFrameWnd* pFrameWnd);
```

### <a name="parameters"></a>Paramètres

*pFrameWnd*<br/>
Pointeur vers la fenêtre frame sur place à détruire.

### <a name="remarks"></a>Notes

Il s’agit d’un substituable avancé.

##  <a name="discardundostate"></a>COleServerDoc ::D iscardUndoState

Si l’utilisateur effectue une opération de modification qui ne peut pas être annulée, appelez cette fonction pour forcer l’application conteneur à ignorer ses informations d’état d’annulation.

```
BOOL DiscardUndoState();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro en cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Cette fonction est fournie afin que les serveurs qui prennent en charge l’annulation puissent libérer des ressources qui seraient autrement consommées par des informations d’état d’annulation qui ne peuvent pas être utilisées.

##  <a name="getclientsite"></a>COleServerDoc :: GetClientSite

Récupère un pointeur vers l’interface de `IOleClientSite` sous-jacente.

```
LPOLECLIENTSITE GetClientSite() const;
```

### <a name="return-value"></a>Valeur de retour

Récupère un pointeur vers l’interface [IOleClientSite](/windows/win32/api/oleidl/nn-oleidl-ioleclientsite) sous-jacente.

##  <a name="getdocobjectserver"></a>COleServerDoc :: GetDocObjectServer

Substituez cette fonction pour créer un nouvel `CDocObjectServer` élément et retourner un pointeur vers celui-ci.

```
virtual CDocObjectServer* GetDocObjectServer(LPOLEDOCUMENTSITE pDocSite);
```

### <a name="parameters"></a>Paramètres

*pDocSite*<br/>
Pointeur vers l’interface `IOleDocumentSite` qui connectera ce document au serveur.

### <a name="return-value"></a>Valeur de retour

Pointeur vers un `CDocObjectServer`; NULL si l’opération a échoué.

### <a name="remarks"></a>Notes

Lorsqu’un serveur DocObject est activé, le retour d’un pointeur non NULL indique que le client peut prendre en charge DocObjects. L’implémentation par défaut retourne la valeur NULL.

Une implémentation classique d’un document qui prend en charge DocObjects allouera simplement un nouvel objet `CDocObjectServer` et le renverra à l’appelant. Par exemple :

[!code-cpp[NVC_MFCOleServer#3](../../mfc/codesnippet/cpp/coleserverdoc-class_1.cpp)]

##  <a name="getembeddeditem"></a>COleServerDoc :: GetEmbeddedItem

Appelez cette fonction pour obtenir un pointeur vers un élément représentant le document entier.

```
COleServerItem* GetEmbeddedItem();
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers un élément représentant l’intégralité du document ; NULL si l’opération a échoué.

### <a name="remarks"></a>Notes

Elle appelle [COleServerDoc :: OnGetEmbeddedItem](#ongetembeddeditem), une fonction virtuelle sans implémentation par défaut.

##  <a name="getitemcliprect"></a>COleServerDoc :: GetItemClipRect

Appelez la fonction membre `GetItemClipRect` pour récupérer les coordonnées du rectangle de découpage de l’élément qui est modifié sur place.

```
void GetItemClipRect(LPRECT lpClipRect) const;
```

### <a name="parameters"></a>Paramètres

*lpClipRect*<br/>
Pointeur vers une structure `RECT` ou un objet `CRect` pour recevoir les coordonnées du rectangle de découpage de l’élément.

### <a name="remarks"></a>Notes

Les coordonnées sont exprimées en pixels par rapport à la zone cliente de la fenêtre d’application du conteneur.

Le dessin ne doit pas se trouver en dehors du rectangle de découpage. En règle générale, le dessin est automatiquement limité. Utilisez cette fonction pour déterminer si l’utilisateur a fait défiler en dehors de la partie visible du document ; dans ce cas, faites défiler le document conteneur en fonction des besoins à l’aide d’un appel à [ScrollContainerBy](#scrollcontainerby).

##  <a name="getitemposition"></a>COleServerDoc :: GetItemPosition

Appelez la fonction membre `GetItemPosition` pour récupérer les coordonnées de l’élément en cours de modification sur place.

```
void GetItemPosition(LPRECT lpPosRect) const;
```

### <a name="parameters"></a>Paramètres

*lpPosRect*<br/>
Pointeur vers une structure `RECT` ou un objet `CRect` pour recevoir les coordonnées de l’élément.

### <a name="remarks"></a>Notes

Les coordonnées sont exprimées en pixels par rapport à la zone cliente de la fenêtre d’application du conteneur.

La position de l’élément peut être comparée au rectangle de découpage actuel pour déterminer dans quelle mesure l’élément est visible (ou non visible) à l’écran.

##  <a name="getzoomfactor"></a>COleServerDoc :: GetZoomFactor

La fonction membre `GetZoomFactor` détermine le facteur de zoom d’un élément qui a été activé pour la modification sur place.

```
BOOL GetZoomFactor(
    LPSIZE lpSizeNum = NULL,
    LPSIZE lpSizeDenom = NULL,
    LPCRECT lpPosRect = NULL) const;
```

### <a name="parameters"></a>Paramètres

*lpSizeNum*<br/>
Pointeur vers un objet de classe `CSize` qui contiendra le numérateur du facteur de zoom. Sa valeur peut être NULL.

*lpSizeDenom*<br/>
Pointeur vers un objet de classe `CSize` qui contiendra le dénominateur du facteur de zoom. Sa valeur peut être NULL.

*lpPosRect*<br/>
Pointeur vers un objet de la classe `CRect` qui décrit la nouvelle position de l’élément. Si cet argument a la valeur NULL, la fonction utilise la position actuelle de l’élément.

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’élément est activé pour la modification sur place et que son facteur de zoom est autre que 100% (1:1); Sinon, 0.

### <a name="remarks"></a>Notes

Le facteur de zoom, en pixels, correspond à la proportion de la taille de l’élément par rapport à son étendue actuelle. Si l’application conteneur n’a pas défini l’étendue de l’élément, son étendue naturelle (telle que déterminée par [COleServerItem :: OnGetExtent](../../mfc/reference/coleserveritem-class.md#ongetextent)) est utilisée.

La fonction définit ses deux premiers arguments sur le numérateur et le dénominateur du « facteur de zoom » de l’élément. Si l’élément n’est pas modifié sur place, la fonction définit ces arguments à une valeur par défaut de 100% (ou 1:1) et retourne zéro. Pour plus d’informations, consultez la note technique 40, [redimensionnement et zoom sur place de MFC/OLE](../../mfc/tn040-mfc-ole-in-place-resizing-and-zooming.md).

##  <a name="isdocobject"></a>COleServerDoc :: IsDocObject

Détermine si le document est un DocObject.

```
BOOL IsDocObject() const;
```

### <a name="return-value"></a>Valeur de retour

TRUE si le document est un DocObject ; Sinon, FALSe.

##  <a name="isembedded"></a>COleServerDoc :: IsEmbedded

Appelez la fonction membre `IsEmbedded` pour déterminer si le document représente un objet incorporé dans un conteneur.

```
BOOL IsEmbedded() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’objet `COleServerDoc` est un document qui représente un objet incorporé dans un conteneur ; Sinon, 0.

### <a name="remarks"></a>Notes

Un document chargé à partir d’un fichier n’est pas incorporé, bien qu’il puisse être manipulé par une application conteneur comme un lien. Un document incorporé dans un document conteneur est considéré comme incorporé.

##  <a name="isinplaceactive"></a>COleServerDoc :: IsInPlaceActive

Appelez la fonction membre `IsInPlaceActive` pour déterminer si l’élément se trouve actuellement dans l’état actif sur place.

```
BOOL IsInPlaceActive() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si l’objet `COleServerDoc` est actif sur place ; Sinon, 0.

##  <a name="notifychanged"></a>COleServerDoc :: NotifyChanged

Appelez cette fonction pour notifier tous les éléments liés connectés au document que le document a changé.

```
void NotifyChanged();
```

### <a name="remarks"></a>Notes

En général, vous appelez cette fonction après que l’utilisateur a modifié un attribut global tel que les dimensions du document serveur. Si un élément OLE est lié au document avec un lien automatique, l’élément est mis à jour pour refléter les modifications. Dans les applications de conteneur écrites avec le bibliothèque MFC (Microsoft Foundation Class), la fonction membre [OnChange](../../mfc/reference/coleclientitem-class.md#onchange) de `COleClientItem` est appelée.

> [!NOTE]
>  Cette fonction est incluse pour la compatibilité avec OLE 1. Les nouvelles applications doivent utiliser [UpdateAllItems](#updateallitems).

##  <a name="notifyclosed"></a>COleServerDoc :: NotifyClosed

Appelez cette fonction pour informer le ou les conteneurs que le document a été fermé.

```
void NotifyClosed();
```

### <a name="remarks"></a>Notes

Quand l’utilisateur choisit la commande fermer dans le menu fichier, `NotifyClosed` est appelée par l’implémentation de `COleServerDoc`de la fonction membre [OnCloseDocument](../../mfc/reference/cdocument-class.md#onclosedocument) . Dans les applications de conteneur écrites avec le bibliothèque MFC (Microsoft Foundation Class), la fonction membre [OnChange](../../mfc/reference/coleclientitem-class.md#onchange) de `COleClientItem` est appelée.

##  <a name="notifyrename"></a>COleServerDoc :: NotifyRename

Appelez cette fonction après que l’utilisateur a renommé le document serveur.

```
void NotifyRename(LPCTSTR lpszNewName);
```

### <a name="parameters"></a>Paramètres

*lpszNewName*<br/>
Pointeur vers une chaîne spécifiant le nouveau nom du document serveur ; Il s’agit généralement d’un chemin d’accès complet.

### <a name="remarks"></a>Notes

Quand l’utilisateur choisit la commande Enregistrer sous dans le menu fichier, `NotifyRename` est appelée par l’implémentation de `COleServerDoc`de la fonction membre [OnSaveDocument](../../mfc/reference/cdocument-class.md#onsavedocument) . Cette fonction avertit les DLL système OLE qui, à leur tour, informent les conteneurs. Dans les applications de conteneur écrites avec le bibliothèque MFC (Microsoft Foundation Class), la fonction membre [OnChange](../../mfc/reference/coleclientitem-class.md#onchange) de `COleClientItem` est appelée.

##  <a name="notifysaved"></a>COleServerDoc :: NotifySaved

Appelez cette fonction après que l’utilisateur a enregistré le document serveur.

```
void NotifySaved();
```

### <a name="remarks"></a>Notes

Quand l’utilisateur choisit la commande Enregistrer dans le menu fichier, `NotifySaved` est appelé pour vous par `COleServerDoc`l’implémentation de [OnSaveDocument](../../mfc/reference/cdocument-class.md#onsavedocument). Cette fonction avertit les DLL système OLE qui, à leur tour, informent les conteneurs. Dans les applications de conteneur écrites avec le bibliothèque MFC (Microsoft Foundation Class), la fonction membre [OnChange](../../mfc/reference/coleclientitem-class.md#onchange) de `COleClientItem` est appelée.

##  <a name="onclose"></a>COleServerDoc :: OnClose

Appelé par le Framework lorsqu’un conteneur demande que le document serveur soit fermé.

```
virtual void OnClose(OLECLOSE dwCloseOption);
```

### <a name="parameters"></a>Paramètres

*dwCloseOption*<br/>
Valeur de l’énumération OLECLOSE. Ce paramètre peut prendre l'une des valeurs suivantes :

- OLECLOSE_SAVEIFDIRTY le fichier est enregistré s’il a été modifié.

- OLECLOSE_NOSAVE le fichier est fermé sans être enregistré.

- OLECLOSE_PROMPTSAVE si le fichier a été modifié, l’utilisateur est invité à l’enregistrer.

### <a name="remarks"></a>Notes

L’implémentation par défaut appelle `CDocument::OnCloseDocument`.

Pour plus d’informations et pour obtenir des valeurs supplémentaires, consultez [OLECLOSE](/windows/win32/api/oleidl/ne-oleidl-oleclose) dans le SDK Windows.

##  <a name="ondeactivate"></a>COleServerDoc :: OnDeactivate

Appelée par l’infrastructure lorsque l’utilisateur désactive un élément incorporé ou lié qui est actuellement actif.

```
virtual void OnDeactivate();
```

### <a name="remarks"></a>Notes

Cette fonction restaure l’interface utilisateur de l’application conteneur à son état d’origine et détruit tous les menus et autres contrôles qui ont été créés pour l’activation sur place.

Les informations d’état d’annulation doivent être libérées sans condition à ce stade.

Pour plus d’informations, consultez l’article [activation](../../mfc/activation-cpp.md)..

##  <a name="ondeactivateui"></a>COleServerDoc :: OnDeactivateUI

Appelé lorsque l’utilisateur désactive un élément qui a été activé sur place.

```
virtual void OnDeactivateUI(BOOL bUndoable);
```

### <a name="parameters"></a>Paramètres

*bUndoable*<br/>
Spécifie si les modifications de modification peuvent être annulées.

### <a name="remarks"></a>Notes

Cette fonction restaure l’état d’origine de l’interface utilisateur de l’application conteneur, en masquant les menus et les autres contrôles qui ont été créés pour l’activation sur place.

L’infrastructure affecte toujours la valeur FALSe à *bUndoable* . Si le serveur prend en charge l’annulation et qu’une opération peut être annulée, appelez l’implémentation de la classe de base avec *bUndoable* défini sur true.

##  <a name="ondocwindowactivate"></a>COleServerDoc :: OnDocWindowActivate

L’infrastructure appelle cette fonction pour activer ou désactiver une fenêtre de document pour la modification sur place.

```
virtual void OnDocWindowActivate(BOOL bActivate);
```

### <a name="parameters"></a>Paramètres

*bActivate*<br/>
Spécifie si la fenêtre de document doit être activée ou désactivée.

### <a name="remarks"></a>Notes

L’implémentation par défaut supprime ou ajoute les éléments de l’interface utilisateur au niveau de la trame, le cas échéant. Remplacez cette fonction si vous souhaitez effectuer des actions supplémentaires lorsque le document contenant votre élément est activé ou désactivé.

Pour plus d’informations, consultez l’article [activation](../../mfc/activation-cpp.md)..

##  <a name="onexecolecmd"></a>COleServerDoc :: OnExecOleCmd

L’infrastructure appelle cette fonction pour exécuter une commande spécifiée ou afficher l’aide de la commande.

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
Pointeur vers un GUID qui identifie un jeu de commandes. Peut avoir la valeur NULL pour indiquer le groupe de commandes par défaut.

*nCmdID*<br/>
Commande à exécuter. Doit se trouver dans le groupe identifié par *pguidCmdGroup*.

*nCmdExecOut*<br/>
La façon dont l’objet doit exécuter la commande, une ou plusieurs des valeurs suivantes de l’énumération OLECMDEXECOPT :

OLECMDEXECOPT_DODEFAULT

OLECMDEXECOPT_PROMPTUSER

OLECMDEXECOPT_DONTPROMPTUSER

OLECMDEXECOPT_SHOWHELP

*pvarargIn*<br/>
Pointeur vers un VARIANTARG contenant des arguments d’entrée pour la commande. Sa valeur peut être NULL.

*pvarargOut*<br/>
Pointeur vers un VARIANTARG pour recevoir les valeurs de retour de sortie de la commande. Sa valeur peut être NULL.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite ; dans le cas contraire, l’un des codes d’erreur suivants :

|Valeur|Description|
|-----------|-----------------|
|E_UNEXPECTED|Une erreur inattendue s’est produite|
|E_FAIL|s'est produite|
|E_NOTIMPL|Indique que MFC lui-même doit tenter de traduire et de distribuer la commande|
|OLECMDERR_E_UNKNOWNGROUP|*pguidCmdGroup* n’est pas null mais ne spécifie pas un groupe de commandes reconnu|
|OLECMDERR_E_NOTSUPPORTED|*nCmdId* n’est pas reconnu en tant que commande valide dans le groupe *pguidCmdGroup*|
|OLECMDERR_DISABLED|La commande identifiée par *nCmdId* est désactivée et ne peut pas être exécutée|
|OLECMDERR_NOHELP|L’appelant a demandé de l’aide sur la commande identifiée par *nCmdId* , mais aucune aide n’est disponible|
|OLECMDERR_CANCELED|L’utilisateur a annulé l’exécution|

### <a name="remarks"></a>Notes

`COleCmdUI` peut être utilisé pour activer, mettre à jour et définir d’autres propriétés des commandes de l’interface utilisateur DocObject. Une fois les commandes initialisées, vous pouvez les exécuter avec `OnExecOleCmd`.

L’infrastructure appelle la fonction avant de tenter de traduire et de distribuer une commande de document OLE. Vous n’avez pas besoin de remplacer cette fonction pour gérer les commandes de document OLE standard, mais vous devez fournir un remplacement à cette fonction si vous souhaitez gérer vos propres commandes personnalisées ou gérer les commandes qui acceptent des paramètres ou retournent des résultats.

La plupart des commandes n’acceptent pas d’arguments ou de valeurs de retour. Pour la plupart des commandes, l’appelant peut passer des valeurs NULL pour *pvarargIn* et *pvarargOut*. Pour les commandes qui attendent des valeurs d’entrée, l’appelant peut déclarer et initialiser une variable VARIANTARG et passer un pointeur vers la variable dans *pvarargIn*. Pour les commandes qui requièrent une seule valeur, l’argument peut être stocké directement dans le VARIANTARG et passé à la fonction. Plusieurs arguments doivent être empaquetés dans le VARIANTARG à l’aide de l’un des types pris en charge (par exemple `IDispatch` et SAFEARRAY).

De même, si une commande retourne des arguments, l’appelant est supposé déclarer un VARIANTARG, l’initialiser pour VT_EMPTY et passer son adresse dans *pvarargOut*. Si une commande retourne une valeur unique, l’objet peut stocker cette valeur directement dans *pvarargOut*. Plusieurs valeurs de sortie doivent être empaquetées de manière appropriée pour le VARIANTARG.

L’implémentation de la classe de base de cette fonction parcourt les structures de OLE_COMMAND_MAP associées à la cible de commande et tente de distribuer la commande vers un gestionnaire approprié. L’implémentation de la classe de base fonctionne uniquement avec les commandes qui n’acceptent pas d’arguments ou de valeurs de retour. Si vous devez gérer des commandes qui acceptent des arguments ou des valeurs de retour, vous devez remplacer cette fonction et utiliser les paramètres *pvarargIn* et *pvarargOut* vous-même.

##  <a name="onframewindowactivate"></a>COleServerDoc :: OnFrameWindowActivate

L’infrastructure appelle cette fonction lorsque la fenêtre frame de l’application conteneur est activée ou désactivée.

```
virtual void OnFrameWindowActivate(BOOL bActivate);
```

### <a name="parameters"></a>Paramètres

*bActivate*<br/>
Spécifie si la fenêtre frame doit être activée ou désactivée.

### <a name="remarks"></a>Notes

L’implémentation par défaut annule tous les modes d’aide dans lesquels se trouve la fenêtre frame. Remplacez cette fonction si vous souhaitez effectuer un traitement spécial lorsque la fenêtre frame est activée ou désactivée.

Pour plus d’informations, consultez l’article [activation](../../mfc/activation-cpp.md)..

##  <a name="ongetembeddeditem"></a>COleServerDoc :: OnGetEmbeddedItem

Appelée par le Framework lorsqu’une application conteneur appelle l’application serveur pour créer ou modifier un élément incorporé.

```
virtual COleServerItem* OnGetEmbeddedItem() = 0;
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers un élément représentant l’intégralité du document ; NULL si l’opération a échoué.

### <a name="remarks"></a>Notes

Il n'y a pas d'implémentation par défaut. Vous devez substituer cette fonction pour retourner un élément qui représente le document entier. Cette valeur de retour doit être un objet d’une classe dérivée de `COleServerItem`.

##  <a name="onreactivateandundo"></a>COleServerDoc :: OnReactivateAndUndo

L’infrastructure appelle cette fonction lorsque l’utilisateur choisit d’annuler les modifications apportées à un élément qui a été activé sur place, modifié et ensuite désactivé.

```
virtual BOOL OnReactivateAndUndo();
```

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

L’implémentation par défaut ne fait rien, sauf que retourne FALSe pour indiquer un échec.

Remplacez cette fonction si votre application prend en charge l’annulation. En général, vous effectuez l’opération d’annulation, puis vous activez l’élément en appelant `ActivateInPlace`. Si l’application conteneur est écrite avec le bibliothèque MFC (Microsoft Foundation Class), l’appel de `COleClientItem::ReactivateAndUndo` entraîne l’appel de cette fonction.

##  <a name="onresizeborder"></a>COleServerDoc :: OnResizeBorder

L’infrastructure appelle cette fonction lorsque les fenêtres frame de l’application conteneur changent de taille.

```
virtual void OnResizeBorder(
    LPCRECT lpRectBorder,
    LPOLEINPLACEUIWINDOW lpUIWindow,
    BOOL bFrame);
```

### <a name="parameters"></a>Paramètres

*lpRectBorder*<br/>
Pointeur vers une structure `RECT` ou un objet `CRect` qui spécifie les coordonnées de la bordure.

*lpUIWindow*<br/>
Pointeur vers un objet de la classe `IOleInPlaceUIWindow` qui possède la session d’édition sur place actuelle.

*bFrame*<br/>
TRUE si *lpUIWindow* pointe vers la fenêtre frame de niveau supérieur de l’application conteneur, ou false si *lpUIWindow* pointe vers la fenêtre frame de niveau document de l’application conteneur.

### <a name="remarks"></a>Notes

Cette fonction redimensionne et ajuste les barres d’outils et autres éléments de l’interface utilisateur en fonction de la nouvelle taille de fenêtre.

Pour plus d’informations, consultez [IOleInPlaceUIWindow](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceuiwindow) dans le SDK Windows.

Il s’agit d’un substituable avancé.

##  <a name="onsethostnames"></a>COleServerDoc :: OnSetHostNames

Appelée par l’infrastructure quand le conteneur définit ou modifie les noms d’hôte pour ce document.

```
virtual void OnSetHostNames(
    LPCTSTR lpszHost,
    LPCTSTR lpszHostObj);
```

### <a name="parameters"></a>Paramètres

*lpszHost*<br/>
Pointeur vers une chaîne qui spécifie le nom de l’application conteneur.

*lpszHostObj*<br/>
Pointeur vers une chaîne qui spécifie le nom du conteneur pour le document.

### <a name="remarks"></a>Notes

L’implémentation par défaut modifie le titre du document pour toutes les vues faisant référence à ce document.

Substituez cette fonction si votre application définit les titres par le biais d’un mécanisme différent.

##  <a name="onsetitemrects"></a>COleServerDoc :: OnSetItemRects

L’infrastructure appelle cette fonction pour positionner la fenêtre frame de modification sur place dans la fenêtre frame de l’application conteneur.

```
virtual void OnSetItemRects(
    LPCRECT lpPosRect,
    LPCRECT lpClipRect);
```

### <a name="parameters"></a>Paramètres

*lpPosRect*<br/>
Pointeur vers une structure `RECT` ou un objet `CRect` qui spécifie la position de la fenêtre frame sur place par rapport à la zone cliente de l’application conteneur.

*lpClipRect*<br/>
Pointeur vers une structure `RECT` ou un objet `CRect` qui spécifie le rectangle de découpage de la fenêtre frame sur place par rapport à la zone cliente de l’application conteneur.

### <a name="remarks"></a>Notes

Remplacez cette fonction pour mettre à jour le facteur de zoom de la vue, si nécessaire.

Cette fonction est généralement appelée en réponse à un appel de `RequestPositionChange`, bien qu’elle puisse être appelée à tout moment par le conteneur pour demander une modification de position pour l’élément sur place.

##  <a name="onshowcontrolbars"></a>COleServerDoc :: OnShowControlBars

L’infrastructure appelle cette fonction pour afficher ou masquer les barres de contrôle de l’application serveur associées à la fenêtre frame identifiée par *pFrameWnd*.

```
virtual void OnShowControlBars(
    CFrameWnd* pFrameWnd,
    BOOL bShow);
```

### <a name="parameters"></a>Paramètres

*pFrameWnd*<br/>
Pointeur vers la fenêtre frame dont les barres de contrôle doivent être masquées ou affichées.

*bShow*<br/>
Détermine si les barres de contrôle sont affichées ou masquées.

### <a name="remarks"></a>Notes

L’implémentation par défaut énumère toutes les barres de contrôle détenues par cette fenêtre frame et les masque ou les affiche.

##  <a name="onshowdocument"></a>COleServerDoc :: OnShowDocument

L’infrastructure appelle la fonction `OnShowDocument` lorsque le document serveur doit être masqué ou affiché.

```
virtual void OnShowDocument(BOOL bShow);
```

### <a name="parameters"></a>Paramètres

*bShow*<br/>
Spécifie si l’interface utilisateur du document doit être affichée ou masquée.

### <a name="remarks"></a>Notes

Si *bShow* a la valeur true, l’implémentation par défaut active l’application serveur, si nécessaire, et fait en sorte que l’application conteneur fasse défiler sa fenêtre pour que l’élément soit visible. Si *bShow* a la valeur false, l’implémentation par défaut désactive l’élément par le biais d’un appel à `OnDeactivate`, puis détruit ou masque toutes les fenêtres frame qui ont été créées pour le document, à l’exception du premier. Si aucun document visible ne subsiste, l’implémentation par défaut masque l’application serveur.

##  <a name="onupdatedocument"></a>COleServerDoc :: OnUpdateDocument

Appelée par l’infrastructure lors de l’enregistrement d’un document qui est un élément incorporé dans un document composé.

```
virtual BOOL OnUpdateDocument();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le document a été mis à jour avec succès ; Sinon, 0.

### <a name="remarks"></a>Notes

L’implémentation par défaut appelle les fonctions membres [COleServerDoc :: NotifySaved](#notifysaved) et [COleServerDoc :: SaveEmbedding](#saveembedding) , puis marque le document comme propre. Remplacez cette fonction si vous souhaitez effectuer un traitement spécial lors de la mise à jour d’un élément incorporé.

##  <a name="requestpositionchange"></a>COleServerDoc :: RequestPositionChange

Appelez cette fonction membre pour que l’application conteneur modifie la position de l’élément.

```
void RequestPositionChange(LPCRECT lpPosRect);
```

### <a name="parameters"></a>Paramètres

*lpPosRect*<br/>
Pointeur vers une structure `RECT` ou un objet `CRect` contenant la nouvelle position de l’élément.

### <a name="remarks"></a>Notes

Cette fonction est généralement appelée (conjointement avec `UpdateAllItems`) lorsque les données d’un élément actif sur place ont été modifiées. Après cet appel, le conteneur peut ou ne peut pas effectuer la modification en appelant `OnSetItemRects`. La position résultante peut être différente de celle demandée.

##  <a name="saveembedding"></a>COleServerDoc :: SaveEmbedding

Appelez cette fonction pour indiquer à l’application conteneur d’enregistrer l’objet incorporé.

```
void SaveEmbedding();
```

### <a name="remarks"></a>Notes

Cette fonction est appelée automatiquement à partir de `OnUpdateDocument`. Notez que cette fonction entraîne la mise à jour de l’élément sur le disque, donc elle est généralement appelée uniquement à la suite d’une action spécifique de l’utilisateur.

##  <a name="scrollcontainerby"></a>COleServerDoc :: ScrollContainerBy

Appelez la fonction membre `ScrollContainerBy` pour faire défiler le document conteneur du montant, en pixels, indiqué par `sizeScroll`.

```
BOOL ScrollContainerBy(CSize sizeScroll);
```

### <a name="parameters"></a>Paramètres

*sizeScroll*<br/>
Indique la distance de défilement du document conteneur.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0.

### <a name="remarks"></a>Notes

Les valeurs positives indiquent le défilement vers le dessous et vers la droite ; les valeurs négatives indiquent le défilement vers le haut et vers la gauche.

##  <a name="updateallitems"></a>COleServerDoc :: UpdateAllItems

Appelez cette fonction pour notifier tous les éléments liés connectés au document que le document a changé.

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

*lHint*<br/>
Contient des informations sur la modification.

*pHint*<br/>
Pointeur vers un objet qui stocke des informations sur la modification.

*nDrawAspect*<br/>
Détermine le mode de dessin de l’élément. Il s’agit d’une valeur de l’énumération DVASPECT. Ce paramètre peut prendre l'une des valeurs suivantes :

- DVASPECT_CONTENT élément est représenté de façon à ce qu’il puisse être affiché sous la forme d’un objet incorporé à l’intérieur de son conteneur.

- DVASPECT_THUMBNAIL élément est rendu dans une représentation « miniature » afin qu’il puisse être affiché dans un outil de navigation.

- DVASPECT_ICON élément est représenté par une icône.

- DVASPECT_DOCPRINT élément est représenté comme s’il avait été imprimé à l’aide de la commande Imprimer du menu fichier.

### <a name="remarks"></a>Notes

En général, vous appelez cette fonction une fois que l’utilisateur a modifié le document serveur. Si un élément OLE est lié au document avec un lien automatique, l’élément est mis à jour pour refléter les modifications. Dans les applications de conteneur écrites avec le bibliothèque MFC (Microsoft Foundation Class), la fonction membre [OnChange](../../mfc/reference/coleclientitem-class.md#onchange) de `COleClientItem` est appelée.

Cette fonction appelle la fonction membre `OnUpdate` pour chacun des éléments du document, à l’exception de l’élément émetteur, passant *pHint*, *lHint*et *nDrawAspect*. Utilisez ces paramètres pour transmettre des informations aux éléments concernant les modifications apportées au document. Vous pouvez encoder des informations à l’aide de *lHint* ou vous pouvez définir une classe dérivée de `CObject`pour stocker des informations sur les modifications et passer un objet de cette classe à l’aide de *pHint*. Substituez la fonction membre `OnUpdate` dans votre classe dérivée de `COleServerItem`pour optimiser la mise à jour de chaque élément selon que sa présentation a changé ou non.

## <a name="see-also"></a>Voir aussi

[Exemple MFC HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[COleLinkingDoc, classe](../../mfc/reference/colelinkingdoc-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[COleDocument, classe](../../mfc/reference/coledocument-class.md)<br/>
[COleLinkingDoc, classe](../../mfc/reference/colelinkingdoc-class.md)<br/>
[COleTemplateServer, classe](../../mfc/reference/coletemplateserver-class.md)
