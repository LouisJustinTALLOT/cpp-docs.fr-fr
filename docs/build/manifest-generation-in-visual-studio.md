---
title: Génération de manifeste dans Visual Studio
ms.date: 11/04/2016
helpviewer_keywords:
- manifests [C++]
ms.assetid: 0af60aa9-d223-42cd-8426-b3fc543a2a81
ms.openlocfilehash: f055e3d16dfc0ea4320883210458ae10daebdc45
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273356"
---
# <a name="manifest-generation-in-visual-studio"></a>Génération de manifeste dans Visual Studio

Génération d’un fichier manifeste pour un projet particulier peut être contrôlée dans le projet **Pages de propriétés** boîte de dialogue. Sur le **propriétés de Configuration** , cliquez sur **l’éditeur de liens**, puis **le fichier manifeste**, puis **génération d’un manifeste**. Par défaut, les propriétés du projet de nouveaux projets sont définies pour générer un fichier manifest. Toutefois, il est possible de désactiver la génération du manifeste pour un projet à l’aide de la **génération d’un manifeste** propriété du projet. Lorsque cette propriété a la valeur **Oui**, le manifeste de ce projet est généré. Sinon, l’éditeur de liens ignore les informations de l’assembly lors de la résolution des dépendances du code d’application et ne génère pas le manifeste.

Le système de génération dans Visual Studio permet le manifeste incorporé dans le fichier d’application binaire finale, ou généré sous la forme d’un fichier externe. Ce comportement est contrôlé par le **incorporer le manifeste** option dans le **propriétés du projet** boîte de dialogue. Pour définir cette propriété, ouvrez le **outil manifeste** nœud, puis sélectionnez **d’entrée et sortie**. Si le manifeste n’est pas incorporé, il est généré sous la forme d’un fichier externe et enregistré dans le même répertoire que le fichier binaire final. Si le manifeste est incorporé, Visual Studio incorpore les derniers manifestes à l’aide de la procédure suivante :

1. Une fois le code source est compilé dans des fichiers de l’objet, l’éditeur de liens collecte des informations de l’assembly dépendant. Lors de la liaison du fichier binaire final, l’éditeur de liens génère un manifeste intermédiaire qui sera utilisé ultérieurement pour générer le manifeste final.

1. Une fois que le manifeste intermédiaire et la liaison sont terminées, l’outil manifeste sera exécuté pour fusionner un manifeste final et les enregistrer dans un fichier externe.

1. Le projet de système de génération, puis détecte si le manifeste généré par l’outil manifeste contient des informations différentes de celles du manifeste déjà incorporé dans le fichier binaire.

1. Si le manifeste incorporé dans le fichier binaire est différent de celui généré par l’outil manifeste, ou le fichier binaire ne contient-elle pas de manifeste incorporé, Visual Studio appelle l’éditeur de liens une fois de plus pour incorporer le fichier manifest externe dans le fichier binaire comme un ressource.

1. Si le manifeste incorporé dans le fichier binaire est le même que le manifeste généré par l’outil manifeste, la génération continue pour les étapes de build.

Le manifeste est incorporé dans le fichier binaire final en tant que texte ressource et elle peut être affichée en ouvrant le fichier binaire final en tant que fichier dans Visual Studio. Pour vous assurer que le manifeste de pointe aux bonnes bibliothèques, suivez les étapes décrites dans [fonctionnement des dépendances d’une Application Visual C++](../windows/understanding-the-dependencies-of-a-visual-cpp-application.md) ou suivre les suggestions décrites dans le [dépannage](troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md) section.

## <a name="see-also"></a>Voir aussi

[Présentation de la génération de manifeste pour les programmes C/C++](understanding-manifest-generation-for-c-cpp-programs.md)
