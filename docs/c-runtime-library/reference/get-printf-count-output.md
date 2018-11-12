---
title: _get_printf_count_output
ms.date: 11/04/2016
apiname:
- _get_printf_count_output
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- get_printf_count_output
- _get_printf_count_output
helpviewer_keywords:
- '%n format'
- get_printf_count_output function
- _get_printf_count_output function
ms.assetid: 850f9f33-8319-433e-98d8-6a694200d994
ms.openlocfilehash: 477e4a9e987f27bd70b9707e91b9ea9d84b69993
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50610633"
---
# <a name="getprintfcountoutput"></a>_get_printf_count_output

Indique si [printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)-fonctions de prise en charge de la famille la **%n** format.

## <a name="syntax"></a>Syntaxe

```C
int _get_printf_count_output();
```

## <a name="return-value"></a>Valeur de retour

Valeur différente de zéro if **%n** est pris en charge, 0 si **%n** n’est pas pris en charge.

## <a name="remarks"></a>Notes

Si **%n** est pas pris en charge (la valeur par défaut), il rencontre **%n** dans la chaîne de format d’une de le **printf** fonctions seront appellent le Gestionnaire de paramètre non valide comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si **%n** prise en charge est activée (consultez [_set_printf_count_output](set-printf-count-output.md)) puis **%n** se comporte comme décrit dans [syntaxe de spécification de Format : printf et wprintf Fonctions](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_get_printf_count_output**|\<stdio.h>|

Pour plus d’informations sur la compatibilité, voir consultez [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Consultez l’exemple relatif à [_set_printf_count_output](set-printf-count-output.md).

## <a name="see-also"></a>Voir aussi

[_set_printf_count_output](set-printf-count-output.md)<br/>
