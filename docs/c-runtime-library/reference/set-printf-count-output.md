---
title: _set_printf_count_output | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _set_printf_count_output
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
- set_printf_count_output
- _set_printf_count_output
dev_langs:
- C++
helpviewer_keywords:
- '%n format'
- set_printf_count_output function
- _set_printf_count_output function
ms.assetid: d8259ec5-764e-42d0-9169-72172e95163b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 783225412b01430d1043dafd4761cb7432eaa1d7
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44108317"
---
# <a name="setprintfcountoutput"></a>_set_printf_count_output

Activer ou désactiver la prise en charge de la **%n** mettre en forme de [printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)-fonctions de famille.

## <a name="syntax"></a>Syntaxe

```C
int _set_printf_count_output(
   int enable
);
```

### <a name="parameters"></a>Paramètres

*enable*<br/>
Une valeur différente de zéro pour activer **%n** prennent en charge, 0 pour désactiver **%n** prennent en charge.

## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour

L’état de **%n** prennent en charge avant d’appeler cette fonction : zéro if **%n** prise en charge a été activée, 0 si elle a été désactivée.

## <a name="remarks"></a>Notes

Pour des raisons de sécurité, la prise en charge pour le **%n** spécificateur de format est désactivé par défaut dans **printf** et toutes ses variantes. Si **%n** est rencontré dans un **printf** spécification de format, le comportement par défaut consiste à appeler le Gestionnaire de paramètre non valide, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Appel **_set_printf_count_output** avec un argument différent de zéro entraîne **printf**-fonctions de famille pour interpréter **%n** comme décrit dans [Format Syntaxe de spécification : les fonctions printf et wprintf](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_set_printf_count_output**|\<stdio.h>|

Pour plus d’informations sur la compatibilité, voir consultez [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_set_printf_count_output.c
#include <stdio.h>

int main()
{
   int e;
   int i;
   e = _set_printf_count_output( 1 );
   printf( "%%n support was %sabled.\n",
        e ? "en" : "dis" );
   printf( "%%n support is now %sabled.\n",
        _get_printf_count_output() ? "en" : "dis" );
   printf( "12345%n6789\n", &i ); // %n format should set i to 5
   printf( "i = %d\n", i );
}
```

```Output
%n support was disabled.
%n support is now enabled.
123456789
i = 5
```

## <a name="see-also"></a>Voir aussi

[_get_printf_count_output](get-printf-count-output.md)<br/>
