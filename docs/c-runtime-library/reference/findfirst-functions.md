---
title: _findfirst, _findfirst32, _findfirst32i64, _findfirst64, _findfirst64i32, _findfirsti64, _wfindfirst, _wfindfirst32, _wfindfirst32i64, _wfindfirst64, _wfindfirst64i32, _wfindfirsti64
ms.date: 4/2/2020
api_name:
- _findfirst
- _wfindfirst
- _findfirst32
- _wfindfirst32
- _findfirst32i64
- _wfindfirst32i64
- _findfirst64
- _wfindfirst64
- _findfirst64i32
- _wfindfirst64i32
- _findfirsti64
- _wfindfirsti64
- _o__findfirst32
- _o__findfirst32i64
- _o__findfirst64
- _o__findfirst64i32
- _o__wfindfirst32
- _o__wfindfirst32i64
- _o__wfindfirst64
- _o__wfindfirst64i32
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- findfirst32i64
- wfindfirst32i64
- tfindfirst64
- _findfirst64i32
- _wfindfirst32i64
- _wfindfirsti64
- wfindfirst
- _tfindfirsti64
- findfirst32
- _tfindfirst32
- _findfirsti64
- findfirst
- wfindfirst64
- wfindfirst32
- tfindfirst32
- _wfindfirst64i32
- findfirst64i32
- tfindfirst64i32
- _wfindfirst
- findfirsti64
- _findfirst32i64
- wfindfirst64i32
- _wfindfirst32
- _findfirst32
- _tfindfirst32i64
- tfindfirst
- _tfindfirst64i32
- findfirst64
- _tfindfirst
- _findfirst64
- _tfindfirst64
- tfindfirst32i64
- _findfirst
- _wfindfirst64
helpviewer_keywords:
- _tfindfirst64 function
- _wfindfirst64i32 function
- _wfindfirst32i64 function
- wfindfirst32 function
- _findfirst function
- wfindfirst64 function
- _wfindfirst function
- _findfirst64i32 function
- wfindfirst function
- _findfirst64 function
- tfindfirst32 function
- _tfindfirst64i32 function
- findfirst function
- findfirst32i64 function
- tfindfirst64 function
- _tfindfirst32 function
- tfindfirst32i64 function
- tfindfirst64i32 function
- _wfindfirsti64 function
- _findfirst32i64 function
- findfirst32 function
- findfirsti64 function
- findfirst64i32 function
- tfindfirsti64 function
- tfindfirst function
- _wfindfirst32 function
- wfindfirsti64 function
- _tfindfirsti64 function
- _tfindfirst function
- _tfindfirst32i64 function
- findfirst64 function
- _findfirst32 function
- _findfirsti64 function
- wfindfirst32i64 function
- wfindfirst64i32 function
- _wfindfirst64 function
ms.assetid: 9bb46d1a-b946-47de-845a-a0b109a33ead
ms.openlocfilehash: d83cc0913584618897cbc4aec45cb137388674b7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346809"
---
# <a name="_findfirst-_findfirst32-_findfirst32i64-_findfirst64-_findfirst64i32-_findfirsti64-_wfindfirst-_wfindfirst32-_wfindfirst32i64-_wfindfirst64-_wfindfirst64i32-_wfindfirsti64"></a>_findfirst, _findfirst32, _findfirst32i64, _findfirst64, _findfirst64i32, _findfirsti64, _wfindfirst, _wfindfirst32, _wfindfirst32i64, _wfindfirst64, _wfindfirst64i32, _wfindfirsti64

Fournir des informations sur la première instance d’un nom de fichier qui correspond au fichier spécifié dans *l’argument de filespec.*

## <a name="syntax"></a>Syntaxe

