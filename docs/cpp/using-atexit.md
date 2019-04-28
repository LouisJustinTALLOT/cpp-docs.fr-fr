---
title: Utilisation d'atexit
ms.date: 11/04/2016
f1_keywords:
- atexit
helpviewer_keywords:
- atexit function
ms.assetid: d28fda17-c3d4-4af6-ba44-f44886bbb237
ms.openlocfilehash: 06baba59b5765f853f081b34d73be28a187730ba
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62257996"
---
# <a name="using-atexit"></a>Utilisation d'atexit

Avec le [atexit](../c-runtime-library/reference/atexit.md) (fonction), vous pouvez spécifier une fonction de sortie de traitement qui s’exécute avant l’arrêt du programme. Aucun objet statique global initialisé avant l’appel à **atexit** sont détruits avant l’exécution de la fonction de sortie de traitement.

## <a name="see-also"></a>Voir aussi

[Considérations supplémentaires sur la terminaison](../cpp/additional-termination-considerations.md)