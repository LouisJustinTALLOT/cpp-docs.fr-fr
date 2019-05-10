---
title: Assistant Projet ATL
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.atl.com.overview
helpviewer_keywords:
- ATL projects, creating
- ATL Project Wizard
ms.assetid: 564d2aaf-5b8e-4c2a-a925-ca40a283ea34
ms.openlocfilehash: 384847738f5410d750d53d3125c18f6a5256cccf
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221243"
---
# <a name="atl-project-wizard"></a>Assistant Projet ATL

La bibliothèque ATL (Active Template) est un ensemble de classes C++ basées sur modèle qui simplifient l’écriture des objets COM petits et rapides. L’Assistant Projet ATL crée un projet avec les structures de contenir des objets COM.

## <a name="overview"></a>Vue d'ensemble

Cette page décrit actuel [paramètres d’application pour le projet ATL](../../atl/reference/application-settings-atl-project-wizard.md) que vous créez. Par défaut, le projet a les paramètres suivants :

- Bibliothèque de liens dynamiques Spécifie que votre serveur est une DLL et donc un serveur in-process.

- Avec attributs Spécifie que votre projet utilise des attributs.

Pour modifier ces valeurs par défaut, cliquez sur **paramètres d’Application** dans la colonne de gauche de l’Assistant et apporter des modifications dans la page de l’Assistant Projet ATL.

Pour plus d’informations sur les paramètres de projet par défaut, y compris le choix du jeu de caractères et les liaisons par défaut, consultez [Configurations de projet ATL par défaut](../../atl/reference/default-atl-project-configurations.md).

Une fois que vous créez un projet ATL, vous pouvez ajouter des objets ou des contrôles à votre projet à l’aide de Visual C++ [Assistants de code](../../ide/adding-functionality-with-code-wizards-cpp.md). Vous pouvez apporter les améliorations apportées à un projet ATL de base à l’aide des Assistants code suivants :

- [Ajouter des objets et des contrôles à un projet ATL](../../atl/reference/adding-objects-and-controls-to-an-atl-project.md)

- [Ajouter une nouvelle interface dans un projet ATL](../../atl/reference/adding-a-new-interface-in-an-atl-project.md)

- [Ajouter un composant COM + 1.0 à un projet ATL](../../atl/reference/adding-an-atl-com-plus-1-0-component.md)

En outre, envisagez les tâches suivantes lorsque vous créez et améliorez un projet ATL :

- [Rendre un objet ATL comme noncreatable](../../atl/reference/making-an-atl-object-noncreatable.md)

- [Optimiser le compilateur pour un projet ATL](../../atl/reference/specifying-compiler-optimization-for-an-atl-project.md)

Vous pouvez spécifier les propriétés du projet (par exemple, [s’il faut lier statiquement à la bibliothèque CRT](../../atl/programming-with-atl-and-c-run-time-code.md)) dans le [propriétés du projet](../../build/reference/general-property-page-project.md) page et vous pouvez définir [des configurations de build](/visualstudio/ide/understanding-build-configurations) pour un Projet ATL.

## <a name="see-also"></a>Voir aussi

[Projets Visual Studio - C++](../../build/creating-and-managing-visual-cpp-projects.md)<br/>
[C++types de projets dans Visual Studio](../../build/reference/visual-cpp-project-types.md)<br/>
[Principes de base des objets ATL COM](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[Programmation avec ATL et le code C Run-Time](../../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[Tutoriel](../../atl/active-template-library-atl-tutorial.md)
