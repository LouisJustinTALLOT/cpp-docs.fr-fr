---
description: 'En savoir plus sur : classe CDocItem'
title: CDocItem, classe
ms.date: 11/04/2016
f1_keywords:
- CDocItem
- AFXOLE/CDocItem
- AFXOLE/CDocItem::GetDocument
- AFXOLE/CDocItem::IsBlank
helpviewer_keywords:
- CDocItem [MFC], GetDocument
- CDocItem [MFC], IsBlank
ms.assetid: 84fb8610-a4c8-4211-adc0-e70e8d002c11
ms.openlocfilehash: 9e126d4351248165a3961739c13cc6ce7330c10c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97185139"
---
# <a name="cdocitem-class"></a>CDocItem, classe

Classe de base des éléments de document, qui sont les composants des données d'un document.

## <a name="syntax"></a>Syntaxe

```
class CDocItem : public CCmdTarget
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CDocItem :: GetDocument](#getdocument)|Retourne le document qui contient l’élément.|
|[CDocItem :: IsBlank](#isblank)|Détermine si l’élément contient des informations.|

## <a name="remarks"></a>Notes

`CDocItem` les objets sont utilisés pour représenter des éléments OLE dans les documents client et serveur.

Pour plus d’informations, consultez l’article [conteneurs : implémentation d’un conteneur](../../mfc/containers-implementing-a-container.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDocItem`

## <a name="requirements"></a>Spécifications

**En-tête :** AFXOLE. h

## <a name="cdocitemgetdocument"></a><a name="getdocument"></a> CDocItem :: GetDocument

Appelez cette fonction pour récupérer le document qui contient l’élément.

```
CDocument* GetDocument() const;
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers le document qui contient l’élément ; NULL, si l’élément ne fait pas partie d’un document.

### <a name="remarks"></a>Notes

Cette fonction est substituée dans les classes dérivées [COleClientItem](../../mfc/reference/coleclientitem-class.md) et [COleServerItem](../../mfc/reference/coleserveritem-class.md), en retournant un pointeur vers un objet [COleDocument](../../mfc/reference/coledocument-class.md), [COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)ou [COleServerDoc](../../mfc/reference/coleserverdoc-class.md) .

## <a name="cdocitemisblank"></a><a name="isblank"></a> CDocItem :: IsBlank

Appelé par l’infrastructure lorsque la sérialisation par défaut se produit.

```
virtual BOOL IsBlank() const;
```

### <a name="return-value"></a>Valeur renvoyée

Différent de zéro si l’élément ne contient aucune information ; Sinon, 0.

### <a name="remarks"></a>Notes

Par défaut, `CDocItem` les objets ne sont pas vides. Les objets [COleClientItem](../../mfc/reference/coleclientitem-class.md) sont parfois vides, car ils dérivent directement de `CDocItem` . Toutefois, les objets [COleServerItem](../../mfc/reference/coleserveritem-class.md) sont toujours vides. Par défaut, les applications OLE qui contiennent des `COleClientItem` objets qui n’ont pas d’étendue x ou y sont sérialisées. Pour ce faire, retournez la valeur TRUE à partir d’une substitution de `IsBlank` lorsque l’élément n’a pas d’étendue x ou y.

Substituez cette fonction si vous souhaitez implémenter d’autres actions au cours de la sérialisation.

## <a name="see-also"></a>Voir aussi

[CCmdTarget, classe](../../mfc/reference/ccmdtarget-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[COleDocument, classe](../../mfc/reference/coledocument-class.md)<br/>
[COleServerItem, classe](../../mfc/reference/coleserveritem-class.md)<br/>
[COleClientItem (classe)](../../mfc/reference/coleclientitem-class.md)
