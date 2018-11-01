---
title: _getw
ms.date: 11/04/2016
apiname:
- _getw
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
- _getw
helpviewer_keywords:
- _getw function
- integers, getting from streams
- getw function
ms.assetid: ef75facc-b84e-470f-9f5f-8746c90822a0
ms.openlocfilehash: 615d3ac9bdc73ad200368eaeabf7c84951bc91ae
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50487605"
---
# <a name="getw"></a>_getw

Obtient un entier à partir d’un flux.

## <a name="syntax"></a>Syntaxe

```C
int _getw(
   FILE *stream
);
```

### <a name="parameters"></a>Paramètres

*flux de données*<br/>
Pointeur désignant la structure **FILE**.

## <a name="return-value"></a>Valeur de retour

**_getw** retourne la valeur entière lue. La valeur de retour **EOF** indique une erreur ou la fin du fichier. Toutefois, étant donné que le **EOF** valeur est également une valeur entière légitime, utilisez **feof** ou **ferror** pour vérifier une condition d’erreur ou de fin de fichier. Si *flux* est **NULL**, le Gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **errno** a la valeur **EINVAL** et la fonction retourne **EOF**.

## <a name="remarks"></a>Notes

Le **_getw** fonction lit la valeur binaire suivante de type **int** à partir du fichier associé *flux* et incrémente le pointeur de fichier associé (le cas échéant) pour pointer le caractère non lu suivant. **_getw** n’assume pas aucun alignement spécial d’éléments dans le flux de données. Des problèmes de portage peuvent se produire avec **_getw** , car la taille de la **int** type et l’ordre des octets dans le **int** type diffèrent entre les systèmes.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_getw**|\<stdio.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

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

### <a name="input-crtgetwtxt"></a>Entrée : crt_getw.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>Sortie

```Output
First data word in file: 0x656e694c
```

## <a name="see-also"></a>Voir aussi

[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[_putw](putw.md)<br/>
