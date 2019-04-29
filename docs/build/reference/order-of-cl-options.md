---
title: Ordre des Options CL (C++) - Visual Studio
ms.date: 12/14/2018
f1_keywords:
- cl
helpviewer_keywords:
- cl.exe compiler, setting options
ms.assetid: 300908ce-ae00-4b45-964b-e4e69ff6777b
ms.openlocfilehash: 93907265bed8141b5c63edd5e75d632e060351fe
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320940"
---
# <a name="order-of-cl-options"></a>Ordre des options CL

Options peuvent apparaître n’importe où sur la ligne de commande CL, à l’exception de l’option /link, qui doit figurer en dernier. Le compilateur commence par les options spécifiées dans le [variable d’environnement CL](cl-environment-variables.md) , puis lit la ligne de commande de gauche à droite : traitement des fichiers de commandes dans l’ordre où il les trouve. Chaque option s’applique à tous les fichiers sur la ligne de commande. Si CL rencontre des options en conflit, elle utilise l’option la plus à droite.

## <a name="see-also"></a>Voir aussi

[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
