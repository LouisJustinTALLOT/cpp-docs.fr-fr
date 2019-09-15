---
title: _fpclass, _fpclassf
ms.date: 04/05/2018
api_name:
- _fpclass
- _fpclassf
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
ms.assetid: 2774872d-3543-446f-bc72-db85f8b95a6b
ms.openlocfilehash: 2e561cff956ca51707834bf869a1c114f0c99a3e
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957042"
---
# <a name="_fpclass-_fpclassf"></a>_fpclass, _fpclassf

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

*x*<br/>
Valeur à virgule flottante à tester.

## <a name="return-value"></a>Valeur de retour

Les fonctions **_fpclass** et **_fpclassf** retournent une valeur entière qui indique la classification à virgule flottante de l’argument *x*. La classification peut avoir une des valeurs suivantes, définies dans \<float.h>.

|Valeur|Description|
|-----------|-----------------|
|**_FPCLASS_SNAN**|NaN signalant|
|**_FPCLASS_QNAN**|NaN silencieux|
|**_FPCLASS_NINF**|Infini négatif (-INF)|
|**_FPCLASS_NN**|Valeur non nulle normalisée négative|
|**_FPCLASS_ND**|Valeur dénormalisée négative|
|**_FPCLASS_NZ**|Zéro négatif (-0)|
|**_FPCLASS_PZ**|Zéro positif (+0)|
|**_FPCLASS_PD**|Valeur dénormalisée positive|
|**_FPCLASS_PN**|Valeur non nulle normalisée positive|
|**_FPCLASS_PINF**|Infini positif (+INF)|

## <a name="remarks"></a>Notes

Les fonctions **_fpclass** et **_fpclassf** sont spécifiques à Microsoft. Elles sont similaires à [fpclassify](fpclassify.md), mais retournent des informations plus détaillées sur l’argument. La fonction **_fpclassf** est disponible uniquement quand elle est compilée pour la plateforme x64.

## <a name="requirements"></a>Configuration requise

|Fonction|En-tête requis|
|--------------|---------------------|
|**_fpclass**, **_fpclassf**|\<float.h>|

Pour plus d’informations sur la compatibilité et la conformité, consultez [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
[fpclassify](fpclassify.md)<br/>