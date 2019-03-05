---
title: Documents, vues et le Framework
ms.date: 11/19/2018
helpviewer_keywords:
- document templates [MFC], template objects
- applications [MFC]
- MFC, application framework
- application objects [MFC], relation to other MFC objects
- documents [MFC]
- MFC, documents
- document objects [MFC], in relation to other MFC objects
- view objects [MFC], relation to other MFC objects
- MFC, views
- document/view architecture [MFC], about document/view architecture
- objects [MFC], MFC applications
- MFC object relationships
- thread objects [MFC]
ms.assetid: 409ddd9b-66ad-4625-84f7-bf55a41d697b
ms.openlocfilehash: 799035976ea55988a635f7dc9b667e87c48d8f7e
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57273502"
---
# <a name="documents-views-and-the-framework"></a>Documents, vues et le Framework

Les concepts du document et de la vue sont au cœur du framework MFC. Un document est un objet de données avec lequel l'utilisateur interagit dans une session d'édition. Il est créé par le **New** ou **Open** commande sur le **fichier** menu et est généralement stocké dans un fichier. (Les documents standard MFC, dérivées de la classe `CDocument`, sont différents des documents actifs et des documents composés OLE.) Une vue est un objet fenêtre via lequel l'utilisateur interagit avec un document.

Les objets principaux dans une application active sont :

- Le document ou les documents.

   Votre classe de document (dérivée de [CDocument](../mfc/reference/cdocument-class.md)) spécifie les données de votre application.

   Si vous souhaitez des fonctionnalités OLE dans votre application, dérivez votre classe de document de [COleDocument](../mfc/reference/coledocument-class.md) ou l’une de ses classes dérivées, selon le type de fonctionnalité dont vous avez besoin.

- La vue ou les vues.

   Votre classe d’affichage (dérivée de [CView](../mfc/reference/cview-class.md)) est « fenêtre sur les données » l’utilisateur. La classe d'affichage contrôle comment l'utilisateur voit les données de votre document et interagit avec. Dans certains cas, vous pouvez vouloir un document avec plusieurs vues des données.

   Si vous avez besoin de défilement, dérivez de [CScrollView](../mfc/reference/cscrollview-class.md). Si votre vue a une interface utilisateur qui est disposée selon une ressource de modèle de boîte de dialogue, dérivez de [CFormView](../mfc/reference/cformview-class.md). Pour les données de texte simple, utiliser ou dériver de [CEditView](../mfc/reference/ceditview-class.md). Pour une application d’accès aux données de formulaire, tel qu’un programme de saisie de données, dérivent [CRecordView](../mfc/reference/crecordview-class.md) (pour ODBC). Sont également disponibles classes [CTreeView](../mfc/reference/ctreeview-class.md), [CListView](../mfc/reference/clistview-class.md), et [CRichEditView](../mfc/reference/cricheditview-class.md).

- Les fenêtres frame

   Les vues sont affichés dans des "fenêtres frame de document". Dans une application SDI, la fenêtre frame de document correspond également à la "fenêtre frame principale" de l'application. Dans une application MDI, les fenêtres de document sont des fenêtres enfants affichées à l'intérieur d'une fenêtre frame principale. Votre classe dérivée de fenêtre frame principale spécifie les styles et d'autres fonctionnalités des fenêtres frame qui contiennent les vues. Si vous avez besoin de personnaliser des fenêtres frame, dérivez de [CFrameWnd](../mfc/reference/cframewnd-class.md) pour personnaliser la fenêtre frame de document pour les applications SDI. Dériver de [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md) pour personnaliser la fenêtre frame principale pour les applications MDI. Également dériver une classe de [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) pour personnaliser chaque type distinct de fenêtres frame de document MDI qui prend en charge de votre application.

- Le(s) modèle(s) de document

   Un modèle de document orchestre la création des documents, des vues et des fenêtres frame. Une classe de modèle de document particulier, dérivé de la classe [CDocTemplate](../mfc/reference/cdoctemplate-class.md), crée et gère tous les documents ouverts d’un type. Les applications qui prennent en charge plusieurs types de documents ont plusieurs modèles de document. Utilisez la classe [CSingleDocTemplate](../mfc/reference/csingledoctemplate-class.md) pour les applications SDI ou la classe [CMultiDocTemplate](../mfc/reference/cmultidoctemplate-class.md) pour les applications MDI.

- L'objet application

   La classe d’application (dérivée de [CWinApp](../mfc/reference/cwinapp-class.md)) contrôle tous les objets ci-dessus et spécifie le comportement de l’application telles que l’initialisation et nettoyage. Le seul et unique objet d'application de l'application crée et gère les modèles de document pour tout type de document pris en charge par l'application.

- Les objets thread

   Si votre application crée des threads d’exécution séparés, par exemple, pour effectuer des calculs en arrière-plan, vous allez utiliser les classes dérivées de [CWinThread](../mfc/reference/cwinthread-class.md). [CWinApp](../mfc/reference/cwinapp-class.md) lui-même est dérivé `CWinThread` et représente le principal thread d’exécution (ou le processus principal) dans votre application. Vous pouvez également utiliser MFC dans les threads secondaires.

Dans une application active, ces objets répondent en coopération aux actions de l'utilisateur, liés par des commandes et d'autres messages. Un objet d'application gère un ou plusieurs modèles de document. Chaque modèle de document crée et gère un ou plusieurs documents (selon que l'application est de type SDI ou MDI). L'utilisateur voit et manipule un document dans une vue contenue dans une fenêtre frame. L'illustration suivante montre les relations entre les objets pour une application SDI.

![Objets dans une application SDI en cours d’exécution](../mfc/media/vc386v1.gif "objets dans une application SDI en cours d’exécution") <br/>
Objets dans une application SDI en cours d'exécution

Le reste de cette famille d'articles explique comment les outils de framework, l'Assistant Application MFC et les éditeurs de ressources créent ces objets, comment ils fonctionnement conjointement et comment les utiliser dans votre programmation. Documents, vues et fenêtres frame sont présentés plus en détail dans [objets fenêtres](../mfc/window-objects.md) et [Architecture Document/vue](../mfc/document-view-architecture.md).

## <a name="see-also"></a>Voir aussi

[Utilisation des classes pour l’écriture d’applications pour Windows](../mfc/using-the-classes-to-write-applications-for-windows.md)
