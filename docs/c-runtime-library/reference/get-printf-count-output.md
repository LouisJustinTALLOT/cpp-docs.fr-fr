---
title: _get_printf_count_output | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- '%n format'
- get_printf_count_output function
- _get_printf_count_output function
ms.assetid: 850f9f33-8319-433e-98d8-6a694200d994
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 216df8d973f391db2b6114d9bbcb50dcf509c5b5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32398363"
---
# <a name="getprintfcountoutput"></a>_get_printf_count_output

Indique si [printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)-famille de fonctions de prise en charge la **%n** format.

## <a name="syntax"></a>Syntaxe

```C
int _get_printf_count_output();
```

## <a name="return-value"></a>Valeur de retour

Non nul if **%n** est pris en charge, 0 si **%n** n’est pas pris en charge.

## <a name="remarks"></a>Notes

Si **%n** est pas pris en charge (la valeur par défaut), il rencontre **%n** dans la chaîne de format d’un de la **printf** fonctions seront appellent le Gestionnaire de paramètre non valide comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si **%n** prise en charge est activée (consultez [_set_printf_count_output](set-printf-count-output.md)) puis **%n** se comporteront comme décrit dans [syntaxe de spécification de Format : printf et wprintf Fonctions](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_get_printf_count_output**|\<stdio.h>|

Pour plus d’informations sur la compatibilité, voir consultez [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Consultez l’exemple relatif à [_set_printf_count_output](set-printf-count-output.md).

## <a name="see-also"></a>Voir aussi

[_set_printf_count_output](set-printf-count-output.md)<br/>
