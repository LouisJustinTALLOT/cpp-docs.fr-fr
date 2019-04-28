---
title: "Génération de fichiers d’informations de consultation : Vue d'ensemble"
ms.date: 11/04/2016
helpviewer_keywords:
- .bsc files, about .bsc files
- bsc files, about bsc files
- browse information files (.bsc)
- browse information files (.bsc), creating
ms.assetid: b5c12832-51f6-4953-8044-4264dd0fb242
ms.openlocfilehash: 4f12bd25ca3ab718a845dbb04aba3169cc6d4b19
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62272882"
---
# <a name="building-browse-information-files-overview"></a>Génération de fichiers d’informations de consultation : Vue d'ensemble

Pour créer des informations de consultation de symboles, le compilateur crée un fichier .sbr pour chaque fichier source dans votre projet, puis BSCMAKE. EXE concatène les fichiers .sbr dans un fichier .bsc.

Génération de fichiers .sbr et .bsc prend du temps, afin de Visual C++ désactive ces fonctions par défaut. Si vous souhaitez parcourir les informations actuelles, vous devez activer les options de navigation et regénérez votre projet.

Utilisez [/FR](fr-fr-create-dot-sbr-file.md) ou [/Fr](fr-fr-create-dot-sbr-file.md) pour indiquer au compilateur de créer des fichiers .sbr. Pour créer les fichiers .bsc, vous pouvez appeler [BSCMAKE](bscmake-command-line.md) à partir de la ligne de commande. En utilisant BSCMAKE à partir de la ligne de commande vous donne un contrôle plus précis sur la manipulation de fichiers d’informations. Consultez [référence BSCMAKE](bscmake-reference.md) pour plus d’informations.

> [!TIP]
>  Vous pouvez activer la génération de fichier .sbr mais laisser la génération du fichier .bsc mises hors tension. Cela vous bénéficierez vous permet également de créer un fichier .bsc fraîches rapidement par l’activation de la génération du fichier .bsc et la génération du projet.

Vous pouvez réduire le temps, mémoire et espace disque requis pour générer un fichier .bsc en réduisant la taille du fichier .bsc.

Consultez [General Property Page (Project)](general-property-page-project.md) pour plus d’informations sur la création d’un fichier de navigateur dans l’environnement de développement.

### <a name="to-create-a-smaller-bsc-file"></a>Pour créer un fichier .bsc plus petit

1. Utilisez [les options de ligne de commande BSCMAKE](bscmake-options.md) pour exclure les informations à partir du fichier d’informations de navigation.

1. Omettre les symboles locaux dans un ou plusieurs fichiers .sbr lors de la compilation ou l’assemblage.

1. Si un fichier objet ne contient pas les informations nécessaires pour votre étape en cours de débogage, omettez son fichier .sbr à partir de la commande BSCMAKE lorsque vous régénérez le fichier d’informations de consultation.

### <a name="to-combine-the-browse-information-from-several-projects-into-one-browser-file-bsc"></a>Pour combiner les informations de consultation de plusieurs projets en un fichier browser (.bsc)

1. Ne pas générer le fichier .bsc au niveau du projet ou utiliser le commutateur /n pour empêcher que les fichiers .sbr tronqués.

1. Une fois que tous les projets sont générés, exécutez BSCMAKE avec tous les fichiers .sbr en tant qu’entrée. Les caractères génériques sont acceptés. Par exemple, si vous aviez des répertoires de projet C:\X, C:\Y et C:\Z des fichiers .sbr que vous souhaitez combiner en un seul fichier .bsc, puis utilisez BSCMAKE C:\X\\\*.sbr C:\Y\\\*.sbr C:\Z\\ \*.sbr /o c:\whatever_directory\combined.bsc pour générer le fichier .bsc combiné.

## <a name="see-also"></a>Voir aussi

[Outils de génération MSVC supplémentaires](c-cpp-build-tools.md)<br/>
[Référence BSCMAKE](bscmake-reference.md)
