---
title: _gcvt
ms.date: 4/2/2020
api_name:
- _gcvt
- _o__gcvt
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
- api-ms-win-crt-convert-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _gcvt
helpviewer_keywords:
- _gcvt function
- _CVTBUFSIZE
- gcvt function
- floating-point functions, converting number to string
- numbers, converting to strings
- conversions, floating point to strings
- strings [C++], converting from floating point
- CVTBUFSIZE
ms.assetid: 5761411e-c06b-409a-912f-810fe7f4bcb5
ms.openlocfilehash: f161256c6dc86a045f49111cde3651bea08ead11
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345317"
---
# <a name="_gcvt"></a>_gcvt

Convertir une valeur à virgule flottante en chaîne, qui est stockée dans une mémoire tampon. Une version plus sécurisée de cette fonction est disponible. Consultez [_gcvt_s](gcvt-s.md).

## <a name="syntax"></a>Syntaxe

```C
char *_gcvt(
   double value,
   int digits,
   char *buffer
);
```

### <a name="parameters"></a>Paramètres

*value*<br/>
Valeur à convertir.

*chiffres*<br/>
Nombre de chiffres significatifs stockés.

*buffer*<br/>
Emplacement de stockage pour le résultat.

## <a name="return-value"></a>Valeur de retour

**_gcvt** renvoie un pointeur à la chaîne de chiffres.

## <a name="remarks"></a>Notes

La fonction **_gcvt** convertit une *valeur* de point flottant en une chaîne de caractère (qui comprend un point décimal et un byte de signe possible) et stocke la chaîne dans *le tampon.* Le *tampon* doit être suffisamment grand pour tenir compte de la valeur convertie plus un caractère nul de fin, qui est joint automatiquement. Si une taille tampon de *chiffres* 1 est utilisée, la fonction dépasse l’extrémité du tampon. En effet, la chaîne convertie comprend une virgule décimale et peut contenir des informations de signe et d’exposant. Le dépassement n’est pas pris en charge. **_gcvt** tente de produire des *chiffres* de chiffres en format décimal. Si elle ne peut pas, il produit *des chiffres* de chiffres en format exponentiel. Les zéros de fin peuvent être supprimés pendant la conversion.

Un *tampon* de longueur **_CVTBUFSIZE** est suffisant pour toute valeur de point flottant.

Cette fonction valide ses paramètres. Si *le tampon* est **NULL**, le gestionnaire de paramètre invalide est invoqué, tel que décrit dans la validation [de paramètres](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, cette fonction définit **errno** à **EINVAL** et retourne **NULL**.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_gcvt**|\<stdlib.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_gcvt.c
// compile with: /W3
#include <stdlib.h>
#include <stdio.h>
#include <string.h>

int main( void )
{
   char buffer[_CVTBUFSIZE];
   double value = -1234567890.123;
   printf( "The following numbers were converted by _gcvt(value,12,buffer):\n" );
   _gcvt( value, 12, buffer ); // C4996
   // Note: _gcvt is deprecated; consider using _gcvt_s instead
   printf( "buffer: '%s' (%d chars)\n", buffer, strlen(buffer) );
   value *= 10;
   _gcvt( value, 12, buffer ); // C4996
   printf( "buffer: '%s' (%d chars)\n", buffer, strlen(buffer) );
   value *= 10;
   _gcvt( value, 12, buffer ); // C4996
   printf( "buffer: '%s' (%d chars)\n", buffer, strlen(buffer) );
   value *= 10;
   _gcvt( value, 12, buffer ); // C4996
   printf( "buffer: '%s' (%d chars)\n", buffer, strlen(buffer) );

   printf( "\n" );
   value = -12.34567890123;
   _gcvt( value, 12, buffer ); // C4996
   printf( "buffer: '%s' (%d chars)\n", buffer, strlen(buffer) );
   value /= 10;
   _gcvt( value, 12, buffer ); // C4996
   printf( "buffer: '%s' (%d chars)\n", buffer, strlen(buffer) );
   value /= 10;
   _gcvt( value, 12, buffer ); // C4996
   printf( "buffer: '%s' (%d chars)\n", buffer, strlen(buffer) );
   value /= 10;
   _gcvt( value, 12, buffer ); // C4996
   printf( "buffer: '%s' (%d chars)\n", buffer, strlen(buffer) );
}
```

```Output
The following numbers were converted by _gcvt(value,12,buffer):
buffer: '-1234567890.12' (14 chars)
buffer: '-12345678901.2' (14 chars)
buffer: '-123456789012' (13 chars)
buffer: '-1.23456789012e+012' (19 chars)

buffer: '-12.3456789012' (14 chars)
buffer: '-1.23456789012' (14 chars)
buffer: '-0.123456789012' (15 chars)
buffer: '-1.23456789012e-002' (19 chars)
```

## <a name="see-also"></a>Voir aussi

[Conversion de données](../../c-runtime-library/data-conversion.md)<br/>
[Soutien à la pointe flottante](../../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_ecvt](ecvt.md)<br/>
[_fcvt](fcvt.md)<br/>
