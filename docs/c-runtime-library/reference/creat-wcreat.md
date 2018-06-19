---
title: _creat, _wcreat | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _creat
- _wcreat
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
- wcreat
- _wcreat
- _creat
- tcreat
- _tcreat
dev_langs:
- C++
helpviewer_keywords:
- wcreat function
- _wcreat function
- files [C++], creating
- _creat function
- tcreat function
- creat function
- _tcreat function
ms.assetid: 3b3b795d-1620-40ec-bd2b-a4bbb0d20fe5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1a6b987faa30439f0f374838fe7fcd4d942b8cc7
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2018
ms.locfileid: "34451847"
---
# <a name="creat-wcreat"></a>_creat, _wcreat

Crée un fichier. **_creat** et **_wcreat** ont été déconseillées ; utilisez [_sopen_s, _wsopen_s](sopen-s-wsopen-s.md) à la place.

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

*filename*<br/>
Nom du nouveau fichier.

*pmode*<br/>
Paramètre d'autorisation.

## <a name="return-value"></a>Valeur de retour

Ces fonctions, en cas de réussite, retournent un descripteur de fichier pour le fichier créé. Dans le cas contraire, les fonctions retournent -1 et la valeur **errno** comme indiqué dans le tableau suivant.

|**errno** paramètre|Description|
|---------------------|-----------------|
|**EACCES**|*nom de fichier* spécifie un fichier en lecture seule existant ou un répertoire au lieu d’un fichier.|
|**EMFILE**|Aucun autre descripteur de fichier n'est disponible.|
|**ENOENT**|Le fichier spécifié est introuvable.|

Si *nom de fichier* est **NULL**, ces fonctions appellent le Gestionnaire de paramètre non valide, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions définissent **errno** à **EINVAL** et retournent -1.

Pour plus d'informations sur ces codes de retour et autres, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

Le **_creat** fonction crée un nouveau fichier ou s’ouvre et tronque une existante. **_wcreat** est une version à caractères larges de **_creat**; le *nom de fichier* argument **_wcreat** est une chaîne à caractères larges. **_wcreat** et **_creat** comportent de façon identique.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcreat**|**_creat**|**_creat**|**_wcreat**|

Si le fichier spécifié par *nom de fichier* n’existe pas, un nouveau fichier est créé avec le paramètre d’autorisation donné et est ouvert en écriture. Si le fichier existe déjà et si son paramètre d’autorisation autorise l’écriture, **_creat** tronque le fichier de longueur 0, détruire le contenu précédent et s’ouvre pour écriture. Le paramètre d’autorisation, *pmode*, s’applique aux fichiers qui vient d’être créés uniquement. Le nouveau fichier reçoit le paramètre d’autorisation spécifié après sa première fermeture. L’expression d’entier *pmode* contient moins le des constantes de manifeste **_S_IWRITE** et **_S_IREAD**, définie dans sys\stat.h. Lorsque les deux constantes sont données, elles sont jointes avec l’opérateur de bits or (opérateur) ( **&#124;** ). Le *pmode* est affectée à une des valeurs suivantes.

|Value|Définition|
|-----------|----------------|
|**_S_IWRITE**|Écriture autorisée.|
|**_S_IREAD**|Lecture autorisée.|
|**_S_IREAD** &AMP;#124; **_S_IWRITE**|Lecture et écriture autorisées.|

Si l'autorisation d'écriture n'est pas accordée, le fichier est en lecture seule. Tous les fichiers sont toujours accessibles en lecture ; il est impossible d’accorder l’autorisation en écriture seule. Les modes **_S_IWRITE** et **_S_IREAD** | **_S_IWRITE** sont ensuite équivalent. Fichiers ouverts à l’aide de **_creat** sont toujours ouverts en mode de compatibilité (consultez [_sopen](sopen-wsopen.md)) avec **_SH_DENYNO**.

**_creat** s’applique le masque d’autorisation de fichier actif à *pmode* avant de définir les autorisations (voir [_umask](umask.md)). **_creat** est fourni principalement pour la compatibilité avec les bibliothèques précédentes. Un appel à **_open** avec **_O_CREAT** et **_O_TRUNC** dans les *oflag* paramètre équivaut à **_creat**et il est préférable pour le nouveau code.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|En-tête facultatif|
|-------------|---------------------|---------------------|
|**_creat**|\<io.h>|\<sys/types.h>, \<sys/stat.h>, \<errno.h>|
|**_wcreat**|\<io.h> ou \<wchar.h>|\<sys/types.h>, \<sys/stat.h>, \<errno.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

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

[E/S de bas niveau](../../c-runtime-library/low-level-i-o.md)<br/>
[_chmod, _wchmod](chmod-wchmod.md)<br/>
[_chsize](chsize.md)<br/>
[_close](close.md)<br/>
[_dup, _dup2](dup-dup2.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_sopen, _wsopen](sopen-wsopen.md)<br/>
[_umask](umask.md)<br/>
