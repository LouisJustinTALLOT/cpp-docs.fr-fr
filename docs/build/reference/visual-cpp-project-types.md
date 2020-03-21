---
title: Types de projets Visual C++
ms.date: 08/13/2019
helpviewer_keywords:
- programs [C++], projects
- project templates [Visual Studio], C++
- TODO comments [C++]
- projects [C++], types
- templates [C++], projects
- applications [C++], projects
- C++ projects, types
ms.assetid: 7337987e-1e7b-4120-9a4b-94f0401f15e7
ms.openlocfilehash: f322d16bbbe91d229fb8efdfb5f2d35cb0a686ae
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079225"
---
# <a name="c-project-templates"></a>Modèles de projet C++

Les modèles de projet Visual Studio génèrent des fichiers de code source, des options du compilateur, des menus, des barres d’outils, des icônes, des références et des instructions `#include` qui conviennent au type de projet que vous souhaitez créer. Visual Studio inclut plusieurs types de C++ modèles de projet et fournit des assistants pour un grand nombre d’entre eux, ce qui vous permet de personnaliser vos projets au fur et à mesure de leur création. Dès que vous avez créé un projet, vous pouvez le générer et exécuter l’application. Une bonne pratique est d’effectuer des générations intermittentes à mesure que vous développez votre application.

> [!NOTE]
> Vous pouvez créer un projet en langage C à partir de modèles de projet C++. Dans le projet généré, recherchez les fichiers ayant une extension de nom de fichier .cpp et remplacez-la par .c. Ensuite, dans la page **Propriétés du projet** du projet (et non de la solution), développez **Propriétés de configuration**, **C/C++** , puis sélectionnez **Avancé**. Modifiez le paramètre **Compilation sous** en choisissant **Compiler comme code C (/TC)** .

## <a name="project-templates"></a>Modèles de projet

Les modèles de projet inclus dans Visual Studio dépendent de la version du produit et des charges de travail que vous avez installées. Si vous avez installé le développement bureautique avec C++ une charge de travail, Visual C++ Studio dispose de ces modèles de projet.

### <a name="windows-desktop"></a>Windows Desktop

|Modèle de projet|Description|
|----------------------|-----------------------------|
|[Application console Windows](../../windows/creating-a-console-application.md)|Projet de création d’une application console Windows.|
|[Application de bureau Windows](../../windows/walkthrough-creating-windows-desktop-applications-cpp.md)|Projet de création d’une application de bureau Windows (Win32).|
|[Bibliothèque de liens dynamiques](../walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)|Projet de création d’une DLL (bibliothèque de liens dynamiques).|
|[Bibliothèque statique](../../windows/walkthrough-creating-and-using-a-static-library-cpp.md)|Projet de création d’une bibliothèque statique (LIB).|
|[Assistant Windows Desktop](../../windows/windows-desktop-wizard.md)|Assistant de création d’applications de bureau Windows et de bibliothèques avec des options supplémentaires.|

### <a name="general"></a>Général

|Modèle de projet|Description|
|----------------------|-----------------------------|
|Projet vide|Projet vide de création d’une application, d’une bibliothèque ou d’une DLL. Vous devez ajouter le code ou les ressources nécessaires.|
|[Projet Makefile](creating-a-makefile-project.md)|Projet qui encapsule un Makefile Windows dans un projet Visual Studio. (Pour ouvrir un Makefile tel quel dans Visual Studio, utilisez [ouvrir le dossier](../open-folder-projects-cpp.md).|
|Projet d’éléments partagés|Projet utilisé pour partager des fichiers de code ou des fichiers de ressources entre plusieurs projets. Ce type de projet ne produit pas de fichier exécutable.|

### <a name="atl"></a>ATL

|Modèle de projet|Description|
|----------------------|-----------------------------|
|[Projet ATL](../../atl/reference/creating-an-atl-project.md)|Projet qui utilise Active Template Library.|

### <a name="test"></a>Test

|Modèle de projet|Description|
|----------------------|-----------------------------|
|[Projet de test unitaire natif](/visualstudio/test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp)|Projet qui contient des tests unitaires C++ natifs.|

### <a name="mfc"></a>MFC

Si vous ajoutez le composant de prise en charge MFC et ATL à votre installation de Visual Studio, ces modèles de projet sont ajoutés à Visual Studio.

|Modèle de projet|Description|
|----------------------|-----------------------------|
|[Application MFC](../../mfc/reference/creating-an-mfc-application.md)|Projet de création d’une application qui utilise la bibliothèque MFC (Microsoft Foundation Class).|
|[Contrôle ActiveX MFC](../../mfc/reference/creating-an-mfc-activex-control.md)|Projet de création d’un contrôle ActiveX qui utilise la bibliothèque MFC.|
|[DLL MFC](../../mfc/reference/creating-an-mfc-dll-project.md)|Projet de création d’une bibliothèque de liens dynamiques qui utilise la bibliothèque MFC.|

### <a name="windows-universal-apps"></a>Applications Windows universelles

Si vous ajoutez le composant des outils de plateforme Windows universelle C++ à votre installation de Visual Studio, ces modèles de projet sont ajoutés à Visual Studio.

Pour une vue d’ensemble des applications Windows universelles en C++, consultez [Applications Windows universelles (C++)](../../cppcx/universal-windows-apps-cpp.md).

|Modèle de projet|Description|
|----------------------|-----------------------------|
|Applications vide|Projet d’application de plateforme Windows universelle (UWP) d’une seule page sans contrôle ni disposition prédéfinis.|
|DirectX 11 App|Projet d’application de plateforme Windows universelle qui utilise DirectX 11.|
|Application DirectX 12|Projet d’application de plateforme Windows universelle qui utilise DirectX 12.|
|Application DirectX 11 et XAML|Projet d’application de plateforme Windows universelle qui utilise DirectX 11 et XAML.|
|Application de tests unitaires|Projet de création d’une application de tests unitaires pour des applications de plateforme Windows universelle (UWP).|
|DLL|Projet de bibliothèque de liens dynamiques (DLL) native pouvant être utilisée par une application de plateforme Windows universelle ou un composant d’exécution.|
|Bibliothèque statique|Projet de bibliothèque de liens statiques (LIB) native pouvant être utilisée par une application de plateforme Windows universelle ou un composant d’exécution.|
|Composant Windows Runtime|Projet de composant Windows Runtime pouvant être utilisé par une application de plateforme Windows universelle, quel que soit le langage de programmation dans lequel l’application est écrite.|
|Projet de création de packages d’application Windows|Projet qui crée un package UWP permettant à une application de bureau d’être chargée indépendamment ou distribuée via le Microsoft Store.|

## <a name="todo-comments"></a>Commentaires TODO

La plupart des fichiers générés par un modèle de projet contiennent des commentaires TODO pour vous aider à repérer les endroits où vous pouvez fournir votre propre code source. Pour plus d’informations sur l’ajout de code, consultez [Ajout de fonctionnalités à l’aide des Assistants Code](../../ide/adding-functionality-with-code-wizards-cpp.md) et [Utilisation des fichiers de ressources](../../windows/working-with-resource-files.md).
