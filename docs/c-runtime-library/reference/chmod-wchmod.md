---
title: _chmod, _wchmod
ms.date: 11/04/2016
api_name:
- _chmod
- _wchmod
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
- api-ms-win-crt-filesystem-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _chmod
- _wchmod
- wchmod
helpviewer_keywords:
- _chmod function
- wchmod function
- file permissions [C++]
- chmod function
- files [C++], changing permissions
- _wchmod function
ms.assetid: 92f7cb86-b3b0-4232-a599-b8c04a2f2c19
ms.openlocfilehash: b224133212f19627a8f975dbbe8c80176e29f112
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939203"
---
# <a name="_chmod-_wchmod"></a>_chmod, _wchmod

Modifie les paramètres d’autorisation de fichier.

## <a name="syntax"></a>Syntaxe

```C
int _chmod( const char *filename, int pmode );
int _wchmod( const wchar_t *filename, int pmode );
```

### <a name="parameters"></a>Paramètres

*filename*<br/>
Nom du fichier existant.

*pmode*<br/>
Paramètre d’autorisation pour le fichier.

## <a name="return-value"></a>Valeur de retour

Ces fonctions retournent 0 si le paramètre d’autorisation a été correctement modifié. Une valeur de retour de-1 indique un échec. Si le fichier spécifié est introuvable, **errno** a la valeur **ENOENT**; Si un paramètre n’est pas valide, **errno** a la valeur **EINVAL**.

## <a name="remarks"></a>Notes

La fonction **_CHMOD** modifie le paramètre d’autorisation du fichier spécifié par *filename*. Le paramètre d’autorisation contrôle l’accès en lecture et écriture au fichier. L’expression entière *PMODE* contient l’une des constantes manifestes suivantes (ou les deux), définie dans SYS\Stat.h.

| *pmode* | Signification |
|-|-|
| **\_\_IREAD** | Lecture autorisée uniquement. |
| **\_\_IWRITE** | Écriture autorisée. (En fait, autorise la lecture et l'écriture.) |
| **\_S\_IREAD** &#124; **SIWRITE\_ \_** | Lecture et écriture autorisées. |

Quand les deux constantes sont données, elles sont jointes avec l’opérateur or **\|** au niveau du bit (). Si l'autorisation d'écriture n'est pas accordée, le fichier est en lecture seule. Notez que tous les fichiers sont toujours accessibles en lecture ; il est impossible d’accorder l’autorisation en écriture seule. Ainsi, les modes **_S_IWRITE** et **_S_IREAD** \| **_S_IWRITE** sont équivalents.

**_wchmod** est une version à caractères larges de **_CHMOD**; l’argument *filename* de **_wchmod** est une chaîne de caractères larges. dans le cas contraire, **_wchmod** et **_CHMOD** se comportent de la même façon.

Cette fonction valide ses paramètres. Si *PMODE* n’est pas une combinaison de l’une des constantes manifestes ou incorpore un autre ensemble de constantes, la fonction ignore simplement celles-ci. Si *filename* a la **valeur null**, le gestionnaire de paramètres non valides est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **errno** a la valeur **EINVAL** et la fonction retourne-1.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tchmod**|**_chmod**|**_chmod**|**_wchmod**|

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|En-tête facultatif|
|-------------|---------------------|---------------------|
|**_chmod**|\<io.h>|\<sys/types.h>, \<sys/stat.h>, \<errno.h>|
|**_wchmod**|\<io.h> ou \<wchar.h>|\<sys/types.h>, \<sys/stat.h>, \<errno.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_chmod.c
// This program uses _chmod to
// change the mode of a file to read-only.
// It then attempts to modify the file.
//

#include <sys/types.h>
#include <sys/stat.h>
#include <io.h>
#include <stdio.h>
#include <stdlib.h>
#include <errno.h>

// Change the mode and report error or success
void set_mode_and_report(char * filename, int mask)
{
   // Check for failure
   if( _chmod( filename, mask ) == -1 )
   {
      // Determine cause of failure and report.
      switch (errno)
      {
         case EINVAL:
            fprintf( stderr, "Invalid parameter to chmod.\n");
            break;
         case ENOENT:
            fprintf( stderr, "File %s not found\n", filename );
            break;
         default:
            // Should never be reached
            fprintf( stderr, "Unexpected error in chmod.\n" );
       }
   }
   else
   {
      if (mask == _S_IREAD)
        printf( "Mode set to read-only\n" );
      else if (mask & _S_IWRITE)
        printf( "Mode set to read/write\n" );
   }
   fflush(stderr);
}

int main( void )
{

   // Create or append to a file.
   system( "echo /* End of file */ >> crt_chmod.c_input" );

   // Set file mode to read-only:
   set_mode_and_report("crt_chmod.c_input ", _S_IREAD );

   system( "echo /* End of file */ >> crt_chmod.c_input " );

   // Change back to read/write:
   set_mode_and_report("crt_chmod.c_input ", _S_IWRITE );

   system( "echo /* End of file */ >> crt_chmod.c_input " );
}
```

```Output

A line of text.
```

```Output

      A line of text.Mode set to read-only
Access is denied.
Mode set to read/write
```

## <a name="see-also"></a>Voir aussi

[Gestion de fichiers](../../c-runtime-library/file-handling.md)<br/>
[_access, _waccess](access-waccess.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32](fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_stat, _wstat, fonctions](stat-functions.md)<br/>
