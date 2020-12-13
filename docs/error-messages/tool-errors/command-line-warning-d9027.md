---
description: 'En savoir plus sur : Command-Line AVERTISSEMENT D9027'
title: Avertissement de ligne de commande D9027
ms.date: 11/04/2016
f1_keywords:
- D9027
helpviewer_keywords:
- D9027
ms.assetid: 2a29edc5-5649-48f2-9058-2057c747284c
ms.openlocfilehash: 8c17750f3310072f8f69c77587a1c17fc9377e79
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97136108"
---
# <a name="command-line-warning-d9027"></a>Avertissement de ligne de commande D9027

fichier source' \<filename> 'ignoré

CL.exe ignoré le fichier source d’entrée.

Cet avertissement peut être provoqué par un espace entre l’option/FO et un nom de fichier de sortie sur une ligne de commande avec l’option/c. Par exemple :

```
cl /c /Fo output.obj input.c
```

Étant donné qu’il y a un espace entre/FO et `output.obj` , CL.exe prend `output.obj` comme nom du fichier d’entrée. Pour résoudre le problème, supprimez l’espace :

```
cl /c /Fooutput.obj input.c
```
