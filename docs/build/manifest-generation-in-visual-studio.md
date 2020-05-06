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

La génération d’un fichier manifeste pour un projet particulier peut être contrôlée dans la boîte de dialogue **pages de propriétés** du projet. Dans l’onglet **Propriétés de configuration** , cliquez sur éditeur de **liens**, puis sur **fichier manifeste**, puis sur **générer le manifeste**. Par défaut, les propriétés de projet des nouveaux projets sont définies pour générer un fichier manifeste. Toutefois, il est possible de désactiver la génération du manifeste pour un projet à l’aide de la propriété **générer le manifeste** du projet. Quand cette propriété a la valeur **Oui**, le manifeste de ce projet est généré. Dans le cas contraire, l’éditeur de liens ignore les informations d’assembly lors de la résolution des dépendances du code de l’application et ne génère pas le manifeste.

Le système de génération de Visual Studio permet d’incorporer le manifeste dans le fichier d’application binaire final ou de le générer sous la forme d’un fichier externe. Ce comportement est contrôlé par l’option **incorporer le manifeste** dans la boîte de dialogue **Propriétés du projet** . Pour définir cette propriété, ouvrez le nœud **outil manifeste** , puis sélectionnez **entrée et sortie**. Si le manifeste n’est pas incorporé, il est généré en tant que fichier externe et enregistré dans le même répertoire que le fichier binaire final. Si le manifeste est incorporé, Visual Studio incorpore les manifestes finaux à l’aide du processus suivant :

1. Une fois que le code source est compilé en fichiers objets, l’éditeur de liens collecte les informations d’assembly dépendantes. Lors de la liaison du fichier binaire final, l’éditeur de liens génère un manifeste intermédiaire qui est utilisé ultérieurement pour générer le manifeste final.

1. Une fois le manifeste intermédiaire et la liaison terminés, l’outil manifeste est exécuté pour fusionner un manifeste final et l’enregistrer en tant que fichier externe.

1. Le système de génération de projet détecte ensuite si le manifeste généré par l’outil manifeste contient des informations différentes de celles du manifeste déjà incorporé dans le fichier binaire.

1. Si le manifeste incorporé dans le fichier binaire est différent du manifeste généré par l’outil manifeste ou si le binaire ne contient pas de manifeste incorporé, Visual Studio appellera l’éditeur de liens une fois de plus pour incorporer le fichier manifeste externe dans le fichier binaire en tant que ressource.

1. Si le manifeste incorporé dans le fichier binaire est le même que le manifeste généré par l’outil manifeste, la génération passe aux étapes de génération suivantes.

Le manifeste est incorporé dans le fichier binaire final comme ressource texte et il peut être affiché en ouvrant le fichier binaire final sous la forme d’un fichier dans Visual Studio. Pour vous assurer que le manifeste pointe vers les bibliothèques appropriées, suivez les étapes décrites dans [fonctionnement des dépendances d’une Application Visual C++](../windows/understanding-the-dependencies-of-a-visual-cpp-application.md) ou suivez les suggestions décrites dans la section [résolution des problèmes](troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md) .

## <a name="see-also"></a>Voir aussi

[Fonctionnement de la génération de manifestes pour les programmes C/C++](understanding-manifest-generation-for-c-cpp-programs.md)
