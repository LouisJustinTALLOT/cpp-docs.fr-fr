---
title: Concurrency::fast_math Namespace | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- amp_math/Concurrency::fast_math
dev_langs:
- C++
ms.assetid: 54fed939-9902-49db-9f29-e98fd9821508
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 04a9cd3d604b18e42202bccb287cce7c7416b51f
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33692156"
---
# <a name="concurrencyfastmath-namespace"></a>Concurrency::fast_math, espace de noms
Les fonctions dans le `fast_math` espace de noms a une précision inférieure, prennent en charge uniquement simple précision (`float`) et appeler les fonctions intrinsèques de DirectX. Il existe deux versions de chaque fonction, par exemple `cos` et `cosf`. Les deux versions acceptent et retournent un `float`, mais chacun appels DirectX même intrinsèque.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
namespace fast_math;  
```  
  
## <a name="members"></a>Membres  
  
### <a name="functions"></a>Fonctions  
  
|Nom|Description|  
|----------|-----------------|  
|[cos](concurrency-fast-math-namespace-functions.md#cos)|Calcule l’arc cosinus de l’argument|  
|[cosf](concurrency-fast-math-namespace-functions.md#cosf)|Calcule l’arc cosinus de l’argument|  
|[asin](concurrency-fast-math-namespace-functions.md#asin)|Calcule l’arc sinus de l’argument|  
|[asinf](concurrency-fast-math-namespace-functions.md#asinf)|Calcule l’arc sinus de l’argument|  
|[atan](concurrency-fast-math-namespace-functions.md#atan)|Calcule l’arc tangente de l’argument|  
|[atan2](concurrency-fast-math-namespace-functions.md#atan2)|Calcule l’arc tangente de _Y/_X|  
|[atan2f](concurrency-fast-math-namespace-functions.md#atan2f)|Calcule l’arc tangente de _Y/_X|  
|[atanf](concurrency-fast-math-namespace-functions.md#atanf)|Calcule l’arc tangente de l’argument|  
|[ceil](concurrency-fast-math-namespace-functions.md#ceil)|Calcule le plafond de l’argument|  
|[ceilf](concurrency-fast-math-namespace-functions.md#ceilf)|Calcule le plafond de l’argument|  
|[cos](concurrency-fast-math-namespace-functions.md#cos)|Calcule le cosinus de l’argument|  
|[cosf](concurrency-fast-math-namespace-functions.md#cosf)|Calcule le cosinus de l’argument|  
|[cosh](concurrency-fast-math-namespace-functions.md#cosh)|Calcule la valeur de cosinus hyperbolique de l’argument|  
|[coshf](concurrency-fast-math-namespace-functions.md#coshf)|Calcule la valeur de cosinus hyperbolique de l’argument|  
|[exp](concurrency-fast-math-namespace-functions.md#exp)|Calcule l’exponentielle de l’argument de base e|  
|[exp2](concurrency-fast-math-namespace-functions.md#exp2)|Calcule la valeur exponentielle de l’argument de base 2|  
|[exp2f](concurrency-fast-math-namespace-functions.md#exp2f)|Calcule la valeur exponentielle de l’argument de base 2|  
|[expf](concurrency-fast-math-namespace-functions.md#expf)|Calcule l’exponentielle de l’argument de base e|  
|[fabs](concurrency-fast-math-namespace-functions.md#fabs)|Retourne la valeur absolue de l’argument|  
|[fabsf](concurrency-fast-math-namespace-functions.md#fabsf)|Retourne la valeur absolue de l’argument|  
|[floor](concurrency-fast-math-namespace-functions.md#floor)|Calcule la valeur plancher de l’argument|  
|[floorf](concurrency-fast-math-namespace-functions.md#floorf)|Calcule la valeur plancher de l’argument|  
|[fmax](concurrency-fast-math-namespace-functions.md#fmax)|Déterminer la valeur numérique maximale des arguments|  
|[fmaxf](concurrency-fast-math-namespace-functions.md#fmaxf)|Déterminer la valeur numérique maximale des arguments|  
|[fmin](concurrency-fast-math-namespace-functions.md#fmin)|Déterminer la valeur numérique minimale des arguments|  
|[fminf](concurrency-fast-math-namespace-functions.md#fminf)|Déterminer la valeur numérique minimale des arguments|  
|[fmod](concurrency-fast-math-namespace-functions.md#fmod)|Calcule le reste à virgule flottante de _X/_Y|  
|[fmodf](concurrency-fast-math-namespace-functions.md#fmodf)|Calcule le reste à virgule flottante de _X/_Y|  
|[frexp](concurrency-fast-math-namespace-functions.md#frexp)|Obtient la mantisse et l’exposant de _X|  
|[frexpf](concurrency-fast-math-namespace-functions.md#frexpf)|Obtient la mantisse et l’exposant de _X|  
|[isfinite](concurrency-fast-math-namespace-functions.md#isfinite)|Détermine si l’argument a une valeur finie|  
|[isinf](concurrency-fast-math-namespace-functions.md#isinf)|Détermine si l’argument est un infini.|  
|[isnan](concurrency-fast-math-namespace-functions.md#isnan)|Détermine si l’argument est une valeur NaN|  
|[ldexp](concurrency-fast-math-namespace-functions.md#ldexp)|Calcule un nombre réel à partir de la mantisse et exposant|  
|[ldexpf](concurrency-fast-math-namespace-functions.md#ldexpf)|Calcule un nombre réel à partir de la mantisse et exposant|  
|[log](concurrency-fast-math-namespace-functions.md#log)|Calcule le logarithme de base e de l’argument|  
|[log10](concurrency-fast-math-namespace-functions.md#log10)|Calcule le logarithme de base 10 de l’argument|  
|[log10f](concurrency-fast-math-namespace-functions.md#log10f)|Calcule le logarithme de base 10 de l’argument|  
|[log2](concurrency-fast-math-namespace-functions.md#log2)|Calcule le logarithme base 2 de l’argument|  
|[log2f](concurrency-fast-math-namespace-functions.md#log2f)|Calcule le logarithme base 2 de l’argument|  
|[logf](concurrency-fast-math-namespace-functions.md#logf)|Calcule le logarithme de base e de l’argument|  
|[modf](concurrency-fast-math-namespace-functions.md#modf)|Fractionne _X en fractions de seconde et un nombre entier.|  
|[modff](concurrency-fast-math-namespace-functions.md#modff)|Fractionne _X en fractions de seconde et un nombre entier.|  
|[pow](concurrency-fast-math-namespace-functions.md#pow)|Calcule _X élevé à la puissance de _Y|  
|[powf](concurrency-fast-math-namespace-functions.md#powf)|Calcule _X élevé à la puissance de _Y|  
|[round](concurrency-fast-math-namespace-functions.md#round)|Arrondit _X à l’entier le plus proche|  
|[roundf](concurrency-fast-math-namespace-functions.md#roundf)|Arrondit _X à l’entier le plus proche|  
|[rsqrt](concurrency-fast-math-namespace-functions.md#rsqrt)|Retourne l’inverse de la racine carrée de l’argument|  
|[rsqrtf](concurrency-fast-math-namespace-functions.md#rsqrtf)|Retourne l’inverse de la racine carrée de l’argument|  
|[signbit](concurrency-fast-math-namespace-functions.md#signbit)|Retourne le signe de l’argument|  
|[signbitf](concurrency-fast-math-namespace-functions.md#signbitf)|Retourne le signe de l’argument|  
|[sin](concurrency-fast-math-namespace-functions.md#sin)|Calcule la valeur du sinus de l’argument|  
|[sincos](concurrency-fast-math-namespace-functions.md#sincos)|Calcule le sinus et le cosinus de _X|  
|[sincosf](concurrency-fast-math-namespace-functions.md#sincosf)|Calcule le sinus et le cosinus de _X|  
|[sinf](concurrency-fast-math-namespace-functions.md#sinf)|Calcule la valeur du sinus de l’argument|  
|[sinh](concurrency-fast-math-namespace-functions.md#sinh)|Calcule la valeur du sinus hyperbolique de l’argument|  
|[sinhf](concurrency-fast-math-namespace-functions.md#sinhf)|Calcule la valeur du sinus hyperbolique de l’argument|  
|[sqrt](concurrency-fast-math-namespace-functions.md#sqrt)|Calcule la racine carrée de l’argument|  
|[sqrtf](concurrency-fast-math-namespace-functions.md#sqrtf)|Calcule la racine carrée de l’argument|  
|[tan](concurrency-fast-math-namespace-functions.md#tan)|Calcule la valeur de l’argument de tangente|  
|[tanf](concurrency-fast-math-namespace-functions.md#tanf)|Calcule la valeur de l’argument de tangente|  
|[tanh](concurrency-fast-math-namespace-functions.md#tanh)|Calcule la valeur de la tangente hyperbolique de l’argument|  
|[tanhf](concurrency-fast-math-namespace-functions.md#tanhf)|Calcule la valeur de la tangente hyperbolique de l’argument|  
|[trunc](concurrency-fast-math-namespace-functions.md#trunc)|Tronque l’argument de la partie entière|  
|[truncf](concurrency-fast-math-namespace-functions.md#truncf)|Tronque l’argument de la partie entière|  

## <a name="requirements"></a>Spécifications  
 **En-tête :** amp_math.h  
  
 **Namespace :** Concurrency::fast_math  
  
## <a name="see-also"></a>Voir aussi  
 [Concurrency, espace de noms (C++ AMP)](concurrency-namespace-cpp-amp.md)
