---
description: 'En savoir plus sur : Assistant Projet ATL'
title: Assistant Projet ATL
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.atl.com.overview
helpviewer_keywords:
- ATL projects, creating
- ATL Project Wizard
ms.assetid: 564d2aaf-5b8e-4c2a-a925-ca40a283ea34
ms.openlocfilehash: a254447d0590abd3d68090dac04c3b6134f94b19
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97158671"
---
# <a name="atl-project-wizard"></a>Assistant Projet ATL

La Active Template Library (ATL) est un ensemble de classes C++ basées sur des modèles qui simplifient l’écriture d’objets COM petits et rapides. L’Assistant Projet ATL crée un projet avec les structures pour contenir des objets COM.

## <a name="overview"></a>Vue d’ensemble

Cette page de l’Assistant décrit les [paramètres d’application actuels pour le projet ATL](../../atl/reference/application-settings-atl-project-wizard.md) que vous créez. Par défaut, le projet a les paramètres suivants :

- Bibliothèque de liens dynamiques spécifie que votre serveur est une DLL et, par conséquent, un serveur in-process.

- Attributed spécifie que votre projet utilise des attributs.

Pour modifier ces valeurs par défaut, cliquez sur paramètres de l' **application** dans la colonne de gauche de l’Assistant et apportez les modifications nécessaires dans cette page de l’Assistant Projet ATL.

Pour plus d’informations sur les paramètres de projet par défaut, notamment le choix du jeu de caractères et la liaison des valeurs par défaut, consultez [configurations de projet ATL par défaut](../../atl/reference/default-atl-project-configurations.md).

Après avoir créé un projet ATL, vous pouvez ajouter des objets ou des contrôles à votre projet à l’aide de Visual C++ [assistants code](../../ide/adding-functionality-with-code-wizards-cpp.md). Vous pouvez apporter les types d’améliorations suivants à un projet ATL de base à l’aide des Assistants Code :

- [Ajouter un objet et des contrôles à un projet ATL](../../atl/reference/adding-objects-and-controls-to-an-atl-project.md)

- [Ajouter une nouvelle interface à un projet ATL](../../atl/reference/adding-a-new-interface-in-an-atl-project.md)

- [Ajouter un composant COM+ 1,0 à un projet ATL](../../atl/reference/adding-an-atl-com-plus-1-0-component.md)

En outre, envisagez ces tâches lorsque vous créez et améliorez un projet ATL :

- [Rendre un objet ATL impossible à créer](../../atl/reference/making-an-atl-object-noncreatable.md)

- [Optimiser le compilateur pour un projet ATL](../../atl/reference/specifying-compiler-optimization-for-an-atl-project.md)

Vous pouvez spécifier des propriétés de projet (par exemple, [si vous souhaitez lier statiquement au CRT](../../atl/programming-with-atl-and-c-run-time-code.md)) dans la page de [Propriétés du projet](../../build/reference/general-property-page-project.md) , et vous pouvez définir des configurations de [Build](/visualstudio/ide/understanding-build-configurations) pour un projet ATL.

## <a name="see-also"></a>Voir aussi

[Projets Visual Studio-C++](../../build/creating-and-managing-visual-cpp-projects.md)<br/>
[Types de projets C++ dans Visual Studio](../../build/reference/visual-cpp-project-types.md)<br/>
[Notions de base des objets COM ATL](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[Programmation avec des Run-Time du code ATL et C](../../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[Didacticiel](../../atl/active-template-library-atl-tutorial.md)
