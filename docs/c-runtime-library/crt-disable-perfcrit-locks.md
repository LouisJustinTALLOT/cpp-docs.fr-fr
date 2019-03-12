---
title: _(CRT)_DISABLE_PERFCRIT_LOCKS
ms.date: 11/04/2016
f1_keywords:
- _CRT_DISABLE_PERFCRIT_LOCKS
- CRT_DISABLE_PERFCRIT_LOCKS
helpviewer_keywords:
- CRT_DISABLE_PERFCRIT_LOCKS constant
- _CRT_DISABLE_PERFCRIT_LOCKS constant
ms.assetid: 36cc2d86-cdb1-4b2b-a03c-c0d3818e7c6f
ms.openlocfilehash: b6f4d8dee5577e88aa59af9bff017aab0c7eef89
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2019
ms.locfileid: "57740256"
---
# <a name="crtdisableperfcritlocks"></a>_(CRT)_DISABLE_PERFCRIT_LOCKS

Désactive le verrouillage critique pour les performances dans les opérations d’E/S.

## <a name="syntax"></a>Syntaxe

```
#define _CRT_DISABLE_PERFCRIT_LOCKS
```

## <a name="remarks"></a>Remarques

Définir ce symbole peut améliorer les performances dans les programmes monothreads utilisant des E/S en forçant toutes les opérations d’E/S à considérer que le modèle d’E/S est monothread. Pour plus d'informations, consultez [Performances des bibliothèques multithreads](../c-runtime-library/multithreaded-libraries-performance.md).

## <a name="see-also"></a>Voir aussi

[Constantes globales](../c-runtime-library/global-constants.md)
