---
description: 'En savoir plus sur : _get_printf_count_output'
title: _get_printf_count_output
ms.date: 11/04/2016
api_name:
- _get_printf_count_output
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
- api-ms-win-crt-stdio-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- get_printf_count_output
- _get_printf_count_output
helpviewer_keywords:
- '%n format'
- get_printf_count_output function
- _get_printf_count_output function
ms.assetid: 850f9f33-8319-433e-98d8-6a694200d994
ms.openlocfilehash: fe5ee728b7bc8400cd93ec4e93131496d59334c5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339002"
---
# <a name="_get_printf_count_output"></a>_get_printf_count_output

Indique si les fonctions [printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)Family prennent en charge le format **% n** .

## <a name="syntax"></a>Syntaxe

```C
int _get_printf_count_output();
```

## <a name="return-value"></a>Valeur de retour

Valeur différente de zéro si **% n** est pris en charge, 0 si **% n** n’est pas pris en charge.

## <a name="remarks"></a>Notes

Si **% n** n’est pas pris en charge (valeur par défaut), la présence de **% n** dans la chaîne de format d’une des fonctions **printf** appellera le gestionnaire de paramètres non valides, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si la prise en charge de **% n** est activée (voir [_set_printf_count_output](set-printf-count-output.md)), **% n** se comporte comme décrit dans syntaxe de la [spécification de format : fonctions printf et wprintf](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_get_printf_count_output**|\<stdio.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Consultez l’exemple relatif à [_set_printf_count_output](set-printf-count-output.md).

## <a name="see-also"></a>Voir aussi

[_set_printf_count_output](set-printf-count-output.md)<br/>
