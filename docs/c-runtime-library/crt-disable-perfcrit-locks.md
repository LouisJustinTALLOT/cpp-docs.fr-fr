---
title: _CRT_DISABLE_PERFCRIT_LOCKS | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- _CRT_DISABLE_PERFCRIT_LOCKS
- CRT_DISABLE_PERFCRIT_LOCKS
dev_langs:
- C++
helpviewer_keywords:
- CRT_DISABLE_PERFCRIT_LOCKS constant
- _CRT_DISABLE_PERFCRIT_LOCKS constant
ms.assetid: 36cc2d86-cdb1-4b2b-a03c-c0d3818e7c6f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 128403009595d85e44007d79c9110b5df530b45e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32386655"
---
# <a name="crtdisableperfcritlocks"></a>_(CRT)_DISABLE_PERFCRIT_LOCKS
Désactive le verrouillage critique pour les performances dans les opérations d’E/S.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#define _CRT_DISABLE_PERFCRIT_LOCKS  
```  
  
## <a name="remarks"></a>Notes  
 Définir ce symbole peut améliorer les performances dans les programmes monothreads utilisant des E/S en forçant toutes les opérations d’E/S à considérer que le modèle d’E/S est monothread. Pour plus d'informations, consultez [Performances des bibliothèques multithreads](../c-runtime-library/multithreaded-libraries-performance.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Constantes globales](../c-runtime-library/global-constants.md)