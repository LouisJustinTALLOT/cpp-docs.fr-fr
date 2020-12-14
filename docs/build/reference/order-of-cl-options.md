---
description: 'En savoir plus sur : ordre des options CL'
title: Ordre des options CL (C++)-Visual Studio
ms.date: 12/14/2018
helpviewer_keywords:
- cl.exe compiler, setting options
ms.assetid: 300908ce-ae00-4b45-964b-e4e69ff6777b
ms.openlocfilehash: bc0290164ff40cf45d8d0a1e9f07e683e408c251
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97226413"
---
# <a name="order-of-cl-options"></a>Ordre des options CL

Les options peuvent apparaître n’importe où sur la ligne de commande CL, à l’exception de l’option/Link, qui doit se produire en dernier. Le compilateur commence par les options spécifiées dans la [variable d’environnement CL](cl-environment-variables.md) , puis lit la ligne de commande de gauche à droite, en traitant les fichiers de commandes dans l’ordre où il les rencontre. Chaque option s’applique à tous les fichiers sur la ligne de commande. Si CL rencontre des options en conflit, il utilise l’option la plus à droite.

## <a name="see-also"></a>Voir aussi

[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)
