---
title: _creat, _wcreat
ms.date: 4/2/2020
api_name:
- _creat
- _wcreat
- _o__creat
- _o__wcreat
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
- wcreat
- _wcreat
- _creat
- tcreat
- _tcreat
helpviewer_keywords:
- wcreat function
- _wcreat function
- files [C++], creating
- _creat function
- tcreat function
- creat function
- _tcreat function
ms.assetid: 3b3b795d-1620-40ec-bd2b-a4bbb0d20fe5
ms.openlocfilehash: 379a4adbf17755341fed6a48c649afe29e150fe5
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82912110"
---
# <a name="_creat-_wcreat"></a>_creat, _wcreat

Crée un nouveau fichier. **_creat** et **_wcreat** ont été dépréciés ; Utilisez [_sopen_s, _wsopen_s](sopen-s-wsopen-s.md) à la place.

## <a name="syntax"></a>Syntaxe

```C
int _creat(
   const char *filename,
   int pmode
);
int _wcreat(
   const wchar_t *filename,
   int pmode
);
```

### <a name="parameters"></a>Paramètres

*extension*<br/>
Nom du nouveau fichier.

*pmode*<br/>
Paramètre d'autorisation.

## <a name="return-value"></a>Valeur de retour

Ces fonctions, en cas de réussite, retournent un descripteur de fichier pour le fichier créé. Sinon, les fonctions retournent-1 et définissent **errno** comme indiqué dans le tableau suivant.

|paramètre **errno**|Description|
|---------------------|-----------------|
|**EACCES**|*filename* spécifie un fichier en lecture seule existant ou spécifie un répertoire au lieu d’un fichier.|
|**EMFILE**|Aucun autre descripteur de fichier n'est disponible.|
|**ENOENT**|Le fichier spécifié est introuvable.|

Si *filename* a la **valeur null**, ces fonctions appellent le gestionnaire de paramètres non valides, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions définissent **errno** sur **EINVAL** et retournent-1.

Pour plus d’informations sur ces codes de retour et les autres, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes 

La fonction **_creat** crée un nouveau fichier ou ouvre et tronque un fichier existant. **_wcreat** est une version à caractères larges de **_creat**; l’argument de *nom de fichier* pour **_wcreat** est une chaîne de caractères larges. dans le cas contraire, **_wcreat** et **_creat** se comportent de la même façon.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcreat**|**_creat**|**_creat**|**_wcreat**|

Si le fichier spécifié par *filename* n’existe pas, un nouveau fichier est créé avec le paramètre d’autorisation donné et est ouvert en écriture. Si le fichier existe déjà et que son paramètre d’autorisation autorise l’écriture, **_creat** tronque le fichier à la longueur 0, en détruisant le contenu précédent et en l’ouvrant pour écriture. Le paramètre d’autorisation, *PMODE*, s’applique uniquement aux fichiers nouvellement créés. Le nouveau fichier reçoit le paramètre d’autorisation spécifié après sa première fermeture. L’expression entière *PMODE* contient l’une des constantes manifestes, ou les deux, **_S_IWRITE** et les **_S_IREAD**, définis dans SYS\Stat.h. Quand les deux constantes sont données, elles sont jointes avec l’opérateur or au niveau du bit ( **&#124;** ). Le paramètre *PMODE* est défini sur l’une des valeurs suivantes.

|Value|Définition|
|-----------|----------------|
|**_S_IWRITE**|Écriture autorisée.|
|**_S_IREAD**|Lecture autorisée.|
|**_S_IREAD** &#124; **_S_IWRITE**|Lecture et écriture autorisées.|

Si l'autorisation d'écriture n'est pas accordée, le fichier est en lecture seule. Tous les fichiers sont toujours accessibles en lecture ; il est impossible d’accorder l’autorisation en écriture seule. Les modes **_S_IWRITE** et **_S_IREAD** | **_S_IWRITE** sont alors équivalents. Les fichiers ouverts à l’aide de **_creat** sont toujours ouverts en mode de compatibilité (consultez [_sopen](sopen-wsopen.md)) avec **_SH_DENYNO**.

**_creat** applique le masque d’autorisation de fichier actuel à *PMODE* avant de définir les autorisations (consultez [_umask](umask.md)). **_creat** est fourni principalement pour la compatibilité avec les bibliothèques précédentes. Un appel à **_open** avec **_O_CREAT** et **_O_TRUNC** dans le paramètre *Oflag* est équivalent à **_creat** et est préférable pour le nouveau code.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|En-tête facultatif|
|-------------|---------------------|---------------------|
|**_creat**|\<io.h>|\<sys/types.h>, \<sys/stat.h>, \<errno.h>|
|**_wcreat**|\<io.h> ou \<wchar.h>|\<sys/types.h>, \<sys/stat.h>, \<errno.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_creat.c
// compile with: /W3
// This program uses _creat to create
// the file (or truncate the existing file)
// named data and open it for writing.

#include <sys/types.h>
#include <sys/stat.h>
#include <io.h>
#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   int fh;

   fh = _creat( "data", _S_IREAD | _S_IWRITE ); // C4996
   // Note: _creat is deprecated; use _sopen_s instead
   if( fh == -1 )
      perror( "Couldn't create data file" );
   else
   {
      printf( "Created data file.\n" );
      _close( fh );
   }
}
```

```Output
Created data file.
```

## <a name="see-also"></a>Voir aussi

[E/S niveau bas](../../c-runtime-library/low-level-i-o.md)<br/>
[_chmod, _wchmod](chmod-wchmod.md)<br/>
[_chsize](chsize.md)<br/>
[_close](close.md)<br/>
[_dup, _dup2](dup-dup2.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_sopen, _wsopen](sopen-wsopen.md)<br/>
[_umask](umask.md)<br/>
