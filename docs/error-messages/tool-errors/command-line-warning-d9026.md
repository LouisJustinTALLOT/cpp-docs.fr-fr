---
title: Avertissement de ligne de commande D9026
ms.date: 11/04/2016
f1_keywords:
- D9026
helpviewer_keywords:
- D9026
ms.assetid: 149fe5e3-5329-4be8-b871-49dfd423aaba
ms.openlocfilehash: 3fd8d442dfabaf2f03d8b564c9fdfb1537f6ff28
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50599431"
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