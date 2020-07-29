---
title: steady_clock, struct
ms.date: 05/22/2018
f1_keywords:
- chrono/std::chrono::steady_clock
ms.assetid: 970d12ec-fc80-4391-a2f7-b57b2aec668d
ms.openlocfilehash: d21d5c2ed7ed667333007f3bd12d13f47b868380
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217400"
---
# <a name="steady_clock-struct"></a>steady_clock, struct

Représente une horloge *stable* .

## <a name="syntax"></a>Syntaxe

```cpp
struct steady_clock;
```

## <a name="remarks"></a>Notes

Sur Windows, `steady_clock` encapsule la `QueryPerformanceCounter` fonction.

Une horloge est *monotonic* si la valeur retournée par un premier appel à `now` est toujours inférieure ou égale à la valeur retournée par un appel ultérieur à `now`. Une horloge est *stable* si elle est *monotone* et si le laps de temps entre les battements d’horloge est constant.

`high_resolution_clock`est un typedef pour `steady_clock` .

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|`steady_clock::duration`|Synonyme de `nanoseconds` , défini dans \<chrono> .|
|`steady_clock::period`|Synonyme de `nano` , défini dans \<ratio> .|
|`steady_clock::rep`|Synonyme de **`long long`** , type utilisé pour représenter le nombre de battements d’horloge dans l’instanciation contenue de `duration` .|
|`steady_clock::time_point`|Synonyme de `chrono::time_point<steady_clock>`.|

## <a name="public-functions"></a>Fonctions publiques

|Fonction|Description|
|--------------|-----------------|
|`now`|Retourne l’heure actuelle en tant que `time_point` valeur.|

## <a name="public-constants"></a>Constantes publiques

|Nom|Description|
|----------|-----------------|
|`steady_clock::is_steady`|Contient **`true`** . Un `steady_clock` est *steady*.|

## <a name="requirements"></a>Spécifications

**En-tête :**\<chrono>

**Espace de noms :** std::chrono

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)
- [\<chrono>](../standard-library/chrono.md)
- [system_clock, structure](../standard-library/system-clock-structure.md)
