---
title: Architecture document / vue | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CView class [MFC], view architecture
- CDocument class [MFC]
- MFC, views
- views [MFC], MFC document/view model
- document objects [MFC]
- document objects [MFC], MFC document/view model
- MFC, documents
- documents [MFC], MFC document/view model
- document objects [MFC], document/view architecture
ms.assetid: 6127768a-553f-462a-b01b-a5ee6068c81e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c9554af9443bbd6a6394789343294630104c96f1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33350053"
---
# <a name="documentview-architecture"></a>Architecture document/vue
Par défaut, l’Assistant Application MFC crée un squelette d’application avec une classe de document et une classe d’affichage. MFC sépare la gestion des données dans ces deux classes. Le document stocke les données et gère l’impression des données et coordonne la mise à jour de plusieurs vues des données. La vue affiche les données et gère l’interaction avec elle, y compris la sélection et la modification de l’utilisateur.  
  
 Dans ce modèle, un objet document MFC lit et écrit des données vers le stockage persistant. Le document peut également fournir une interface aux données, qu’elles résident (comme dans une base de données). Un objet vue distinct gère l’affichage de données, de rendu des données dans une fenêtre de sélection de l’utilisateur et de modifier des données. La vue obtient des données d’affichage à partir du document et communique avec le document de modifications de données.  
  
 Pendant que vous pouvez facilement remplacer ou ignorer la séparation de document/vue, il existe des motifs pour suivre ce modèle dans la plupart des cas. Un des meilleurs est lorsque vous avez besoin de plusieurs vues du même document, par exemple une feuille de calcul et affichage d’un graphique. Le modèle document/vue permet à un objet de vue séparé de représenter chaque vue des données, tandis que le code commun à toutes les vues (par exemple, un moteur de calcul) peuvent résider dans le document. Le document prend également la tâche de mise à jour toutes les vues chaque fois que les données sont modifiées.  
  
 L’architecture document/vue MFC facilite la prise en charge de plusieurs vues, plusieurs types de documents, fenêtres fractionnées et autres fonctionnalités importantes de l’interface utilisateur.  
  
 Les parties de l’infrastructure MFC plus visible à l’utilisateur et à vous, le programmeur, sont le document et la vue. La plupart de votre travail de développement d’une application avec l’infrastructure est placé dans l’écriture de vos classes de document et la vue. Cette série d’articles décrit :  
  
-   Les besoins de documents, des vues et comment ils interagissent dans l’infrastructure.  
  
-   Ce que vous devez faire pour les implémenter.  
  
 Au cœur de document/vue sont quatre classes clés :  
  
 Le [CDocument](../mfc/reference/cdocument-class.md) (ou [COleDocument](../mfc/reference/coledocument-class.md)) classe prend en charge les objets utilisés pour stocker ou contrôler les données de votre programme et fournit les fonctionnalités de base pour les classes de documents définies par le programmeur. Un document représente l’unité de données en général, l’utilisateur s’ouvre avec la commande Ouvrir dans le menu fichier et enregistre avec la commande Enregistrer dans le menu fichier.  
  
 Le [CView](../mfc/reference/cview-class.md) (ou un de ses nombreuses classes dérivées) fournit les fonctionnalités de base pour les classes d’affichage défini par le programmeur. Une vue est attachée à un document et joue le rôle d’intermédiaire entre le document et l’utilisateur : la vue restitue une image du document sur l’écran et interprète les entrées utilisateur en tant qu’opérations destinées au document. La vue affiche également l’image pour l’aperçu avant impression et impression.  
  
 [CFrameWnd](../mfc/reference/cframewnd-class.md) (ou une de ses variantes) prend en charge les objets qui fournit le cadre autour d’une ou plusieurs vues d’un document.  
  
 [CDocTemplate](../mfc/reference/cdoctemplate-class.md) (ou [CSingleDocTemplate](../mfc/reference/csingledoctemplate-class.md) ou [CMultiDocTemplate](../mfc/reference/cmultidoctemplate-class.md)) prend en charge un objet qui coordonne un ou plusieurs documents existants d’un type donné et gère la création approprié document, vue et objets de fenêtre frame pour ce type.  
  
 L’illustration suivante montre la relation entre un document et sa vue.  
  
 ![Vue est la partie du document qui s’affiche](../mfc/media/vc379n1.gif "vc379n1")  
Document et affichage  
  
 L’implémentation de document/vue dans la bibliothèque de classes sépare les données à partir de son affichage et d’opérations sur les données de l’utilisateur. Toutes les modifications apportées aux données sont gérées via la classe de document. La vue appelle cette interface pour accéder et mettre à jour les données.  
  
 Documents, leurs vues associées et les fenêtres frames les vues qui sont créés par un modèle de document. Le modèle de document est responsable de la création et la gestion de tous les documents d’un type de document.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus  
  
-   [Portrait de l’architecture document/vue](../mfc/a-portrait-of-the-document-view-architecture.md)  
  
-   [Avantages de l’architecture document/vue](../mfc/advantages-of-the-document-view-architecture.md)  
  
-   [Classes de document et la vue créées par l’Assistant Application](../mfc/document-and-view-classes-created-by-the-mfc-application-wizard.md)  
  
-   [Alternatives à l’architecture document/vue](../mfc/alternatives-to-the-document-view-architecture.md)  
  
-   [Ajout de plusieurs vues à un seul document](../mfc/adding-multiple-views-to-a-single-document.md)  
  
-   [Utilisation de documents](../mfc/using-documents.md)  
  
-   [Utilisation de vues](../mfc/using-views.md)  
  
-   [Types multidocuments, vues et fenêtres frame](../mfc/multiple-document-types-views-and-frame-windows.md)  
  
-   [Initialisation et nettoyage des documents et vues](../mfc/initializing-and-cleaning-up-documents-and-views.md)  
  
-   [Initialiser vos propres ajouts aux classes documents & vues](../mfc/creating-new-documents-windows-and-views.md)  
  
-   [À l’aide des classes de base de données avec des documents et vues](../data/mfc-using-database-classes-with-documents-and-views.md)  
  
-   [À l’aide des classes de base de données sans document ni vue](../data/mfc-using-database-classes-without-documents-and-views.md)  
  
-   [Exemples](../visual-cpp-samples.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Éléments d’Interface utilisateur](../mfc/user-interface-elements-mfc.md)   
 [Windows](../mfc/windows.md)   
 [Fenêtres frame](../mfc/frame-windows.md)   
 [Modèles de document et le processus de création de Document/Vue](../mfc/document-templates-and-the-document-view-creation-process.md)   
 [La création de document/vue](../mfc/document-view-creation.md)   
 [Création de documents, fenêtres et vues](../mfc/creating-new-documents-windows-and-views.md)

