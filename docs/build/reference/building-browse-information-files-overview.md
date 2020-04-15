---
title: "Génération de fichiers d'informations de consultation : vue d'ensemble"
ms.date: 05/06/2019
helpviewer_keywords:
- .bsc files, about .bsc files
- bsc files, about bsc files
- browse information files (.bsc)
- browse information files (.bsc), creating
ms.assetid: b5c12832-51f6-4953-8044-4264dd0fb242
ms.openlocfilehash: ffacb7aaf9ac1f7ad6fc4cf12ab479099dc57725
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320668"
---
# <a name="building-browse-information-files-overview"></a>Génération de fichiers d'informations de consultation : vue d'ensemble

> [!WARNING]
> Bien que BSCMAKE soit toujours installé avec Visual Studio, il n'est plus utilisé par l'environnement IDE. Depuis Visual Studio 2008, les informations de consultation et de symbole sont stockées automatiquement dans un fichier SQL Server .sdf, dans le dossier de solution.

Pour créer des informations de navigation pour la navigation des symboles, le compilateur crée un fichier .sbr pour chaque fichier source dans votre projet, puis BSCMAKE. EXE concatenates les fichiers .sbr dans un fichier .bsc.

Génération .sbr et .bsc fichiers prend du temps, donc Visual Studio éteint ces fonctions par défaut. Si vous souhaitez parcourir les informations actuelles, vous devez activer les options de navigation et construire à nouveau votre projet.

Utilisez [/FR](fr-fr-create-dot-sbr-file.md) ou [/Fr](fr-fr-create-dot-sbr-file.md) pour dire au compilateur de créer des fichiers .sbr. Pour créer des fichiers .bsc, vous pouvez appeler [BSCMAKE](bscmake-command-line.md) à partir de la ligne de commande. L’utilisation de BSCMAKE à partir de la ligne de commande vous donne un contrôle plus précis sur la manipulation des fichiers d’information de navigation. Voir [BSCMAKE Référence](bscmake-reference.md) pour plus d’informations.

> [!TIP]
> Vous pouvez activer la génération de fichiers .sbr, mais laisser la génération de fichiers .bsc désactivée. Cela fournit des constructions rapides, mais vous permet également de créer un fichier nouveau .bsc rapidement en allumant la génération de fichiers .bsc et la construction du projet.

Vous pouvez réduire le temps, la mémoire et l’espace disque nécessaire pour construire un fichier .bsc en réduisant la taille du fichier .bsc.

Consultez [la Page de propriété générale (Projet)](general-property-page-project.md) pour obtenir des informations sur la façon de créer un fichier de navigateur dans l’environnement de développement.

### <a name="to-create-a-smaller-bsc-file"></a>Pour créer un fichier .bsc plus petit

1. Utilisez les [options de ligne de commande BSCMAKE](bscmake-options.md) pour exclure les informations du fichier d’information de navigation.

1. Omettre les symboles locaux dans un ou plusieurs fichiers .sbr lors de la compilation ou de l’assemblage.

1. Si un fichier d’objets ne contient pas d’informations nécessaires pour votre étape actuelle de débogage, omettez son fichier .sbr de la commande BSCMAKE lorsque vous reconstruisez le fichier d’information de navigation.

### <a name="to-combine-the-browse-information-from-several-projects-into-one-browser-file-bsc"></a>Pour combiner les informations de navigation de plusieurs projets dans un fichier de navigateur (.bsc)

1. Soit ne construisez pas le fichier .bsc au niveau du projet ou utilisez le commutateur /n pour empêcher les fichiers .sbr d’être tronqués.

1. Après que tous les projets sont construits, exécuter BSCMAKE avec tous les fichiers .sbr comme entrée. Les Wildcards sont acceptés. Par exemple, si vous aviez des répertoires de projetS C: 'X, C:'Y, et C:'Z avec des fichiers .sbr en eux et\\\*vous vouliez les\\\*combiner tous en un fichier .bsc, puis utilisez BSCMAKE C:X .sbr C: 'Y .sbr C:'Z\\\*.sbr /o c:'whatever_directory’combiné.bsc pour construire le fichier combiné .bsc.

## <a name="see-also"></a>Voir aussi

[Outils de construction MSVC supplémentaires](c-cpp-build-tools.md)<br/>
[Référence BSCMAKE](bscmake-reference.md)
