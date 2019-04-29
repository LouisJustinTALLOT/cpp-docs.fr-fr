---
title: Exécution d'un programme en prétraitement
ms.date: 11/04/2016
helpviewer_keywords:
- program execution [C++]
ms.assetid: 5ecf123a-20e5-40cd-b8d8-dd5a9fdd4b24
ms.openlocfilehash: 564e4aebb3a0502f18550fb9d323e8b30f1303f6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62271591"
---
# <a name="executing-a-program-in-preprocessing"></a>Exécution d'un programme en prétraitement

Pour utiliser le code de sortie d’une commande lors du prétraitement, spécifiez la commande, avec tous les arguments, entre crochets ([]). Les macros sont développées avant l’exécution de la commande. NMAKE remplace la spécification de la commande avec le code de sortie de la commande, qui peut être utilisé dans une expression pour contrôler le prétraitement.

## <a name="see-also"></a>Voir aussi

[Expressions utilisées dans le prétraitement d’un makefile](expressions-in-makefile-preprocessing.md)
