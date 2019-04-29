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
ms.openlocfilehash: 674937df9b4ecef0d159a47a45a716d1175ad5d9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62372112"
---
# <a name="cricheditcntritem-class"></a>CRichEditCntrItem, classe

Avec [CRichEditView](../../mfc/reference/cricheditview-class.md) et [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md), fournit les fonctionnalités du contrôle RichEdit dans le contexte de l’architecture document / vue de MFC.

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
|[CRichEditCntrItem::SyncToRichEditObject](#synctoricheditobject)|Active l’élément dans un autre type.|

## <a name="remarks"></a>Notes

Un « contrôle RichEdit » est une fenêtre dans laquelle l’utilisateur peut entrer et modifier du texte. Le texte peut avoir de caractère et de mise en forme de paragraphe et peut inclure des objets OLE incorporés. Les contrôles RichEdit fournissent une interface de programmation pour la mise en forme de texte. Toutefois, une application doit implémenter les composants d’interface utilisateur nécessaires pour rendre les opérations de mise en forme disponibles à l’utilisateur.

`CRichEditView` gère le texte et les caractéristiques de mise en forme du texte. `CRichEditDoc` gère la liste des éléments de client OLE qui se trouvent dans la vue. `CRichEditCntrItem` fournit l’accès côté conteneur à l’élément client OLE.

Ce contrôle commun de Windows (et par conséquent le [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) et les classes associées) est disponible uniquement pour les programmes s’exécutant sous Windows 95/98 et Windows NT versions 3.51 et ultérieures.

Pour obtenir un exemple d’utilisation des éléments de conteneur d’édition enrichi dans une application MFC, consultez le [WORDPAD](../../overview/visual-cpp-samples.md) exemple d’application.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocItem](../../mfc/reference/cdocitem-class.md)

[COleClientItem](../../mfc/reference/coleclientitem-class.md)

`CRichEditCntrItem`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxrich.h

##  <a name="cricheditcntritem"></a>  CRichEditCntrItem::CRichEditCntrItem

Appelez cette fonction pour créer un `CRichEditCntrItem` de l’objet et l’ajouter au document conteneur.

```
CRichEditCntrItem(
    REOBJECT* preo = NULL,
    CRichEditDoc* pContainer = NULL);
```

### <a name="parameters"></a>Paramètres

*preo*<br/>
Pointeur vers un [REOBJECT](/windows/desktop/api/richole/ns-richole-_reobject) structure qui décrit un élément OLE. La nouvelle `CRichEditCntrItem` objet est construit autour de cet élément OLE. Si *preo* est NULL, l’élément client est vide.

*pContainer*<br/>
Pointeur vers le document conteneur qui contiendra cet élément. Si *pContainer* est NULL, vous devez appeler explicitement [COleDocument::AddItem](../../mfc/reference/coledocument-class.md#additem) à ajouter cet élément de client à un document.

### <a name="remarks"></a>Notes

Cette fonction n’effectue pas de toute initialisation OLE.

Pour plus d’informations, consultez le [REOBJECT](/windows/desktop/api/richole/ns-richole-_reobject) structure dans le SDK Windows.

##  <a name="synctoricheditobject"></a>  CRichEditCntrItem::SyncToRichEditObject

Appelez cette fonction pour synchroniser l’aspect de l’appareil, [DVASPECT](/windows/desktop/api/wtypes/ne-wtypes-tagdvaspect), de ce `CRichEditCntrltem` à celle spécifiée par *REO ne possèdent*.

```
void SyncToRichEditObject(REOBJECT& reo);
```

### <a name="parameters"></a>Paramètres

*REO ne possèdent*<br/>
Référence à un [REOBJECT](/windows/desktop/api/richole/ns-richole-_reobject) structure qui décrit un élément OLE.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [DVASPECT](/windows/desktop/api/wtypes/ne-wtypes-tagdvaspect) dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[Exemple MFC WORDPAD](../../overview/visual-cpp-samples.md)<br/>
[COleClientItem, classe](../../mfc/reference/coleclientitem-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CRichEditDoc, classe](../../mfc/reference/cricheditdoc-class.md)<br/>
[CRichEditView, classe](../../mfc/reference/cricheditview-class.md)
