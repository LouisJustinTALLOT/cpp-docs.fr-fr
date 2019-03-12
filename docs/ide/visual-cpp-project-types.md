---
title: Types de projets Visual C++
ms.date: 10/30/2017
helpviewer_keywords:
- programs [C++], projects
- project templates [Visual Studio], C++
- TODO comments [C++]
- projects [C++], types
- templates [C++], projects
- applications [C++], projects
- Visual C++ projects, types
ms.assetid: 7337987e-1e7b-4120-9a4b-94f0401f15e7
ms.openlocfilehash: 7a81d73100ef52b61f834f7bffe4467bd296c079
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2019
ms.locfileid: "57744552"
---
# <a name="visual-c-project-types"></a>Types de projets Visual C++

Vous pouvez utiliser un modèle de projet pour créer la structure de base du programme, les menus, les barres d’outils, les icônes, les références et les instructions `#include` adaptés au type de projet que vous voulez créer. Visual Studio intègre plusieurs types de modèles de projet Visual C++ qui s’accompagnent pour la plupart d’Assistants qui vous permettent de personnaliser vos projets au moment de les créer. Dès que vous avez créé un projet, vous pouvez le générer et exécuter l’application. Une bonne pratique est d’effectuer des générations intermittentes à mesure que vous développez votre application.

Vous n’êtes pas tenu d’utiliser un modèle pour créer un projet. Cependant, dans la plupart des cas, c’est un choix judicieux, car il est plus facile de modifier les fichiers et la structure de projet fournis que de les créer entièrement.

> [!NOTE]
> Vous pouvez créer un projet en langage C à partir de modèles de projet C++. Dans le projet généré, recherchez les fichiers ayant une extension de nom de fichier .cpp et remplacez-la par .c. Ensuite, dans la page **Propriétés du projet** du projet (et non de la solution), développez **Propriétés de configuration**, **C/C++** , puis sélectionnez **Avancé**. Modifiez le paramètre **Compilation sous** en choisissant **Compiler comme code C (/TC)**.

## <a name="project-templates"></a>Modèles de projet

Les modèles de projet inclus dans Visual Studio dépendent de la version du produit et des charges de travail que vous avez installées. Si vous avez installé la charge de travail Développement Desktop en C++, Visual Studio propose ces modèles de projet Visual C++.

### <a name="windows-desktop"></a>Bureau Windows

|Modèle de projet|Description|
|----------------------|-----------------------------|
|[Application console Windows](../windows/creating-a-console-application.md)|Projet de création d’une application console Windows.|
|[Application de bureau Windows](../windows/walkthrough-creating-windows-desktop-applications-cpp.md)|Projet de création d’une application de bureau Windows (Win32).|
|[Bibliothèque de liens dynamiques](../build/walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)|Projet de création d’une DLL (bibliothèque de liens dynamiques).|
|[Bibliothèque statique](../windows/walkthrough-creating-and-using-a-static-library-cpp.md)|Projet de création d’une bibliothèque statique (LIB).|
|Assistant Windows Desktop|Assistant de création d’applications de bureau Windows et de bibliothèques avec des options supplémentaires.|

### <a name="general"></a>Général

|Modèle de projet|Description|
|----------------------|-----------------------------|
|Projet vide|Projet vide de création d’une application, d’une bibliothèque ou d’une DLL. Vous devez ajouter le code ou les ressources nécessaires.|
|[Projet Makefile](../ide/creating-a-makefile-project.md)|Projet d’utilisation d’un système de génération externe.|
|Projet d’éléments partagés|Projet utilisé pour partager des fichiers entre plusieurs projets.|

### <a name="atl"></a>ATL

|Modèle de projet|Description|
|----------------------|-----------------------------|
|[Projet ATL](../atl/reference/creating-an-atl-project.md)|Projet qui utilise Active Template Library.|

### <a name="test"></a>Tester

|Modèle de projet|Description|
|----------------------|-----------------------------|
|[Projet de test unitaire natif](/visualstudio/test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp)|Projet qui contient des tests unitaires C++ natifs.|

### <a name="mfc"></a>MFC

Si vous ajoutez le composant de prise en charge MFC et ATL à votre installation de Visual Studio, ces modèles de projet sont ajoutés à Visual Studio.

|Modèle de projet|Description|
|----------------------|-----------------------------|
|[Application MFC](../mfc/reference/creating-an-mfc-application.md)|Projet de création d’une application qui utilise la bibliothèque MFC (Microsoft Foundation Class).|
|[Contrôle ActiveX MFC](../mfc/reference/creating-an-mfc-activex-control.md)|Projet de création d’un contrôle ActiveX qui utilise la bibliothèque MFC.|
|[DLL MFC](../mfc/reference/creating-an-mfc-dll-project.md)|Projet de création d’une bibliothèque de liens dynamiques qui utilise la bibliothèque MFC.|

### <a name="windows-universal-apps"></a>Applications Windows universelles

Si vous ajoutez le composant des outils de plateforme Windows universelle C++ à votre installation de Visual Studio, ces modèles de projet sont ajoutés à Visual Studio.

Pour une vue d’ensemble des applications Windows universelles en C++, consultez [Applications Windows universelles (C++)](../windows/universal-windows-apps-cpp.md).

|Modèle de projet|Description|
|----------------------|-----------------------------|
|Applications vide|Projet d’application de plateforme Windows universelle (UWP) d’une seule page sans contrôle ni disposition prédéfinis.|
|DirectX 11 App|Projet d’application de plateforme Windows universelle qui utilise DirectX 11.|
|Application DirectX 12|Projet d’application de plateforme Windows universelle qui utilise DirectX 12.|
|Application DirectX 11 et XAML|Projet d’application de plateforme Windows universelle qui utilise DirectX 11 et XAML.|
|Application de tests unitaires|Projet de création d’une application de tests unitaires pour des applications de plateforme Windows universelle (UWP).|
|DLL|Projet de bibliothèque de liens dynamiques (DLL) native pouvant être utilisée par une application de plateforme Windows universelle ou un composant d’exécution.|
|Bibliothèque statique|Projet de bibliothèque de liens statiques (LIB) native pouvant être utilisée par une application de plateforme Windows universelle ou un composant d’exécution.|
|Composant Windows Runtime|Projet de composant Windows Runtime pouvant être utilisé par une application de plateforme Windows universelle, quel que soit le langage de programmation dans lequel l’application est écrite.|
|Projet de création de packages d’application Windows|Projet qui crée un package UWP permettant à une application de bureau d’être chargée indépendamment ou distribuée via le Microsoft Store.|

## <a name="todo-comments"></a>Commentaires TODO

La plupart des fichiers générés par un modèle de projet contiennent des commentaires TODO pour vous aider à repérer les endroits où vous pouvez fournir votre propre code source. Pour plus d’informations sur l’ajout de code, consultez [Ajout de fonctionnalités à l’aide des Assistants Code](../ide/adding-functionality-with-code-wizards-cpp.md) et [Utilisation des fichiers de ressources](../windows/working-with-resource-files.md).

## <a name="see-also"></a>Voir aussi

[Création de projets de bureau à l’aide des Assistants Application](../ide/creating-desktop-projects-by-using-application-wizards.md)
