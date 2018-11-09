---
title: Indicateurs de contrôle
ms.date: 11/04/2016
f1_keywords:
- c.flags
helpviewer_keywords:
- flags, control
- heap allocation, control flags
- debug heap, control flags
ms.assetid: 8dbd24a5-0633-42d1-9771-776db338465f
ms.openlocfilehash: 45349099ed5c607468430d2f0a901c6374d88fc7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50475736"
---
# <a name="control-flags"></a>Indicateurs de contrôle

La version Debug de la bibliothèque Runtime C de Microsoft utilise les indicateurs suivants pour contrôler l’allocation de tas et le processus de création de rapports. Pour plus d’informations, consultez [Techniques de débogage CRT](/visualstudio/debugger/crt-debugging-techniques).

|Indicateur|Description|
|----------|-----------------|
|[_CRTDBG_MAP_ALLOC](../c-runtime-library/crtdbg-map-alloc.md)|Mappe les fonctions du tas de base à leurs équivalents de la version Debug|
|[_DEBUG](../c-runtime-library/debug.md)|Permet d’utiliser les versions de débogage des fonctions Runtime|
|[_crtDbgFlag](../c-runtime-library/crtdbgflag.md)|Contrôle la façon dont le gestionnaire de tas de débogage effectue le suivi des allocations|

Ces indicateurs peuvent être définis avec une option de ligne de commande /D ou avec une directive `#define`. Quand l’indicateur est défini avec `#define`, la directive doit apparaître avant l’instruction include du fichier d’en-tête pour les déclarations de routine.

## <a name="see-also"></a>Voir aussi

[Variables globales et types standard](../c-runtime-library/global-variables-and-standard-types.md)