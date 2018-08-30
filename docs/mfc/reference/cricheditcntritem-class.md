---
title: CRichEditCntrItem, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CRichEditCntrItem
- AFXRICH/CRichEditCntrItem
- AFXRICH/CRichEditCntrItem::CRichEditCntrItem
- AFXRICH/CRichEditCntrItem::SyncToRichEditObject
dev_langs:
- C++
helpviewer_keywords:
- CRichEditCntrItem [MFC], CRichEditCntrItem
- CRichEditCntrItem [MFC], SyncToRichEditObject
ms.assetid: 6c0b4efe-0fb8-4621-b5e1-fdcb8ec48c3b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 17f50f5e4fb8b9330a09d4964aa99fbf01f4b34d
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43206969"
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
  
 Pour obtenir un exemple d’utilisation des éléments de conteneur d’édition enrichi dans une application MFC, consultez le [WORDPAD](../../visual-cpp-samples.md) exemple d’application.  
  
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
 *preo*  
 Pointeur vers un [REOBJECT](/windows/desktop/api/richole/ns-richole-_reobject) structure qui décrit un élément OLE. La nouvelle `CRichEditCntrItem` objet est construit autour de cet élément OLE. Si *preo* est NULL, l’élément client est vide.  
  
 *pContainer*  
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
 *REO ne possèdent*  
 Référence à un [REOBJECT](/windows/desktop/api/richole/ns-richole-_reobject) structure qui décrit un élément OLE.  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations, consultez [DVASPECT](/windows/desktop/api/wtypes/ne-wtypes-tagdvaspect) dans le SDK Windows.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple MFC WORDPAD](../../visual-cpp-samples.md)   
 [COleClientItem, classe](../../mfc/reference/coleclientitem-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [CRichEditDoc (classe)](../../mfc/reference/cricheditdoc-class.md)   
 [CRichEditView, classe](../../mfc/reference/cricheditview-class.md)
