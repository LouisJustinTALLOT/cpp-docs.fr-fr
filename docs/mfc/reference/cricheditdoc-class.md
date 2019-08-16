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
ms.openlocfilehash: def0c55ff1faf12729226aa445c9614119c546c4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502678"
---
# <a name="cricheditdoc-class"></a>CRichEditDoc, classe

Avec [CRichEditView](../../mfc/reference/cricheditview-class.md) et [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md), fournit les fonctionnalités du contrôle RichEdit dans le contexte de l’architecture d’affichage de document MFC.

## <a name="syntax"></a>Syntaxe

```
class CRichEditDoc : public COleServerDoc
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CRichEditDoc::CreateClientItem](#createclientitem)|Appelée pour effectuer le nettoyage du document.|
|[CRichEditDoc::GetStreamFormat](#getstreamformat)|Indique si l’entrée et la sortie de flux doivent inclure des informations de mise en forme.|
|[CRichEditDoc::GetView](#getview)|Récupère l’objet [CRichEditView](../../mfc/reference/cricheditview-class.md) Asssociated.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CRichEditDoc::m_bRTF](#m_brtf)|Indique si les e/s de flux doivent inclure la mise en forme.|

## <a name="remarks"></a>Notes

Un «contrôle RichEdit» est une fenêtre dans laquelle l’utilisateur peut entrer et modifier du texte. Le texte peut être affecté à la mise en forme des caractères et des paragraphes, et peut inclure des objets OLE incorporés. Les contrôles RichEdit fournissent une interface de programmation pour mettre en forme le texte. Toutefois, une application doit implémenter tous les composants d’interface utilisateur nécessaires pour rendre les opérations de mise en forme disponibles pour l’utilisateur.

`CRichEditView`conserve le texte et les caractéristiques de mise en forme du texte. `CRichEditDoc`conserve la liste des éléments clients qui figurent dans la vue. `CRichEditCntrItem`fournit un accès côté conteneur aux éléments du client OLE.

Ce contrôle commun Windows (et par conséquent l' [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) et les classes associées) est uniquement disponible pour les programmes qui s’exécutent sous Windows 95/98 et Windows NT versions 3,51 et ultérieures.

Pour obtenir un exemple d’utilisation d’un document Rich Edit dans une application MFC, consultez l’exemple d’application [WordPad](../../overview/visual-cpp-samples.md) .

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocument](../../mfc/reference/cdocument-class.md)

[COleDocument](../../mfc/reference/coledocument-class.md)

[COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)

[COleServerDoc](../../mfc/reference/coleserverdoc-class.md)

`CRichEditDoc`

## <a name="requirements"></a>Configuration requise

**En-tête:** afxrich. h

##  <a name="createclientitem"></a>  CRichEditDoc::CreateClientItem

Appelez cette fonction pour créer un `CRichEditCntrItem` objet et l’ajouter à ce document.

```
virtual CRichEditCntrItem* CreateClientItem(REOBJECT* preo = NULL) const = 0;
```

### <a name="parameters"></a>Paramètres

*preo*<br/>
Pointeur vers une structure de [REOBJECT](/windows/win32/api/richole/ns-richole-reobject) qui décrit un élément OLE. Le nouvel `CRichEditCntrItem` objet est construit autour de cet élément OLE. Si *Preo* a la valeur null, le nouvel élément client est vide.

### <a name="return-value"></a>Valeur de retour

Pointeur vers un nouvel objet [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md) qui a été ajouté à ce document.

### <a name="remarks"></a>Notes

Cette fonction n’effectue aucune initialisation OLE.

Pour plus d’informations, consultez la structure de [REOBJECT](/windows/win32/api/richole/ns-richole-reobject) dans le SDK Windows.

##  <a name="getstreamformat"></a>  CRichEditDoc::GetStreamFormat

Appelez cette fonction pour déterminer le format de texte pour la diffusion en continu du contenu de la modification enrichie.

```
int GetStreamFormat() const;
```

### <a name="return-value"></a>Valeur de retour

Un des indicateurs suivants:

- SF_TEXT indique que le contrôle Rich Edit ne conserve pas les informations de mise en forme.

- SF_RTF indique que le contrôle Rich Edit conserve les informations de mise en forme.

### <a name="remarks"></a>Notes

La valeur de retour est basée sur le membre de données [m_bRTF](#m_brtf) . Cette fonction retourne SF_RTF si `m_bRTF` a la valeur true; sinon, SF_TEXT.

##  <a name="getview"></a>  CRichEditDoc::GetView

Appelez cette fonction pour accéder à l’objet [CRichEditView](../../mfc/reference/cricheditview-class.md) associé à `CRichEditDoc` cet objet.

```
virtual CRichEditView* GetView() const;
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers l' `CRichEditView` objet associé au document.

### <a name="remarks"></a>Notes

Le texte et les informations de mise en forme sont `CRichEditView` contenus dans l’objet. L' `CRichEditDoc` objet gère les éléments OLE pour la sérialisation. Il ne doit y avoir `CRichEditView` qu’un `CRichEditDoc`seul pour chaque.

##  <a name="m_brtf"></a>  CRichEditDoc::m_bRTF

Lorsque la valeur est TRUE, indique que [CRichEditCtrl:: Streamy](../../mfc/reference/cricheditctrl-class.md#streamin) et [CRichEditCtrl:: StreamOut](../../mfc/reference/cricheditctrl-class.md#streamout) doivent stocker les caractéristiques des paragraphes et de la mise en forme des caractères.

```
BOOL m_bRTF;
```

## <a name="see-also"></a>Voir aussi

[Exemple MFC WORDPAD](../../overview/visual-cpp-samples.md)<br/>
[COleServerDoc, classe](../../mfc/reference/coleserverdoc-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CRichEditView, classe](../../mfc/reference/cricheditview-class.md)<br/>
[CRichEditCntrItem, classe](../../mfc/reference/cricheditcntritem-class.md)<br/>
[COleDocument, classe](../../mfc/reference/coledocument-class.md)<br/>
[CRichEditCtrl, classe](../../mfc/reference/cricheditctrl-class.md)
