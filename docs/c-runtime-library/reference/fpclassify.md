---
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
ms.openlocfilehash: e9b5aa1f7dc20cc920a51c2c36371eb907469875
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957063"
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

## <a name="return-value"></a>Valeur de retour

**fpclassify** retourne une valeur entière qui indique la classe à virgule flottante de l’argument *x*. Ce tableau montre les valeurs possibles retournées par **fpclassify**, \<définies dans Math. h >.

|Valeur|Description|
|-----------|-----------------|
|**FP_NAN**|NaN silencieux, signalant ou indéterminé|
|**FP_INFINITE**|Infini positif ou négatif|
|**FP_NORMAL**|Valeur non nulle normalisée positive ou négative|
|**FP_SUBNORMAL**|Valeur dénormalisée positive ou négative|
|**FP_ZERO**|Valeur nulle positive ou négative|

## <a name="remarks"></a>Notes

En C, **fpclassify** est une macro ; dans C++, **fpclassify** est une fonction surchargée à l’aide des types d’arguments **float**, **double**ou **long** **double**. Dans les deux cas, la valeur retournée dépend du type effectif de l’expression d’argument et non d’une représentation intermédiaire. Par exemple, une valeur normale **double** ou **long** **double** peut devenir une valeur infinie, dénormalisée ou nulle lorsqu’elle est convertie en valeur **float**.

## <a name="requirements"></a>Configuration requise

|Fonction/macro|En-tête requis (C)|En-tête requis (C++)|
|---------------------|---------------------------|-------------------------------|
|**fpclassify**|\<math.h>|\<math.h> ou \<cmath>|

La macro **fpclassify** et les fonctions **fpclassify** sont conformes aux spécifications ISO C99 et c++ 11. Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
