---
title: _fpclass, _fpclassf
ms.date: 04/05/2018
apiname:
- _fpclass
- _fpclassf
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
ms.openlocfilehash: 987c87cc7a03f4a24e47654ae52e8a2416a15184
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62333220"
---
# <a name="fpclass-fpclassf"></a>_fpclass, _fpclassf

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

Le **_fpclass** et **_fpclassf** fonctions retournent une valeur entière qui indique la classification à virgule flottante de l’argument *x*. La classification peut avoir une des valeurs suivantes, définies dans \<float.h>.

|Value|Description|
|-----------|-----------------|
|**_FPCLASS_SNAN**|NaN signalant|
|**_FPCLASS_QNAN**|NaN silencieux|
|**_FPCLASS_NINF**|Infini négatif (-INF)|
|**_FPCLASS_NN**|Valeur non nulle normalisée négative|
|**_FPCLASS_ND**|Valeur dénormalisée négative|
|**_FPCLASS_NZ**|Un zéro négatif (- 0)|
|**_FPCLASS_PZ**|Zéro positif (+0)|
|**_FPCLASS_PD**|Valeur dénormalisée positive|
|**_FPCLASS_PN**|Valeur non nulle normalisée positive|
|**_FPCLASS_PINF**|Infini positif (+INF)|

## <a name="remarks"></a>Notes

Le **_fpclass** et **_fpclassf** fonctions sont propres à Microsoft. Elles sont similaires à [fpclassify](fpclassify.md), mais retournent des informations plus détaillées sur l’argument. Le **_fpclassf** fonction est uniquement disponible lors de la compilation pour le x64 plateforme.

## <a name="requirements"></a>Configuration requise

|Fonction|En-tête requis|
|--------------|---------------------|
|**_fpclass**, **_fpclassf**|\<float.h>|

Pour plus d’informations sur la compatibilité et la conformité, consultez [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Prise en charge de la virgule flottante](../../c-runtime-library/floating-point-support.md)<br/>
[isnan, _isnan, _isnanf](isnan-isnan-isnanf.md)<br/>
[fpclassify](fpclassify.md)<br/>