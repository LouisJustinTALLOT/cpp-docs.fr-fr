---
title: _makepath_s, _wmakepath_s
ms.date: 11/04/2016
apiname:
- _wmakepath_s
- _makepath_s
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
- ntoskrnl.exe
apitype: DLLExport
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
ms.openlocfilehash: 3536569fd3e77a353003e1372d5dc4ee6e4ee3fb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62156926"
---
# <a name="makepaths-wmakepaths"></a>_makepath_s, _wmakepath_s

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
Mémoire tampon du chemin d’accès complet.

*sizeInWords*<br/>
Taille, en mots, de la mémoire tampon.

*sizeInBytes*<br/>
Taille, en octets, de la mémoire tampon.

*drive*<br/>
Contient une lettre (A, B, etc.) correspondant au lecteur souhaité et un signe deux-points de fin facultatif. **_makepath_s** insère automatiquement le signe deux-points dans le chemin d’accès composite s’il est manquant. Si *lecteur* est **NULL** ou pointe vers une chaîne vide, aucune lettre de lecteur s’affiche dans le service composite *chemin d’accès* chaîne.

*dir*<br/>
Contient le chemin d’accès des répertoires, sans l’indicateur de lecteur ou le nom de fichier réel. La barre oblique de fin est facultative et une barre oblique (/) ou une barre oblique inverse (\\) ou les deux peuvent être utilisées dans un seul *dir* argument. Si aucune barre oblique finale (/ ou \\) n’est spécifiée, elle est insérée automatiquement. Si *dir* est **NULL** ou pointe vers une chaîne vide, aucun chemin d’accès du répertoire est inséré dans le service composite *chemin d’accès* chaîne.

*fname*<br/>
Contient le nom de fichier de base sans les extensions du nom de fichier. Si *fname* est **NULL** ou pointe vers une chaîne vide, aucun nom de fichier est inséré dans le service composite *chemin d’accès* chaîne.

*ext*<br/>
Contient l’extension de nom de fichier réelle, avec ou sans point initial (.). **_makepath_s** insère automatiquement la période si elle n’apparaît pas dans *ext*. Si *ext* est **NULL** ou pointe vers une chaîne vide, aucune extension est inséré dans le service composite *chemin d’accès* chaîne.

## <a name="return-value"></a>Valeur de retour

Zéro si l'opération a réussi ; code d'erreur en cas de échec.

### <a name="error-conditions"></a>Conditions d’erreur

|*path*|*sizeInWords* / *sizeInBytes*|Retourner|Contenu de *chemin d’accès*|
|------------|------------------------------------|------------|------------------------|
|**NULL**|any|**EINVAL**|non modifié|
|any|<= 0|**EINVAL**|non modifié|

Si une des conditions d’erreur ci-dessus se produit, ces fonctions appellent le gestionnaire de paramètres non valides, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **errno** a la valeur **EINVAL** et les fonctions retournent **EINVAL**. **NULL** est autorisée pour les paramètres *lecteur*, *fname*, et *ext*. Pour plus d'informations sur le comportement lorsque ces paramètres sont des pointeurs null ou des chaînes vides, consultez la section Notes.

## <a name="remarks"></a>Notes

Le **_makepath_s** fonction crée une chaîne de chemin d’accès composite à partir des composants individuels, en stockant le résultat dans *chemin d’accès*. Le *chemin d’accès* peut inclure une lettre de lecteur, chemin d’accès du répertoire, fichier, nom et extension de fichier. **_wmakepath_s** est une version à caractères larges de **_makepath_s**; les arguments de **_wmakepath_s** sont des chaînes à caractères larges. **_wmakepath_s** et **_makepath_s** se comportent de façon identique dans le cas contraire.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmakepath_s**|**_makepath_s**|**_makepath_s**|**_wmakepath_s**|

Le *chemin d’accès* argument doit pointer vers une mémoire tampon vide suffisamment grande pour contenir le chemin d’accès complet. Le service composite *chemin d’accès* doit pas être supérieure à la **_MAX_PATH** constante, définie dans Stdlib.h.

Si le chemin d’accès est **NULL**, le Gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). En outre, **errno** a la valeur **EINVAL**. **NULL** valeurs sont autorisées pour tous les autres paramètres.

En C++, l’utilisation de ces fonctions est simplifiée par les surcharges de modèle ; les surcharges peuvent déduire la longueur de la mémoire tampon automatiquement (ce qui évite d’avoir à spécifier un argument taille) et peuvent remplacer automatiquement les fonctions plus anciennes et non sécurisées par leurs équivalentes plus récentes et sécurisées. Pour plus d'informations, consultez [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

Les versions debug de ces fonctions remplissent d'abord la mémoire tampon avec 0xFD. Pour désactiver ce comportement, utilisez [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**_makepath_s**|\<stdlib.h>|
|**_wmakepath_s**|\<stdlib.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

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
