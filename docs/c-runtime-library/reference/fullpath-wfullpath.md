---
title: _fullpath, _wfullpath | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _fullpath
- _wfullpath
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
- api-ms-win-crt-filesystem-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- wfullpath
- fullpath
- _wfullpath
- _fullpath
dev_langs:
- C++
helpviewer_keywords:
- _wfullpath function
- relative file paths
- absolute paths
- wfullpath function
- _fullpath function
- fullpath function
ms.assetid: 4161ec17-0d22-45dd-b07d-0222553afae9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b472987b0cac41c57e5fd22b2eedecef522613b4
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2018
---
# <a name="fullpath-wfullpath"></a>_fullpath, _wfullpath

Créer un nom de chemin absolu ou complet pour le nom de chemin relatif spécifié.

## <a name="syntax"></a>Syntaxe

```C
char *_fullpath(
   char *absPath,
   const char *relPath,
   size_t maxLength
);
wchar_t *_wfullpath(
   wchar_t *absPath,
   const wchar_t *relPath,
   size_t maxLength
);
```

### <a name="parameters"></a>Paramètres

*absPath*<br/>
Pointeur vers une mémoire tampon contenant le nom de chemin d’accès absolu ou complet, ou **NULL**.

*relPath*<br/>
Nom de chemin d’accès relatif.

*maxLength*<br/>
Longueur maximale du tampon du nom de chemin d’accès absolu (*absPath*). Cette longueur est exprimée en octets pour **_fullpath** mais en caractères larges (**wchar_t**) pour **_wfullpath**.

## <a name="return-value"></a>Valeur de retour

Chacune de ces fonctions retourne un pointeur vers une mémoire tampon contenant le nom de chemin d’accès absolu (*absPath*). S’il existe une erreur (par exemple, si la valeur passée dans *relPath* comprend une lettre de lecteur qui n’est pas valide ou est introuvable, ou si la longueur du nom de chemin d’accès absolu créé (*absPath*) est supérieur à *maxLength*), la fonction retourne **NULL**.

## <a name="remarks"></a>Notes

Le **_fullpath** développe le nom de chemin d’accès relatif dans *relPath* et son chemin d’accès complet ou absolu stocke ce nom dans *absPath*. Si *absPath* est **NULL**, **malloc** est utilisé pour allouer une mémoire tampon de longueur suffisante pour contenir le nom de chemin d’accès. Il incombe à l’appelant de libérer cette mémoire tampon. Un nom de chemin relatif spécifie un chemin vers un autre emplacement à partir de l’emplacement actuel (tel que le répertoire de travail actuel : « . »). Un nom de chemin absolu est l’extension d’un nom de chemin relatif qui indique le chemin complet requis pour atteindre l’emplacement souhaité à partir de la racine du système de fichiers. Contrairement aux **_makepath**, **_fullpath** peut être utilisé pour obtenir le nom de chemin d’accès absolu pour les chemins d’accès relatifs (*relPath*) qui incluent «. / « ou ».. / » dans leur nom.

Par exemple, pour utiliser les routines du runtime C, l’application doit inclure les fichiers d’en-tête qui contiennent les déclarations pour les routines. Chaque instruction include du fichier d’en-tête référence l’emplacement du fichier de manière relative (à partir du répertoire de travail de l’application) :

```C
#include <stdlib.h>
```

quand le chemin absolu (emplacement de système de fichiers actuel) du fichier peut être :

`\\machine\shareName\msvcSrc\crt\headerFiles\stdlib.h`

**_fullpath** gère automatiquement les arguments de chaîne de caractères multioctets selon le cas, le cas des séquences de caractères multioctets selon la page de codes multioctets en cours d’utilisation. **_wfullpath** est une version à caractères larges de **_fullpath**; les arguments de chaîne pour **_wfullpath** sont des chaînes à caractères larges. **_wfullpath** et **_fullpath** se comportent de façon identique, sauf que **_wfullpath** ne gère pas les chaînes de caractères multioctets.

Si **_DEBUG** et **_CRTDBG_MAP_ALLOC** sont toutes les deux définie, les appels à **_fullpath** et **_wfullpath** sont remplacés par les appels à **_fullpath_dbg** et **_wfullpath_dbg** pour permettre le débogage des allocations de mémoire. Pour plus d’informations, consultez [_fullpath_dbg, _wfullpath_dbg](fullpath-dbg-wfullpath-dbg.md).

Cette fonction appelle le Gestionnaire de paramètre non valide, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md)si *maxlen* est inférieure ou égale à 0. Si l’exécution est autorisée à se poursuivre, cette fonction affecte **errno** à **EINVAL** et retourne **NULL**.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfullpath**|**_fullpath**|**_fullpath**|**_wfullpath**|

Si le *absPath* mémoire tampon est **NULL**, **_fullpath** appelle [malloc](malloc.md) pour allouer une mémoire tampon et ignore le *maxLength*  argument. Il incombe à l’appelant de libérer cette mémoire tampon (à l’aide de [free](free.md)) selon les besoins. Si le *relPath* argument spécifie un lecteur de disque, le répertoire actuel de ce lecteur est combiné avec le chemin d’accès.

## <a name="requirements"></a>Spécifications

|Fonction|En-tête requis|
|--------------|---------------------|
|**_fullpath**|\<stdlib.h>|
|**_wfullpath**|\<stdlib.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_fullpath.c
// This program demonstrates how _fullpath
// creates a full path from a partial path.

#include <stdio.h>
#include <conio.h>
#include <stdlib.h>
#include <direct.h>

void PrintFullPath( char * partialPath )
{
   char full[_MAX_PATH];
   if( _fullpath( full, partialPath, _MAX_PATH ) != NULL )
      printf( "Full path is: %s\n", full );
   else
      printf( "Invalid path\n" );
}

int main( void )
{
   PrintFullPath( "test" );
   PrintFullPath( "\\test" );
   PrintFullPath( "..\\test" );
}
```

```Output
Full path is: C:\Documents and Settings\user\My Documents\test
Full path is: C:\test
Full path is: C:\Documents and Settings\user\test
```

## <a name="see-also"></a>Voir aussi

[Gestion de fichiers](../../c-runtime-library/file-handling.md)<br/>
[_getcwd, _wgetcwd](getcwd-wgetcwd.md)<br/>
[_getdcwd, _wgetdcwd](getdcwd-wgetdcwd.md)<br/>
[_makepath, _wmakepath](makepath-wmakepath.md)<br/>
[_splitpath, _wsplitpath](splitpath-wsplitpath.md)<br/>
