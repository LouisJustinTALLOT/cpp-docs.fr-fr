---
title: Classes de conteneur OLE | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.ole
dev_langs:
- C++
helpviewer_keywords:
- ActiveX classes [MFC]
- container classes [MFC]
- OLE classes [MFC]
- visual editing [MFC], classes
- OLE [MFC], classes
- containers [MFC], OLE container applications
ms.assetid: 1e27e1ab-4c22-41eb-8547-6915c72668ae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6f8214b2f40926cc4ab1471dce99ce5215362011
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930488"
---
# <a name="ole-container-classes"></a>Classes de conteneur OLE
Ces classes sont utilisées par les applications de conteneur. Les deux `COleLinkingDoc` et `COleDocument` gérer des collections de `COleClientItem` objets. Au lieu de dériver votre classe de document à partir de `CDocument`, vous devez dériver de `COleLinkingDoc` ou `COleDocument`, selon que vous souhaitez la prise en charge des liens vers des objets incorporés dans votre document.  
  
 Utilisez un `COleClientItem` objet pour représenter chaque élément OLE dans votre document qui est incorporé à partir d’un autre document ou un lien vers un autre document.  
  
 [COleDocObjectItem](../mfc/reference/coledocobjectitem-class.md)  
 Prend en charge la relation contenant-contenu de document actif.  
  
 [COleDocument](../mfc/reference/coledocument-class.md)  
 Utilisé pour l’implémentation d’un document composé, ainsi que la prise en charge des conteneurs de base. Sert de conteneur pour les classes dérivées de `CDocItem`. Cette classe peut être utilisée comme classe de base pour le conteneur de documents et est la classe de base pour `COleServerDoc`.  
  
 [COleLinkingDoc plutôt](../mfc/reference/colelinkingdoc-class.md)  
 Une classe dérivée de `COleDocument` qui fournit l’infrastructure de la liaison. Vous devez dériver les classes de documents pour vos applications de conteneur à partir de cette classe et non à partir de `COleDocument` si vous souhaitez qu’ils prennent en charge les liens vers des objets incorporés.  
  
 [CRichEditDoc](../mfc/reference/cricheditdoc-class.md)  
 Gère la liste des éléments client OLE qui sont dans le contrôle RichEdit. Utilisé avec [CRichEditView](../mfc/reference/cricheditview-class.md) et [CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md).  
  
 [CDocItem](../mfc/reference/cdocitem-class.md)  
 De classe de base abstraite `COleClientItem` et `COleServerItem`. Les objets des classes dérivées de `CDocItem` représentent les parties de documents.  
  
 [COleClientItem](../mfc/reference/coleclientitem-class.md)  
 Une classe d’élément client qui représente le côté client de la connexion à un élément OLE incorporé ou lié. Dériver des éléments de votre client de cette classe.  
  
 [CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md)  
 Fournit un accès côté client à l’élément stocké dans un contrôle RichEdit lorsqu’il est utilisé avec OLE `CRichEditView` et `CRichEditDoc`.  
  
 [COleException](../mfc/reference/coleexception-class.md)  
 Une exception résultant d’une défaillance lors du traitement de OLE. Cette classe est utilisée par les conteneurs et les serveurs.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de la classe](../mfc/class-library-overview.md)

