---
title: Classe de CDocItem | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDocItem
- AFXOLE/CDocItem
- AFXOLE/CDocItem::GetDocument
- AFXOLE/CDocItem::IsBlank
dev_langs:
- C++
helpviewer_keywords:
- CDocItem [MFC], GetDocument
- CDocItem [MFC], IsBlank
ms.assetid: 84fb8610-a4c8-4211-adc0-e70e8d002c11
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 724e5017f51a3527e2ad81bcf707179053cc3e88
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33366591"
---
# <a name="cdocitem-class"></a>Classe de CDocItem
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
|[CDocItem::IsBlank](#isblank)|Détermine si l’élément contient toutes les informations.|  
  
## <a name="remarks"></a>Notes  
 `CDocItem` objets sont utilisés pour représenter des éléments OLE dans des documents de client et le serveur.  
  
 Pour plus d’informations, consultez l’article [conteneurs : implémentation d’un conteneur](../../mfc/containers-implementing-a-container.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CDocItem`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxole.h  
  
##  <a name="getdocument"></a>  CDocItem::GetDocument  
 Appelez cette fonction pour obtenir le document qui contient l’élément.  
  
```  
CDocument* GetDocument() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers le document qui contient l’élément ; **NULL**, si l’élément n’est pas partie d’un document.  
  
### <a name="remarks"></a>Notes  
 Cette fonction est substituée dans les classes dérivées [COleClientItem](../../mfc/reference/coleclientitem-class.md) et [COleServerItem](../../mfc/reference/coleserveritem-class.md), qui retourne un pointeur soit un [COleDocument](../../mfc/reference/coledocument-class.md), un [ COleLinkingDoc plutôt](../../mfc/reference/colelinkingdoc-class.md), ou un [COleServerDoc](../../mfc/reference/coleserverdoc-class.md) objet.  
  
##  <a name="isblank"></a>  CDocItem::IsBlank  
 Appelé par l’infrastructure lors de la sérialisation par défaut.  
  
```  
virtual BOOL IsBlank() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’élément ne contient aucune information ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Par défaut, `CDocItem` objets ne sont pas vides. [COleClientItem](../../mfc/reference/coleclientitem-class.md) objets sont parfois vides, car ils dérivent directement `CDocItem`. Toutefois, [COleServerItem](../../mfc/reference/coleserveritem-class.md) les objets sont toujours vides. Par défaut, les applications OLE contenant `COleClientItem` les objets qui n’ont aucune x ou les y étendue sont sérialisés. Pour ce faire, vous devez retourner **TRUE** à partir d’une substitution de `IsBlank` lorsque l’élément n’a ni y ni x étendue.  
  
 Remplacez cette fonction si vous souhaitez implémenter d’autres actions pendant la sérialisation.  
  
## <a name="see-also"></a>Voir aussi  
 [CCmdTarget (classe)](../../mfc/reference/ccmdtarget-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [COleDocument (classe)](../../mfc/reference/coledocument-class.md)   
 [Classe COleServerItem](../../mfc/reference/coleserveritem-class.md)   
 [COleClientItem, classe](../../mfc/reference/coleclientitem-class.md)
