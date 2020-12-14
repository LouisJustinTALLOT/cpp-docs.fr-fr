---
description: 'En savoir plus sur : _set_SSE2_enable'
title: _set_SSE2_enable
ms.date: 04/05/2018
api_name:
- _set_SSE2_enable
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-math-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _set_SSE2_enable
- set_SSE2_enable
helpviewer_keywords:
- _set_SSE2_enable function
- Streaming SIMD Extensions 2 instructions
- set_SSE2_enable function
ms.assetid: 55db895d-fc1e-475a-9110-b781a9bb51c5
ms.openlocfilehash: a9c82b2f17d90bc158ac77b8d7ad9625491856aa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97211204"
---
# <a name="_set_sse2_enable"></a>_set_SSE2_enable

Active ou désactive l’utilisation d’instructions SSE2 (Streaming SIMD Extensions 2) dans les routines mathématiques CRT. (Cette fonction n’est pas disponible dans les architectures x64, car SSE2 est activé par défaut.)

## <a name="syntax"></a>Syntaxe

```C
int _set_SSE2_enable(
   int flag
);
```

### <a name="parameters"></a>Paramètres

*flag*<br/>
1 pour activer l’implémentation SSE2 ; 0 pour désactiver l’implémentation SSE2. Par défaut, l’implémentation SSE2 est activée sur les processeurs qui la prennent en charge.

## <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro si l’implémentation SSE2 est activée ; zéro si l’implémentation SSE2 est désactivée.

## <a name="remarks"></a>Notes

Les fonctions suivantes ont des implémentations SSE2 qui peuvent être activées à l’aide de **_set_SSE2_enable**:

- [atan](atan-atanf-atanl-atan2-atan2f-atan2l.md)

- [ceil](ceil-ceilf-ceill.md)

- [exp](exp-expf.md)

- [floor](floor-floorf-floorl.md)

- [Sign](log-logf-log10-log10f.md)

- [log10](log-logf-log10-log10f.md)

- [modf](modf-modff-modfl.md)

- [Poe](pow-powf-powl.md)

Les implémentations SSE2 de ces fonctions peuvent donner des réponses légèrement différentes de celles apportées par les implémentations par défaut, car les valeurs intermédiaires SSE2 sont des quantités en virgule flottante de 64 bits, alors que les valeurs intermédiaires des implémentations par défaut sont des quantités en virgule flottante de 80 bits.

> [!NOTE]
> Si vous utilisez l’option du compilateur [/Oi (générer des fonctions intrinsèques)](../../build/reference/oi-generate-intrinsic-functions.md) pour compiler le projet, cela peut sembler que **_set_SSE2_enable** n’a aucun effet. L’option du compilateur **/OI** donne au compilateur l’autorité d’utiliser des fonctions intrinsèques pour remplacer les appels CRT. ce comportement remplace l’effet de **_set_SSE2_enable**. Si vous souhaitez garantir que **/OI** ne remplace pas **_set_SSE2_enable**, utilisez **/OI-** pour compiler votre projet. Cela peut également être une bonne pratique lorsque vous utilisez d’autres commutateurs de compilateur qui impliquent **/OI**.

L’implémentation SSE2 n’est utilisée que si toutes les exceptions sont masquées. Pour masquer les exceptions, utilisez [_control87, _controlfp](control87-controlfp-control87-2.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_set_SSE2_enable**|\<math.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_set_SSE2_enable.c
// processor: x86
#include <math.h>
#include <stdio.h>

int main()
{
   int i = _set_SSE2_enable(1);

   if (i)
      printf("SSE2 enabled.\n");
   else
      printf("SSE2 not enabled; processor does not support SSE2.\n");
}
```

```Output
SSE2 enabled.
```

## <a name="see-also"></a>Voir aussi

[Fonctionnalités de la bibliothèque CRT](../../c-runtime-library/crt-library-features.md)<br/>
