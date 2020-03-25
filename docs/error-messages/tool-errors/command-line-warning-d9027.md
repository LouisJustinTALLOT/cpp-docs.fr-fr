---
title: Avertissement de ligne de commande D9027
ms.date: 11/04/2016
f1_keywords:
- D9027
helpviewer_keywords:
- D9027
ms.assetid: 2a29edc5-5649-48f2-9058-2057c747284c
ms.openlocfilehash: 46ed5750bd1f315f20658ace9b83fac532fbbabb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80196675"
---
# <a name="command-line-warning-d9027"></a>Avertissement de ligne de commande D9027

le fichier source'\<filename > 'est ignoré

CL. exe a ignoré le fichier source d’entrée.

Cet avertissement peut être provoqué par un espace entre l’option/FO et un nom de fichier de sortie sur une ligne de commande avec l’option/c. Par exemple :

```
cl /c /Fo output.obj input.c
```

Étant donné qu’il y a un espace entre/FO et `output.obj`, CL. exe prend `output.obj` comme nom du fichier d’entrée. Pour résoudre le problème, supprimez l’espace :

```
cl /c /Fooutput.obj input.c
```
