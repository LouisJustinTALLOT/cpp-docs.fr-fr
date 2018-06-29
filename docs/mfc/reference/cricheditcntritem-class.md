---
title: Classe de CRichEditCntrItem | Documents Microsoft
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
ms.openlocfilehash: b0b4c038389810fcc6a847cdbf7837568b3007b6
ms.sourcegitcommit: be0e3457f2884551f18e183ef0ea65c3ded7f689
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37078606"
---
# <a name="cricheditcntritem-class"></a>Classe de CRichEditCntrItem
Avec [CRichEditView](../../mfc/reference/cricheditview-class.md) et [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md), fournit les fonctionnalités du contrôle RichEdit dans le contexte du document architecture vue de MFC.  
  
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
 Un « contrôle RichEdit » est une fenêtre dans laquelle l’utilisateur peut entrer et modifier du texte. Le texte de caractère et de mise en forme peut être alloué et peut inclure des objets OLE incorporés. Les contrôles RichEdit fournissent une interface de programmation pour la mise en forme de texte. Toutefois, une application doit implémenter tous les composants d’interface utilisateur nécessaires pour effectuer les opérations de mise en forme disponibles à l’utilisateur.  
  
 `CRichEditView` conserve le texte et les caractéristiques de mise en forme du texte. `CRichEditDoc` gère la liste des éléments de client OLE qui se trouvent dans la vue. `CRichEditCntrItem` fournit l’accès côté conteneur à l’élément client OLE.  
  
 Ce contrôle commun de Windows (et par conséquent la [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) et des classes connexes) est disponible uniquement pour les programmes s’exécutant sous Windows 95/98 et Windows NT versions 3.51 et ultérieures.  
  
 Pour obtenir un exemple d’utilisation des éléments de conteneur RichEdit dans une application MFC, consultez le [WORDPAD](../../visual-cpp-samples.md) exemple d’application.  
  
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
 Pointeur vers un [REOBJECT](http://msdn.microsoft.com/library/windows/desktop/bb787946) structure qui décrit un élément OLE. La nouvelle `CRichEditCntrItem` objet est construit autour de cet élément OLE. Si *preo* est **NULL**, l’élément client est vide.  
  
 *pContainer*  
 Pointeur vers le document conteneur qui contiendra cet élément. Si *pContainer* est **NULL**, vous devez appeler explicitement [COleDocument::AddItem](../../mfc/reference/coledocument-class.md#additem) pour ajouter cet élément client à un document.  
  
### <a name="remarks"></a>Notes  
 Cette fonction n’effectue pas de toute initialisation d’OLE.  
  
 Pour plus d’informations, consultez la [REOBJECT](http://msdn.microsoft.com/library/windows/desktop/bb787946) structure dans le SDK Windows.  
  
##  <a name="synctoricheditobject"></a>  CRichEditCntrItem::SyncToRichEditObject  
 Appelez cette fonction pour synchroniser l’aspect de l’appareil, [DVASPECT](http://msdn.microsoft.com/library/windows/desktop/ms690318), de ce `CRichEditCntrltem` à celle spécifiée par *REO ne possèdent*.  
  
```  
void SyncToRichEditObject(REOBJECT& reo);
```  
  
### <a name="parameters"></a>Paramètres  
 *REO ne possèdent*  
 Référence à un [REOBJECT](http://msdn.microsoft.com/library/windows/desktop/bb787946) structure qui décrit un élément OLE.  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations, consultez [DVASPECT](http://msdn.microsoft.com/library/windows/desktop/ms690318) dans le Kit de développement logiciel Windows.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple MFC WORDPAD](../../visual-cpp-samples.md)   
 [Classe de COleClientItem](../../mfc/reference/coleclientitem-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [CRichEditDoc (classe)](../../mfc/reference/cricheditdoc-class.md)   
 [CRichEditView, classe](../../mfc/reference/cricheditview-class.md)
