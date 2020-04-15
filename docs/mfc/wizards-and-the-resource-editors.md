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
ms.openlocfilehash: 04d9f2cf615636b151af93a3c3880f7357496048
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365278"
---
# <a name="wizards-and-the-resource-editors"></a>Assistants et les Éditeurs de ressources

Visual CMD comprend plusieurs assistants pour une utilisation dans la programmation MFC, ainsi que de nombreux éditeurs de ressources intégrées. Pour activeX contrôle la programmation, [l’Assistant de Contrôle ActiveX](../mfc/reference/mfc-activex-control-wizard.md) sert un but un peu comme celui de l’Assistant d’Application MFC. Alors que vous pouvez écrire des applications MFC sans la plupart de ces outils, les outils simplifient et accélèrent considérablement votre travail.

## <a name="use-the-mfc-application-wizard-to-create-an-mfc-application"></a><a name="_core_use_appwizard_to_create_an_mfc_application"></a>Utilisez l’assistant d’application MFC pour créer une application MFC

Utilisez [l’assistant d’application MFC](../mfc/reference/mfc-application-wizard.md) pour créer un projet MFC dans Visual C, qui peut inclure l’OLE et le support de base de données. Les fichiers du projet contiennent vos classes d’application, de document, de vue et de fenêtre de cadre; ressources standard, y compris des menus et une barre d’outils facultative; autres fichiers Windows requis; et des fichiers .rtf optionnels contenant des sujets Windows Help standard que vous pouvez réviser et augmenter pour créer le fichier d’aide de votre programme.

## <a name="use-class-view-to-manage-classes-and-windows-messages"></a><a name="_core_use_classwizard_to_manage_classes_and_windows_messages"></a>Utilisez la vue de classe pour gérer les classes et les messages Windows

Class View vous aide à créer des fonctions de gestionnaire pour les messages et les commandes Windows, à créer et à gérer des classes, à créer des variables de membres de la classe, à créer des méthodes et des propriétés d’automatisation, à créer des classes de base de données, et plus encore.

> [!NOTE]
> Class View vous aide également à remplacer les fonctions virtuelles dans les classes MFC. Sélectionnez la classe et la fonction virtuelle pour passer outre. Le reste du processus est similaire à la manipulation des messages, tel que décrit dans les paragraphes suivants.

Les applications fonctionnant sous Windows sont [pilotées par message](../mfc/message-handling-and-mapping.md). Les actions de l’utilisateur et d’autres événements qui se produisent dans le programme en cours d’exécution font que Windows envoie des messages aux fenêtres du programme. Par exemple, si l’utilisateur clique sur la souris dans une fenêtre, Windows envoie un message WM_LBUTTONDOWN lorsque le bouton de la souris gauche est appuyé et qu’un message WM_LBUTTONUP lorsque le bouton est libéré. Windows envoie également des messages WM_COMMAND lorsque l’utilisateur sélectionne les commandes à partir de la barre de menu.

Dans le cadre MFC, divers objets, tels que des documents, des vues, des fenêtres d’encadrement, des modèles de documents et l’objet d’application, peuvent « manipuler » des messages. Un tel objet fournit une « fonction de gestionnaire » comme l’une de ses fonctions membres, et le cadre cartographie le message entrant à son gestionnaire.

Une grande partie de votre tâche de programmation consiste à choisir les messages à cartographier vers quels objets, puis à mettre en œuvre cette cartographie. Pour ce faire, vous utilisez Class View et le [Class Wizard](reference/mfc-class-wizard.md).

Le [Maître de classe](reference/mfc-class-wizard.md) créera des fonctions de membre de message vide, et vous utiliserez l’éditeur de code source pour implémenter le corps du gestionnaire. Vous pouvez également créer ou modifier des classes (y compris des classes de vos propres classes, non dérivées des classes MFC) et leurs membres avec Class View. Pour plus d’informations sur l’utilisation de Class View et sur les assistants qui ajoutent du code à un projet, voir [Ajouter la fonctionnalité avec Code Wizards](../ide/adding-functionality-with-code-wizards-cpp.md).

## <a name="use-the-resource-editors-to-create-and-edit-resources"></a><a name="_core_use_the_resource_editors_to_create_and_edit_resources"></a>Utiliser les éditeurs de ressources pour créer et modifier les ressources

Utilisez les éditeurs de ressources Visual CMD pour créer et modifier des menus, des boîtes de dialogue, des commandes [personnalisées,](../windows/resource-editors.md) des touches d’accélérateur, des bitmaps, des icônes, des curseurs, des cordes et des ressources de version. À partir de la version 4.0 Visual C, un éditeur de barre d’outils facilite beaucoup la création de barres d’outils.

Pour vous aider encore plus, la Microsoft Foundation Class Library fournit un fichier appelé COMMON. RES, qui contient des ressources "clip art" que vous pouvez copier à partir de COMMON. RES et coller dans votre propre fichier de ressources. Commun. RES comprend des boutons de barre d’outils, des curseurs communs, des icônes, et plus encore. Vous pouvez utiliser, modifier et redistribuer ces ressources dans votre application. Pour plus d’informations sur COMMON. RES, voir [l’échantillon Clipart](../overview/visual-cpp-samples.md).

L’assistant d’application MFC, les assistants Visual C, les éditeurs de ressources et le cadre MFC font beaucoup de travail pour vous et facilitent la gestion de votre code. La majeure partie de votre code spécifique à l’application se trouve dans vos classes de documents et de vision.

## <a name="see-also"></a>Voir aussi

[Utilisation des classes pour l’écriture d’applications pour Windows](../mfc/using-the-classes-to-write-applications-for-windows.md)
