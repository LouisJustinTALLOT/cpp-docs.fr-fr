---
description: En savoir plus sur les assistants et les éditeurs de ressources
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
ms.openlocfilehash: b493746365809ca6fd193a31d0e7f53917a9646f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97284913"
---
# <a name="wizards-and-the-resource-editors"></a>Assistants et les Éditeurs de ressources

Visual C++ comprend plusieurs assistants à utiliser dans la programmation MFC, ainsi que de nombreux éditeurs de ressources intégrés. Pour la programmation de contrôles ActiveX, l' [Assistant contrôle ActiveX](../mfc/reference/mfc-activex-control-wizard.md) a une fonction similaire à celle de l’Assistant Application MFC. Bien que vous puissiez écrire des applications MFC sans la plupart de ces outils, les outils simplifient et accélèrent votre travail.

## <a name="use-the-mfc-application-wizard-to-create-an-mfc-application"></a><a name="_core_use_appwizard_to_create_an_mfc_application"></a> Utiliser l’Assistant Application MFC pour créer une application MFC

Utilisez l' [Assistant Application MFC](../mfc/reference/mfc-application-wizard.md) pour créer un projet mfc dans Visual C++, qui peut inclure la prise en charge OLE et de la base de données. Les fichiers du projet contiennent vos classes d’application, de document, de vue et de fenêtre frame. ressources standard, y compris les menus et une barre d’outils facultative ; autres fichiers Windows requis ; et les fichiers. rtf facultatifs contenant les rubriques d’aide Windows standard que vous pouvez modifier et compléter pour créer le fichier d’aide de votre programme.

## <a name="use-class-view-to-manage-classes-and-windows-messages"></a><a name="_core_use_classwizard_to_manage_classes_and_windows_messages"></a> Utiliser Affichage de classes pour gérer des classes et des messages Windows

Affichage de classes vous aide à créer des fonctions de gestionnaire pour les messages et les commandes Windows, à créer et à gérer des classes, à créer des variables de membre de classe, à créer des méthodes et des propriétés d’automatisation, à créer des classes de base de données, etc.

> [!NOTE]
> Affichage de classes vous aide également à substituer des fonctions virtuelles dans les classes MFC. Sélectionnez la classe et la fonction virtuelle à substituer. Le reste du processus est similaire à la gestion des messages, comme décrit dans les paragraphes suivants.

Les applications qui s’exécutent sous Windows sont [pilotées par des messages](../mfc/message-handling-and-mapping.md). Les actions de l’utilisateur et les autres événements qui se produisent dans le programme en cours d’exécution entraînent l’envoi par Windows des messages aux fenêtres du programme. Par exemple, si l’utilisateur clique sur la souris dans une fenêtre, Windows envoie un message de WM_LBUTTONDOWN lorsque le bouton gauche de la souris est enfoncé et un message WM_LBUTTONUP lorsque le bouton est relâché. Windows envoie également des messages WM_COMMAND lorsque l’utilisateur sélectionne des commandes à partir de la barre de menus.

Dans l’infrastructure MFC, divers objets, tels que les documents, les vues, les fenêtres Frame, les modèles de document et l’objet application, peuvent « gérer » les messages. Un tel objet fournit une « fonction de gestionnaire » comme l’une de ses fonctions membres, et l’infrastructure mappe le message entrant à son gestionnaire.

Une grande partie de votre tâche de programmation consiste à choisir les messages à mapper aux objets, puis à implémenter ce mappage. Pour ce faire, vous utilisez Affichage de classes et l' [Assistant classe](reference/mfc-class-wizard.md).

L' [Assistant classe](reference/mfc-class-wizard.md) va créer des fonctions membres de gestionnaires de messages vides, et vous utiliserez l’éditeur de code source pour implémenter le corps du gestionnaire. Vous pouvez également créer ou modifier des classes (y compris les classes de votre choix, et non dérivées des classes MFC) et leurs membres avec Affichage de classes. Pour plus d’informations sur l’utilisation de Affichage de classes et sur les assistants qui ajoutent du code à un projet, consultez [Ajout de fonctionnalités à l’aide des assistants de code](../ide/adding-functionality-with-code-wizards-cpp.md).

## <a name="use-the-resource-editors-to-create-and-edit-resources"></a><a name="_core_use_the_resource_editors_to_create_and_edit_resources"></a> Utiliser les éditeurs de ressources pour créer et modifier des ressources

Utilisez les [éditeurs de ressources](../windows/resource-editors.md) Visual C++ pour créer et modifier des menus, des boîtes de dialogue, des contrôles personnalisés, des touches accélérateur, des bitmaps, des icônes, des curseurs, des chaînes et des ressources de version. À partir de Visual C++ version 4,0, un éditeur de barres d’outils simplifie grandement la création de barres d’outils.

Pour vous aider encore plus, le bibliothèque MFC (Microsoft Foundation Class) fournit un fichier appelé COMMON. RES, qui contient des ressources « clip art » que vous pouvez copier à partir d’un élément commun. RES et coller dans votre propre fichier de ressources. Classiques. RES comprend des boutons de barre d’outils, des curseurs courants, des icônes, etc. Vous pouvez utiliser, modifier et redistribuer ces ressources dans votre application. Pour plus d’informations sur COMMON. RES, consultez l' [exemple d’image clipart](../overview/visual-cpp-samples.md).

L’Assistant Application MFC, les assistants de Visual C++, les éditeurs de ressources et l’infrastructure MFC réalisent beaucoup de travail pour vous et facilitent la gestion de votre code. L’essentiel du code spécifique à votre application se trouve dans vos classes de document et de vue.

## <a name="see-also"></a>Voir aussi

[Utilisation des classes pour écrire des applications pour Windows](../mfc/using-the-classes-to-write-applications-for-windows.md)
