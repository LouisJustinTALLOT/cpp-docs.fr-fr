---
title: _set_SSE2_enable
ms.date: 04/05/2018
apiname:
- _set_SSE2_enable
apilocation:
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
apitype: DLLExport
f1_keywords:
- _set_SSE2_enable
- set_SSE2_enable
helpviewer_keywords:
- _set_SSE2_enable function
- Streaming SIMD Extensions 2 instructions
- set_SSE2_enable function
ms.assetid: 55db895d-fc1e-475a-9110-b781a9bb51c5
ms.openlocfilehash: c340423e93b6487a4a951e4b96055cba6e474269
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62356535"
---
# <a name="setsse2enable"></a>_set_SSE2_enable

Active ou désactive l’utilisation d’instructions Extensions Streaming SIMD 2 (SSE2) dans les routines mathématiques CRT. (Cette fonction n’est pas disponible dans les architectures x64, car SSE2 est activé par défaut.)

## <a name="syntax"></a>Syntaxe

```C
int _set_SSE2_enable(
   int flag
);
```

### <a name="parameters"></a>Paramètres

*flag*<br/>
1 pour activer l’implémentation SSE2 ; 0 pour désactiver l’implémentation SSE2. Par défaut, l’implémentation SSE2 est activée sur les processeurs qui la prennent en charge.

## <a name="return-value"></a>Valeur de retour

Valeur différente de zéro si l’implémentation SSE2 est activée ; zéro si l’implémentation SSE2 est désactivée.

## <a name="remarks"></a>Notes

Les fonctions suivantes ont des implémentations SSE2 qui peuvent être activées à l’aide de **_set_SSE2_enable**:

- [atan](atan-atanf-atanl-atan2-atan2f-atan2l.md)

- [ceil](ceil-ceilf-ceill.md)

- [exp](exp-expf.md)

- [floor](floor-floorf-floorl.md)

- [log](log-logf-log10-log10f.md)

- [log10](log-logf-log10-log10f.md)

- [modf](modf-modff-modfl.md)

- [pow](pow-powf-powl.md)

Les implémentations SSE2 de ces fonctions peuvent donner des réponses légèrement différentes de celles apportées par les implémentations par défaut, car les valeurs intermédiaires SSE2 sont des quantités en virgule flottante de 64 bits, alors que les valeurs intermédiaires des implémentations par défaut sont des quantités en virgule flottante de 80 bits.

> [!NOTE]
> Si vous utilisez le [/Oi (générer des fonctions intrinsèques)](../../build/reference/oi-generate-intrinsic-functions.md) option du compilateur pour compiler le projet, il peut sembler que **_set_SSE2_enable** n’a aucun effet. Le **/Oi** option du compilateur donne au compilateur l’autorité nécessaire pour utiliser des fonctions intrinsèques pour remplacer les appels CRT ; ce comportement substitue à l’effet de **_set_SSE2_enable**. Si vous souhaitez garantir que **/Oi** ne se substitue pas **_set_SSE2_enable**, utilisez **/Oi** pour compiler votre projet. Cela peut être également les bonnes pratiques lorsque vous utilisez d’autres commutateurs du compilateur qui impliquent le **/Oi**.

L’implémentation SSE2 n’est utilisée que si toutes les exceptions sont masquées. Pour masquer les exceptions, utilisez [_control87, _controlfp](control87-controlfp-control87-2.md).

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_set_SSE2_enable**|\<math.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

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

[Fonctionnalités de bibliothèque CRT](../../c-runtime-library/crt-library-features.md)<br/>
