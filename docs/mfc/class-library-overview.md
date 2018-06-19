---
title: Vue d’ensemble de la bibliothèque de classe | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.mfc
dev_langs:
- C++
helpviewer_keywords:
- grouping MFC classes
- MFC, class library
- classes [MFC], MFC
- class libraries, MFC
- class libraries
ms.assetid: 9b0e3152-ac39-4f52-91b4-f20aa3a674aa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f144ce4dd6ed9cd29adca27aaff51a79af0abec1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33346898"
---
# <a name="class-library-overview"></a>Vue d'ensemble de la bibliothèque de classes
Cette vue d’ensemble de la catégorie et décrit les classes dans les MFC Microsoft Foundation Class Library () version 9.0. Les classes de MFC, ensemble, constituent une infrastructure d’application, l’infrastructure d’une application écrite pour l’API Windows. Votre tâche de programmation consiste à fournir le code qui est spécifique à votre application.  
  
 Les classes de la bibliothèque sont présentées dans les catégories suivantes :  
  
-   [Classe racine : CObject](../mfc/root-class-cobject.md)  
  
-   [Classes d’architecture des applications MFC](../mfc/mfc-application-architecture-classes.md)  
  
    -   [Classes de prise en charge des applications et des threads](../mfc/application-and-thread-support-classes.md)  
  
    -   [Classes de routage des commandes](../mfc/command-routing-classes.md)  
  
    -   [Classes de documents](../mfc/document-classes.md)  
  
    -   [Classes d’affichage (Architecture)](../mfc/view-classes-architecture.md)  
  
    -   [Classes de fenêtre frame (Architecture)](../mfc/frame-window-classes-architecture.md)  
  
    -   [Classes de modèle de document](../mfc/document-template-classes.md)  
  
-   [Classes de fenêtre, de boîte de dialogue et de contrôle](../mfc/window-dialog-and-control-classes.md)  
  
    -   [Classes de fenêtre frame (Fenêtres)](../mfc/frame-window-classes-windows.md)  
  
    -   [Classes d’affichage (Fenêtres)](../mfc/view-classes-windows.md)  
  
    -   [Classes de boîte de dialogue](../mfc/dialog-box-classes.md)  
  
    -   [Classes de contrôle](../mfc/control-classes.md)  
  
    -   [Classes de barre de contrôle](../mfc/control-bar-classes.md)  
  
-   [Dessin et impression de classes](../mfc/drawing-and-printing-classes.md)  
  
    -   [Classes de sortie (Contexte d’appareil)](../mfc/output-device-context-classes.md)  
  
    -   [Classes d’outil de dessin](../mfc/drawing-tool-classes.md)  
  
-   [Classes de type de données simple](../mfc/simple-data-type-classes.md)  
  
-   [Classes de tableaux, listes et mappages](../mfc/array-list-and-map-classes.md)  
  
    -   [Classes de modèle pour les tableaux, listes et tables](../mfc/template-classes-for-arrays-lists-and-maps.md)  
  
    -   [Classes de tableaux prêtes à être utilisées](../mfc/ready-to-use-array-classes.md)  
  
    -   [Classes de listes prêtes à être utilisées](../mfc/ready-to-use-list-classes.md)  
  
    -   [Classes de mappage prêtes à être utilisées](../mfc/ready-to-use-map-classes.md)  
  
-   [Classes de fichiers et de bases de données](../mfc/file-and-database-classes.md)  
  
    -   [Classes d’e/s de fichier](../mfc/file-i-o-classes.md)  
  
    -   [Classes DAO](../mfc/dao-classes.md)  
  
    -   [Classes ODBC](../mfc/odbc-classes.md)  
  
    -   [Classes OLE DB](../mfc/ole-db-classes.md)  
  
-   [Internet et classes réseau](../mfc/internet-and-networking-classes.md)  
  
    -   [Windows Sockets, classes](../mfc/windows-sockets-classes.md)  
  
    -   [Internet Win32, classes](../mfc/win32-internet-classes.md)  
  
-   [OLE, classes](../mfc/ole-classes.md)  
  
    -   [OLE, classes de conteneur](../mfc/ole-container-classes.md)  
  
    -   [OLE, classes de serveur](../mfc/ole-server-classes.md)  
  
    -   [OLE, classes de glisser-déposer et de transfert de données](../mfc/ole-drag-and-drop-and-data-transfer-classes.md)  
  
    -   [OLE, classes de boîtes de dialogue communes](../mfc/ole-common-dialog-classes.md)  
  
    -   [OLE, classes Automation](../mfc/ole-automation-classes.md)  
  
    -   [OLE, classes de contrôle](../mfc/ole-control-classes.md)  
  
    -   [OLE, classes de documents actifs](../mfc/active-document-classes.md)  
  
    -   [OLE, classes liées](../mfc/ole-related-classes.md)  
  
-   [Débogage et classes d’exceptions](../mfc/debugging-and-exception-classes.md)  
  
    -   [Classes de prise en charge du débogage](../mfc/debugging-support-classes.md)  
  
    -   [Classes d’exceptions](../mfc/exception-classes.md)  
  
 La section [général philosophie de conception de classe](../mfc/general-class-design-philosophy.md) explique comment la bibliothèque MFC a été conçue.  
  
 Pour une vue d’ensemble de l’infrastructure, consultez [l’utilisation des Classes pour l’écriture d’Applications Windows](../mfc/using-the-classes-to-write-applications-for-windows.md). Certaines des classes répertoriées ci-dessus sont des classes à usage général qui peuvent être utilisés en dehors de l’infrastructure et fournissent des abstractions utiles telles que les collections, les exceptions, les fichiers et les chaînes.  
  
 Pour afficher l’héritage d’une classe, utilisez le [graphique de hiérarchie de classe](../mfc/hierarchy-chart.md).  
  
 En plus des classes répertoriées dans cette vue d’ensemble, la bibliothèque MFC contient un nombre de fonctions globales, les variables globales et les macros. Il existe une vue d’ensemble et une liste détaillée de ces éléments dans la rubrique [MFC Macros and Globals](../mfc/reference/mfc-macros-and-globals.md), ce qui suit la référence alphabétique aux classes MFC.  
  
## <a name="see-also"></a>Voir aussi  
 [MFC, applications de bureau](../mfc/mfc-desktop-applications.md)

