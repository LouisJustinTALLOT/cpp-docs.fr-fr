---
description: 'En savoir plus sur : __setusermatherr'
title: __setusermatherr
ms.date: 11/04/2016
api_name:
- __setusermatherr
api_location:
- msvcr80.dll
- msvcr90.dll
- msvcrt.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr100.dll
- api-ms-win-crt-math-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __setusermatherr
helpviewer_keywords:
- __setusermatherr
ms.assetid: f306818d-381a-4d68-8739-71b92bacb5ea
ms.openlocfilehash: 11b470f3c39a22b212187936dc4bad36c3cefd1d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97277074"
---
# <a name="__setusermatherr"></a>__setusermatherr

Spécifie une routine fournie par l’utilisateur pour gérer les erreurs mathématiques, à la place de la routine [_matherr](../c-runtime-library/reference/matherr.md).

## <a name="syntax"></a>Syntaxe

```cpp
void __setusermatherr(
   _HANDLE_MATH_ERROR pf
   )
```

#### <a name="parameters"></a>Paramètres

*util*<br/>
Pointeur vers une implémentation de `_matherr` qui est fournie par l’utilisateur.

Le type du paramètre *pf* est déclaré comme `typedef int (__cdecl * _HANDLE_MATH_ERROR)(struct _exception *)`.

## <a name="remarks"></a>Notes

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|__setusermatherr|matherr.c|
