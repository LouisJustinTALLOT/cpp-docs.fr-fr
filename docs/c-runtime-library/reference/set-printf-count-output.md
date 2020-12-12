---
description: 'En savoir plus sur : _set_printf_count_output'
title: _set_printf_count_output
ms.date: 11/04/2016
api_name:
- _set_printf_count_output
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
- set_printf_count_output
- _set_printf_count_output
helpviewer_keywords:
- '%n format'
- set_printf_count_output function
- _set_printf_count_output function
ms.assetid: d8259ec5-764e-42d0-9169-72172e95163b
ms.openlocfilehash: 455c4f0e49ce111853145a05d78efabcd76386fe
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97114245"
---
# <a name="_set_printf_count_output"></a>_set_printf_count_output

Active ou désactive la prise en charge du format **% n** dans les fonctions [printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)Family.

## <a name="syntax"></a>Syntaxe

```C
int _set_printf_count_output(
   int enable
);
```

### <a name="parameters"></a>Paramètres

*enable*<br/>
Valeur différente de zéro pour activer la prise en charge de **% n** , 0 pour désactiver la prise en charge de **% n** .

## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour

L’état de la prise en charge de **% n** avant d’appeler cette fonction : différent de zéro si la prise en charge de **% n** a été activée, 0 si elle a été désactivée.

## <a name="remarks"></a>Notes

Pour des raisons de sécurité, la prise en charge du spécificateur de format **% n** est désactivée par défaut dans **printf** et toutes ses variantes. Si **% n** est rencontré dans une spécification de format **printf** , le comportement par défaut consiste à appeler le gestionnaire de paramètre non valide comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). L’appel de **_set_printf_count_output** avec un argument différent de zéro entraîne l’interprétation de **% n** par les fonctions de la famille **printf**, comme décrit dans la [syntaxe de spécification de format : fonctions printf et wprintf](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_set_printf_count_output**|\<stdio.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

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