```C
intptr_t _findfirst(
   const char *filespec,
   struct _finddata_t *fileinfo
);
intptr_t _findfirst32(
   const char *filespec,
   struct _finddata32_t *fileinfo
);
intptr_t _findfirst64(
   const char *filespec,
   struct _finddata64_t *fileinfo
);
intptr_t _findfirsti64(
   const char *filespec,
   struct _finddatai64_t *fileinfo
);
intptr_t _findfirst32i64(
   const char *filespec,
   struct _finddata32i64_t *fileinfo
);
intptr_t _findfirst64i32(
   const char *filespec,
   struct _finddata64i32_t *fileinfo
);
intptr_t _wfindfirst(
   const wchar_t *filespec,
   struct _wfinddata_t *fileinfo
);
intptr_t _wfindfirst32(
   const wchar_t *filespec,
   struct _wfinddata32_t *fileinfo
);
intptr_t _wfindfirst64(
   const wchar_t *filespec,
   struct _wfinddata64_t *fileinfo
);
intptr_t _wfindfirsti64(
   const wchar_t *filespec,
   struct _wfinddatai64_t *fileinfo
);
intptr_t _wfindfirst32i64(
   const wchar_t *filespec,
   struct _wfinddata32i64_t *fileinfo
);
intptr_t _wfindfirst64i32(
   const wchar_t *filespec,
   struct _wfinddata64i32_t *fileinfo
);
```

### <a name="parameters"></a>Paramètres

*Fichiers*<br/>
Spécification du fichier cible (peut inclure des caractères génériques).

*Fileinfo*<br/>
Mémoire tampon des informations du fichier.

## <a name="return-value"></a>Valeur de retour

En cas de succès, **_findfirst** renvoie une poignée de recherche unique identifiant le fichier ou le groupe de fichiers qui correspondent aux *spécifications de filespec,* qui peuvent être utilisées dans un appel ultérieur pour [_findnext](findnext-functions.md) ou pour [_findclose](findclose.md). Sinon, **_findfirst** retourne -1 et définit **errno** à l’une des valeurs suivantes.

| Valeur de la variable errno | Condition |
|-|-|
| **EINVAL (EN)** | Paramètre invalide : *filespec* ou *fileinfo* était **NULL**. Ou bien, le système d’exploitation a retourné une erreur inattendue. |
| **ENOENT (ENOENT)** | Spécification de fichier impossible à mettre en correspondance. |
| **ENOMEM (ENOMEM)** | Mémoire insuffisante. |
| **EINVAL (EN)** | La spécification du nom de fichier invalide ou le nom du fichier donné était plus grand que **MAX_PATH**. |

Pour plus d’informations sur ces codes de retour et les autres, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Si un paramètre non valide est passé, ces fonctions appellent le gestionnaire de paramètres non valides, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md).

## <a name="remarks"></a>Notes

Vous devez appeler [_findclose](findclose.md) une fois que vous avez terminé la fonction **_findfirst** ou [_findnext](findnext-functions.md) (ou toute variante). Cette opération libère les ressources utilisées par ces fonctions dans votre application.

Les variations de ces fonctions qui ont le préfixe **w** sont des versions à caractère large; autrement, elles sont identiques aux fonctions mono-byte correspondantes.

Les variantes de ces fonctions prennent en charge les types d’heures 32 bits ou 64 bits, ainsi que les tailles de fichiers 32 bits ou 64 bits. Le premier suffixe numérique (**32** ou **64**) indique la taille du type de temps; le deuxième suffixe est **i32** ou **i64**, et indique si la taille du fichier est représenté comme un intégriste 32 ou 64 bits. Pour plus d’informations sur les versions qui prennent en charge les tailles de fichiers et les types d’heures 32 bits et 64 bits, consultez le tableau suivant. Le suffixe **i32** ou **i64** est omis s’il est le même que la taille du type de temps, de sorte **que _findfirst64** prend également en charge les longueurs de fichiers 64 bits et **_findfirst32** ne prend en charge que les longueurs de fichiers 32 bits.

Ces fonctions utilisent diverses formes de la structure **_finddata_t** pour le paramètre *fileinfo.* Pour plus d’informations sur la structure, consultez [Fonctions de recherche de nom de fichier](../../c-runtime-library/filename-search-functions.md).

