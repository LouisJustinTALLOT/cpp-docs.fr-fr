---
title: Assistants et les éditeurs de ressources | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- application wizards [MFC], and MFC
- MFC, resource editors
- resource editors, MFC
- MFC Application Wizard
- editors [MFC], resource
- wizards [MFC]
- wizards [MFC], MFC programming
- MFC, wizards
- Class View tool, managing Windows messages
ms.assetid: f5dd4d13-9dc1-4a49-b6bf-5b3cb45fa8ba
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 33fb1caa496c34111de133a113433a614ff5eb22
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33383833"
---
# <a name="wizards-and-the-resource-editors"></a>Assistants et les Éditeurs de ressources
Visual C++ inclut plusieurs Assistants à utiliser dans la programmation MFC, ainsi que de nombreux éditeurs de ressources intégrés. Pour la programmation, les contrôles ActiveX le [Assistant contrôle ActiveX](../mfc/reference/mfc-activex-control-wizard.md) joue un rôle de façon très similaire à celle de l’Assistant Application MFC. Si vous pouvez écrire des applications MFC sans que la plupart de ces outils, les outils considérablement simplifieront et accélérer votre travail.  
  
##  <a name="_core_use_appwizard_to_create_an_mfc_application"></a> Utilisez l’Assistant Application MFC pour créer une Application MFC  
 Utilisez le [Assistant Application MFC](../mfc/reference/mfc-application-wizard.md) pour créer un projet MFC dans Visual C++, ce qui peut inclure OLE et prise en charge de base de données. Contiennent des fichiers dans le projet de votre application, document, vue et les classes de fenêtre frame ; ressources standard, y compris les menus et une barre d’outils facultative ; autres fichiers Windows requis ; et fichiers .rtf facultatifs contenant des rubriques d’aide Windows standard que vous pouvez réviser et enrichir pour créer le fichier d’aide de votre programme.  
  
##  <a name="_core_use_classwizard_to_manage_classes_and_windows_messages"></a> Affichage de classes permet de gérer les Classes et les Messages Windows  
 Classe vue vous permet de créez des fonctions de gestionnaires pour les messages Windows et les commandes, créez et gérez des classes, créez des variables membres de classe, créer des propriétés et méthodes Automation, créer des classes de base de données et bien plus encore.  
  
> [!NOTE]
>  Affichage de classes vous permet également de substituer des fonctions virtuelles dans les classes MFC. Sélectionnez la classe et la fonction virtuelle à substituer. Le reste du processus est similaire à la gestion des messages, comme décrit dans les paragraphes suivants.  
  
 Applications s’exécutant sous Windows sont [orientées messages](../mfc/message-handling-and-mapping.md). Actions de l’utilisateur et d’autres événements qui se produisent dans le programme en cours d’exécution que Windows envoyer des messages aux fenêtres dans le programme. Par exemple, si l’utilisateur clique sur la souris dans une fenêtre, Windows envoie une `WM_LBUTTONDOWN` message lorsque le bouton gauche de la souris est enfoncé et un `WM_LBUTTONUP` message lorsque le bouton est relâché. Windows envoie également **WM_COMMAND** messages lorsque l’utilisateur sélectionne des commandes à partir de la barre de menus.  
  
 Dans l’infrastructure MFC, divers objets, tels que des documents, vues, fenêtres frame, les modèles de document et l’objet d’application peuvent « gérer » les messages. Un tel objet fournit une fonction « gestionnaire » comme l’un de ses membres des fonctions et l’infrastructure mappe le message entrant à son gestionnaire.  
  
 Une grande partie de votre tâche de programmation est choisir les messages à mapper aux différents objets et implémenter le mappage. Pour ce faire, vous utilisez affichage de classes et la fenêtre Propriétés.  
  
 La fenêtre Propriétés crée des fonctions membres de gestionnaire de messages vides, et vous utilisez l’éditeur de code source pour implémenter le corps du gestionnaire. Vous pouvez également créer ou modifier les classes (y compris les classes de votre choix, non dérivées des classes MFC) et leurs membres avec l’affichage de classes. Pour plus d’informations sur l’affichage de la classe et sur les Assistants qui ajoutent du code à un projet, consultez [Ajout de fonctionnalités avec les Assistants Code](../ide/adding-functionality-with-code-wizards-cpp.md).  
  
##  <a name="_core_use_the_resource_editors_to_create_and_edit_resources"></a> Les éditeurs de ressources permet de créer et modifier des ressources  
 Utiliser Visual C++ [éditeurs de ressources](../windows/resource-editors.md) pour créer et modifier des menus, boîtes de dialogue, des contrôles personnalisés, touches accélérateur, bitmaps, icônes, curseurs, des chaînes et des ressources de version. À compter de Visual C++ version 4.0, un éditeur de barre d’outils est facilitée, barres d’outils de création.  
  
 Pour vous aider à encore plus, la bibliothèque Microsoft Foundation Class fournit un fichier appelé COMMON. RES, qui contient des ressources « clipart » que vous pouvez copier à partir de COMMON. RES et les coller dans votre propre fichier de ressources. COURANTES. RES comporte des boutons de barre d’outils, common curseurs, icônes et bien plus encore. Vous pouvez utiliser, modifier et redistribuer ces ressources dans votre application. Pour plus d’informations sur COMMON. RES, consultez le [Clipart, exemple](../visual-cpp-samples.md).  
  
 L’Assistant Application MFC, les Assistants Visual C++, éditeurs de ressources et l’infrastructure MFC ne beaucoup de travail à votre place et vous permettent de gérer votre code beaucoup plus facile. L’essentiel de votre code d’application se trouve dans vos classes de document et la vue.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des classes pour l’écriture d’applications pour Windows](../mfc/using-the-classes-to-write-applications-for-windows.md)
