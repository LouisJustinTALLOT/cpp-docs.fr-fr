---
description: En savoir plus sur les indicateurs de contrôle
title: Indicateurs de contrôle
ms.date: 11/04/2016
f1_keywords:
- c.flags
helpviewer_keywords:
- flags, control
- heap allocation, control flags
- debug heap, control flags
ms.assetid: 8dbd24a5-0633-42d1-9771-776db338465f
ms.openlocfilehash: 6b49bfa49e2e231a64af8d88739778964ce8ed21
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97195734"
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
