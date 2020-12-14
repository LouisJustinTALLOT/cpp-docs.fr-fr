---
description: 'En savoir plus sur : modèles de projet C++'
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
ms.openlocfilehash: 924e53e0d977b4f9b3b40bf7444f8495dbe1d451
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97253167"
---
# <a name="c-project-templates"></a>Modèles de projet C++

Les modèles de projet Visual Studio génèrent des fichiers de code source, des options du compilateur, des menus, des barres d’outils, des icônes, des références et des `#include` instructions qui conviennent au type de projet que vous souhaitez créer. Visual Studio inclut plusieurs types de modèles de projet C++ et fournit des assistants pour un grand nombre d’entre eux, ce qui vous permet de personnaliser vos projets au fur et à mesure de leur création. Dès que vous avez créé un projet, vous pouvez le générer et exécuter l’application. Une bonne pratique est d’effectuer des générations intermittentes à mesure que vous développez votre application.

> [!NOTE]
> Vous pouvez créer un projet en langage C à partir de modèles de projet C++. Dans le projet généré, recherchez les fichiers ayant une extension de nom de fichier .cpp et remplacez-la par .c. Ensuite, dans la page **Propriétés du projet** du projet (et non de la solution), développez **Propriétés de configuration**, **C/C++** , puis sélectionnez **Avancé**. Modifiez le paramètre **Compilation sous** en choisissant **Compiler comme code C (/TC)**.

## <a name="project-templates"></a>Modèles de projet

Les modèles de projet inclus dans Visual Studio dépendent de la version du produit et des charges de travail que vous avez installées. Si vous avez installé la charge de travail développement Desktop en C++, Visual Studio dispose de ces modèles de projet C++.

### <a name="windows-desktop"></a>Bureau Windows

|Modèle de projet|Description|
|----------------------|-----------------------------|
|[Application console Windows](../../windows/overview-of-windows-programming-in-cpp.md)|Projet de création d’une application console Windows.|
|[Application de bureau Windows](../../windows/walkthrough-creating-windows-desktop-applications-cpp.md)|Projet de création d’une application de bureau Windows (Win32).|
|[Bibliothèque de liens dynamiques](../walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)|Projet pour la création d’une bibliothèque de liens dynamiques (DLL).|
|[Bibliothèque statique](../walkthrough-creating-and-using-a-static-library-cpp.md)|Projet pour la création d’une bibliothèque statique (LIB).|
|[Assistant Windows Desktop](../../windows/windows-desktop-wizard.md)|Assistant de création d’applications de bureau Windows et de bibliothèques avec des options supplémentaires.|

### <a name="general"></a>Général

|Modèle de projet|Description|
|----------------------|-----------------------------|
|Projet vide|Projet vide pour créer une application, une bibliothèque ou une DLL. Vous devez ajouter le code ou les ressources nécessaires.|
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
|Application vide|Projet d’application de plateforme Windows universelle (UWP) d’une seule page sans contrôle ni disposition prédéfinis.|
|DirectX 11 App|Projet d’application de plateforme Windows universelle qui utilise DirectX 11.|
|Application DirectX 12|Projet d’application de plateforme Windows universelle qui utilise DirectX 12.|
|Application DirectX 11 et XAML|Projet d’application de plateforme Windows universelle qui utilise DirectX 11 et XAML.|
|Application de tests unitaires|Projet de création d’une application de tests unitaires pour des applications de plateforme Windows universelle (UWP).|
|DLL|Projet de bibliothèque de liens dynamiques (DLL) native pouvant être utilisée par une application de plateforme Windows universelle ou un composant d’exécution.|
|Bibliothèque statique|Projet de bibliothèque de liens statiques (LIB) native pouvant être utilisée par une application de plateforme Windows universelle ou un composant d’exécution.|
|Composant Windows Runtime|Projet de composant Windows Runtime pouvant être utilisé par une application de plateforme Windows universelle, quel que soit le langage de programmation dans lequel l’application est écrite.|
|Projet de création de package d’application Windows|Projet qui crée un package UWP permettant à une application de bureau d’être chargée indépendamment ou distribuée via le Microsoft Store.|

## <a name="todo-comments"></a>Commentaires TODO

La plupart des fichiers générés par un modèle de projet contiennent des commentaires TODO pour vous aider à repérer les endroits où vous pouvez fournir votre propre code source. Pour plus d’informations sur l’ajout de code, consultez [Ajout de fonctionnalités à l’aide des Assistants Code](../../ide/adding-functionality-with-code-wizards-cpp.md) et [Utilisation des fichiers de ressources](../../windows/working-with-resource-files.md).
