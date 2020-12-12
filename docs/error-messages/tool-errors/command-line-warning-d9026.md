---
description: 'En savoir plus sur : Command-Line AVERTISSEMENT D9026'
title: Avertissement de ligne de commande D9026
ms.date: 11/04/2016
f1_keywords:
- D9026
helpviewer_keywords:
- D9026
ms.assetid: 149fe5e3-5329-4be8-b871-49dfd423aaba
ms.openlocfilehash: 910471215d350f266319f5e14b7bb1a62f641028
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97115480"
---
# <a name="command-line-warning-d9026"></a>Avertissement de ligne de commande D9026

les options s’appliquent à la ligne de commande entière

Une option a été spécifiée sur une commande après la spécification d’un nom de fichier. L’option a été appliquée au fichier qui l’a précédé.

Par exemple, dans la commande

```
CL verdi.c /G5 puccini.c
```

le fichier VERDI. c est compilé à l’aide de l’option/G5, pas de la valeur par défaut/G4.

Ce comportement est différent de celui de certaines versions précédentes, qui n’appliquaient que les options spécifiées avant le nom de fichier, ce qui entraînait la compilation de VERDI. c à l’aide de/G4 et de PUCCINI. c en cours de compilation à l’aide de/G5.
