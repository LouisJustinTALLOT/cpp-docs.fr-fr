---
title: Avertissement de ligne de commande D9027 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- D9027
dev_langs:
- C++
helpviewer_keywords:
- D9027
ms.assetid: 2a29edc5-5649-48f2-9058-2057c747284c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 105ebbf62027ac3d9377c513c4f7c59e261b983d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46112523"
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