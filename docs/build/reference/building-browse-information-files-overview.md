---
title: "Génération de fichiers d'informations de consultation : vue d'ensemble"
ms.date: 05/06/2019
helpviewer_keywords:
- .bsc files, about .bsc files
- bsc files, about bsc files
- browse information files (.bsc)
- browse information files (.bsc), creating
ms.assetid: b5c12832-51f6-4953-8044-4264dd0fb242
ms.openlocfilehash: 94cb5865e56e12f51ef4a8598a5df3fcbe69fa0f
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078357"
---
# <a name="building-browse-information-files-overview"></a>Génération de fichiers d'informations de consultation : vue d'ensemble

> [!WARNING]
> Bien que BSCMAKE soit toujours installé avec Visual Studio, il n'est plus utilisé par l'environnement IDE. Depuis Visual Studio 2008, les informations de consultation et de symbole sont stockées automatiquement dans un fichier SQL Server .sdf, dans le dossier de solution.

Pour créer des informations de consultation pour la navigation dans les symboles, le compilateur crée un fichier. SBR pour chaque fichier source de votre projet, puis BSCMAKE. EXE concatène les fichiers. SBR dans un fichier. bsc.

La génération de fichiers. SBR et. bsc prend du temps. par conséquent, Visual Studio désactive ces fonctions par défaut. Si vous souhaitez parcourir les informations actuelles, vous devez activer les options de navigation et générer à nouveau votre projet.

Utilisez [/fr](fr-fr-create-dot-sbr-file.md) ou [/fr](fr-fr-create-dot-sbr-file.md) pour indiquer au compilateur de créer des fichiers. sbr. Pour créer des fichiers. bsc, vous pouvez appeler [BSCMAKE](bscmake-command-line.md) à partir de la ligne de commande. L’utilisation de BSCMAKE à partir de la ligne de commande vous donne un contrôle plus précis sur la manipulation des fichiers d’informations de consultation. Pour plus d’informations, consultez [référence BSCMAKE](bscmake-reference.md) .

> [!TIP]
>  Vous pouvez activer la génération de fichiers. SBR tout en laissant la génération de fichier. bsc désactivée. Cela permet d’obtenir des builds rapides, mais également de créer un fichier. bsc actualisé rapidement en activant la génération du fichier. BSC et en générant le projet.

Vous pouvez réduire le temps, la mémoire et l’espace disque requis pour générer un fichier. bsc en réduisant la taille du fichier. bsc.

Pour plus d’informations sur la création d’un fichier browser dans l’environnement de développement, consultez [général, page de propriétés (projet)](general-property-page-project.md) .

### <a name="to-create-a-smaller-bsc-file"></a>Pour créer un fichier. bsc plus petit

1. Utilisez les [options de ligne de commande BSCMAKE](bscmake-options.md) pour exclure des informations du fichier d’informations de consultation.

1. Omettez les symboles locaux dans un ou plusieurs fichiers. SBR lors de la compilation ou de l’assemblage.

1. Si un fichier objet ne contient pas les informations nécessaires à votre étape de débogage en cours, omettez son fichier. SBR dans la commande BSCMAKE lorsque vous régénérez le fichier d’informations de consultation.

### <a name="to-combine-the-browse-information-from-several-projects-into-one-browser-file-bsc"></a>Pour combiner les informations de consultation de plusieurs projets dans un seul fichier browser (. bsc)

1. Ne générez pas le fichier. bsc au niveau du projet ou utilisez le commutateur/n pour empêcher la troncation des fichiers. sbr.

1. Une fois tous les projets générés, exécutez BSCMAKE avec tous les fichiers. SBR comme entrée. Les caractères génériques sont acceptés. Par exemple, si vous aviez des répertoires de projet C:\X, C:\Y et C:\Z avec des fichiers. SBR et que vous souhaitiez les combiner tous dans un seul fichier. bsc, utilisez BSCMAKE C:\X\\\*. SBR C:\Y\\\*. SBR C:\Z\\\*. SBR/o c:\ whatever_directory \combined.bsc pour générer le fichier. bsc combiné.

## <a name="see-also"></a>Voir aussi

[Outils de build MSVC supplémentaires](c-cpp-build-tools.md)<br/>
[Référence BSCMAKE](bscmake-reference.md)
