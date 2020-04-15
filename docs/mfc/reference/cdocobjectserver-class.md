---
title: CDocObjectServer, classe
ms.date: 09/12/2018
f1_keywords:
- CDocObjectServer
- AFXDOCOB/CDocObjectServer
- AFXDOCOB/CDocObjectServer::CDocObjectServer
- AFXDOCOB/CDocObjectServer::ActivateDocObject
- AFXDOCOB/CDocObjectServer::OnActivateView
- AFXDOCOB/CDocObjectServer::OnApplyViewState
- AFXDOCOB/CDocObjectServer::OnSaveViewState
helpviewer_keywords:
- CDocObjectServer [MFC], CDocObjectServer
- CDocObjectServer [MFC], ActivateDocObject
- CDocObjectServer [MFC], OnActivateView
- CDocObjectServer [MFC], OnApplyViewState
- CDocObjectServer [MFC], OnSaveViewState
ms.assetid: 18cd0dff-0616-4472-b8d9-66c081bc383a
ms.openlocfilehash: ccd8ddc9f4981b3d9f7f4e1decdf6790cd05b98b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375493"
---
# <a name="cdocobjectserver-class"></a>CDocObjectServer, classe

Implémente les interfaces OLE supplémentaires nécessaires pour transformer un serveur normal `COleDocument` en serveur DocObject complet : `IOleDocument`, `IOleDocumentView`, `IOleCommandTarget`et `IPrint`.

## <a name="syntax"></a>Syntaxe

```
class CDocObjectServer : public CCmdTarget
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CDocObjectServer::CDocObjectServer](#cdocobjectserver)|Construit un objet `CDocObjectServer`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CDocObjectServer::ActivateDocObject](#activatedocobject)|Active le serveur d’objets de document, mais ne le montre pas.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CDocObjectServer::OnActivateView](#onactivateview)|Affiche la vue DocObject.|
|[CDocObjectServer::OnApplyViewState](#onapplyviewstate)|Restaure l’état de la vue DocObject.|
|[CDocObjectServer::OnSaveViewState](#onsaveviewstate)|Enregistre l’état de la vue DocObject.|

## <a name="remarks"></a>Notes

`CDocObjectServer`est dérivé `CCmdTarget` et travaille `COleServerDoc` en étroite collaboration avec pour exposer les interfaces.

Un document serveur DocObject peut contenir des objets [CDocObjectServerItem,](../../mfc/reference/cdocobjectserveritem-class.md) qui représentent l’interface serveur des éléments DocObject.

Pour personnaliser votre serveur DocObject, dérivez votre propre classe et remplacez ses fonctions de `CDocObjectServer` configuration de vue, [OnActivateView](#onactivateview), [OnApplyViewState](#onapplyviewstate), et [OnSaveViewState](#onsaveviewstate). Vous devrez fournir une nouvelle instance de votre classe en réponse aux appels-cadres.

Pour plus d’informations sur DocObjects, voir [CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md) et [COleCmdUI](../../mfc/reference/colecmdui-class.md) dans la *référence MFC*.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDocObjectServer`

## <a name="requirements"></a>Spécifications

**En-tête:** afxdocob.h

## <a name="cdocobjectserveractivatedocobject"></a><a name="activatedocobject"></a>CDocObjectServer::ActivateDocObject

Appelez cette fonction pour activer (mais pas afficher) le serveur d’objets de document.

```
void ActivateDocObject();
```

### <a name="remarks"></a>Notes

