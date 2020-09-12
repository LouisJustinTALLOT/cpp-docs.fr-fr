---
title: struct high_resolution_clock | Microsoft Docs
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
ms.openlocfilehash: 341cae04742d72fdcc7483e74977bf413854df82
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90039649"
---
# <a name="high_resolution_clock-struct"></a>struct high_resolution_clock

Représente une horloge de *high_resolution* .

## <a name="syntax"></a>Syntaxe

```cpp
class high_resolution_clock
```

## <a name="members"></a>Membres

### <a name="typedefs"></a>Typedefs

|Nom|Description|
|----------|-----------------|
|`duration`|Synonyme de `nanoseconds` , défini dans \<chrono> .|
|`period`|Synonyme de `nano` , défini dans \<ratio> .|
|`rep`|Synonyme de **`long long`** , type utilisé pour représenter le nombre de battements d’horloge dans l’instanciation contenue de `duration` .|
|`time_point`|Synonyme de `chrono::time_point<high_resolution_clock>`.|

## <a name="functions"></a>Fonctions

|Nom|Description|
|-|-|
|`now`|Retourne l’heure actuelle en tant que `time_point` valeur.|

## <a name="constants"></a>Constantes

|Nom|Description|
|----------|-----------------|
|`is_steady`|Contient **`true`** . Un `high_resolution_clock` est *steady*.|
