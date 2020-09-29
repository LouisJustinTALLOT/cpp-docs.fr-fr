---
title: Documents, vues et infrastructure de bibliothèque MFC (Microsoft Foundation Class)
description: Description des documents et des vues dans la bibliothèque MFC (Microsoft Foundation Class).
ms.date: 09/25/2020
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
ms.openlocfilehash: 41e145224e512b95d8674109f6ed3dcee39fffb1
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2020
ms.locfileid: "91414098"
---
# <a name="documents-views-and-the-framework"></a>Documents, affichages et infrastructure

Les concepts du document et de la vue sont au cœur du framework MFC. Un document est un objet de données avec lequel l'utilisateur interagit dans une session d'édition. Elle est créée par la commande **nouveau** ou **ouvrir** du menu **fichier** et est généralement enregistrée dans un fichier. (Les documents MFC standard, dérivés de la classe `CDocument` , sont différents des documents actifs et des documents composés OLE.) Une vue est un objet de fenêtre par le biais duquel l’utilisateur interagit avec un document.

Les objets principaux dans une application active sont :

- Les objets thread

   Si votre application crée des threads d’exécution distincts, par exemple pour effectuer des calculs en arrière-plan, vous utiliserez les classes dérivées de [`CWinThread`](reference/cwinthread-class.md) . [`CWinApp`](reference/cwinapp-class.md) elle-même est dérivée de `CWinThread` et représente le thread principal d’exécution (ou le processus principal) dans votre application. Vous pouvez également utiliser MFC dans les threads secondaires.

- L'objet application

   Votre classe d’application (dérivée de [`CWinApp`](reference/cwinapp-class.md) ) contrôle tous les objets ci-dessus et spécifie le comportement de l’application, comme l’initialisation et le nettoyage. Le seul et unique objet d'application de l'application crée et gère les modèles de document pour tout type de document pris en charge par l'application.

- Le(s) modèle(s) de document

   Un modèle de document orchestre la création des documents, des vues et des fenêtres frame. Une classe de modèle de document particulière, dérivée de la classe [`CDocTemplate`](reference/cdoctemplate-class.md) , crée et gère tous les documents ouverts d’un type. Les applications qui prennent en charge plusieurs types de documents ont plusieurs modèles de document. Utilisez la classe [CSingleDocTemplate](reference/csingledoctemplate-class.md) pour les applications SDI ou utilisez la classe [`CMultiDocTemplate`](reference/cmultidoctemplate-class.md) pour les applications MDI.

- Les fenêtres frame

   Les vues sont affichés dans des "fenêtres frame de document". Dans une application SDI, la fenêtre frame de document correspond également à la "fenêtre frame principale" de l'application. Dans une application MDI, les fenêtres de document sont des fenêtres enfants affichées à l'intérieur d'une fenêtre frame principale. Votre classe dérivée de fenêtre frame principale spécifie les styles et d'autres fonctionnalités des fenêtres frame qui contiennent les vues. Si vous avez besoin de personnaliser des fenêtres Frame, dérivez de [`CFrameWnd`](reference/cframewnd-class.md) pour personnaliser la fenêtre frame de document pour les applications SDI. Dérivez de [`CMDIFrameWnd`](reference/cmdiframewnd-class.md) pour personnaliser la fenêtre frame principale pour les applications MDI. Dérivez également une classe de [`CMDIChildWnd`](reference/cmdichildwnd-class.md) pour personnaliser chaque type distinct de fenêtres frame de document MDI que votre application prend en charge.

- Le document ou les documents.

   Votre classe de document (dérivée de [`CDocument`](reference/cdocument-class.md) ) spécifie les données de votre application.

   Si vous souhaitez une fonctionnalité OLE dans votre application, dérivez votre classe de document à partir de [`COleDocument`](reference/coledocument-class.md) ou de l’une de ses classes dérivées, selon le type de fonctionnalité dont vous avez besoin.

- La vue ou les vues.

   Votre classe d’affichage (dérivée de [`CView`](reference/cview-class.md) ) est la « fenêtre » de l’utilisateur sur les données. La classe d'affichage contrôle comment l'utilisateur voit les données de votre document et interagit avec. Dans certains cas, vous pouvez vouloir un document avec plusieurs vues des données.

   Si vous avez besoin de faire défiler, dérivez de [`CScrollView`](reference/cscrollview-class.md) . Si votre vue a une interface utilisateur qui est présentée dans une ressource de modèle de boîte de dialogue, dérivez de [`CFormView`](reference/cformview-class.md) . Pour les données de texte simples, utilisez ou dérivez de [`CEditView`](reference/ceditview-class.md) . Pour une application d’accès aux données basée sur les formulaires, telle qu’un programme de saisie de données, dérivez de [`CRecordView`](reference/crecordview-class.md) (pour ODBC). Les classes, et sont également disponibles [`CTreeView`](reference/ctreeview-class.md) [`CListView`](reference/clistview-class.md) [`CRichEditView`](reference/cricheditview-class.md) .

Dans une application active, ces objets répondent en coopération aux actions de l'utilisateur, liés par des commandes et d'autres messages. Un objet d'application gère un ou plusieurs modèles de document. Chaque modèle de document crée et gère un ou plusieurs documents (selon que l'application est de type SDI ou MDI). L'utilisateur voit et manipule un document dans une vue contenue dans une fenêtre frame. L'illustration suivante montre les relations entre les objets pour une application SDI.

![Objets dans une application SDI en cours d’exécution](../mfc/media/vc386v1.gif "Objets dans une application SDI en cours d'exécution")\
Objets dans une application SDI en cours d'exécution

Le reste de cette famille d'articles explique comment les outils de framework, l'Assistant Application MFC et les éditeurs de ressources créent ces objets, comment ils fonctionnement conjointement et comment les utiliser dans votre programmation. Les documents, les vues et les fenêtres Frame sont décrits plus en détail dans la section [objets de fenêtre](window-objects.md) et l' [architecture document/vue](document-view-architecture.md).

## <a name="see-also"></a>Voir aussi

[Utilisation des classes pour écrire des applications pour Windows](using-the-classes-to-write-applications-for-windows.md)