Les variantes qui utilisent un type d’heure 64 bits permettent d’exprimer les dates de création de fichiers jusqu’au 31 décembre 3000 à 23:59:59, heure UTC. Celles qui utilisent des types d’heure 32 bits représentent les dates uniquement jusqu’au 18 janvier 2038 à 23:59:59, heure UTC. Le 1er janvier 1970 à minuit est la limite inférieure de la plage de dates pour toutes ces fonctions.

Sauf si vous avez une raison spécifique d’utiliser les versions qui spécifient explicitement la taille du temps, utilisez **_findfirst** ou **_wfindfirst** ou, si vous avez besoin de prendre en charge les tailles de fichiers supérieures à 3 Go, utilisez **_findfirsti64** ou **_wfindfirsti64**. Toutes ces fonctions utilisent le type d’heure 64 bits. Dans les versions antérieures, ces fonctions utilisaient un type d’heure 32 bits. S’il s’agit d’un changement de rupture pour une application, vous pouvez définir **_USE_32BIT_TIME_T** pour revenir à l’ancien comportement. Si **_USE_32BIT_TIME_T** est définie, **_findfirst**, **_finfirsti64**, et leurs versions Unicode correspondantes utilisent un temps 32 bits.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

### <a name="time-type-and-file-length-type-variations-of-_findfirst"></a>Variantes de type d’heure et de type de longueur de fichier de _findfirst

|Fonctions|**_USE_32BIT_TIME_T** défini?|Type d’heure|Type de longueur de fichier|
|---------------|----------------------------------|---------------|----------------------|
|**_findfirst**, **_wfindfirst**|Non défini|64 bits|32 bits|
|**_findfirst**, **_wfindfirst**|Défini|32 bits|32 bits|
|**_findfirst32**, **_wfindfirst32**|Non affecté par la définition de macro|32 bits|32 bits|
|**_findfirst64**, **_wfindfirst64**|Non affecté par la définition de macro|64 bits|64 bits|
|**_findfirsti64**, **_wfindfirsti64**|Non défini|64 bits|64 bits|
|**_findfirsti64**, **_wfindfirsti64**|Défini|32 bits|64 bits|
|**_findfirst32i64**, **_wfindfirst32i64**|Non affecté par la définition de macro|32 bits|64 bits|
|**_findfirst64i32**, **_wfindfirst64i32**|Non affecté par la définition de macro|64 bits|32 bits|

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfindfirst**|**_findfirst**|**_findfirst**|**_wfindfirst**|
|**_tfindfirst32**|**_findfirst32**|**_findfirst32**|**_wfindfirst32**|
|**_tfindfirst64**|**_findfirst64**|**_findfirst64**|**_wfindfirst64**|
|**_tfindfirsti64**|**_findfirsti64**|**_findfirsti64**|**_wfindfirsti64**|
|**_tfindfirst32i64**|**_findfirst32i64**|**_findfirst32i64**|**_wfindfirst32i64**|
|**_tfindfirst64i32**|**_findfirst64i32**|**_findfirst64i32**|**_wfindfirst64i32**|

## <a name="requirements"></a>Spécifications

|Fonction|En-tête requis|
|--------------|---------------------|
|**_findfirst**|\<io.h>|
|**_findfirst32**|\<io.h>|
|**_findfirst64**|\<io.h>|
|**_findfirsti64**|\<io.h>|
|**_findfirst32i64**|\<io.h>|
|**_findfirst64i32**|\<io.h>|
|**_wfindfirst**|\<io.h> ou \<wchar.h>|
|**_wfindfirst32**|\<io.h> ou \<wchar.h>|
|**_wfindfirst64**|\<io.h> ou \<wchar.h>|
|**_wfindfirsti64**|\<io.h> ou \<wchar.h>|
|**_wfindfirst32i64**|\<io.h> ou \<wchar.h>|
|**_wfindfirst64i32**|\<io.h> ou \<wchar.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[Appels système](../../c-runtime-library/system-calls.md)<br/>
[Fonctions de recherche de nom de fichier](../../c-runtime-library/filename-search-functions.md)<br/>
