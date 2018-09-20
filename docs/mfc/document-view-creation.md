---
title: La création de document / vue | Microsoft Docs
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
ms.openlocfilehash: 0deb187a6540af71a1dc72b730347374bc25f963
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46423058"
---
# <a name="documentview-creation"></a>Création d'un document/d'une vue

Le framework fournit également des implémentations de la **New** et **Open** commandes (entre autres) sur le **fichier** menu. Création d’un nouveau document et sa vue associée et la fenêtre frame est un effort conjoint de l’objet application, un modèle de document, du document nouvellement créé et la fenêtre frame nouvellement créé. Le tableau suivant récapitule les objets créent ce que.

### <a name="object-creators"></a>Créateurs d’objets

|créateur|Crée|
|-------------|-------------|
|Objet Application|Modèle de document|
|Modèle de document|Document|
|Modèle de document|Fenêtre frame|
|Fenêtre frame|Vue|

## <a name="see-also"></a>Voir aussi

[Modèles de document et le processus de création de Document/Vue](../mfc/document-templates-and-the-document-view-creation-process.md)<br/>
[Création de modèle de document](../mfc/document-template-creation.md)<br/>
[Relations entre les objets MFC](../mfc/relationships-among-mfc-objects.md)<br/>
[Création de documents, fenêtres et vues](../mfc/creating-new-documents-windows-and-views.md)

