---
title: Création de document / vue | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- documents [MFC], creating
- views [MFC], and frame windows
- views [MFC], creating
- tables [MFC]
- MFC, views
- document/view architecture [MFC], creating document/view
- object creators
- MFC, documents
- tables [MFC], objects each MFC object creates
ms.assetid: bda14f41-ed50-439d-af9e-591174e7dd64
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 894bb5a0b3a4c86d764fc6f4a0e4b9ae18422669
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36931851"
---
# <a name="documentview-creation"></a>Création d'un document/d'une vue
Le framework fournit des implémentations de la **nouveau** et **ouvrir** commandes (entre autres) sur le **fichier** menu. Création d’un nouveau document et sa vue associée et la fenêtre frame est un effort conjoint de l’objet d’application, un modèle de document, du document nouvellement créé et la fenêtre frame nouvellement créé. Le tableau suivant récapitule les objets créent que.  
  
### <a name="object-creators"></a>Créateurs d’objets  
  
|créateur|Crée|  
|-------------|-------------|  
|Objet Application|Modèle de document|  
|Modèle de document|Document|  
|Modèle de document|Fenêtre frame|  
|Fenêtre frame|Vue|  
  
## <a name="see-also"></a>Voir aussi  
 [Modèles de document et le processus de création de Document/Vue](../mfc/document-templates-and-the-document-view-creation-process.md)   
 [Création de modèle de document](../mfc/document-template-creation.md)   
 [Relations entre les objets MFC](../mfc/relationships-among-mfc-objects.md)   
 [Création de documents, fenêtres et vues](../mfc/creating-new-documents-windows-and-views.md)

