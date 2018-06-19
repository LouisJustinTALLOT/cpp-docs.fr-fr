---
title: Classes de documents | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.document
dev_langs:
- C++
helpviewer_keywords:
- document classes [MFC]
ms.assetid: 4bf19b02-0a4f-4319-b68e-cddcba2705cb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2073e432dd0d0792e358a3f159892aea405197c9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33346615"
---
# <a name="document-classes"></a>Classes de documents
Objets de classe de document, créés par les objets de modèle de document, gérer les données de l’application. Vous serez dériver une classe pour vos documents à partir d’une de ces classes.  
  
 Les objets de classe de document interagissent avec les objets de vue. Afficher les objets représentent la zone cliente d’une fenêtre, affichent les données d’un document et permettent aux utilisateurs d’interagir avec elle. Documents et vues sont créées par un objet de modèle de document.  
  
 [CDocument](../mfc/reference/cdocument-class.md)  
 La classe de base pour les documents spécifiques à l’application. Dérivez votre classe de document ou les classes de **CDocument**.  
  
 [COleDocument](../mfc/reference/coledocument-class.md)  
 Utilisé pour l’implémentation d’un document composé, ainsi que la prise en charge des conteneurs de base. Sert de conteneur pour les classes dérivées de [CDocItem](../mfc/reference/cdocitem-class.md). Cette classe peut être utilisée comme classe de base pour le conteneur de documents et est la classe de base pour `COleServerDoc`.  
  
 [COleLinkingDoc plutôt](../mfc/reference/colelinkingdoc-class.md)  
 Une classe dérivée de `COleDocument` qui fournit l’infrastructure de la liaison. Vous devez dériver les classes de documents pour vos applications de conteneur à partir de cette classe et non à partir de `COleDocument` si vous souhaitez qu’ils prennent en charge les liens vers des objets incorporés.  
  
 [CRichEditDoc](../mfc/reference/cricheditdoc-class.md)  
 Gère la liste des éléments client OLE qui sont dans le contrôle RichEdit. Utilisé avec [CRichEditView](../mfc/reference/cricheditview-class.md) et [CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md).  
  
 [COleServerDoc](../mfc/reference/coleserverdoc-class.md)  
 Utilisé comme classe de base pour les classes de documents de l’application serveur. `COleServerDoc` objets fournissent l’essentiel de la prise en charge de serveur via les interactions avec [COleServerItem](../mfc/reference/coleserveritem-class.md) objets. Capacité d’édition Visual est fournie à l’aide de l’architecture document/vue de la bibliothèque de classes.  
  
 [CHtmlEditDoc](../mfc/reference/chtmleditdoc-class.md)  
 Fournit, avec [CHtmlEditView](../mfc/reference/chtmleditview-class.md), les fonctionnalités de la plateforme d’édition WebBrowser HTML dans le contexte de l’architecture document / vue MFC.  
  
## <a name="related-classes"></a>Classes associées  
 Les objets de classe de document peuvent être persistants — en d’autres termes, ils peuvent écrire leur état dans un support de stockage et les lire. MFC fournit la `CArchive` classe afin de faciliter le transfert de données du document sur un support de stockage.  
  
 [CArchive](../mfc/reference/carchive-class.md)  
 Collabore avec un [CFile](../mfc/reference/cfile-class.md) objet à mettre en œuvre le stockage persistant pour les objets via la sérialisation (consultez [CObject::Serialize](../mfc/reference/cobject-class.md#serialize)).  
  
 Documents peuvent également contenir des objets OLE. `CDocItem` est la classe de base des éléments de serveur et client.  
  
 [CDocItem](../mfc/reference/cdocitem-class.md)  
 De classe de base abstraite [COleClientItem](../mfc/reference/coleclientitem-class.md) et [COleServerItem](../mfc/reference/coleserveritem-class.md). Les objets des classes dérivées de `CDocItem` représentent les parties de documents.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de la classe](../mfc/class-library-overview.md)

