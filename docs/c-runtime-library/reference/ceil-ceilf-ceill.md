---
title: ceil, ceilf, ceill | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- ceilf
- ceil
- ceill
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
- ntdll.dll
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- ceil
- ceilf
- ceill
dev_langs:
- C++
helpviewer_keywords:
- calculating value ceilings
- ceill function
- ceil function
- ceilf function
ms.assetid: f4e5acab-5c8f-4b10-9ae2-9561e6453718
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fa68ff857db09d1426fbed6ea497624e13cc362a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32394263"
---
# <a name="ceil-ceilf-ceill"></a>ceil, ceilf, ceill

Calcule le plafond d’une valeur.

## <a name="syntax"></a>Syntaxe

```C
double ceil(
   double x
);
float ceil(
   float x
);  // C++ only
long double ceil(
   long double x
);  // C++ only
float ceilf(
   float x
);
long double ceill(
   long double x
);
```

### <a name="parameters"></a>Paramètres

*x*<br/>
Valeur à virgule flottante.

## <a name="return-value"></a>Valeur de retour

Le **ceil** fonctions retournent une valeur à virgule flottante qui représente le plus petit entier qui est supérieur ou égal à *x*. Aucun retour d'erreur.

|Entrée|Exception SEH|Exception{b> <b}Matherr|
|-----------|-------------------|-----------------------|
|± **QNAN**, **IND**|aucun|**_DOMAIN**|

**ceil** possède une implémentation qui utilise des Extensions Streaming SIMD 2 (SSE2). Pour obtenir des informations sur l’utilisation de l’implémentation SSE2 et sur les restrictions qui s’y rattachent, consultez [_set_SSE2_enable](set-sse2-enable.md).

## <a name="remarks"></a>Notes

C++ autorisant la surcharge, vous pouvez appeler des surcharges de **ceil** acceptant **float** ou **long** **double** types. Dans un programme C, **ceil** accepte et retourne toujours un **double**.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**ceil**, **ceilf**, **ceill**|\<math.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Consultez l’exemple relatif à [floor](floor-floorf-floorl.md).

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[floor, floorf, floorl](floor-floorf-floorl.md)<br/>
[fmod, fmodf](fmod-fmodf.md)<br/>
[round, roundf, roundl](round-roundf-roundl.md)<br/>
