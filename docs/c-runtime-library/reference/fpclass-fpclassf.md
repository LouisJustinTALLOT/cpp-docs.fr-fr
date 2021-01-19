---
description: 'En savoir plus sur : _fpclass, _fpclassf'
title: _fpclass, _fpclassf
ms.date: 1/15/2021
api_name:
- _fpclass
- _fpclassf
- _o__fpclass
- _o__fpclassf
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- fpclass
- _fpclass
- _fpclassf
- math/_fpclass
- float/_fpclass
- math/_fpclassf
helpviewer_keywords:
- fpclass function
- floating-point numbers, IEEE representation
- _fpclass function
- _fpclassf function
ms.openlocfilehash: 3fb97c5aa787c4c102e787fa3b08650f23ca546a
ms.sourcegitcommit: 92dc6d99ba5dcf3b64dee164df2d29beb1e608da
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/18/2021
ms.locfileid: "98563989"
---
# <a name="_fpclass-_fpclassf"></a>`_fpclass`, `_fpclassf`

Retourne une valeur indiquant la classification à virgule flottante de l’argument.

## <a name="syntax"></a>Syntaxe

```C
int _fpclass(
   double x
);

int _fpclassf(
   float x
); /* x64 only */
```

### <a name="parameters"></a>Paramètres

*`x`*\
Valeur à virgule flottante à tester.

## <a name="return-value"></a>Valeur renvoyée

Les **`_fpclass`** **`_fpclassf`** fonctions et retournent une valeur entière qui indique la classification à virgule flottante de l’argument *`x`* . La classification peut avoir l’une des valeurs suivantes, définie dans `<float.h>` .

|Valeur|Description|
|-----------|-----------------|
|**`_FPCLASS_SNAN`**|NaN signalant|
|**`_FPCLASS_QNAN`**|NaN silencieux|
|**`_FPCLASS_NINF`**|Infini négatif ( `-INF` )|
|**`_FPCLASS_NN`**|Valeur non nulle normalisée négative|
|**`_FPCLASS_ND`**|Valeur dénormalisée négative|
|**`_FPCLASS_NZ`**|Zéro négatif (-0)|
|**`_FPCLASS_PZ`**|Zéro positif (+0)|
|**`_FPCLASS_PD`**|Valeur dénormalisée positive|
|**`_FPCLASS_PN`**|Valeur non nulle normalisée positive|
|**`_FPCLASS_PINF`**|Infini positif ( `+INF` )|

## <a name="remarks"></a>Remarques

Les **`_fpclass`** **`_fpclassf`** fonctions et sont spécifiques à Microsoft. Elles sont similaires à [`fpclassify`](fpclassify.md) , mais retournent des informations plus détaillées sur l’argument. La **`_fpclassf`** fonction n’est disponible que lorsqu’elle est compilée pour la plateforme x64.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Configuration requise

|Fonction|En-tête requis|
|--------------|---------------------|
|**`_fpclass`**, **`_fpclassf`**|`<float.h>`|

Pour plus d’informations sur la compatibilité et la conformité, consultez [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)\
[`isnan`, `_isnan`, `_isnanf`](isnan-isnan-isnanf.md)\
[`fpclassify`](fpclassify.md)