---
description: 'En savoir plus sur : présentation des étapes de génération personnalisée et des événements de build'
title: Présentation des étapes de génération personnalisée et des événements de build
ms.date: 08/29/2019
helpviewer_keywords:
- builds [C++], events
- custom build steps [C++], customizing builds
- events [C++], build
- custom build steps [C++]
- build steps [C++]
- build events [C++], order of events and build steps
- build steps [C++], build events
- builds [C++], custom build steps
ms.assetid: beb2f017-3e9f-4b2c-9b57-2572fd2628e4
ms.openlocfilehash: da7e9399a1502c3d7ddaccbfb10a4d2b71fb85cf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97277399"
---
# <a name="understanding-custom-build-steps-and-build-events"></a>Présentation des étapes de génération personnalisée et des événements de build

Dans l’environnement de développement Visual C++, vous pouvez personnaliser le processus de build de trois façons :

- **Étapes de build personnalisée**

   Une étape de build personnalisée est une règle de build associée à un projet. Une étape de build personnalisée peut spécifier une ligne de commande à exécuter, une entrée supplémentaire ou des fichiers de sortie, et un message à afficher. Pour plus d’informations, consultez [Guide pratique pour ajouter une étape de build personnalisée à des projets MSBuild](how-to-add-a-custom-build-step-to-msbuild-projects.md).

- **Outils de build personnalisée**

   Un outil de build personnalisée est une règle de build associée à un ou plusieurs fichiers. Une étape de build personnalisée peut passer des fichiers d’entrée à un outil de build personnalisée, ce qui produit un ou plusieurs fichiers de sortie. Par exemple, les fichiers d’aide dans une application MFC sont générés avec un outil de build personnalisée. Pour plus d’informations, consultez [Guide pratique pour ajouter des outils de build personnalisée à des projets MSBuild](how-to-add-custom-build-tools-to-msbuild-projects.md) et [Spécification des outils de build personnalisée](specifying-custom-build-tools.md).

- **Événements de build**

   Les événements de build vous permettent de personnaliser la génération d’un projet. Il existe trois événements de build : *pré-build*, *avant l’édition des liens* et *post-build*. Un événement de build vous permet de spécifier une action qui doit se produire à un moment précis dans le processus de build. Par exemple, vous pouvez utiliser un événement de build pour inscrire un fichier avec **regsvr32.exe** une fois le projet généré. Pour plus d’informations, consultez [Spécification d’événements de build](specifying-build-events.md).

[Résolution des problèmes de personnalisations de build](troubleshooting-build-customizations.md) peut vous aider à faire en sorte que vos étapes de build personnalisée et vos événements de build s’exécutent comme prévu.

Le format de sortie d’une étape de build personnalisée ou d’un événement de build peut aussi améliorer la maniabilité de l’outil. Pour plus d’informations, consultez [Mise en forme de la sortie d’une étape de génération personnalisée ou d’un événement de build](formatting-the-output-of-a-custom-build-step-or-build-event.md).

Pour chaque projet dans une solution, les événements de build et les étapes de génération personnalisée s’exécutent dans l’ordre suivant avec d’autres étapes de génération :

1. Événement pré-build

2. Outils de build personnalisée sur des fichiers individuels

3. MIDL

4. Compilateur de ressources

5. Compilateur C/C++

6. événement avant l'édition des liens

7. Éditeur de liens ou Générateur de bibliothèques (selon ce qui convient le mieux)

8. Outil Manifeste

9. BSCMake

10. Étape de build personnalisée sur le projet

11. Événement post-build

L’`custom build step on the project` et un `post-build event` s’exécutent de manière séquentielle une fois que tous les autres processus de build sont terminés.

## <a name="in-this-section"></a>Dans cette section

[Spécifier les outils de génération personnalisée](specifying-custom-build-tools.md)<br/>
[Spécifier les événements de build](specifying-build-events.md)<br/>
[Dépanner les personnalisations de build](troubleshooting-build-customizations.md)<br/>
[Mettre en forme la sortie d’une étape de génération personnalisée ou d’un événement de build](formatting-the-output-of-a-custom-build-step-or-build-event.md)

## <a name="see-also"></a>Voir aussi

[Projets Visual Studio-C++](creating-and-managing-visual-cpp-projects.md)<br>
[Macros courantes pour les propriétés et les commandes de build](reference/common-macros-for-build-commands-and-properties.md)
