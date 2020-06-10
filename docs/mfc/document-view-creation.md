---
title: Création de document-vue
ms.date: 11/04/2016
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
ms.openlocfilehash: 5441827188f5bff98638cc85cd29e2efd79f8ae8
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620342"
---
# <a name="documentview-creation"></a>Création d'un document/d'une vue

Le Framework fournit des implémentations des commandes **nouvelles** et **ouvertes** (entre autres) dans le menu **fichier** . La création d’un nouveau document et de la vue et de la fenêtre frame associées est un effort coopératif entre l’objet d’application, un modèle de document, le document nouvellement créé et la fenêtre frame nouvellement créée. Le tableau suivant récapitule les objets qui créent quoi que ce soit.

### <a name="object-creators"></a>Créateurs d’objets

|Creator|Créée|
|-------------|-------------|
|Objet application|Modèle de document|
|Modèle de document|Document|
|Modèle de document|Fenêtre frame|
|Fenêtre frame|Affichage|

## <a name="see-also"></a>Voir aussi

[Modèles de document et processus de création de document/vue](document-templates-and-the-document-view-creation-process.md)<br/>
[Création de modèle de document](document-template-creation.md)<br/>
[Relations entre les objets MFC](relationships-among-mfc-objects.md)<br/>
[Création de documents, fenêtres et vues](creating-new-documents-windows-and-views.md)
