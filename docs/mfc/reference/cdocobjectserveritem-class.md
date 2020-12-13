---
description: 'En savoir plus sur : classe CDocObjectServerItem'
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
ms.openlocfilehash: a2d0d924433d812ec5f283d67e8313d20203ca3e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97184918"
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
|[CDocObjectServerItem :: CDocObjectServerItem](#cdocobjectserveritem)|Construit un objet `CDocObjectServerItem`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CDocObjectServerItem :: GetDocument](#getdocument)|Récupère un pointeur vers le document qui contient l’élément.|

### <a name="protected-methods"></a>Méthodes protégées

|Nom|Description|
|----------|-----------------|
|[CDocObjectServerItem :: OnDoVerb](#ondoverb)|Appelé pour exécuter un verbe.|
|[CDocObjectServerItem :: OnHide](#onhide)|Lève une exception si le Framework tente de masquer un élément DocObject.|
|[CDocObjectServerItem :: OnShow](#onshow)|Appelé par le Framework pour rendre l’élément DocObject actif sur place. Si l’élément n’est pas un DocObject, appelle [COleServerItem :: onshow](../../mfc/reference/coleserveritem-class.md#onshow).|

## <a name="remarks"></a>Notes

`CDocObjectServerItem` définit des fonctions membres substituables : [OnHide](#onhide), [OnDoVerb](#ondoverb)et [onshow](#onshow).

Pour utiliser `CDocObjectServerItem` , assurez-vous que la substitution [OnGetEmbeddedItem](../../mfc/reference/coleserverdoc-class.md#ongetembeddeditem) dans votre `COleServerDoc` classe dérivée de retourne un nouvel `CDocObjectServerItem` objet. Si vous avez besoin de modifier des fonctionnalités dans votre élément, vous pouvez créer une nouvelle instance de votre propre `CDocObjectServerItem` classe dérivée de.

Pour plus d’informations sur DocObjects, consultez [CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md) et [COleCmdUI](../../mfc/reference/colecmdui-class.md) dans la *référence MFC*.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocItem](../../mfc/reference/cdocitem-class.md)

[COleServerItem](../../mfc/reference/coleserveritem-class.md)

`CDocObjectServerItem`

## <a name="requirements"></a>Spécifications

**En-tête :** AfxDocOb. h

## <a name="cdocobjectserveritemcdocobjectserveritem"></a><a name="cdocobjectserveritem"></a> CDocObjectServerItem :: CDocObjectServerItem

Construit un objet `CDocObjectServerItem`.

```
CDocObjectServerItem(COleServerDoc* pServerDoc, BOOL bAutoDelete);
```

### <a name="parameters"></a>Paramètres

*pServerDoc*<br/>
Pointeur vers le document qui contiendra le nouvel élément DocObject.

*bAutoDelete*<br/>
Indique si l’objet peut être supprimé lorsqu’un lien vers celui-ci est libéré. Affectez à l’argument la valeur FALSe si l' `CDocObjectServerItem` objet fait partie intégrante des données de votre document. Affectez-lui la valeur TRUE si l’objet est une structure secondaire utilisée pour identifier une plage dans les données de votre document qui peut être supprimée par l’infrastructure.

## <a name="cdocobjectserveritemgetdocument"></a><a name="getdocument"></a> CDocObjectServerItem :: GetDocument

Récupère un pointeur vers le document qui contient l’élément.

```
COleServerDoc* GetDocument() const;
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers le document qui contient l’élément ; NULL si l’élément ne fait pas partie d’un document.

### <a name="remarks"></a>Notes

Cela permet d’accéder au document de serveur que vous avez passé comme argument au constructeur [CDocObjectServerItem](#cdocobjectserveritem) .

## <a name="cdocobjectserveritemondoverb"></a><a name="ondoverb"></a> CDocObjectServerItem :: OnDoVerb

Appelé par le Framework pour exécuter le verbe spécifié.

```
virtual void OnDoVerb(LONG iVerb);
```

### <a name="parameters"></a>Paramètres

*iVerb*<br/>
Spécifie le verbe à exécuter. Pour connaître les valeurs possibles, consultez [IOleObject ::D overb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb) dans le SDK Windows.

### <a name="remarks"></a>Notes

L’implémentation par défaut appelle la fonction membre [onshow](#onshow) si l’élément est un DocObject et que le OLEIVERB_INPLACEACTIVATE ou OLEIVERB_SHOW est spécifié. Si l’élément n’est pas un DocObject ou si un verbe différent est spécifié, l’implémentation par défaut appelle [COleServerItem :: OnDoVerb](../../mfc/reference/coleserveritem-class.md#ondoverb).

## <a name="cdocobjectserveritemonhide"></a><a name="onhide"></a> CDocObjectServerItem :: OnHide

Appelé par l’infrastructure pour masquer l’élément.

```
virtual void OnHide();
```

### <a name="remarks"></a>Notes

L’implémentation par défaut lève une exception si l’élément est un DocObject. Vous ne pouvez pas masquer un élément DocObject actif, car il prend la vue entière. Vous devez désactiver l’élément DocObject pour qu’il disparaisse. Si l’élément n’est pas un DocObject, l’implémentation par défaut appelle [COleServerItem :: OnHide](../../mfc/reference/coleserveritem-class.md#onhide).

## <a name="cdocobjectserveritemonshow"></a><a name="onshow"></a> CDocObjectServerItem :: OnShow

Appelée par l’infrastructure pour indiquer à l’application serveur de rendre l’élément de DocObject actif sur place.

```
virtual void OnShow();
```

### <a name="remarks"></a>Notes

Si l’élément n’est pas un DocObject, l’implémentation par défaut appelle [COleServerItem :: onshow](../../mfc/reference/coleserveritem-class.md#onopen). Remplacez cette fonction si vous souhaitez effectuer un traitement spécial lors de l’ouverture d’un élément DocObject.

## <a name="see-also"></a>Voir aussi

[COleServerItem, classe](../../mfc/reference/coleserveritem-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CDocObjectServer, classe](../../mfc/reference/cdocobjectserver-class.md)<br/>
[COleDocObjectItem, classe](../../mfc/reference/coledocobjectitem-class.md)
