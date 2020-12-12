---
description: 'En savoir plus sur : création d’un. Fichier SBR'
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
ms.openlocfilehash: 7f3e056418fe1716dc0130330b09c369e9bdceff
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97196917"
---
# <a name="creating-an-sbr-file"></a>Création d'un fichier .sbr

> [!WARNING]
> Bien que BSCMAKE soit toujours installé avec Visual Studio, il n'est plus utilisé par l'environnement IDE. Depuis Visual Studio 2008, les informations de consultation et de symbole sont stockées automatiquement dans un fichier SQL Server .sdf, dans le dossier de solution.

Les fichiers d’entrée pour BSCMAKE sont des fichiers. sbr. Le compilateur crée un fichier. SBR pour chaque fichier objet (. obj) qui est compilé. Lorsque vous générez ou mettez à jour votre fichier d’informations de consultation, tous les fichiers. sbr de votre projet doivent être disponibles sur le disque.

Pour créer un fichier. SBR contenant toutes les informations possibles, spécifiez [/fr](fr-fr-create-dot-sbr-file.md).

Pour créer un fichier. sbr qui ne contient pas de symboles locaux, spécifiez [/fr](fr-fr-create-dot-sbr-file.md). Si les fichiers. sbr contiennent des symboles locaux, vous pouvez toujours les omettre dans le fichier. bsc en utilisant l' [option/El](bscmake-options.md) de BSCMAKE`.`

Vous pouvez créer un fichier. SBR sans effectuer de compilation complète. Par exemple, vous pouvez spécifier l’option/ZS pour que le compilateur effectue une vérification de la syntaxe tout en générant un fichier. SBR si vous spécifiez/FR ou/fr.

Le processus de génération peut être plus efficace si les fichiers. SBR sont d’abord empaquetés pour supprimer les définitions non référencées. Le compilateur compresse automatiquement les fichiers. sbr.

## <a name="see-also"></a>Voir aussi

[Génération d’un. Fichier BSC](building-a-dot-bsc-file.md)
