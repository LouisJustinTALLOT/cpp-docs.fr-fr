---
title: cimag, cimagf, cimagl
ms.date: 11/04/2016
api_name:
- cimag
- cimagf
- cimagl
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
- cimagf
- cimagl
- complex/cimag
- complex/cimagf
- complex/cimagl
- cimag
helpviewer_keywords:
- cimag function
- cimagf function
- cimagl function
ms.assetid: 0d8836f5-d61d-44cd-8731-6f75cb776def
ms.openlocfilehash: af7d15ee1b5dfd863025565bf8827199f7492841
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232545"
---
# <a name="cimag-cimagf-cimagl"></a>cimag, cimagf, cimagl

Récupère la partie imaginaire d’un nombre complexe.

## <a name="syntax"></a>Syntaxe

```C
double cimag( _Dcomplex z );
float cimagf( _Fcomplex z );
long double cimagl( _Lcomplex z );
```

```cpp
float cimag( _Fcomplex z );  // C++
long double cimag( _Lcomplex z );  // C++
```

### <a name="parameters"></a>Paramètres

*Lettre*<br/>
Nombre complexe.

## <a name="return-value"></a>Valeur de retour

Partie imaginaire de *z*.

## <a name="remarks"></a>Notes

C++ autorisant la surcharge, vous pouvez appeler des surcharges de **Cimag** qui acceptent des valeurs **_Fcomplex** ou **_Lcomplex** , et retournent des **`float`** **`long double`** valeurs ou. Dans un programme C, **Cimag** prend toujours une valeur **_Dcomplex** et retourne une **`double`** valeur.

## <a name="requirements"></a>Spécifications

|Routine|En-tête C|En-tête C++|
|-------------|--------------|------------------|
|**Cimag**, **cimagf**, **cimagl**|\<complex.h>|\<ccomplex>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Référence de fonction alphabétique](crt-alphabetical-function-reference.md)<br/>
[norm, normf, norml](norm-normf-norml1.md)<br/>
[creal, crealf, creall](creal-crealf-creall.md)<br/>
[cproj, cprojf, cprojl](cproj-cprojf-cprojl.md)<br/>
[conj, conjf, conjl](conj-conjf-conjl.md)<br/>
[carg, cargf, cargl](carg-cargf-cargl.md)<br/>
[cabs, cabsf, cabsl](cabs-cabsf-cabsl.md)<br/>
