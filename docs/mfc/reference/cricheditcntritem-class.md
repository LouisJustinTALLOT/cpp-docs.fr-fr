---
description: 'En savoir plus sur : classe CRichEditCntrItem'
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
ms.openlocfilehash: 9e65e70a3fb03b65ebf9af7a619a5c4fbd3dba32
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97342958"
---
# <a name="cricheditcntritem-class"></a>CRichEditCntrItem, classe

Avec [CRichEditView](../../mfc/reference/cricheditview-class.md) et [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md), fournit les fonctionnalités du contrôle RichEdit dans le contexte de l’architecture d’affichage de document MFC.

## <a name="syntax"></a>Syntaxe

```
class CRichEditCntrItem : public COleClientItem
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CRichEditCntrItem :: CRichEditCntrItem](#cricheditcntritem)|Construit un objet `CRichEditCntrItem`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CRichEditCntrItem :: SyncToRichEditObject](#synctoricheditobject)|Active l’élément comme un autre type.|

## <a name="remarks"></a>Notes

Un « contrôle RichEdit » est une fenêtre dans laquelle l’utilisateur peut entrer et modifier du texte. Le texte peut être affecté à la mise en forme des caractères et des paragraphes, et peut inclure des objets OLE incorporés. Les contrôles RichEdit fournissent une interface de programmation pour mettre en forme le texte. Toutefois, une application doit implémenter tous les composants d’interface utilisateur nécessaires pour rendre les opérations de mise en forme disponibles pour l’utilisateur.

`CRichEditView` conserve le texte et les caractéristiques de mise en forme du texte. `CRichEditDoc` conserve la liste des éléments du client OLE qui sont dans la vue. `CRichEditCntrItem` fournit un accès côté conteneur à l’élément client OLE.

Ce contrôle commun Windows (et par conséquent l' [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) et les classes associées) est uniquement disponible pour les programmes qui s’exécutent sous Windows 95/98 et Windows NT versions 3,51 et ultérieures.

Pour obtenir un exemple d’utilisation d’éléments de conteneur RichEdit dans une application MFC, consultez l’exemple d’application [WordPad](../../overview/visual-cpp-samples.md) .

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocItem](../../mfc/reference/cdocitem-class.md)

[COleClientItem](../../mfc/reference/coleclientitem-class.md)

`CRichEditCntrItem`

## <a name="requirements"></a>Spécifications

**En-tête :** afxrich. h

## <a name="cricheditcntritemcricheditcntritem"></a><a name="cricheditcntritem"></a> CRichEditCntrItem :: CRichEditCntrItem

Appelez cette fonction pour créer un `CRichEditCntrItem` objet et l’ajouter au document conteneur.

```
CRichEditCntrItem(
    REOBJECT* preo = NULL,
    CRichEditDoc* pContainer = NULL);
```

### <a name="parameters"></a>Paramètres

*preo*<br/>
Pointeur vers une structure de [réobjet](/windows/win32/api/richole/ns-richole-reobject) qui décrit un élément OLE. Le nouvel `CRichEditCntrItem` objet est construit autour de cet élément OLE. Si *Preo* a la valeur null, l’élément client est vide.

*pContainer*<br/>
Pointeur vers le document conteneur qui contiendra cet élément. Si *pContainer peut avoir* a la valeur null, vous devez appeler de manière explicite [COleDocument :: AddItem](../../mfc/reference/coledocument-class.md#additem) pour ajouter cet élément client à un document.

### <a name="remarks"></a>Notes

Cette fonction n’effectue aucune initialisation OLE.

Pour plus d’informations, consultez la structure de [réobjet](/windows/win32/api/richole/ns-richole-reobject) dans le SDK Windows.

## <a name="cricheditcntritemsynctoricheditobject"></a><a name="synctoricheditobject"></a> CRichEditCntrItem :: SyncToRichEditObject

Appelez cette fonction pour synchroniser l’aspect de l’appareil, [DVASPECT](/windows/win32/api/wtypes/ne-wtypes-dvaspect), de ce `CRichEditCntrltem` à celui spécifié par *REO*.

```cpp
void SyncToRichEditObject(REOBJECT& reo);
```

### <a name="parameters"></a>Paramètres

*reo*<br/>
Référence à une structure de [réobjet](/windows/win32/api/richole/ns-richole-reobject) qui décrit un élément OLE.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [DVASPECT](/windows/win32/api/wtypes/ne-wtypes-dvaspect) dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[Exemple MFC WORDPAD](../../overview/visual-cpp-samples.md)<br/>
[COleClientItem (classe)](../../mfc/reference/coleclientitem-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CRichEditDoc, classe](../../mfc/reference/cricheditdoc-class.md)<br/>
[CRichEditView (classe)](../../mfc/reference/cricheditview-class.md)
