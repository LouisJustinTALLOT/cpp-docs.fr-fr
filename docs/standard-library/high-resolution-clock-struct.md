---
title: struct de high_resolution_clock | Microsoft Docs
ms.custom: ''
ms.date: 05/22/2018
ms.technology: cpp-standard-libraries
ms.topic: reference
f1_keywords:
- chrono/std::chrono::high_resolution_clock
dev_langs:
- C++
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0b00b20e7cea4fa24b37ad33d5536eb9844e6953
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68269121"
---
# <a name="steadyclock-struct"></a>steady_clock, struct

Représente un *high_resolution* horloge.

## <a name="syntax"></a>Syntaxe

```cpp
class high_resolution_clock
```

## <a name="members"></a>Membres

### <a name="typedefs"></a>Typedef

|Name|Description|
|----------|-----------------|
|`duration`|Un synonyme de `nanoseconds`, défini dans \<chrono >.|
|`period`|Un synonyme de `nano`, défini dans \<ratio >.|
|`rep`|Un synonyme de **long** **long**, le type qui est utilisé pour représenter le nombre de battements d’horloge dans l’instanciation contenue de `duration`.|
|`time_point`|Synonyme de `chrono::time_point<high_resolution_clock>`.|

## <a name="functions"></a>Fonctions

|||
|-|-|
|`now`|Retourne l’heure actuelle comme un `time_point` valeur.|

## <a name="constants"></a>Constantes

|Nom|Description|
|----------|-----------------|
|`is_steady`|Contient **true**. Un `high_resolution_clock` est *steady*.|
