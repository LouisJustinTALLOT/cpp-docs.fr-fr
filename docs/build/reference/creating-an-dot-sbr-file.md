---
title: Création d’un. Les fichiers sbr | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- SBR files
- BSCMAKE, input files
- .sbr files
- source browser files
- local symbols in browse information
- symbols
ms.assetid: bdb4b93c-a88a-441a-84fd-01087d03be25
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ac872dd13458c3fe15971f30a72b06e5510c5bd0
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45723682"
---
# <a name="creating-an-sbr-file"></a>Création d'un fichier .sbr

Les fichiers d’entrée pour BSCMAKE sont des fichiers .sbr. Le compilateur crée un fichier .sbr pour chaque fichier objet (.obj) il est compilé. Lorsque vous générez ou mettez à jour votre fichier d’informations de consultation, tous les fichiers .sbr pour votre projet doivent être disponibles sur le disque.

Pour créer un fichier .sbr contenant toutes les informations possibles, spécifiez [/FR](../../build/reference/fr-fr-create-dot-sbr-file.md).

Pour créer un fichier .sbr qui ne contient aucun symbole local, spécifiez [/Fr](../../build/reference/fr-fr-create-dot-sbr-file.md). Si les fichiers .sbr contiennent des symboles locaux, vous pouvez néanmoins les omettre dans le fichier .bsc à l’aide de BSCMAKE [option /El](../../build/reference/bscmake-options.md)`.`

Vous pouvez créer un fichier .sbr sans effectuer une compilation complète. Par exemple, vous pouvez spécifier l’option /Zs au compilateur d’effectuer une vérification de syntaxe et de générer un fichier .sbr si vous spécifiez /FR ou /Fr.

Le processus de génération peut être plus efficace si les fichiers .sbr sont compressés au préalable pour supprimer les définitions non référencées. Le compilateur compresse automatiquement les fichiers .sbr.

## <a name="see-also"></a>Voir aussi

[Génération d’un fichier .bsc](../../build/reference/building-a-dot-bsc-file.md)