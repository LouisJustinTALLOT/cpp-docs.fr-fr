---
title: Architecture document-vue
ms.date: 11/19/2018
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
ms.openlocfilehash: a74aeba651d385cf3a5386e94ec20e4e56b7cd57
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624787"
---
# <a name="documentview-architecture"></a>Architecture document/vue

Par défaut, l’Assistant Application MFC crée un squelette d’application avec une classe de document et une classe de vue. MFC sépare la gestion des données en ces deux classes. Le document stocke les données et gère l’impression des données et les coordonnées de la mise à jour de plusieurs vues des données. La vue affiche les données et gère l’interaction de l’utilisateur avec elle, y compris la sélection et la modification.

Dans ce modèle, un objet document MFC lit et écrit des données dans un stockage persistant. Le document peut également fournir une interface aux données, où qu’elles se trouvent (par exemple, dans une base de données). Un objet de vue distinct gère l’affichage des données, du rendu des données dans une fenêtre à la sélection et à la modification des données par l’utilisateur. La vue obtient des données d’affichage du document et communique avec le document toutes les modifications apportées aux données.

Bien que vous puissiez facilement remplacer ou ignorer la séparation du document/de la vue, il existe des raisons impérieuses de suivre ce modèle dans la plupart des cas. L’une des meilleures est lorsque vous avez besoin de plusieurs vues du même document, par exemple une feuille de calcul et une vue de graphique. Le modèle document/vue permet à un objet de vue distinct de représenter chaque vue des données, tandis que le code commun à tous les affichages (par exemple, un moteur de calcul) peut résider dans le document. Le document prend également la tâche de mise à jour de toutes les vues chaque fois que les données sont modifiées.

L’architecture document/vue MFC facilite la prise en charge de plusieurs vues, de plusieurs types de documents, de fenêtres fractionnées et d’autres fonctionnalités précieuses de l’interface utilisateur.

Les parties de l’infrastructure MFC les plus visibles à la fois pour l’utilisateur et pour vous, le programmeur, sont le document et la vue. La majeure partie de votre travail lors du développement d’une application avec le Framework passe par l’écriture de vos classes de document et de vue. Cette famille d’articles décrit les éléments suivants :

- Les objectifs des documents et des vues et la façon dont ils interagissent dans le Framework.

- Ce que vous devez faire pour les implémenter.

Au cœur de document/vue se trouvent quatre classes principales :

La classe [CDocument](reference/cdocument-class.md) (ou [COleDocument](reference/coledocument-class.md)) prend en charge les objets utilisés pour stocker ou contrôler les données de votre programme et fournit les fonctionnalités de base pour les classes de documents définies par le programmeur. Un document représente l’unité de données que l’utilisateur ouvre généralement à l’aide de la commande ouvrir du menu fichier et enregistre à l’aide de la commande Enregistrer du menu fichier.

Le [CView](reference/cview-class.md) (ou l’une de ses nombreuses classes dérivées) fournit les fonctionnalités de base pour les classes d’affichage définies par le programmeur. Une vue est attachée à un document et agit en tant qu’intermédiaire entre le document et l’utilisateur : la vue affiche une image du document à l’écran et interprète les entrées utilisateur comme des opérations sur le document. La vue restitue également l’image pour l’impression et l’aperçu avant impression.

[CFrameWnd](reference/cframewnd-class.md) (ou l’une de ses variantes) prend en charge des objets qui fournissent le cadre autour d’une ou plusieurs vues d’un document.

[CDocTemplate](reference/cdoctemplate-class.md) (ou [CSingleDocTemplate](reference/csingledoctemplate-class.md) ou [CMultiDocTemplate](reference/cmultidoctemplate-class.md)) prend en charge un objet qui coordonne un ou plusieurs documents existants d’un type donné et gère la création des objets de document, de vue et de fenêtre frame appropriés pour ce type.

L’illustration suivante montre la relation entre un document et sa vue.

![La vue est la partie du document qui s'affiche](../mfc/media/vc379n1.gif "La vue est la partie du document qui s'affiche") <br/>
Document et vue

L’implémentation du document/de la vue dans la bibliothèque de classes sépare les données elles-mêmes de leur affichage et des opérations de l’utilisateur sur les données. Toutes les modifications apportées aux données sont gérées par le biais de la classe de document. La vue appelle cette interface pour accéder aux données et les mettre à jour.

Les documents, leurs vues associées et les fenêtres frame qui décadrent les vues sont créés par un modèle de document. Le modèle de document est responsable de la création et de la gestion de tous les documents d’un type de document.

## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus sur

- [Portrait de l’architecture document/vue](a-portrait-of-the-document-view-architecture.md)

- [Avantages de l’architecture document/vue](advantages-of-the-document-view-architecture.md)

- [Classes de document et de vue créées par l’Assistant Application](document-and-view-classes-created-by-the-mfc-application-wizard.md)

- [Alternatives à l’architecture document/vue](alternatives-to-the-document-view-architecture.md)

- [Ajout de plusieurs vues à un seul document](adding-multiple-views-to-a-single-document.md)

- [Utilisation de documents](using-documents.md)

- [Utilisation des vues](using-views.md)

- [Types multidocuments, vues et fenêtres frame](multiple-document-types-views-and-frame-windows.md)

- [Initialisation et nettoyage des documents et des vues](initializing-and-cleaning-up-documents-and-views.md)

- [Initialiser vos propres ajouts aux classes de vue de document &](creating-new-documents-windows-and-views.md)

- [Utilisation de classes de bases de données avec des documents et des vues](../data/mfc-using-database-classes-with-documents-and-views.md)

- [Utilisation de classes de bases de données sans document ni vue](../data/mfc-using-database-classes-without-documents-and-views.md)

- [Exemples](../overview/visual-cpp-samples.md)

## <a name="see-also"></a>Voir aussi

[Éléments de l’interface utilisateur](user-interface-elements-mfc.md)<br/>
[Windows](windows.md)<br/>
[Fenêtres frame](frame-windows.md)<br/>
[Modèles de document et processus de création de document/vue](document-templates-and-the-document-view-creation-process.md)<br/>
[Création d'un document/d'une vue](document-view-creation.md)<br/>
[Création de documents, fenêtres et vues](creating-new-documents-windows-and-views.md)
