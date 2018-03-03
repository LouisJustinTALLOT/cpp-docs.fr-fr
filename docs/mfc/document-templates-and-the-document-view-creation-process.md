---
title: "Modèles de document et le processus de création de Document / Vue | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- icons, for multiple document templates
- document templates [MFC], and views
- document/view architecture [MFC], creating document/view
- single document template
- MFC, document templates
- multiple document template
- CDocTemplate class [MFC]
- templates [MFC], document templates
ms.assetid: 311ce4cd-fbdf-4ea1-a51b-5bb043abbcee
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fd47720009449d51abadd1e5f513149a83702ea3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="document-templates-and-the-documentview-creation-process"></a>Modèles de document et processus de création de document/vue
Pour gérer le processus complexe de création de documents avec leurs vues associées et les fenêtres frame, le framework utilise deux classes de modèle de document : [CSingleDocTemplate](../mfc/reference/csingledoctemplate-class.md) pour les applications SDI et [CMultiDocTemplate ](../mfc/reference/cmultidoctemplate-class.md) pour les applications MDI. Un `CSingleDocTemplate` peut créer et stocker un document d'un type à la fois. Un `CMultiDocTemplate` conserve une liste de plusieurs documents ouverts d'un type.  
  
 Certaines applications prennent en charge plusieurs types de documents. Par exemple, une application peut prendre en charge les documents texte et les documents graphiques. Dans une telle application, lorsque l'utilisateur sélectionne la commande Nouveau du menu Fichier, une boîte de dialogue affiche une liste des nouveaux types de documents pouvant être ouverts. Pour chaque type de document pris en charge, l'application utilise un objet de modèle de document distinct. La figure suivante illustre la configuration d'une application MDI qui prend en charge deux types de documents et montre plusieurs documents ouverts.  
  
 ![Application MDI qui possède deux types de documents](../mfc/media/vc387h1.gif "vc387h1")  
Une application MDI qui possède deux types de documents  
  
 Les modèles de document sont créés et entretenus par l'objet d'application. L'une des tâches clé effectuées pendant la fonction `InitInstance` de votre application consiste à créer un ou plusieurs modèles de document du type approprié. Cette fonctionnalité est décrite dans [création d’un modèle de Document](../mfc/document-template-creation.md). L'objet d'application enregistre un pointeur à chaque modèle de document dans sa liste de modèles et fournit une interface pour ajouter des modèles de document.  
  
 Si vous avez besoin prendre en charge de deux ou plusieurs types de documents, vous devez ajouter un appel supplémentaire à [AddDocTemplate](../mfc/reference/cwinapp-class.md#adddoctemplate) pour chaque type de document.  
  
 Une icône est stockée pour chaque modèle de document en fonction de sa position dans la liste des applications de modèles de document. L'ordre des modèles de document est déterminé par l'ordre dans lequel ils sont ajoutés avec les appels à `AddDocTemplate`. MFC suppose que la première ressource d'icône dans l'application est l'icône d'application, la ressource d'icône suivante est la première icône de document, et ainsi de suite.  
  
 Par exemple, un modèle de document est la troisième icône sur trois pour l'application. S'il existe une ressource d'icône dans l'application à l'index 3, cette icône est utilisée pour le modèle de document. Sinon, l'icône à l'index 0 est utilisée comme valeur par défaut.  
  
## <a name="see-also"></a>Voir aussi  
 [Rubriques MFC générales](../mfc/general-mfc-topics.md)   
 [Création de modèle de document](../mfc/document-template-creation.md)   
 [La création de document/vue](../mfc/document-view-creation.md)   
 [Relations entre les objets MFC](../mfc/relationships-among-mfc-objects.md)   
 [Création de documents, fenêtres et vues](../mfc/creating-new-documents-windows-and-views.md)

