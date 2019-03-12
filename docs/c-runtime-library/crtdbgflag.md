---
title: _crtDbgFlag
ms.date: 11/04/2016
f1_keywords:
- _crtDbgFlag
- crtDbgFlag
helpviewer_keywords:
- memory allocation, tracking flag
- crtDbgFlag constant
- _crtDbgFlag constant
- debug heap, tracking memory on
- debug heap, control flags
- enable memory allocation tracking flag
- memory, tracking on the debug heap
ms.assetid: 9e7adb47-8ab9-4e19-81d5-e2f237979973
ms.openlocfilehash: a967b436d53acab6d76fa36fdf9b13c7c24d49c3
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2019
ms.locfileid: "57746980"
---
# <a name="crtdbgflag"></a>_crtDbgFlag

L'indicateur **_crtDbgFlag** est constitué de cinq champs de bits qui contrôlent la façon dont les allocations de mémoire sur la version Debug du tas sont suivies, vérifiées, signalées et vidées. Les champs de bits de l’indicateur sont définis à l’aide de la fonction [_CrtSetDbgFlag](../c-runtime-library/reference/crtsetdbgflag.md). Cet indicateur et ses champs de bits sont déclarés dans Crtdbg.h. Cet indicateur n’est disponible que quand l’indicateur [_DEBUG](../c-runtime-library/debug.md) a été défini dans l’application.

Pour plus d’informations sur l’utilisation de cet indicateur avec d’autres fonctions de débogage, consultez [Fonctions de création de rapports sur l’état du tas](/visualstudio/debugger/crt-debug-heap-details).

## <a name="see-also"></a>Voir aussi

[Indicateurs de contrôle](../c-runtime-library/control-flags.md)
