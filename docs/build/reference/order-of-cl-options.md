---
title: Ordre des options CL
ms.date: 11/04/2016
f1_keywords:
- cl
helpviewer_keywords:
- cl.exe compiler, setting options
ms.assetid: 300908ce-ae00-4b45-964b-e4e69ff6777b
ms.openlocfilehash: d87e3214d4829f81258acd00abebced34d7d969d
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57423688"
---
# <a name="order-of-cl-options"></a>Ordre des options CL

Options peuvent apparaître n’importe où sur la ligne de commande CL, à l’exception de l’option /link, qui doit figurer en dernier. Le compilateur commence par les options spécifiées dans le [variable d’environnement CL](../../build/reference/cl-environment-variables.md) , puis lit la ligne de commande de gauche à droite : traitement des fichiers de commandes dans l’ordre où il les trouve. Chaque option s’applique à tous les fichiers sur la ligne de commande. Si CL rencontre des options en conflit, elle utilise l’option la plus à droite.

## <a name="see-also"></a>Voir aussi

[Syntaxe de la ligne de commande du compilateur](../../build/reference/compiler-command-line-syntax.md)
