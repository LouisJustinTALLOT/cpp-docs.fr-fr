---
title: Avertissement de ligne de commande D9026 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- D9026
dev_langs:
- C++
helpviewer_keywords:
- D9026
ms.assetid: 149fe5e3-5329-4be8-b871-49dfd423aaba
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 07be633e56dad6c8f0b304a3c88c1b9919221d4a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46079152"
---
# <a name="command-line-warning-d9026"></a>Avertissement de ligne de commande D9026

options s’appliquent à toute ligne de commande

Une option a été spécifiée sur une commande après qu’un nom de fichier a été spécifié. L’option a été appliquée au fichier qui l’ont précédé.

Par exemple, dans la commande

```
CL verdi.c /G5 puccini.c
```

le fichier VERDI.c qui est compilé à l’aide de l’option/G5, pas la valeur par défaut/G4.

Ce comportement est différent de celui des versions précédentes, ce qui est appliqué uniquement les options spécifiées avant le nom de fichier, ce qui entraîne de VERDI.c par qui est compilé à l’aide de/G4 et Puccini.c par en cours de compilation/G5.