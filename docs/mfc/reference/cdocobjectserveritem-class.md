---
title: CDocObjectServerItem, classe
ms.date: 03/27/2019
f1_keywords:
- CDocObjectServerItem
- AFXDOCOB/CDocObjectServerItem
- AFXDOCOB/CDocObjectServerItem::CDocObjectServerItem
- AFXDOCOB/CDocObjectServerItem::GetDocument
- AFXDOCOB/CDocObjectServerItem::OnDoVerb
- AFXDOCOB/CDocObjectServerItem::OnHide
- AFXDOCOB/CDocObjectServerItem::OnShow
helpviewer_keywords:
- CDocObjectServerItem [MFC], CDocObjectServerItem
- CDocObjectServerItem [MFC], GetDocument
- CDocObjectServerItem [MFC], OnDoVerb
- CDocObjectServerItem [MFC], OnHide
- CDocObjectServerItem [MFC], OnShow
ms.assetid: 530f7156-50c8-4806-9328-602c9133f622
ms.openlocfilehash: 1f0f5cf93aab35a17f7174b2beee0d1398564a3d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375525"
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
|[CDocObjectServerItem::GetDocument](#getdocument)|Récupère un pointeur sur le document qui contient l’élément.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CDocObjectServerItem::OnDoVerb](#ondoverb)|Appelé pour exécuter un verbe.|
|[CDocObjectServerItem::OnHide](#onhide)|Jetez une exception si le cadre tente de cacher un élément DocObject.|
|[CDocObjectServerItem::OnShow](#onshow)|Appelé par le cadre pour rendre l’élément DocObject actif. Si l’article n’est pas un DocObject, appelle [COleServerItem::OnShow](../../mfc/reference/coleserveritem-class.md#onshow).|

## <a name="remarks"></a>Notes

`CDocObjectServerItem`définit les fonctions des membres primordiales : [OnHide](#onhide), [OnDoVerb](#ondoverb), et [OnShow](#onshow).

Pour `CDocObjectServerItem`utiliser, assurez-vous que le remplacement [OnGetEmbeddedItem](../../mfc/reference/coleserverdoc-class.md#ongetembeddeditem) dans votre `COleServerDoc`classe dérivée renvoie un nouvel `CDocObjectServerItem` objet. Si vous avez besoin de modifier n’importe quelle fonctionnalité dans `CDocObjectServerItem`votre élément, vous pouvez créer une nouvelle instance de votre propre classe dérivée.

Pour plus d’informations sur DocObjects, voir [CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md) et [COleCmdUI](../../mfc/reference/colecmdui-class.md) dans la *référence MFC*.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocItem](../../mfc/reference/cdocitem-class.md)

[COleServerItem](../../mfc/reference/coleserveritem-class.md)

`CDocObjectServerItem`

## <a name="requirements"></a>Spécifications

**En-tête:** afxdocob.h

## <a name="cdocobjectserveritemcdocobjectserveritem"></a><a name="cdocobjectserveritem"></a>CDocObjectServerItem::CDocObjectServerItem

Construit un objet `CDocObjectServerItem`.

```
CDocObjectServerItem(COleServerDoc* pServerDoc, BOOL bAutoDelete);
```

### <a name="parameters"></a>Paramètres

*pServerDoc*<br/>
Un pointeur sur le document qui contiendra le nouvel élément DocObject.

*bAutoDelete*<br/>
Indique si l’objet peut être supprimé lorsqu’un lien vers lui est libéré. Définissez l’argument `CDocObjectServerItem` à FALSE si l’objet fait partie intégrante des données de votre document. Définissez-le à TRUE si l’objet est une structure secondaire utilisée pour identifier une plage dans les données de votre document qui peut être supprimée par le cadre.

## <a name="cdocobjectserveritemgetdocument"></a><a name="getdocument"></a>CDocObjectServerItem::GetDocument

Récupère un pointeur sur le document qui contient l’élément.

```
COleServerDoc* GetDocument() const;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur sur le document qui contient l’élément; NULL si l’élément ne fait pas partie d’un document.

### <a name="remarks"></a>Notes

Cela permet l’accès au document serveur que vous avez passé comme argument au constructeur [CDocObjectServerItem.](#cdocobjectserveritem)

## <a name="cdocobjectserveritemondoverb"></a><a name="ondoverb"></a>CDocObjectServerItem::OnDoVerb

Appelé par le cadre pour exécuter le verbe spécifié.

```
virtual void OnDoVerb(LONG iVerb);
```

### <a name="parameters"></a>Paramètres

*iVerb (en)*<br/>
Spécifie le verbe à exécuter. Pour les valeurs possibles, voir [IOleObject::DoVerb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb) dans le SDK Windows.

### <a name="remarks"></a>Notes

La implémentation par défaut appelle la fonction membre [OnShow](#onshow) si l’élément est un DocObject et que le OLEIVERB_INPLACEACTIVATE ou OLEIVERB_SHOW est spécifié. Si l’élément n’est pas un DocObject ou un verbe différent est spécifié, la implémentation par défaut appelle [COleServerItem::OnDoVerb](../../mfc/reference/coleserveritem-class.md#ondoverb).

## <a name="cdocobjectserveritemonhide"></a><a name="onhide"></a>CDocObjectServerItem::OnHide

Appelé par le cadre pour cacher l’élément.

```
virtual void OnHide();
```

### <a name="remarks"></a>Notes

L’implémentation par défaut jette une exception si l’élément est un DocObject. Vous ne pouvez pas cacher un élément DocObject actif parce qu’il prend toute la vue. Vous devez désactiver l’article DocObject pour le faire disparaître. Si l’élément n’est pas un DocObject, la implémentation par défaut appelle [COleServerItem::OnHide](../../mfc/reference/coleserveritem-class.md#onhide).

## <a name="cdocobjectserveritemonshow"></a><a name="onshow"></a>CDocObjectServerItem::OnShow

Appelé par le cadre pour instruire l’application serveur pour rendre l’élément DocObject actif.

```
virtual void OnShow();
```

### <a name="remarks"></a>Notes

Si l’élément n’est pas un DocObject, la implémentation par défaut appelle [COleServerItem::OnShow](../../mfc/reference/coleserveritem-class.md#onopen). Remplacez cette fonction si vous souhaitez effectuer un traitement spécial lors de l’ouverture d’un élément DocObject.

## <a name="see-also"></a>Voir aussi

[COleServerItem, classe](../../mfc/reference/coleserveritem-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CDocObjectServer, classe](../../mfc/reference/cdocobjectserver-class.md)<br/>
[Classe COleDocObjectItem](../../mfc/reference/coledocobjectitem-class.md)
