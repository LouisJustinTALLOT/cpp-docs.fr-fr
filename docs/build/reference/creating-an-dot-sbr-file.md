---
title: Création d'un fichier .sbr
ms.date: 11/04/2016
helpviewer_keywords:
- SBR files
- BSCMAKE, input files
- .sbr files
- source browser files
- local symbols in browse information
- symbols
ms.assetid: bdb4b93c-a88a-441a-84fd-01087d03be25
ms.openlocfilehash: 6a2e685d33b108ce542fdc6e3e0565cc37299c1c
ms.sourcegitcommit: 06fc71a46e3c4f6202a1c0bc604aa40611f50d36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58508739"
---
# <a name="creating-an-sbr-file"></a>Création d'un fichier .sbr

> [!WARNING]
> Bien que BSCMAKE soit toujours installé avec Visual Studio, il n'est plus utilisé par l'environnement IDE. Depuis Visual Studio 2008, les informations de consultation et de symbole sont stockées automatiquement dans un fichier SQL Server .sdf, dans le dossier de solution.

Les fichiers d’entrée pour BSCMAKE sont des fichiers .sbr. Le compilateur crée un fichier .sbr pour chaque fichier objet (.obj) il est compilé. Lorsque vous générez ou mettez à jour votre fichier d’informations de consultation, tous les fichiers .sbr pour votre projet doivent être disponibles sur le disque.

Pour créer un fichier .sbr contenant toutes les informations possibles, spécifiez [/FR](fr-fr-create-dot-sbr-file.md).

Pour créer un fichier .sbr qui ne contient aucun symbole local, spécifiez [/Fr](fr-fr-create-dot-sbr-file.md). Si les fichiers .sbr contiennent des symboles locaux, vous pouvez néanmoins les omettre dans le fichier .bsc à l’aide de BSCMAKE [option /El](bscmake-options.md)`.`

Vous pouvez créer un fichier .sbr sans effectuer une compilation complète. Par exemple, vous pouvez spécifier l’option /Zs au compilateur d’effectuer une vérification de syntaxe et de générer un fichier .sbr si vous spécifiez /FR ou /Fr.

Le processus de génération peut être plus efficace si les fichiers .sbr sont compressés au préalable pour supprimer les définitions non référencées. Le compilateur compresse automatiquement les fichiers .sbr.

## <a name="see-also"></a>Voir aussi

[Génération d’un fichier .bsc](building-a-dot-bsc-file.md)
