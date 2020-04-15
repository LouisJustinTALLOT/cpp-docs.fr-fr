---
title: CRichEditCntrItem, classe
ms.date: 11/04/2016
f1_keywords:
- CRichEditCntrItem
- AFXRICH/CRichEditCntrItem
- AFXRICH/CRichEditCntrItem::CRichEditCntrItem
- AFXRICH/CRichEditCntrItem::SyncToRichEditObject
helpviewer_keywords:
- CRichEditCntrItem [MFC], CRichEditCntrItem
- CRichEditCntrItem [MFC], SyncToRichEditObject
ms.assetid: 6c0b4efe-0fb8-4621-b5e1-fdcb8ec48c3b
ms.openlocfilehash: b8158105d09d5cfc7c25512567a98121b194a82a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368286"
---
# <a name="cricheditcntritem-class"></a>CRichEditCntrItem, classe

Avec [CRichEditView](../../mfc/reference/cricheditview-class.md) et [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md), fournit la fonctionnalité du contrôle d’édition riche dans le cadre de l’architecture de vue de document de MFC.

## <a name="syntax"></a>Syntaxe

```
class CRichEditCntrItem : public COleClientItem
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CRichEditCntrItem::CRichEditCntrItem](#cricheditcntritem)|Construit un objet `CRichEditCntrItem`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CRichEditCntrItem::SyncToRichEditObject](#synctoricheditobject)|Active l’élément comme un autre type.|

## <a name="remarks"></a>Notes

Un « contrôle d’édition riche » est une fenêtre dans laquelle l’utilisateur peut entrer et modifier le texte. Le texte peut être attribué formatage de caractère et de paragraphe, et peut inclure des objets OLE intégrés. Les contrôles d’édition riches fournissent une interface de programmation pour le formatage du texte. Toutefois, une application doit implémenter tous les composants d’interface utilisateur nécessaires pour mettre les opérations de formatage à la disposition de l’utilisateur.

`CRichEditView`conserve le texte et la caractéristique de formatage du texte. `CRichEditDoc`maintient la liste des éléments clients OLE qui sont dans la vue. `CRichEditCntrItem`offre un accès côté conteneur à l’article client OLE.

Ce contrôle Windows Common (et donc le [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) et les classes connexes) n’est disponible que pour les programmes fonctionnant sous Windows 95/98 et Windows NT versions 3.51 et plus tard.

Pour un exemple d’utilisation d’articles de conteneurs d’édition riches dans une application MFC, voir l’application d’échantillon [WORDPAD.](../../overview/visual-cpp-samples.md)

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocItem](../../mfc/reference/cdocitem-class.md)

[COleClientItem](../../mfc/reference/coleclientitem-class.md)

`CRichEditCntrItem`

## <a name="requirements"></a>Spécifications

**En-tête:** afxrich.h

## <a name="cricheditcntritemcricheditcntritem"></a><a name="cricheditcntritem"></a>CRichEditCntrItem::CRichEditCntrItem

Appelez cette fonction `CRichEditCntrItem` pour créer un objet et l’ajouter au document de conteneur.

```
CRichEditCntrItem(
    REOBJECT* preo = NULL,
    CRichEditDoc* pContainer = NULL);
```

### <a name="parameters"></a>Paramètres

*preo*<br/>
Pointeur vers une structure [REOBJECT](/windows/win32/api/richole/ns-richole-reobject) qui décrit un élément OLE. Le `CRichEditCntrItem` nouvel objet est construit autour de cet article OLE. Si *le preo* est NULL, l’article du client est vide.

*pContainer*<br/>
Pointeur vers le document de conteneur qui contiendra cet article. Si *pContainer* est NULL, vous devez appeler explicitement [COleDocument::AddItem](../../mfc/reference/coledocument-class.md#additem) pour ajouter cet article client à un document.

### <a name="remarks"></a>Notes

Cette fonction n’effectue aucune initialisation OLE.

Pour plus d’informations, voir la structure [REOBJECT](/windows/win32/api/richole/ns-richole-reobject) dans le SDK Windows.

## <a name="cricheditcntritemsynctoricheditobject"></a><a name="synctoricheditobject"></a>CRichEditCntrItem::SyncToRichEditObject

Appelez cette fonction pour synchroniser l’aspect de `CRichEditCntrltem` l’appareil, [DVASPECT](/windows/win32/api/wtypes/ne-wtypes-dvaspect), de cela à celui spécifié par *reo*.

```
void SyncToRichEditObject(REOBJECT& reo);
```

### <a name="parameters"></a>Paramètres

*Reo*<br/>
Référence à une structure [REOBJECT](/windows/win32/api/richole/ns-richole-reobject) qui décrit un élément OLE.

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [DVASPECT](/windows/win32/api/wtypes/ne-wtypes-dvaspect) dans windows SDK.

## <a name="see-also"></a>Voir aussi

[Échantillon MFC WORDPAD](../../overview/visual-cpp-samples.md)<br/>
[Classe COleClientItem](../../mfc/reference/coleclientitem-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CRichEditDoc, classe](../../mfc/reference/cricheditdoc-class.md)<br/>
[Classe CRichEditView](../../mfc/reference/cricheditview-class.md)
