---
title: Assistants et les Éditeurs de ressources
ms.date: 11/04/2016
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
ms.openlocfilehash: 5316899b7eb8828847af6d7db95edf3d8ba3822a
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57265520"
---
# <a name="wizards-and-the-resource-editors"></a>Assistants et les Éditeurs de ressources

Visual C++ inclut plusieurs Assistants à utiliser dans la programmation MFC, ainsi que de nombreux éditeurs de ressources intégré. Pour la programmation, les contrôles ActiveX les [Assistant contrôle ActiveX](../mfc/reference/mfc-activex-control-wizard.md) a un objectif similaire à celle de l’Assistant Application MFC. Bien que vous pouvez écrire des applications MFC sans que la plupart de ces outils, les outils considérablement simplifient et à accélèrent votre travail.

##  <a name="_core_use_appwizard_to_create_an_mfc_application"></a> Utilisez l’Assistant Application MFC pour créer une Application MFC

Utilisez le [Assistant Application MFC](../mfc/reference/mfc-application-wizard.md) pour créer un projet MFC dans Visual C++, ce qui peut inclure OLE et prise en charge de base de données. Fichiers dans le projet contiennent votre application, document, vue et les classes de fenêtre frame ; ressources standard, y compris les menus et une barre d’outils facultatif ; autres fichiers requis par le Windows ; et fichiers .rtf facultatif qui contient des rubriques d’aide Windows standard que vous pouvez réviser et enrichir pour créer le fichier d’aide de votre programme.

##  <a name="_core_use_classwizard_to_manage_classes_and_windows_messages"></a> Utilisez l’affichage de classes pour gérer les Classes et les Messages Windows

Classe vue vous permet de créez des fonctions de gestionnaire pour les messages Windows et les commandes, créez et gérez des classes, créez des variables membres de classe, créer des propriétés et méthodes d’automatisation, créer des classes de base de données et bien plus encore.

> [!NOTE]
>  Affichage de classes vous permet également de substituer des fonctions virtuelles dans les classes MFC. Sélectionnez la classe et la fonction virtuelle à substituer. Le reste du processus est similaire à la gestion des messages, comme décrit dans les paragraphes suivants.

Applications s’exécutant sous Windows sont [orientées messages](../mfc/message-handling-and-mapping.md). Actions de l’utilisateur et d’autres événements qui se produisent dans le programme en cours d’exécution entraînent Windows envoyer des messages pour les fenêtres dans le programme. Par exemple, si l’utilisateur clique sur la souris dans une fenêtre, Windows envoie un message WM_LBUTTONDOWN quand le bouton gauche de la souris est enfoncé et un message WM_LBUTTONUP lorsque le bouton est relâché. Windows envoie également des messages WM_COMMAND lorsque l’utilisateur sélectionne des commandes à partir de la barre de menus.

Dans l’infrastructure MFC, divers objets, tels que des documents, vues, fenêtres frame, modèles de document et l’objet d’application peuvent « gérer » les messages. Un tel objet fournit une « fonction gestionnaire » comme l’un de ses membres des fonctions, et l’infrastructure mappe le message entrant à son gestionnaire.

Une grande partie de votre tâche de programmation est choisir les messages à mapper aux différents objets et implémenter le mappage. Pour ce faire, vous utilisez affichage de classes et la fenêtre Propriétés.

La fenêtre Propriétés crée des fonctions membres de gestionnaire de messages vide, et vous utilisez l’éditeur de code source pour implémenter le corps du gestionnaire. Vous pouvez également créer ou modifier des classes (y compris les classes de votre choix, non dérivées de classes MFC) et leurs membres avec l’affichage de classes. Pour plus d’informations sur l’utilisation d’affichage de classes et des Assistants qui ajoutent du code à un projet, consultez [Ajout de fonctionnalités avec les Assistants Code](../ide/adding-functionality-with-code-wizards-cpp.md).

##  <a name="_core_use_the_resource_editors_to_create_and_edit_resources"></a> Utiliser les éditeurs de ressources pour créer et modifier des ressources

Utiliser le Visual C++ [éditeurs de ressources](../windows/resource-editors.md) pour créer et modifier des menus, boîtes de dialogue, des contrôles personnalisés, touches accélérateur, bitmaps, icônes, curseurs, chaînes et des ressources de version. À compter de Visual C++ version 4.0, un éditeur de la barre d’outils facilite barres d’outils de création.

Pour vous aider à encore plus, la bibliothèque Microsoft Foundation Class fournit un fichier appelé COMMON. RES, qui contient des ressources « clipart » que vous pouvez copier à partir de COMMON. RES et les coller dans votre propre fichier de ressources. COURANTS. RES comporte des boutons de barre d’outils, common curseurs, les icônes et bien plus encore. Vous pouvez utiliser, modifier et redistribuer ces ressources dans votre application. Pour plus d’informations sur COMMON. RES, consultez le [Clipart, exemple](../visual-cpp-samples.md).

L’Assistant Application MFC, les Assistants Visual C++, éditeurs de ressources et l’infrastructure MFC faire beaucoup de travail pour vous et faciliter la gestion de votre code beaucoup plus facile. L’essentiel de votre code spécifique à l’application se trouve dans vos classes de document et la vue.

## <a name="see-also"></a>Voir aussi

[Utilisation des classes pour l’écriture d’applications pour Windows](../mfc/using-the-classes-to-write-applications-for-windows.md)
