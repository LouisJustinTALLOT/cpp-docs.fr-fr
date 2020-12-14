---
description: 'En savoir plus sur : _getw'
title: _getw
ms.date: 4/2/2020
api_name:
- _getw
- _o__getw
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _getw
helpviewer_keywords:
- _getw function
- integers, getting from streams
- getw function
ms.assetid: ef75facc-b84e-470f-9f5f-8746c90822a0
ms.openlocfilehash: 2f951305351b4693b9787b6eac926c719afd3f3e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97296535"
---
# <a name="_getw"></a>_getw

Obtient un entier à partir d’un flux.

## <a name="syntax"></a>Syntaxe

```C
int _getw(
   FILE *stream
);
```

### <a name="parameters"></a>Paramètres

*train*<br/>
Pointeur désignant la structure **FILE**.

## <a name="return-value"></a>Valeur renvoyée

**_getw** retourne la valeur entière lue. Une valeur de retour de **EOF** indique une erreur ou la fin du fichier. Toutefois, étant donné que la valeur **EOF** est également une valeur entière légitime, utilisez **feof** ou un pour vérifier une condition d’erreur **ou de fin** de fichier. Si *Stream* a la **valeur null**, le gestionnaire de paramètres non valides est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **errno** a la valeur **EINVAL** et la fonction retourne **EOF**.

## <a name="remarks"></a>Notes

La fonction **_getw** lit la valeur binaire suivante du type **`int`** à partir du fichier associé au *flux* et incrémente le pointeur de fichier associé (le cas échéant) pour pointer vers le caractère non lu suivant. **_getw** n’assume pas l’alignement spécial des éléments dans le flux. Des problèmes de Portage peuvent survenir avec **_getw** car la taille du **`int`** type et l’ordre des octets dans le **`int`** type diffèrent d’un système à l’autre.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_getw**|\<stdio.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_getw.c
// This program uses _getw to read a word
// from a stream, then performs an error check.

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   FILE *stream;
   int i;

   if( fopen_s( &stream, "crt_getw.txt", "rb" ) )
      printf( "Couldn't open file\n" );
   else
   {
      // Read a word from the stream:
      i = _getw( stream );

      // If there is an error...
      if( ferror( stream ) )
      {
         printf( "_getw failed\n" );
         clearerr_s( stream );
      }
      else
         printf( "First data word in file: 0x%.4x\n", i );
      fclose( stream );
   }
}
```

### <a name="input-crt_getwtxt"></a>Entrée : crt_getw.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>Output

```Output
First data word in file: 0x656e694c
```

## <a name="see-also"></a>Voir aussi

[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[_putw](putw.md)<br/>