`ActivateDocObject`la `IOleDocumentSite`méthode `ActivateMe` des appels, mais ne montre pas la vue parce qu’elle attend des instructions spécifiques sur la façon de configurer et d’afficher la vue, donnée dans l’appel à [CDocObjectServer::OnActivateView](#onactivateview).

Ensemble, `ActivateDocObject` `OnActivateView` activez et affichez la vue DocObject. L’activation docObject diffère des autres types d’activation OLE sur place. Les contournements d’activation DocObject affichant les bordures d’écoutilles sur place et les ornements d’objets (comme les poignées de dimensionnement), ignorent les fonctions d’étendue de l’objet et dessinent des barres de défilement dans le rectangle de vue plutôt que de les dessiner à l’extérieur de ce rectangle (comme dans l’activation normale sur place).

## <a name="cdocobjectservercdocobjectserver"></a><a name="cdocobjectserver"></a>CDocObjectServer::CDocObjectServer

Construit et initialise un objet `CDocObjectServer`.

```
explicit CDocObjectServer(
    COleServerDoc* pOwner,
    LPOLEDOCUMENTSITE pDocSite = NULL);
```

### <a name="parameters"></a>Paramètres

*pOwner (en)*<br/>
Un pointeur vers le document de site client qui est le client pour le serveur DocObject.

*pDocSite (en)*<br/>
Un pointeur `IOleDocumentSite` à l’interface implémentée par le conteneur.

### <a name="remarks"></a>Notes

Lorsqu’un DocObject est actif, l’interface OLE du site client ( `IOleDocumentSite`) est ce qui permet au serveur DocObject de communiquer avec son client (le conteneur). Lorsqu’un serveur DocObject est activé, il vérifie `IOleDocumentSite` d’abord que le conteneur implémente l’interface. Si c’est le cas, [COleServerDoc:GetDocObjectServer](../../mfc/reference/coleserverdoc-class.md#getdocobjectserver) est appelé pour voir si le conteneur prend en charge DocObjects. Par défaut, `GetDocObjectServer` retourne NULL. Vous devez `COleServerDoc::GetDocObjectServer` passer outre `CDocObjectServer` pour construire un nouvel objet ou un `COleServerDoc` objet dérivé `IOleDocumentSite` de votre propre, avec des pointeurs sur le conteneur et son interface comme arguments pour le constructeur.

## <a name="cdocobjectserveronactivateview"></a><a name="onactivateview"></a>CDocObjectServer::OnActivateView

Appelez cette fonction pour afficher la vue DocObject.

```
virtual HRESULT OnActivateView();
```

### <a name="return-value"></a>Valeur de retour

Renvoie une valeur d’erreur ou d’avertissement. Par défaut, les retours NOERROR en cas de succès; autrement, E_FAIL.

### <a name="remarks"></a>Notes

Cette fonction crée une fenêtre de cadre en place, dessine des barres de défilement dans la vue, met en place les menus que le serveur partage avec son conteneur, ajoute des contrôles de cadre, définit l’objet actif, puis affiche enfin la fenêtre de cadre en place et met l’accent.

## <a name="cdocobjectserveronapplyviewstate"></a><a name="onapplyviewstate"></a>CDocObjectServer::OnApplyViewState

Remplacer cette fonction pour restaurer l’état de la vue DocObject.

```
virtual void OnApplyViewState(CArchive& ar);
```

### <a name="parameters"></a>Paramètres

*Ar*<br/>
Un `CArchive` objet à partir duquel sérialiser l’état de vue.

### <a name="remarks"></a>Notes

Cette fonction est appelée lorsque la vue est affichée pour la première fois après son instantanéisation. `OnApplyViewState`indique une vue de se réinitialiser `CArchive` en fonction des données de l’objet précédemment enregistré avec [OnSaveViewState](#onsaveviewstate). La vue doit valider `CArchive` les données dans l’objet parce que le conteneur ne tente pas d’interpréter les données d’état de vue de quelque façon que ce soit.

Vous pouvez `OnSaveViewState` utiliser pour stocker des informations persistantes spécifiques à l’état de votre vue. Si vous `OnSaveViewState` remplacez pour stocker des informations, vous voudrez passer outre `OnApplyViewState` pour lire ces informations et les appliquer à votre vue lorsqu’elle est nouvellement activée.

## <a name="cdocobjectserveronsaveviewstate"></a><a name="onsaveviewstate"></a>CDocObjectServer::OnSaveViewState

Remplacez cette fonction pour enregistrer des informations d’état supplémentaires sur votre vue DocObject.

```
virtual void OnSaveViewState(CArchive& ar);
```

### <a name="parameters"></a>Paramètres

*Ar*<br/>
Objet `CArchive` dont l’état de vue est sérialisé.

### <a name="remarks"></a>Notes

Votre état peut inclure des propriétés comme le type de vue, le facteur de zoom, l’insertion et le point de sélection, et ainsi de suite. Le conteneur appelle généralement cette fonction avant de désactiver la vue. L’état sauvé peut plus tard être restauré par [OnApplyViewState](#onapplyviewstate).

Vous pouvez `OnSaveViewState` utiliser pour stocker des informations persistantes spécifiques à l’état de votre vue. Si vous `OnSaveViewState` remplacez pour stocker des informations, vous voudrez passer outre `OnApplyViewState` pour lire ces informations et les appliquer à votre vue lorsqu’elle est nouvellement activée.

## <a name="see-also"></a>Voir aussi

[CCmdTarget, classe](../../mfc/reference/ccmdtarget-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CDocObjectServerItem, classe](../../mfc/reference/cdocobjectserveritem-class.md)
