---
title: Exécution d’un programme en prétraitement | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- program execution [C++]
ms.assetid: 5ecf123a-20e5-40cd-b8d8-dd5a9fdd4b24
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e2b0571e67e7c5d24cf31dce6fce548735cad966
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45721459"
---
# <a name="executing-a-program-in-preprocessing"></a>Exécution d'un programme en prétraitement

Pour utiliser le code de sortie d’une commande lors du prétraitement, spécifiez la commande, avec tous les arguments, entre crochets ([]). Les macros sont développées avant l’exécution de la commande. NMAKE remplace la spécification de la commande avec le code de sortie de la commande, qui peut être utilisé dans une expression pour contrôler le prétraitement.

## <a name="see-also"></a>Voir aussi

[Expressions utilisées dans le prétraitement d’un makefile](../build/expressions-in-makefile-preprocessing.md)