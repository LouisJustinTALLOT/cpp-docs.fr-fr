---
title: clearerr_s | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- clearerr_s
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
- clearerr_s
dev_langs:
- C++
helpviewer_keywords:
- error indicator for streams
- resetting stream error indicator
- clearerr_s function
ms.assetid: b74d014d-b7a8-494a-a330-e5ffd5614772
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 34feccd2d4d6de53ed9c5a446bf6c7d065dd4e62
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2018
ms.locfileid: "34450864"
---
# <a name="clearerrs"></a>clearerr_s

Réinitialiser l’indicateur d’erreur pour un flux. Il s’agit d’une version de [clearerr](clearerr.md) assortie des améliorations de sécurité décrites dans [Fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t clearerr_s(
   FILE *stream
);
```

### <a name="parameters"></a>Paramètres

*Flux de données*<br/>
Pointeur vers **fichier** structure

## <a name="return-value"></a>Valeur de retour

Zéro en cas de réussite ; **EINVAL** si *flux* est **NULL**.

## <a name="remarks"></a>Notes

Le **clearerr_s** fonction réinitialise l’indicateur d’erreur et l’indicateur de fin de fichier pour *flux*. Indicateurs d’erreur ne sont pas automatiquement supprimées ; une fois que l’indicateur d’erreur pour un flux de données spécifié est défini, les opérations sur ce flux de données continuent à retourner une valeur d’erreur jusqu'à ce que **clearerr_s**, **clearerr**, [fseek](fseek-fseeki64.md), **fsetpos**, ou [rembobiner](rewind.md) est appelée.

Si *flux* est **NULL**, le Gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, cette fonction affecte **errno** à **EINVAL** et retourne **EINVAL**.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**clearerr_s**|\<stdio.h>|

Pour plus d’informations sur la compatibilité, voir consultez [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_clearerr_s.c
// This program creates an error
// on the standard input stream, then clears
// it so that future reads won't fail.

#include <stdio.h>

int main( void )
{
   int c;
   errno_t err;

   // Create an error by writing to standard input.
   putc( 'c', stdin );
   if( ferror( stdin ) )
   {
      perror( "Write error" );
      err = clearerr_s( stdin );
      if (err != 0)
      {
         abort();
      }
   }

   // See if read causes an error.
   printf( "Will input cause an error? " );
   c = getc( stdin );
   if( ferror( stdin ) )
   {
      perror( "Read error" );
      err = clearerr_s( stdin );
      if (err != 0)
      {
         abort();
      }
   }
}
```

```Output

n

```

```Output

      nWrite error: Bad file descriptor
Will input cause an error? n
```

## <a name="see-also"></a>Voir aussi

[Gestion des erreurs](../../c-runtime-library/error-handling-crt.md)<br/>
[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[clearerr](clearerr.md)<br/>
[_eof](eof.md)<br/>
[feof](feof.md)<br/>
[ferror](ferror.md)<br/>
[perror, _wperror](perror-wperror.md)<br/>
