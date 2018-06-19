---
title: _CRTDBG_MAP_ALLOC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- CRTDBG_MAP_ALLOC
- _CRTDBG_MAP_ALLOC
dev_langs:
- C++
helpviewer_keywords:
- _CRTDBG_MAP_ALLOC macro
- memory allocation, in debug builds
- CRTDBG_MAP_ALLOC macro
ms.assetid: 435242b8-caea-4063-b765-4a608200312b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 855b057223d7bdd69d7275e8c2acc0dd72bc256c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32386477"
---
# <a name="crtdbgmapalloc"></a>_CRTDBG_MAP_ALLOC
Quand l’indicateur **_CRTDBG_MAP_ALLOC** est défini dans la version Debug d’une application, la version de base des fonctions du tas est directement mappée à sa version Debug. L’indicateur est utilisé dans Crtdbg.h pour effectuer le mappage. Cet indicateur n’est disponible que quand l’indicateur [_DEBUG](../c-runtime-library/debug.md) a été défini dans l’application.  
  
 Pour plus d’informations sur l’utilisation de la version Debug ou de la version de base d’une fonction de tas, consultez [Utilisation de la version Debug ou de la version de base](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).  
  
## <a name="see-also"></a>Voir aussi  
 [Indicateurs de contrôle](../c-runtime-library/control-flags.md)