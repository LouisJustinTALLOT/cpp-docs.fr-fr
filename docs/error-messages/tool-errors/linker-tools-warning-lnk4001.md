---
title: Avertissement des outils Éditeur de liens LNK4001
ms.date: 11/04/2016
f1_keywords:
- LNK4001
helpviewer_keywords:
- LNK4001
ms.assetid: 0a8b1c3a-64ce-4311-b7c0-065995059246
ms.openlocfilehash: 75ca9ec92bbba1c15efc11a731b3894ea03e33dd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62298787"
---
# <a name="linker-tools-warning-lnk4001"></a>Avertissement des outils Éditeur de liens LNK4001

Aucun fichier objet spécifié ; bibliothèques utilisées

L’éditeur de liens a été passé à un ou plusieurs fichiers .lib, mais aucun fichier .obj.

Étant donné que l’éditeur de liens n’est pas en mesure d’accéder aux informations dans un fichier .lib qu’il est capable d’accéder à un fichier .obj, cet avertissement indique que vous devrez spécifier explicitement d’autres options de l’éditeur de liens. Par exemple, vous devrez peut-être spécifier le [/MACHINE](../../build/reference/machine-specify-target-platform.md), [/OUT](../../build/reference/out-output-file-name.md), ou [/Entry](../../build/reference/entry-entry-point-symbol.md) options.