---
title: fpclassify | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.topic: reference
apiname:
- fpclassify
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
apitype: HeaderDef
f1_keywords:
- fpclassify
- math/fpclassify
helpviewer_keywords:
- fpclassify macro
- fpclassify function
ms.assetid: bf549499-7ff9-4a58-8692-f2d1cb6bab81
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: da55cb87804d178d5a305ed466aa498de4bc1ee5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32398430"
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

**fpclassify** retourne une valeur entière qui indique la classe à virgule flottante de l’argument *x*. Ce tableau montre les valeurs possibles retournées par **fpclassify**, défini dans \<math.h >.

|Value|Description|
|-----------|-----------------|
|**FP_NAN**|NaN silencieux, signalant ou indéterminé|
|**FP_INFINITE**|Infini positif ou négatif|
|**FP_NORMAL**|Valeur non nulle normalisée positive ou négative|
|**FP_SUBNORMAL**|Valeur dénormalisée positive ou négative|
|**FP_ZERO**|Valeur nulle positive ou négative|

## <a name="remarks"></a>Notes

En C, **fpclassify** est une macro ; en C++, **fpclassify** est une fonction surchargée à l’aide des types d’arguments de **float**, **double**, ou **long** **double**. Dans les deux cas, la valeur retournée dépend du type effectif de l’expression d’argument et non d’une représentation intermédiaire. Par exemple, un vecteur normal **double** ou **long** **double** valeur peut devenir un infini, denormal ou zéro valeur lorsque converti en un **float**.

## <a name="requirements"></a>Spécifications

|Fonction/macro|En-tête requis (C)|En-tête requis (C++)|
|---------------------|---------------------------|-------------------------------|
|**fpclassify**|\<math.h>|\<math.h> ou \<cmath>|

Le **fpclassify** macro et **fpclassify** fonctions sont conformes à la norme ISO C99 et C ++ 11 spécifications. Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
