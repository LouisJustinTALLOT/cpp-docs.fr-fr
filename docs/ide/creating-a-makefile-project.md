---
title: Création d’un projet Makefile | Microsoft Docs
ms.custom: ''
ms.date: 02/28/2018
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.appwiz.makefile.project
dev_langs:
- C++
helpviewer_keywords:
- Makefile projects, creating
- project files [C++], Makefile projects
ms.assetid: dd077af3-97a8-48fb-baaa-cf7e07ddef61
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dc854f96f1c41baf28a5af4ca1f253e47d9a8914
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "33336776"
---
# <a name="creating-a-makefile-project"></a>Création d'un projet Makefile

Si vous disposez d’un projet de code source existant que vous générez à partir de la ligne de commande à l’aide d’un makefile, l’environnement de développement Visual Studio vous propose plusieurs méthodes pour le transformer en projet capable de tirer pleinement parti des fonctionnalités de l’IDE de Visual Studio. Cet article décrit comment créer un projet Makefile dans Visual Studio qui utilise votre makefile existant pour générer votre code dans l’IDE. Vous pouvez également utiliser l’Assistant **Créer un projet à partir de fichiers de code existants** pour créer un projet MSBuild natif à partir de votre code source. Pour plus d’informations, consultez [Guide pratique pour créer un projet C++ à partir d’un code existant](how-to-create-a-cpp-project-from-existing-code.md). À compter de Visual Studio 2017, vous pouvez également recourir à la fonctionnalité **Ouvrir un dossier**. Celle-ci peut utiliser plusieurs systèmes de génération existants comme s’il s’agissait de projets Visual Studio natifs. Pour plus d’informations, consultez [Ouvrir un dossier dans Visual C++](non-msbuild-projects.md).

Pour ouvrir et générer votre code source à l’aide de votre makefile existant dans Visual Studio, commencez par créer un projet en sélectionnant le modèle de projet Makefile. Un Assistant vous aide à spécifier les commandes et l’environnement utilisé par votre makefile. Vous pouvez ensuite utiliser ce projet pour générer votre code dans l’environnement de développement Visual Studio.

Par défaut, le projet makefile n’affiche aucun fichier dans l’Explorateur de solutions. Le projet makefile spécifie les paramètres de génération qui sont reflétés dans la page de propriétés du projet.

Le fichier de sortie que vous spécifiez dans le projet n'a pas d'incidence sur le nom que le script génère ; il déclare uniquement une intention. Votre makefile contrôle toujours le processus de génération et spécifie les cibles de génération.

## <a name="to-create-a-makefile-project"></a>Pour créer un projet Makefile

1. Suivez les instructions de la rubrique d’aide [Création d’un projet à l’aide d’un Assistant Application Visual C++](../ide/creating-desktop-projects-by-using-application-wizards.md).

1. Dans la boîte de dialogue **Nouveau projet**, développez **Visual C++** > **Général**, puis sélectionnez **Projet Makefile** dans le volet Modèles pour ouvrir l’Assistant Projet.

1. Dans la page [Paramètres de l’application](../ide/application-settings-makefile-project-wizard.md), indiquez les informations relatives à la ligne de commande, à la sortie, au nettoyage et à la regénération pour les builds Debug et Retail.

1. Cliquez sur **Terminer** pour fermer l’Assistant et ouvrir le projet que vous venez de créer dans **l’Explorateur de solutions**.

Vous pouvez afficher et modifier les propriétés du projet dans sa page de propriétés. Pour obtenir des informations sur l’affichage de la page de propriétés, consultez [Définition des propriétés de projets Visual C++](../ide/working-with-project-properties.md).

## <a name="see-also"></a>Voir aussi

[Projet Makefile (Assistant)](../ide/makefile-project-wizard.md)<br/>
[Caractères spéciaux dans un makefile](../build/special-characters-in-a-makefile.md)<br/>
[Contenu d’un makefile](../build/contents-of-a-makefile.md)<br/>
