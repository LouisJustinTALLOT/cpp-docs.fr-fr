---
title: fseek, _fseeki64 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _fseeki64
- fseek
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
apitype: DLLExport
f1_keywords:
- fseek
- _fseeki64
dev_langs:
- C++
helpviewer_keywords:
- _fseeki64 function
- fseeki64 function
- fseek function
- file pointers [C++], moving
- file pointers [C++]
- seek file pointers
ms.assetid: f6bb1f8b-891c-426e-9e14-0e7e5c62df70
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a327bf196da71f47262c957e7fe6a8352971c36d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32403740"
---
# <a name="fseek-fseeki64"></a>fseek, _fseeki64

Déplace le pointeur de fichier vers un emplacement spécifié.

## <a name="syntax"></a>Syntaxe

```C
int fseek(
   FILE *stream,
   long offset,
   int origin
);
int _fseeki64(
   FILE *stream,
   __int64 offset,
   int origin
);
```

### <a name="parameters"></a>Paramètres

*Flux de données*<br/>
Pointeur désignant la structure **FILE**.

*offset*<br/>
Nombre d’octets à partir d’*origin*.

*origin*<br/>
Position initiale.

## <a name="return-value"></a>Valeur de retour

En cas de réussite, **fseek** et **_fseeki64** retourne 0. Dans le cas contraire, une valeur différente de zéro est retournée. Sur les appareils incapables de rechercher, la valeur de retour n’est pas définie. Si *flux* est un pointeur null, ou si *origine* n’est pas une des valeurs autorisées décrites ci-dessous, **fseek** et **_fseeki64** appel non valide Gestionnaire de paramètres, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions définissent **errno** à **EINVAL** et retournent -1.

## <a name="remarks"></a>Notes

Le **fseek** et **_fseeki64** déplace le pointeur de fichier (le cas échéant) associé à des fonctions *flux* vers un nouvel emplacement est *offset* octets à partir de *origine*. L’opération suivante sur le flux a lieu au nouvel emplacement. Sur un flux ouvert pour la mise à jour, l’opération suivante peut être une lecture ou une écriture. L’argument *origine* doit être une des constantes suivantes, définies dans STDIO. H :

|valeur d’origine|Signification|
|-|-|
**SEEK_CUR**|Position actuelle du pointeur de fichier.
**SEEK_END**|Fin du fichier.
**SEEK_SET**|Début du fichier.

Vous pouvez utiliser **fseek** et **_fseeki64** pour repositionner le pointeur n’importe où dans un fichier. Le pointeur peut également être positionné au-delà de la fin du fichier. **fseek** et **_fseeki64** efface l’indicateur de fin de fichier et annule l’effet du tout avant [ungetc](ungetc-ungetwc.md) les appels de fonction *flux*.

Quand un fichier est ouvert pour un ajout de données, la position de fichier actuelle est déterminée par la dernière opération d’E/S, pas par l’emplacement auquel l’écriture suivante se produirait. Si aucune opération d’E/S ne s’est produite sur un fichier ouvert pour un ajout, la position de fichier correspond au début du fichier.

Pour les flux ouverts en mode texte, **fseek** et **_fseeki64** est limitée utilisation, comme des traductions chariot / sauts de ligne peuvent entraîner **fseek** et **_ fseeki64** pour produire des résultats inattendus. La seule **fseek** et **_fseeki64** opérations fonctionnent sur les flux ouverts en mode texte sont :

- Recherche avec un décalage de 0 par rapport à toute valeur d’origine.

- La recherche à partir du début du fichier avec une valeur de décalage retourné par un appel à [ftell](ftell-ftelli64.md) lors de l’utilisation **fseek** ou [_ftelli64](ftell-ftelli64.md) lors de l’utilisation **_fseeki64**.

Également en mode texte, Ctrl+Z est interprété comme un caractère de fin de fichier en entrée. Dans les fichiers ouverts en lecture/écriture, [fopen](fopen-wfopen.md) et toutes les routines connexes d’un CTRL + Z à la fin du fichier et si possible de le supprimer. Pour cela, car il est à l’aide de la combinaison de **fseek** et [ftell](ftell-ftelli64.md) ou **_fseeki64** et [_ftelli64](ftell-ftelli64.md), pour se déplacer dans un fichier qui se termine par CTRL + Z peut provoquer **fseek** ou **_fseeki64** comportement incorrect vers la fin du fichier.

Quand la bibliothèque CRT ouvre un fichier qui commence par une marque d’ordre d’octet, le pointeur de fichier est positionné après la marque (autrement dit, au début du contenu réel du fichier). Si vous devez **fseek** au début du fichier, utilisez [ftell](ftell-ftelli64.md) pour obtenir la position initiale et **fseek** à elle plutôt qu’à la position 0.

Cette fonction verrouille les autres threads pendant l’exécution et est donc thread-safe. Pour une version sans verrouillage, consultez [_fseek_nolock, _fseeki64_nolock](fseek-nolock-fseeki64-nolock.md).

## <a name="requirements"></a>Spécifications

|Fonction|En-tête requis|
|--------------|---------------------|
|**fseek**|\<stdio.h>|
|**_fseeki64**|\<stdio.h>|

Pour plus d’informations sur la compatibilité, voir consultez [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_fseek.c
// This program opens the file FSEEK.OUT and
// moves the pointer to the file's beginning.

#include <stdio.h>

int main( void )
{
   FILE *stream;
   char line[81];
   int  result;

   if ( fopen_s( &stream, "fseek.out", "w+" ) != 0 )
   {
      printf( "The file fseek.out was not opened\n" );
      return -1;
   }
   fprintf( stream, "The fseek begins here: "
                    "This is the file 'fseek.out'.\n" );
   result = fseek( stream, 23L, SEEK_SET);
   if( result )
      perror( "Fseek failed" );
   else
   {
      printf( "File pointer is set to middle of first line.\n" );
      fgets( line, 80, stream );
      printf( "%s", line );
    }
   fclose( stream );
}
```

```Output
File pointer is set to middle of first line.
This is the file 'fseek.out'.
```

## <a name="see-also"></a>Voir aussi

[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[ftell, _ftelli64](ftell-ftelli64.md)<br/>
[_lseek, _lseeki64](lseek-lseeki64.md)<br/>
[rewind](rewind.md)<br/>
