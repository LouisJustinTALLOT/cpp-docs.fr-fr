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
ms.openlocfilehash: 850d5e3a5434aa44e23a7f74aeb9c306ab6c0a8e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87203206"
---
# <a name="steady_clock-struct"></a>steady_clock, struct

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

|||
|-|-|
|`now`|Retourne l’heure actuelle en tant que `time_point` valeur.|

## <a name="constants"></a>Constantes

|Nom|Description|
|----------|-----------------|
|`is_steady`|Contient **`true`** . Un `high_resolution_clock` est *steady*.|
