---
title: Ordre des options CL (C++)-Visual Studio
ms.date: 12/14/2018
helpviewer_keywords:
- cl.exe compiler, setting options
ms.assetid: 300908ce-ae00-4b45-964b-e4e69ff6777b
ms.openlocfilehash: 6c57a68dd15d82a9d6a01bfe145374bda6eb1510
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439202"
---
# <a name="order-of-cl-options"></a>Ordre des options CL

Les options peuvent apparaître n’importe où sur la ligne de commande CL, à l’exception de l’option/Link, qui doit se produire en dernier. Le compilateur commence par les options spécifiées dans la [variable d’environnement CL](cl-environment-variables.md) , puis lit la ligne de commande de gauche à droite, en traitant les fichiers de commandes dans l’ordre où il les rencontre. Chaque option s’applique à tous les fichiers sur la ligne de commande. Si CL rencontre des options en conflit, il utilise l’option la plus à droite.

## <a name="see-also"></a>Voir aussi

[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
