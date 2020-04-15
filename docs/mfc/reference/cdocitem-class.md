---
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
ms.openlocfilehash: 438bc2a03239946dbfca53d5f2989c731b682ab0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375620"
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
|[CDocItem::GetDocument](#getdocument)|Retourne le document qui contient l’élément.|
|[CDocItem::IsBlank](#isblank)|Détermine si l’élément contient des informations.|

## <a name="remarks"></a>Notes

`CDocItem`les objets sont utilisés pour représenter les éléments OLE dans les documents clients et serveur.

Pour plus d’informations, voir l’article [Containers: Implementing a Container](../../mfc/containers-implementing-a-container.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDocItem`

## <a name="requirements"></a>Spécifications

**En-tête:** afxole.h

## <a name="cdocitemgetdocument"></a><a name="getdocument"></a>CDocItem::GetDocument

Appelez cette fonction pour obtenir le document qui contient l’élément.

```
CDocument* GetDocument() const;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur sur le document qui contient l’élément; NULL, si l’article ne fait pas partie d’un document.

### <a name="remarks"></a>Notes

Cette fonction est remplacée dans les classes dérivées [COleClientItem](../../mfc/reference/coleclientitem-class.md) et [COleServerItem](../../mfc/reference/coleserveritem-class.md), retournant un pointeur à soit un [COleDocument](../../mfc/reference/coledocument-class.md), un [COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md), ou un objet [COleServerDoc.](../../mfc/reference/coleserverdoc-class.md)

## <a name="cdocitemisblank"></a><a name="isblank"></a>CDocItem::IsBlank

Appelé par le cadre lorsque la sérialisation par défaut se produit.

```
virtual BOOL IsBlank() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si l’élément ne contient aucune information; sinon 0.

### <a name="remarks"></a>Notes

Par défaut, les `CDocItem` objets ne sont pas vides. Les objets [COleClientItem](../../mfc/reference/coleclientitem-class.md) sont parfois `CDocItem`vides parce qu’ils dérivent directement de . Cependant, les objets [COleServerItem](../../mfc/reference/coleserveritem-class.md) sont toujours vides. Par défaut, les `COleClientItem` applications OLE contenant des objets qui n’ont pas d’étendue x ou y sont sérialisées. Ceci est fait en retournant `IsBlank` TRUE d’un remplacement de quand l’élément n’a pas d’étendue x ou y.

Remplacez cette fonction si vous souhaitez implémenter d’autres actions lors de la sérialisation.

## <a name="see-also"></a>Voir aussi

[CCmdTarget, classe](../../mfc/reference/ccmdtarget-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[COleDocument, classe](../../mfc/reference/coledocument-class.md)<br/>
[COleServerItem, classe](../../mfc/reference/coleserveritem-class.md)<br/>
[Classe COleClientItem](../../mfc/reference/coleclientitem-class.md)
