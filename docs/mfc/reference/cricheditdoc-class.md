---
title: CRichEditDoc, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CRichEditDoc
- AFXRICH/CRichEditDoc
- AFXRICH/CRichEditDoc::CreateClientItem
- AFXRICH/CRichEditDoc::GetStreamFormat
- AFXRICH/CRichEditDoc::GetView
- AFXRICH/CRichEditDoc::m_bRTF
dev_langs:
- C++
helpviewer_keywords:
- CRichEditDoc [MFC], CreateClientItem
- CRichEditDoc [MFC], GetStreamFormat
- CRichEditDoc [MFC], GetView
- CRichEditDoc [MFC], m_bRTF
ms.assetid: c936ec18-d516-49d4-b7fb-c9aa0229eddc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 23aacdfca1dbc958c16223d7d57cec39ef65267b
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43221799"
---
# <a name="cricheditdoc-class"></a>CRichEditDoc (classe)
Avec [CRichEditView](../../mfc/reference/cricheditview-class.md) et [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md), fournit les fonctionnalités du contrôle RichEdit dans le contexte de l’architecture document / vue de MFC.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CRichEditDoc : public COleServerDoc  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CRichEditDoc::CreateClientItem](#createclientitem)|Appelée pour effectuer un nettoyage du document.|  
|[CRichEditDoc::GetStreamFormat](#getstreamformat)|Indique si les flux d’entrée et sortie doivent inclure des informations de mise en forme.|  
|[CRichEditDoc::GetView](#getview)|Récupère l’associé [CRichEditView](../../mfc/reference/cricheditview-class.md) objet.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CRichEditDoc::m_bRTF](#m_brtf)|Indique si le flux d’e/s doit inclure la mise en forme.|  
  
## <a name="remarks"></a>Notes  
 Un « contrôle RichEdit » est une fenêtre dans laquelle l’utilisateur peut entrer et modifier du texte. Le texte peut avoir de caractère et de mise en forme de paragraphe et peut inclure des objets OLE incorporés. Les contrôles RichEdit fournissent une interface de programmation pour la mise en forme de texte. Toutefois, une application doit implémenter les composants d’interface utilisateur nécessaires pour rendre les opérations de mise en forme disponibles à l’utilisateur.  
  
 `CRichEditView` gère le texte et les caractéristiques de mise en forme du texte. `CRichEditDoc` gère la liste des éléments de clients qui se trouvent dans la vue. `CRichEditCntrItem` fournit l’accès côté conteneur aux éléments client OLE.  
  
 Ce contrôle commun de Windows (et par conséquent le [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) et les classes associées) est disponible uniquement pour les programmes s’exécutant sous Windows 95/98 et Windows NT versions 3.51 et ultérieures.  
  
 Pour obtenir un exemple d’utilisation d’un document RichEdit dans une application MFC, consultez le [WORDPAD](../../visual-cpp-samples.md) exemple d’application.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocument](../../mfc/reference/cdocument-class.md)  
  
 [COleDocument](../../mfc/reference/coledocument-class.md)  
  
 [COleLinkingDoc plutôt](../../mfc/reference/colelinkingdoc-class.md)  
  
 [COleServerDoc](../../mfc/reference/coleserverdoc-class.md)  
  
 `CRichEditDoc`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxrich.h  
  
##  <a name="createclientitem"></a>  CRichEditDoc::CreateClientItem  
 Appelez cette fonction pour créer un `CRichEditCntrItem` de l’objet et l’ajouter à ce document.  
  
```  
virtual CRichEditCntrItem* CreateClientItem(REOBJECT* preo = NULL) const = 0;  
```  
  
### <a name="parameters"></a>Paramètres  
 *preo*  
 Pointeur vers un [REOBJECT](/windows/desktop/api/richole/ns-richole-_reobject) structure qui décrit un élément OLE. La nouvelle `CRichEditCntrItem` objet est construit autour de cet élément OLE. Si *preo* est NULL, le nouvel élément de client est vide.  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers un nouveau [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md) objet qui a été ajouté à ce document.  
  
### <a name="remarks"></a>Notes  
 Cette fonction n’effectue pas de toute initialisation OLE.  
  
 Pour plus d’informations, consultez le [REOBJECT](/windows/desktop/api/richole/ns-richole-_reobject) structure dans le SDK Windows.  
  
##  <a name="getstreamformat"></a>  CRichEditDoc::GetStreamFormat  
 Appelez cette fonction pour déterminer le format de texte pour le contenu de l’édition enrichie de diffusion en continu.  
  
```  
int GetStreamFormat() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un des indicateurs suivants :  
  
- SF_TEXT indique que le contrôle RichEdit ne conserve pas les informations de mise en forme.  
  
- SF_RTF indique que le contrôle RichEdit ne conserve pas les informations de mise en forme.  
  
### <a name="remarks"></a>Notes  
 La valeur de retour est basée sur le [m_bRTF](#m_brtf) membre de données. Cette fonction retourne SF_RTF si `m_bRTF` est TRUE ; sinon, SF_TEXT.  
  
##  <a name="getview"></a>  CRichEditDoc::GetView  
 Appelez cette fonction pour accéder à la [CRichEditView](../../mfc/reference/cricheditview-class.md) objet associé à cet `CRichEditDoc` objet.  
  
```  
virtual CRichEditView* GetView() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers le `CRichEditView` objet associé au document.  
  
### <a name="remarks"></a>Notes  
 Le texte et les informations de mise en forme sont contenus dans le `CRichEditView` objet. Le `CRichEditDoc` objet gère les éléments OLE pour la sérialisation. Il doit y avoir qu’un seul `CRichEditView` pour chaque `CRichEditDoc`.  
  
##  <a name="m_brtf"></a>  CRichEditDoc::m_bRTF  
 Quand la valeur est TRUE, indique que [CRichEditCtrl::StreamIn](../../mfc/reference/cricheditctrl-class.md#streamin) et [CRichEditCtrl::StreamOut](../../mfc/reference/cricheditctrl-class.md#streamout) doit stocker paragraphe et caractéristiques de mise en forme des caractères.  
  
```  
BOOL m_bRTF;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple MFC WORDPAD](../../visual-cpp-samples.md)   
 [COleServerDoc, classe](../../mfc/reference/coleserverdoc-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [CRichEditView (classe)](../../mfc/reference/cricheditview-class.md)   
 [CRichEditCntrItem, classe](../../mfc/reference/cricheditcntritem-class.md)   
 [COleDocument, classe](../../mfc/reference/coledocument-class.md)   
 [CRichEditCtrl, classe](../../mfc/reference/cricheditctrl-class.md)
