---
title: CRichEditDoc, classe
ms.date: 11/04/2016
f1_keywords:
- CRichEditDoc
- AFXRICH/CRichEditDoc
- AFXRICH/CRichEditDoc::CreateClientItem
- AFXRICH/CRichEditDoc::GetStreamFormat
- AFXRICH/CRichEditDoc::GetView
- AFXRICH/CRichEditDoc::m_bRTF
helpviewer_keywords:
- CRichEditDoc [MFC], CreateClientItem
- CRichEditDoc [MFC], GetStreamFormat
- CRichEditDoc [MFC], GetView
- CRichEditDoc [MFC], m_bRTF
ms.assetid: c936ec18-d516-49d4-b7fb-c9aa0229eddc
ms.openlocfilehash: 587cf65543e24e586fb8b2336481d6e841473134
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368260"
---
# <a name="cricheditdoc-class"></a>CRichEditDoc, classe

Avec [CRichEditView](../../mfc/reference/cricheditview-class.md) et [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md), fournit la fonctionnalité du contrôle d’édition riche dans le cadre de l’architecture de vue de document de MFC.

## <a name="syntax"></a>Syntaxe

```
class CRichEditDoc : public COleServerDoc
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CRichEditDoc::CreateClientItem](#createclientitem)|Appelé pour effectuer le nettoyage du document.|
|[CRichEditDoc::GetStreamFormat](#getstreamformat)|Indique si l’entrée et la sortie du flux devraient inclure l’information de formatage.|
|[CRichEditDoc::GetView](#getview)|Récupère l’objet [CRichEditView](../../mfc/reference/cricheditview-class.md) associé.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CRichEditDoc::m_bRTF](#m_brtf)|Indique si le flux I/O devrait inclure le formatage.|

## <a name="remarks"></a>Notes

Un « contrôle d’édition riche » est une fenêtre dans laquelle l’utilisateur peut entrer et modifier le texte. Le texte peut être attribué formatage de caractère et de paragraphe, et peut inclure des objets OLE intégrés. Les contrôles d’édition riches fournissent une interface de programmation pour le formatage du texte. Toutefois, une application doit implémenter tous les composants d’interface utilisateur nécessaires pour mettre les opérations de formatage à la disposition de l’utilisateur.

`CRichEditView`conserve le texte et la caractéristique de formatage du texte. `CRichEditDoc`maintient la liste des éléments clients qui sont dans la vue. `CRichEditCntrItem`offre un accès côté conteneur aux articles des clients OLE.

Ce contrôle Windows Common (et donc le [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) et les classes connexes) n’est disponible que pour les programmes fonctionnant sous Windows 95/98 et Windows NT versions 3.51 et plus tard.

Pour l’utilisation d’un document de modification riche dans une application MFC, consultez l’application [d’échantillon WORDPAD.](../../overview/visual-cpp-samples.md)

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocument](../../mfc/reference/cdocument-class.md)

[COleDocument](../../mfc/reference/coledocument-class.md)

[COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)

[COleServerDoc](../../mfc/reference/coleserverdoc-class.md)

`CRichEditDoc`

## <a name="requirements"></a>Spécifications

**En-tête:** afxrich.h

## <a name="cricheditdoccreateclientitem"></a><a name="createclientitem"></a>CRichEditDoc::CreateClientItem

Appelez cette fonction `CRichEditCntrItem` pour créer un objet et l’ajouter à ce document.

```
virtual CRichEditCntrItem* CreateClientItem(REOBJECT* preo = NULL) const = 0;
```

### <a name="parameters"></a>Paramètres

*preo*<br/>
Pointeur vers une structure [REOBJECT](/windows/win32/api/richole/ns-richole-reobject) qui décrit un élément OLE. Le `CRichEditCntrItem` nouvel objet est construit autour de cet article OLE. Si *preo* est NULL, le nouvel article client est vide.

### <a name="return-value"></a>Valeur de retour

Pointeur vers un nouvel objet [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md) qui a été ajouté à ce document.

### <a name="remarks"></a>Notes

Cette fonction n’effectue aucune initialisation OLE.

Pour plus d’informations, voir la structure [REOBJECT](/windows/win32/api/richole/ns-richole-reobject) dans le SDK Windows.

## <a name="cricheditdocgetstreamformat"></a><a name="getstreamformat"></a>CRichEditDoc::GetStreamFormat

Appelez cette fonction pour déterminer le format de texte pour la diffusion en continu du contenu de la modification riche.

```
int GetStreamFormat() const;
```

### <a name="return-value"></a>Valeur de retour

Un des drapeaux suivants:

- SF_TEXT indique que le contrôle de modification riche ne maintient pas l’information de formatage.

- SF_RTF indique que le contrôle d’édition riche maintient l’information de formatage.

### <a name="remarks"></a>Notes

La valeur de rendement est basée sur le [m_bRTF](#m_brtf) membre des données. Cette fonction renvoie SF_RTF `m_bRTF` si elle est VRAI; autrement, SF_TEXT.

## <a name="cricheditdocgetview"></a><a name="getview"></a>CRichEditDoc::GetView

Appelez cette fonction pour accéder à l’objet `CRichEditDoc` [CRichEditView](../../mfc/reference/cricheditview-class.md) associé à cet objet.

```
virtual CRichEditView* GetView() const;
```

### <a name="return-value"></a>Valeur de retour

Pointeur `CRichEditView` vers l’objet associé au document.

### <a name="remarks"></a>Notes

Les informations de texte et `CRichEditView` de formatage sont contenues dans l’objet. L’objet `CRichEditDoc` maintient les éléments OLE pour la sérialisation. Il ne devrait `CRichEditView` y `CRichEditDoc`en avoir qu’un pour chacun .

## <a name="cricheditdocm_brtf"></a><a name="m_brtf"></a>CRichEditDoc::m_bRTF

Lorsque VRAI, indique que [CRichEditCtrl::StreamIn](../../mfc/reference/cricheditctrl-class.md#streamin) et [CRichEditCtrl::StreamOut](../../mfc/reference/cricheditctrl-class.md#streamout) devrait stocker des caractéristiques de paragraphe et de formatage de caractère.

```
BOOL m_bRTF;
```

## <a name="see-also"></a>Voir aussi

[Échantillon MFC WORDPAD](../../overview/visual-cpp-samples.md)<br/>
[COleServerDoc, classe](../../mfc/reference/coleserverdoc-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classe CRichEditView](../../mfc/reference/cricheditview-class.md)<br/>
[CRichEditCntrItem, classe](../../mfc/reference/cricheditcntritem-class.md)<br/>
[COleDocument, classe](../../mfc/reference/coledocument-class.md)<br/>
[Classe CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md)
