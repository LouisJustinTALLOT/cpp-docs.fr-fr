---
title: _makepath_s, _wmakepath_s
ms.date: 4/2/2020
api_name:
- _wmakepath_s
- _makepath_s
- _o__makepath_s
- _o__wmakepath_s
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
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _wmakepath_s
- makepath_s
- _makepath_s
- wmakepath_s
helpviewer_keywords:
- _makepath_s function
- wmakepath_s function
- paths
- _wmakepath_s function
- makepath_s function
ms.assetid: 4405e43c-3d63-4697-bb80-9b8dcd21d027
ms.openlocfilehash: 3a44651cb9ff8be806c45c6b6c5f41f810319a85
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341600"
---
# <a name="_makepath_s-_wmakepath_s"></a>_makepath_s, _wmakepath_s

Crée un nom de chemin d’accès à partir des composants. Ces versions de [_makepath, _wmakepath](makepath-wmakepath.md) intègrent les améliorations de sécurité décrites dans [Fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t _makepath_s(
   char *path,
   size_t sizeInBytes,
   const char *drive,
   const char *dir,
   const char *fname,
   const char *ext
);
errno_t _wmakepath_s(
   wchar_t *path,
   size_t sizeInWords,
   const wchar_t *drive,
   const wchar_t *dir,
   const wchar_t *fname,
   const wchar_t *ext
);
template <size_t size>
errno_t _makepath_s(
   char (&path)[size],
   const char *drive,
   const char *dir,
   const char *fname,
   const char *ext
); // C++ only
template <size_t size>
errno_t _wmakepath_s(
   wchar_t (&path)[size],
   const wchar_t *drive,
   const wchar_t *dir,
   const wchar_t *fname,
   const wchar_t *ext
); // C++ only
```

### <a name="parameters"></a>Paramètres

*path*<br/>
Mémoire tampon du chemin d'accès complet.

*sizeInWords*<br/>
Taille, en mots, de la mémoire tampon.

*sizeInBytes*<br/>
Taille, en octets, de la mémoire tampon.

*Disque*<br/>
Contient une lettre (A, B, etc.) correspondant au lecteur souhaité et un signe deux-points de fin facultatif. **_makepath_s** insère automatiquement le côlon dans la trajectoire composite s’il manque. Si *le lecteur* est **NULL** ou pointe vers une chaîne vide, aucune lettre d’entraînement n’apparaît dans la chaîne de *trajectoire* composite.

*Dir*<br/>
Contient le chemin d’accès des répertoires, sans l’indicateur de lecteur ou le nom de fichier réel. La barre oblique de fuite est facultative, et soit\\une barre oblique avant (/) ou une barre oblique inverse ( ) ou les deux pourraient être utilisés dans un seul argument *dir.* Si aucune barre oblique finale (/ ou \\) n’est spécifiée, elle est insérée automatiquement. Si *le dir* est **NULL** ou pointe vers une chaîne vide, aucun chemin de répertoire n’est inséré dans la chaîne de *chemin* composite.

*Fname*<br/>
Contient le nom de fichier de base sans les extensions du nom de fichier. Si *la fname* est **NULL** ou indique une chaîne vide, aucun nom de fichier n’est inséré dans la chaîne de *trajectoire* composite.

*Poste*<br/>
Contient l’extension de nom de fichier réelle, avec ou sans point initial (.). **_makepath_s** insère automatiquement la période si elle n’apparaît pas dans *ext*. Si *l’ext* est **NULL** ou pointe vers une chaîne vide, aucune extension n’est insérée dans la chaîne de *trajectoire* composite.

## <a name="return-value"></a>Valeur de retour

Zéro si l'opération a réussi ; code d'erreur en cas de échec.

### <a name="error-conditions"></a>Conditions d'erreur

|*path*|*tailleInWords* / *sizeInBytes*|Renvoie|Contenu du *chemin*|
|------------|------------------------------------|------------|------------------------|
|**Null**|n'importe laquelle|**EINVAL (EN)**|non modifié|
|n'importe laquelle|<= 0|**EINVAL (EN)**|non modifié|

Si une des conditions d’erreur ci-dessus se produit, ces fonctions appellent le gestionnaire de paramètres non valides, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **errno** est réglé sur **EINVAL** et les fonctions **retourneNT EINVAL**. **NULL** est autorisé pour les paramètres *lecteur*, *fname*, et *ext*. Pour plus d’informations sur le comportement lorsque ces paramètres sont des pointeurs nuls ou des chaînes vides, consultez la section Remarques.

## <a name="remarks"></a>Notes

La fonction **_makepath_s** crée une chaîne de chemin composite à partir de composants individuels, le stockage du résultat dans le *chemin*. Le *chemin* peut inclure une lettre d’entraînement, un parcours d’annuaire, un nom de fichier et une extension du nom de fichier. **_wmakepath_s** est une version à caractère large de **_makepath_s**; les arguments pour **_wmakepath_s** sont des chaînes de caractère large. **_wmakepath_s** et **_makepath_s** se comportent de façon identique autrement.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmakepath_s**|**_makepath_s**|**_makepath_s**|**_wmakepath_s**|

*L’argument du chemin* doit indiquer un tampon vide assez grand pour maintenir le chemin complet. Le *chemin* composite ne doit pas être plus grand que la **constante _MAX_PATH,** définie dans Stdlib.h.

Si le chemin est **NULL**, le gestionnaire de paramètre invalide est invoqué, tel que décrit dans [La validation de paramètres](../../c-runtime-library/parameter-validation.md). En outre, **errno** est fixé à **EINVAL**. **Les** valeurs NULL sont autorisées pour tous les autres paramètres.

En C++, l’utilisation de ces fonctions est simplifiée par les surcharges de modèle ; les surcharges peuvent déduire la longueur de la mémoire tampon automatiquement (ce qui évite d’avoir à spécifier un argument taille) et peuvent remplacer automatiquement les fonctions plus anciennes et non sécurisées par leurs équivalentes plus récentes et sécurisées. Pour plus d’informations, consultez [Sécuriser les surcharges de modèle](../../c-runtime-library/secure-template-overloads.md).

Les versions de bibliothèque de débogé de ces fonctions remplissent d’abord le tampon avec 0xFE. Pour désactiver ce comportement, utilisez [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_makepath_s**|\<stdlib.h>|
|**_wmakepath_s**|\<stdlib.h> ou \<wchar.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_makepath_s.c

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char path_buffer[_MAX_PATH];
   char drive[_MAX_DRIVE];
   char dir[_MAX_DIR];
   char fname[_MAX_FNAME];
   char ext[_MAX_EXT];
   errno_t err;

   err = _makepath_s( path_buffer, _MAX_PATH, "c", "\\sample\\crt\\",
                      "crt_makepath_s", "c" );
   if (err != 0)
   {
      printf("Error creating path. Error code %d.\n", err);
      exit(1);
   }
   printf( "Path created with _makepath_s: %s\n\n", path_buffer );
   err = _splitpath_s( path_buffer, drive, _MAX_DRIVE, dir, _MAX_DIR, fname,
                       _MAX_FNAME, ext, _MAX_EXT );
   if (err != 0)
   {
      printf("Error splitting the path. Error code %d.\n", err);
      exit(1);
   }
   printf( "Path extracted with _splitpath_s:\n" );
   printf( "   Drive: %s\n", drive );
   printf( "   Dir: %s\n", dir );
   printf( "   Filename: %s\n", fname );
   printf( "   Ext: %s\n", ext );
}
```

```Output
Path created with _makepath_s: c:\sample\crt\crt_makepath_s.c

Path extracted with _splitpath_s:
   Drive: c:
   Dir: \sample\crt\
   Filename: crt_makepath_s
   Ext: .c
```

## <a name="see-also"></a>Voir aussi

[Gestion de fichiers](../../c-runtime-library/file-handling.md)<br/>
[_fullpath, _wfullpath](fullpath-wfullpath.md)<br/>
[_splitpath_s, _wsplitpath_s](splitpath-s-wsplitpath-s.md)<br/>
[_makepath, _wmakepath](makepath-wmakepath.md)<br/>
