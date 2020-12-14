---
description: 'En savoir plus sur : _CRT_DISABLE_PERFCRIT_LOCKS'
title: _(CRT)_DISABLE_PERFCRIT_LOCKS
ms.date: 11/04/2016
f1_keywords:
- _CRT_DISABLE_PERFCRIT_LOCKS
- CRT_DISABLE_PERFCRIT_LOCKS
helpviewer_keywords:
- CRT_DISABLE_PERFCRIT_LOCKS constant
- _CRT_DISABLE_PERFCRIT_LOCKS constant
ms.assetid: 36cc2d86-cdb1-4b2b-a03c-c0d3818e7c6f
ms.openlocfilehash: b96e29fad635ac9e7f3d622ace3c43bb26c8805a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97195682"
---
# <a name="_crt_disable_perfcrit_locks"></a>_(CRT)_DISABLE_PERFCRIT_LOCKS

Désactive le verrouillage critique pour les performances dans les opérations d’E/S.

## <a name="syntax"></a>Syntaxe

```
#define _CRT_DISABLE_PERFCRIT_LOCKS
```

## <a name="remarks"></a>Notes

Définir ce symbole peut améliorer les performances dans les programmes monothreads utilisant des E/S en forçant toutes les opérations d’E/S à considérer que le modèle d’E/S est monothread. Pour plus d'informations, consultez [Performances des bibliothèques multithreads](../c-runtime-library/multithreaded-libraries-performance.md).

## <a name="see-also"></a>Voir aussi

[Constantes globales](../c-runtime-library/global-constants.md)
