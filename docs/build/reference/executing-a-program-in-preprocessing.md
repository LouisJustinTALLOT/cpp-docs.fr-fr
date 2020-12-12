---
description: 'En savoir plus sur : exécution d’un programme en prétraitement'
title: Exécution d'un programme en prétraitement
ms.date: 11/04/2016
helpviewer_keywords:
- program execution [C++]
ms.assetid: 5ecf123a-20e5-40cd-b8d8-dd5a9fdd4b24
ms.openlocfilehash: 72743fe1b75e170ce1aa7ea04dd5a0c70440de59
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97192367"
---
# <a name="executing-a-program-in-preprocessing"></a>Exécution d'un programme en prétraitement

Pour utiliser le code de sortie d’une commande pendant le prétraitement, spécifiez la commande, avec n’importe quel argument, entre crochets ([]). Toutes les macros sont développées avant l’exécution de la commande. NMAKE remplace la spécification de commande par le code de sortie de la commande, qui peut être utilisé dans une expression pour contrôler le prétraitement.

## <a name="see-also"></a>Voir aussi

[Expressions dans le prétraitement d’un Makefile](expressions-in-makefile-preprocessing.md)
