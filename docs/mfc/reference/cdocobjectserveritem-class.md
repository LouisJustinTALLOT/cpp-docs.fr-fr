---
title: CDocObjectServerItem, classe
ms.date: 09/12/2018
f1_keywords:
- CDocObjectServerItem
- AFXDOCOB/CDocObjectServerItem
- AFXDOCOB/CDocObjectServerItem::CDocObjectServerItem
- AFXDOCOB/CDocObjectServerItem::GetDocument
- AFXDOCOB/CDocObjectServerItem::OnHide
- AFXDOCOB/CDocObjectServerItem::OnShow
helpviewer_keywords:
- CDocObjectServerItem [MFC], CDocObjectServerItem
- CDocObjectServerItem [MFC], GetDocument
- CDocObjectServerItem [MFC], OnHide
- CDocObjectServerItem [MFC], OnShow
ms.assetid: 530f7156-50c8-4806-9328-602c9133f622
ms.openlocfilehash: cecbab366b64c85b39131a13233598abec83d5ab
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50536524"
---
# <a name="cdocobjectserveritem-class"></a>CDocObjectServerItem, classe

Implémente les verbes de serveur OLE , en particulier pour les serveurs DocObject.

## <a name="syntax"></a>Syntaxe

```
class CDocObjectServerItem : public COleServerItem
```

## <a name="members"></a>Membres

### <a name="protected-constructors"></a>Constructeurs protégés

|Nom|Description|
|----------|-----------------|
|[CDocObjectServerItem::CDocObjectServerItem](#cdocobjectserveritem)|Construit un objet `CDocObjectServerItem`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CDocObjectServerItem::GetDocument](#getdocument)|Récupère un pointeur vers le document qui contient l’élément.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CDocObjectServerItem::OnDoVerb](#ondoverb)|Lève une exception si le framework tente de masquer un élément DocObject.|
|[CDocObjectServerItem::OnHide](#onhide)|Lève une exception si le framework tente de masquer un élément DocObject.|
|[CDocObjectServerItem::OnShow](#onshow)|Appelé par l’infrastructure pour rendre le DocObject élément in situ active. Si l’élément n’est pas un DocObject, appelle [COleServerItem::OnShow](../../mfc/reference/coleserveritem-class.md#onshow).|

## <a name="remarks"></a>Notes

`CDocObjectServerItem` définit les fonctions membres substituables : [OnHide](#onhide), [OnDoVerb](#ondoverb), et [OnShow](#onshow).

Pour utiliser `CDocObjectServerItem`, s’assurer que le [OnGetEmbeddedItem](../../mfc/reference/coleserverdoc-class.md#ongetembeddeditem) remplacer dans votre `COleServerDoc`-classe dérivée retourne un nouvel `CDocObjectServerItem` objet. Si vous devez modifier toutes les fonctionnalités dans votre élément, vous pouvez créer une nouvelle instance de votre propre `CDocObjectServerItem`-classe dérivée.

Pour plus d’informations sur DocObjects, consultez [CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md) et [COleCmdUI](../../mfc/reference/colecmdui-class.md) dans le *référence MFC*.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocItem](../../mfc/reference/cdocitem-class.md)

[Classe dérivée COleServerItem](../../mfc/reference/coleserveritem-class.md)

`CDocObjectServerItem`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxdocob.h

##  <a name="cdocobjectserveritem"></a>  CDocObjectServerItem::CDocObjectServerItem

Construit un objet `CDocObjectServerItem`.

```
CDocObjectServerItem(COleServerDoc* pServerDoc, BOOL bAutoDelete);
```

### <a name="parameters"></a>Paramètres

*pServerDoc*<br/>
Pointeur vers le document qui contiendra le nouvel élément DocObject.

*bAutoDelete*<br/>
Indique si l’objet peut être supprimé lors de la publication d’un lien vers celle-ci. La valeur FALSE si l’argument le `CDocObjectServerItem` objet fait partie intégrante de données de votre document. Affectez-lui la valeur TRUE si l’objet est une structure secondaire utilisée pour identifier une plage dans les données de votre document qui peuvent être supprimées par l’infrastructure.

##  <a name="getdocument"></a>  CDocObjectServerItem::GetDocument

Récupère un pointeur vers le document qui contient l’élément.

```
COleServerDoc* GetDocument() const;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur vers le document qui contient l’élément ; NULL si l’élément ne fait pas partie d’un document.

### <a name="remarks"></a>Notes

Cela permet d’accéder au document serveur que vous avez passé en tant qu’argument à la [CDocObjectServerItem](#cdocobjectserveritem) constructeur.

##  <a name="onhide"></a>  CDocObjectServerItem::OnHide

Appelé par l’infrastructure pour masquer l’élément.

```
virtual void OnHide();
```

### <a name="remarks"></a>Notes

L’implémentation par défaut lève une exception si l’élément est un DocObject. Vous ne pouvez pas masquer un élément de DocObject actif car elle accepte la vue entière. Vous devez désactiver l’élément DocObject pour la faire disparaître. Si l’élément n’est pas un DocObject, l’implémentation par défaut appelle [COleServerItem::OnHide](../../mfc/reference/coleserveritem-class.md#onhide).

##  <a name="onshow"></a>  CDocObjectServerItem::OnShow

Appelé par l’infrastructure pour indiquer à l’application de serveur pour effectuer le DocObject élément in situ active.

```
virtual void OnShow();
```

### <a name="remarks"></a>Notes

Si l’élément n’est pas un DocObject, l’implémentation par défaut appelle [COleServerItem::OnShow](../../mfc/reference/coleserveritem-class.md#onopen). Remplacez cette fonction si vous souhaitez effectuer un traitement lors de l’ouverture d’un élément DocObject particulier.

## <a name="see-also"></a>Voir aussi

[COleServerItem, classe](../../mfc/reference/coleserveritem-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CDocObjectServer, classe](../../mfc/reference/cdocobjectserver-class.md)<br/>
[COleDocObjectItem, classe](../../mfc/reference/coledocobjectitem-class.md)
