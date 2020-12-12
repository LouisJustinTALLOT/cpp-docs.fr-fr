---
description: 'En savoir plus sur : fpclassify'
title: fpclassify
ms.date: 04/05/2018
api_name:
- fpclassify
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
api_type:
- HeaderDef
f1_keywords:
- fpclassify
- math/fpclassify
helpviewer_keywords:
- fpclassify macro
- fpclassify function
ms.assetid: bf549499-7ff9-4a58-8692-f2d1cb6bab81
ms.openlocfilehash: 716684f15e82fb439c16239a61401b892a244f93
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97164833"
---
# <a name="fpclassify"></a>fpclassify

Retourne la classification à virgule flottante de l’argument.

## <a name="syntax"></a>Syntaxe

```C
int fpclassify(
   /* floating-point */ x
);

int fpclassify(
   float x
); // C++ only

int fpclassify(
   double x
); // C++ only

int fpclassify(
   long double x
); // C++ only
```

### <a name="parameters"></a>Paramètres

*x*<br/>
Valeur à virgule flottante à tester.

## <a name="return-value"></a>Valeur renvoyée

**fpclassify** retourne une valeur entière qui indique la classe à virgule flottante de l’argument *x*. Ce tableau montre les valeurs possibles retournées par **fpclassify**, définies dans \<math.h> .

|Valeur|Description|
|-----------|-----------------|
|**FP_NAN**|NaN silencieux, signalant ou indéterminé|
|**FP_INFINITE**|Infini positif ou négatif|
|**FP_NORMAL**|Valeur non nulle normalisée positive ou négative|
|**FP_SUBNORMAL**|Valeur dénormalisée positive ou négative|
|**FP_ZERO**|Valeur nulle positive ou négative|

## <a name="remarks"></a>Notes

En C, **fpclassify** est une macro ; en C++, **fpclassify** est une fonction surchargée à l’aide des types d’arguments de **`float`** , **`double`** ou **`long double`** . Dans les deux cas, la valeur retournée dépend du type effectif de l’expression d’argument et non d’une représentation intermédiaire. Par exemple, une valeur normale **`double`** ou **`long double`** peut devenir une valeur infinie, dénormalisée ou nulle lorsqu’elle est convertie en **`float`** .

## <a name="requirements"></a>Spécifications

|Fonction/macro|En-tête requis (C)|En-tête requis (C++)|
|---------------------|---------------------------|-------------------------------|
|**fpclassify**|\<math.h>|\<math.h> ou \<cmath>|

La macro **fpclassify** et les fonctions **fpclassify** sont conformes aux spécifications ISO C99 et c++ 11. Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
