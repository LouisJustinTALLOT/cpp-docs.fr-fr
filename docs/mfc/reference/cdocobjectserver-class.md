---
description: 'En savoir plus sur : classe CDocObjectServer'
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
ms.openlocfilehash: 5a87363fef66a4819fc8efd504da96398cf3c89e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97184944"
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
|[CDocObjectServer :: CDocObjectServer](#cdocobjectserver)|Construit un objet `CDocObjectServer`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CDocObjectServer :: ActivateDocObject](#activatedocobject)|Active le serveur d’objets de document, mais ne l’affiche pas.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CDocObjectServer :: OnActivateView](#onactivateview)|Affiche la vue DocObject.|
|[CDocObjectServer :: OnApplyViewState](#onapplyviewstate)|Restaure l’état de la vue DocObject.|
|[CDocObjectServer :: OnSaveViewState](#onsaveviewstate)|Enregistre l’état de la vue DocObject.|

## <a name="remarks"></a>Notes

`CDocObjectServer` est dérivée de `CCmdTarget` et fonctionne en étroite collaboration avec `COleServerDoc` pour exposer les interfaces.

Un document de serveur DocObject peut contenir des objets [CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md) , qui représentent l’interface de serveur à DocObject éléments.

Pour personnaliser votre serveur DocObject, dérivez votre propre classe de `CDocObjectServer` et remplacez ses fonctions de configuration d’affichage, [OnActivateView](#onactivateview), [OnApplyViewState](#onapplyviewstate)et [OnSaveViewState](#onsaveviewstate). Vous devrez fournir une nouvelle instance de votre classe en réponse aux appels de l’infrastructure.

Pour plus d’informations sur DocObjects, consultez [CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md) et [COleCmdUI](../../mfc/reference/colecmdui-class.md) dans la *référence MFC*.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDocObjectServer`

## <a name="requirements"></a>Spécifications

**En-tête :** AfxDocOb. h

## <a name="cdocobjectserveractivatedocobject"></a><a name="activatedocobject"></a> CDocObjectServer :: ActivateDocObject

Appelez cette fonction pour activer (mais pas afficher) le serveur d’objets de document.

```cpp
void ActivateDocObject();
```

### <a name="remarks"></a>Notes

`ActivateDocObject` appelle `IOleDocumentSite` `ActivateMe` la méthode, mais n’affiche pas la vue, car elle attend des instructions spécifiques sur la manière de configurer et d’afficher la vue, dans l’appel à [CDocObjectServer :: OnActivateView](#onactivateview).

Ensemble, `ActivateDocObject` et `OnActivateView` activent et affichent la vue DocObject. L’activation DocObject diffère des autres types d’activations OLE sur place. L’activation de DocObject ignore l’affichage des bordures de hachurage sur place et des ornements d’objets (tels que les poignées de redimensionnement), ignore les fonctions d’extension d’objet et dessine des barres de défilement dans le rectangle d’affichage au lieu de les dessiner en dehors de ce rectangle (comme dans l’activation sur place normale).

## <a name="cdocobjectservercdocobjectserver"></a><a name="cdocobjectserver"></a> CDocObjectServer :: CDocObjectServer

Construit et initialise un objet `CDocObjectServer`.

```
explicit CDocObjectServer(
    COleServerDoc* pOwner,
    LPOLEDOCUMENTSITE pDocSite = NULL);
```

### <a name="parameters"></a>Paramètres

*pOwner*<br/>
Pointeur vers le document de site client qui est le client pour le serveur DocObject.

*pDocSite*<br/>
Pointeur vers l' `IOleDocumentSite` interface implémentée par le conteneur.

### <a name="remarks"></a>Notes

Lorsqu’un DocObject est actif, l’interface OLE du site client ( `IOleDocumentSite` ) permet au serveur DocObject de communiquer avec son client (le conteneur). Lorsqu’un serveur DocObject est activé, il vérifie d’abord que le conteneur implémente l' `IOleDocumentSite` interface. Si c’est le cas, [COleServerDoc :: GetDocObjectServer](../../mfc/reference/coleserverdoc-class.md#getdocobjectserver) est appelé pour voir si le conteneur prend en charge DocObjects. Par défaut, `GetDocObjectServer` retourne la valeur null. Vous devez substituer `COleServerDoc::GetDocObjectServer` pour construire un nouvel `CDocObjectServer` objet ou un objet dérivé de votre choix, avec des pointeurs vers le `COleServerDoc` conteneur et son `IOleDocumentSite` interface comme arguments pour le constructeur.

## <a name="cdocobjectserveronactivateview"></a><a name="onactivateview"></a> CDocObjectServer :: OnActivateView

Appelez cette fonction pour afficher la vue DocObject.

```
virtual HRESULT OnActivateView();
```

### <a name="return-value"></a>Valeur renvoyée

Retourne une valeur d’erreur ou d’avertissement. Par défaut, retourne noerreur en cas de réussite ; Sinon, E_FAIL.

### <a name="remarks"></a>Notes

Cette fonction crée une fenêtre frame sur place, dessine des barres de défilement dans la vue, configure les menus que le serveur partage avec son conteneur, ajoute des contrôles Frame, définit l’objet actif, puis affiche la fenêtre frame sur place et définit le focus.

## <a name="cdocobjectserveronapplyviewstate"></a><a name="onapplyviewstate"></a> CDocObjectServer :: OnApplyViewState

Remplacez cette fonction pour restaurer l’état de la vue DocObject.

```
virtual void OnApplyViewState(CArchive& ar);
```

### <a name="parameters"></a>Paramètres

*ar*<br/>
`CArchive`Objet à partir duquel sérialiser l’état d’affichage.

### <a name="remarks"></a>Notes

Cette fonction est appelée lorsque la vue est affichée pour la première fois après son instanciation. `OnApplyViewState` demande à une vue de se réinitialiser lui-même en fonction des données de l' `CArchive` objet précédemment enregistré avec [OnSaveViewState](#onsaveviewstate). La vue doit valider les données dans l' `CArchive` objet, car le conteneur n’essaie pas d’interpréter les données d’état d’affichage de quelque manière que ce soit.

Vous pouvez utiliser `OnSaveViewState` pour stocker des informations persistantes spécifiques à l’état de votre vue. Si vous substituez `OnSaveViewState` pour stocker des informations, vous souhaiterez peut-être remplacer `OnApplyViewState` pour lire ces informations et les appliquer à votre vue lorsqu’il vient d’être activé.

## <a name="cdocobjectserveronsaveviewstate"></a><a name="onsaveviewstate"></a> CDocObjectServer :: OnSaveViewState

Remplacez cette fonction pour enregistrer des informations d’État supplémentaires sur votre vue DocObject.

```
virtual void OnSaveViewState(CArchive& ar);
```

### <a name="parameters"></a>Paramètres

*ar*<br/>
`CArchive`Objet dans lequel l’état d’affichage est sérialisé.

### <a name="remarks"></a>Notes

Votre état peut inclure des propriétés telles que le type de vue, le facteur de zoom, le point d’insertion et de sélection, et ainsi de suite. Le conteneur appelle généralement cette fonction avant de désactiver la vue. L’état enregistré peut être restauré par la suite par le biais de [OnApplyViewState](#onapplyviewstate).

Vous pouvez utiliser `OnSaveViewState` pour stocker des informations persistantes spécifiques à l’état de votre vue. Si vous substituez `OnSaveViewState` pour stocker des informations, vous souhaiterez peut-être remplacer `OnApplyViewState` pour lire ces informations et les appliquer à votre vue lorsqu’il vient d’être activé.

## <a name="see-also"></a>Voir aussi

[CCmdTarget, classe](../../mfc/reference/ccmdtarget-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CDocObjectServerItem, classe](../../mfc/reference/cdocobjectserveritem-class.md)
