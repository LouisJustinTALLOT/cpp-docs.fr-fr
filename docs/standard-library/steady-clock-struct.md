---
title: steady_clock, struct
ms.date: 05/22/2018
f1_keywords:
- chrono/std::chrono::steady_clock
ms.assetid: 970d12ec-fc80-4391-a2f7-b57b2aec668d
ms.openlocfilehash: 19e9f5c4dcfc7306b989605894e9a0787e0920ff
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62412395"
---
# <a name="steadyclock-struct"></a>steady_clock, struct

Représente un *stable* horloge.

## <a name="syntax"></a>Syntaxe

```cpp
struct steady_clock;
```

## <a name="remarks"></a>Notes

Sur Windows, `steady_clock` encapsule le `QueryPerformanceCounter` (fonction).

Une horloge est *monotone* si la valeur retournée par un premier appel à `now` est toujours inférieure ou égale à la valeur retournée par un appel ultérieur à `now`. Une horloge est *stable* si elle est *monotone* et si le laps de temps entre les battements d’horloge est constant.

`high_resolution_clock` est un typedef pour `steady_clock`.

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|`steady_clock::duration`|Un synonyme de `nanoseconds`, défini dans \<chrono >.|
|`steady_clock::period`|Un synonyme de `nano`, défini dans \<ratio >.|
|`steady_clock::rep`|Un synonyme de **long** **long**, le type qui est utilisé pour représenter le nombre de battements d’horloge dans l’instanciation contenue de `duration`.|
|`steady_clock::time_point`|Synonyme de `chrono::time_point<steady_clock>`.|

## <a name="public-functions"></a>Fonctions publiques

|Fonction|Description|
|--------------|-----------------|
|`now`|Retourne l’heure actuelle comme un `time_point` valeur.|

## <a name="public-constants"></a>Constantes publiques

|Nom|Description|
|----------|-----------------|
|`steady_clock::is_steady`|Contient **true**. Un `steady_clock` est *steady*.|

## <a name="requirements"></a>Configuration requise

**En-tête :** \<chrono >

**Espace de noms :** std::chrono

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)
- [\<chrono>](../standard-library/chrono.md)
- [system_clock, structure](../standard-library/system-clock-structure.md)
