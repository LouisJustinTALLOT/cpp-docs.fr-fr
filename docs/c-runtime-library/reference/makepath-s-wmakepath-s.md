---
title: _makepath_s, _wmakepath_s | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
apitype: DLLExport
f1_keywords:
- _wmakepath_s
- makepath_s
- _makepath_s
- wmakepath_s
dev_langs: C++
helpviewer_keywords:
- _makepath_s function
- wmakepath_s function
- paths
- _wmakepath_s function
- makepath_s function
ms.assetid: 4405e43c-3d63-4697-bb80-9b8dcd21d027
caps.latest.revision: "29"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0e3a2885adffda35b4e55117b5ffa591ecf487c0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="makepaths-wmakepaths"></a>_makepath_s, _wmakepath_s
Crée un nom de chemin d’accès à partir des composants. Ces versions de [_makepath, _wmakepath](../../c-runtime-library/reference/makepath-wmakepath.md) intègrent les améliorations de sécurité décrites dans [Fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
  
#### <a name="parameters"></a>Paramètres  
 [out] `path`  
 Mémoire tampon du chemin d'accès complet.  
  
 [in] `sizeInWords`  
 Taille, en mots, de la mémoire tampon.  
  
 [in] `sizeInBytes`  
 Taille, en octets, de la mémoire tampon.  
  
 [in] `drive`  
 Contient une lettre (A, B, etc.) correspondant au lecteur souhaité et un signe deux-points de fin facultatif. `_makepath_s` insère automatiquement le signe deux-points dans le chemin d'accès composite s'il est manquant. Si `drive` a la valeur `NULL` ou pointe vers une chaîne vide, aucune lettre de lecteur ne s'affiche dans la chaîne composite `path`.  
  
 [in] `dir`  
 Contient le chemin d’accès des répertoires, sans l’indicateur de lecteur ou le nom de fichier réel. La barre oblique finale est facultative, et une barre oblique (/) ou une barre oblique inverse (\\) ou les deux peuvent être utilisées dans un seul argument `dir`. Si aucune barre oblique finale (/ ou \\) n’est spécifiée, elle est insérée automatiquement. Si `dir` a la valeur `NULL` ou pointe vers une chaîne vide, aucun chemin d'accès de répertoire n'est inséré dans la chaîne composite `path`.  
  
 [in] `fname`  
 Contient le nom de fichier de base sans les extensions du nom de fichier. Si `fname` a la valeur `NULL` ou pointe vers une chaîne vide, aucun nom de fichier n'est inséré dans la chaîne composite `path`.  
  
 [in] `ext`  
 Contient l'extension de nom de fichier réelle, avec ou sans point initial (.). `_makepath_s` insère automatiquement le point s'il n'apparaît pas dans `ext`. Si `ext` a la valeur `NULL` ou pointe vers une chaîne vide, aucune extension n'est insérée dans la chaîne composite `path`.  
  
## <a name="return-value"></a>Valeur de retour  
 Zéro si l'opération a réussi ; code d'erreur en cas de échec.  
  
### <a name="error-conditions"></a>Conditions d’erreur  
  
|`path`|`sizeInWords` / `sizeInBytes`|Retourner|Contenu de `path`|  
|------------|------------------------------------|------------|------------------------|  
|`NULL`|any|`EINVAL`|non modifié|  
|any|<= 0|`EINVAL`|non modifié|  
  
 Si une des conditions d’erreur ci-dessus se produit, ces fonctions appellent le gestionnaire de paramètres non valides, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, `errno` est défini sur `EINVAL` et la fonction retourne `EINVAL`. `NULL` est autorisé pour les paramètres `drive`, `fname` et `ext`. Pour plus d'informations sur le comportement lorsque ces paramètres sont des pointeurs null ou des chaînes vides, consultez la section Notes.  
  
## <a name="remarks"></a>Notes  
 La fonction `_makepath_s` crée une chaîne de chemin d'accès composite à partir de chaque composant, en stockant le résultat dans `path`. `path` peut inclure une lettre de lecteur, un chemin d'accès de répertoire, un nom de fichier et une extension de nom de fichier. `_wmakepath_s` est une version à caractères larges de `_makepath_s` ; les arguments de `_wmakepath_s` sont des chaînes à caractères larges. Sinon, `_wmakepath_s` et `_makepath_s` se comportent de la même façon.  
  
### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique  
  
|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tmakepath_s`|`_makepath_s`|`_makepath_s`|`_wmakepath_s`|  
  
 L'argument `path` doit pointer vers une mémoire tampon vide suffisamment grande pour contenir le chemin d'accès complet. L'argument composite `path` ne doit pas être supérieur à la constante `_MAX_PATH`, définie dans Stdlib.h.  
  
 Si path a la valeur `NULL`, le gestionnaire de paramètres non valides est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). En outre, `errno` prend la valeur `EINVAL`. Les valeurs `NULL` sont autorisées pour tous les autres paramètres.  
  
 En C++, l’utilisation de ces fonctions est simplifiée par les surcharges de modèle ; les surcharges peuvent déduire la longueur de la mémoire tampon automatiquement (ce qui évite d’avoir à spécifier un argument taille) et peuvent remplacer automatiquement les fonctions plus anciennes et non sécurisées par leurs équivalentes plus récentes et sécurisées. Pour plus d’informations, consultez [Sécuriser les surcharges de modèle](../../c-runtime-library/secure-template-overloads.md).  
  
 Les versions debug de ces fonctions remplissent d'abord la mémoire tampon avec 0xFD. Pour désactiver ce comportement, utilisez [_CrtSetDebugFillThreshold](../../c-runtime-library/reference/crtsetdebugfillthreshold.md).  
  
## <a name="requirements"></a>Spécifications  
  
|Routine|En-tête requis|  
|-------------|---------------------|  
|`_makepath_s`|\<stdlib.h>|  
|`_wmakepath_s`|\<stdlib.h> ou \<wchar.h>|  
  
 Pour plus d’informations sur la compatibilité, consultez [Compatibilité](../../c-runtime-library/compatibility.md) dans l’introduction.  
  
## <a name="example"></a>Exemple  
  
```  
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
   printf( "  Drive: %s\n", drive );  
   printf( "  Dir: %s\n", dir );  
   printf( "  Filename: %s\n", fname );  
   printf( "  Ext: %s\n", ext );  
}  
```  
  
## <a name="output"></a>Sortie  
  
```  
Path created with _makepath_s: c:\sample\crt\crt_makepath_s.c  
  
Path extracted with _splitpath_s:  
  Drive: c:  
  Dir: \sample\crt\  
  Filename: crt_makepath_s  
  Ext: .c  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion de fichiers](../../c-runtime-library/file-handling.md)   
 [_fullpath, _wfullpath](../../c-runtime-library/reference/fullpath-wfullpath.md)   
 [_splitpath_s, _wsplitpath_s](../../c-runtime-library/reference/splitpath-s-wsplitpath-s.md)   
 [_makepath, _wmakepath](../../c-runtime-library/reference/makepath-wmakepath.md)