---
title: Avertissement de ligne de commande D9027
ms.date: 11/04/2016
f1_keywords:
- D9027
helpviewer_keywords:
- D9027
ms.assetid: 2a29edc5-5649-48f2-9058-2057c747284c
ms.openlocfilehash: f89e7416efe7a0069ee2dae8df921933bbe76bcf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62214114"
---
# <a name="command-line-warning-d9027"></a>Avertissement de ligne de commande D9027

fichier source '\<nom_fichier >' ignoré

CL.exe a ignoré le fichier source d’entrée.

Cet avertissement peut être provoqué par un espace entre l’option /Fo et un nom de fichier de sortie sur une ligne de commande avec l’option /c. Exemple :

```
cl /c /Fo output.obj input.c
```

Car il existe un espace entre /Fo et `output.obj`, CL.exe prend `output.obj` en tant que le nom du fichier d’entrée. Pour corriger le problème, supprimez l’espace :

```
cl /c /Fooutput.obj input.c
```