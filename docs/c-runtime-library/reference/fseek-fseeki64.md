---
description: 'En savoir plus sur : fseek, _fseeki64'
title: fseek, _fseeki64
ms.date: 4/2/2020
api_name:
- _fseeki64
- fseek
- _o__fseeki64
- _o_fseek
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
- fseek
- _fseeki64
helpviewer_keywords:
- _fseeki64 function
- fseeki64 function
- fseek function
- file pointers [C++], moving
- file pointers [C++]
- seek file pointers
ms.assetid: f6bb1f8b-891c-426e-9e14-0e7e5c62df70
ms.openlocfilehash: 7e15bd7cd273da2f73a58c2bd012670216c1938c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97114323"
---
# <a name="fseek-_fseeki64"></a>fseek, _fseeki64

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

*train*<br/>
Pointeur désignant la structure **FILE**.

*offset*<br/>
Nombre d’octets à partir d’*origin*.

*lancé*<br/>
Position initiale.

## <a name="return-value"></a>Valeur renvoyée

En cas de réussite, **fseek** et **_fseeki64** retourne 0. Sinon, elle retourne une valeur différente de zéro. Sur les appareils incapables de rechercher, la valeur de retour n’est pas définie. Si *Stream* est un pointeur null ou si *origin* ne fait pas partie des valeurs autorisées décrites ci-dessous, **fseek** et **_fseeki64** appeler le gestionnaire de paramètres non valides, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions définissent **errno** sur **EINVAL** et retournent-1.

## <a name="remarks"></a>Notes

Les fonctions **fseek** et **_fseeki64** déplacent le pointeur de fichier (le cas échéant) associé au *flux* vers un nouvel emplacement qui est *décalé* d’octets de l' *origine*. L’opération suivante sur le flux a lieu au nouvel emplacement. Sur un flux ouvert pour la mise à jour, l’opération suivante peut être une lecture ou une écriture. L’argument *origin* doit être l’une des constantes suivantes, définies dans stdio. Manutention

|valeur d’origine|Signification|
|-|-|
| **SEEK_CUR** | Position actuelle du pointeur de fichier. |
| **SEEK_END** | Fin du fichier. |
| **SEEK_SET** | Début du fichier. |

Vous pouvez utiliser **fseek** et **_fseeki64** pour repositionner le pointeur n’importe où dans un fichier. Le pointeur peut également être positionné au-delà de la fin du fichier. **fseek** et **_fseeki64** efface l’indicateur de fin de fichier et annule l’effet des appels [ungetc](ungetc-ungetwc.md) antérieurs sur *Stream*.

Quand un fichier est ouvert pour un ajout de données, la position de fichier actuelle est déterminée par la dernière opération d’E/S, pas par l’emplacement auquel l’écriture suivante se produirait. Si aucune opération d’E/S ne s’est produite sur un fichier ouvert pour un ajout, la position de fichier correspond au début du fichier.

Pour les flux ouverts en mode texte, **fseek** et **_fseeki64** ont une utilisation limitée, car les traductions de retour chariot-saut de ligne peuvent entraîner des résultats inattendus pour les **fseek** et les **_fseeki64** . Les seules opérations **fseek** et **_fseeki64** garanties de fonctionner sur les flux ouverts en mode texte sont les suivantes :

- Recherche avec un décalage de 0 par rapport à toute valeur d’origine.

- Recherche à partir du début du fichier avec une valeur de décalage retournée par un appel à [ftell](ftell-ftelli64.md) lors de l’utilisation de **fseek** ou de [_ftelli64](ftell-ftelli64.md) lors de l’utilisation de **_fseeki64**.

Également en mode texte, Ctrl+Z est interprété comme un caractère de fin de fichier en entrée. Dans les fichiers ouverts en lecture/écriture, [fopen](fopen-wfopen.md) et toutes les routines associées vérifient la disponibilité d’un Ctrl + Z à la fin du fichier et le suppriment si possible. Cela est dû au fait que l’utilisation de la combinaison de **fseek** et [ftell](ftell-ftelli64.md) ou **_fseeki64** et [_ftelli64](ftell-ftelli64.md), pour se déplacer dans un fichier qui se termine par un Ctrl + Z peut provoquer un comportement incorrect de **fseek** ou de **_fseeki64** vers la fin du fichier.

Quand la bibliothèque CRT ouvre un fichier qui commence par une marque d’ordre d’octet, le pointeur de fichier est positionné après la marque (autrement dit, au début du contenu réel du fichier). Si vous devez **fseek** au début du fichier, utilisez [ftell](ftell-ftelli64.md) pour obtenir la position initiale et **fseek** plutôt que de positionner 0.

Cette fonction verrouille les autres threads pendant l’exécution et est donc thread-safe. Pour une version sans verrouillage, consultez [_fseek_nolock, _fseeki64_nolock](fseek-nolock-fseeki64-nolock.md).

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Fonction|En-tête requis|
|--------------|---------------------|
|**fseek**|\<stdio.h>|
|**_fseeki64**|\<stdio.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

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
[Rewind](rewind.md)<br/>
