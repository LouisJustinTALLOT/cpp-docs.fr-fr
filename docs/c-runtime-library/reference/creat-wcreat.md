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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 18ecf78d2cbff3647eae912a1bb1b17d5340f185
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348337"
---
# <a name="_creat-_wcreat"></a>_creat, _wcreat

Crée un nouveau fichier. **_creat** et **_wcreat** ont été dépréciés; utiliser [_sopen_s, _wsopen_s](sopen-s-wsopen-s.md) à la place.

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

*Fichier*<br/>
Nom du nouveau fichier.

*pmode*<br/>
Paramètre d'autorisation.

## <a name="return-value"></a>Valeur de retour

Ces fonctions, en cas de réussite, retournent un descripteur de fichier pour le fichier créé. Sinon, les fonctions retournent -1 et **placent errno** comme indiqué dans le tableau suivant.

|**réglage errno**|Description|
|---------------------|-----------------|
|**LES EACCES**|*nom de fichier* spécifie un fichier existant de lecture seulement ou spécifie un répertoire au lieu d’un fichier.|
|**EMFILE**|Aucun autre descripteur de fichier n'est disponible.|
|**ENOENT (ENOENT)**|Le fichier spécifié est introuvable.|

Si *le nom de fichier* est **NULL**, ces fonctions invoquent le gestionnaire de paramètres invalides, tel que décrit dans La validation [des paramètres](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions **définies errno** à **EINVAL** et retour -1.

Pour plus d’informations sur ces codes de retour et les autres, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

La fonction **_creat** crée un nouveau fichier ou ouvre et tronque un fichier existant. **_wcreat** est une version à caractère large de **_creat**; l’argument *du nom de fichier* pour **_wcreat** est une chaîne de caractère large. **_wcreat** et **_creat** se comportent de façon identique autrement.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcreat**|**_creat**|**_creat**|**_wcreat**|

Si le fichier spécifié par *nom de fichier* n’existe pas, un nouveau fichier est créé avec le paramètre d’autorisation donné et est ouvert pour l’écriture. Si le fichier existe déjà et que son paramètre d’autorisation permet d’écrire, **_creat** tronque le fichier à la longueur 0, détruisant le contenu précédent, et l’ouvre pour l’écriture. Le paramètre d’autorisation, *pmode*, s’applique uniquement aux fichiers nouvellement créés. Le nouveau fichier reçoit le paramètre d’autorisation spécifié après sa première fermeture. L’expression *integer pmode* contient une ou les deux constantes manifestes **_S_IWRITE** et **_S_IREAD**, définies dans SYS-Stat.h. Lorsque les deux constantes sont données, elles sont jointes avec le bitwise ou l’opérateur **(&#124;** ). Le *paramètre pmode* est réglé sur l’une des valeurs suivantes.

|Value|Définition|
|-----------|----------------|
|**_S_IWRITE**|Écriture autorisée.|
|**_S_IREAD**|Lecture autorisée.|
|**_S_IREAD** **_S_IWRITE** &#124;|Lecture et écriture autorisées.|

Si l'autorisation d'écriture n'est pas accordée, le fichier est en lecture seule. Tous les fichiers sont toujours accessibles en lecture ; il est impossible d’accorder l’autorisation en écriture seule. Les modes **_S_IWRITE** et **_S_IREAD** | **_S_IWRITE** sont alors équivalents. Les fichiers ouverts à **l’aide de _creat** sont toujours ouverts en mode compatibilité (voir [_sopen)](sopen-wsopen.md)avec **_SH_DENYNO**.

**_creat** applique le masque actuel d’autorisation de fichier à *hode* avant de définir les autorisations (voir [_umask](umask.md)). **_creat** est principalement fournie pour la compatibilité avec les bibliothèques précédentes. Un appel à **_open** avec **_O_CREAT** et **_O_TRUNC** dans le paramètre *oflag* est équivalent à **_creat** et est préférable pour un nouveau code.

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
