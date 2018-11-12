---
title: _CRTDBG_MAP_ALLOC
ms.date: 11/04/2016
f1_keywords:
- CRTDBG_MAP_ALLOC
- _CRTDBG_MAP_ALLOC
helpviewer_keywords:
- _CRTDBG_MAP_ALLOC macro
- memory allocation, in debug builds
- CRTDBG_MAP_ALLOC macro
ms.assetid: 435242b8-caea-4063-b765-4a608200312b
ms.openlocfilehash: a6b6ca5d3e6fdc1bac43d082b0d7df5a87830050
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50453437"
---
# <a name="crtdbgmapalloc"></a>_CRTDBG_MAP_ALLOC

Quand l’indicateur **_CRTDBG_MAP_ALLOC** est défini dans la version Debug d’une application, la version de base des fonctions du tas est directement mappée à sa version Debug. L’indicateur est utilisé dans Crtdbg.h pour effectuer le mappage. Cet indicateur n’est disponible que quand l’indicateur [_DEBUG](../c-runtime-library/debug.md) a été défini dans l’application.

Pour plus d’informations sur l’utilisation de la version Debug ou de la version de base d’une fonction de tas, consultez [Utilisation de la version Debug ou de la version de base](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="see-also"></a>Voir aussi

[Indicateurs de contrôle](../c-runtime-library/control-flags.md)