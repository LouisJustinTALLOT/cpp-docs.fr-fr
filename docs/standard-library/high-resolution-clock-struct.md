---
description: 'En savoir plus sur : struct high_resolution_clock'
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
ms.openlocfilehash: 2c5272413636e40dadf9201f684d32aaaa6708ac
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97324052"
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
