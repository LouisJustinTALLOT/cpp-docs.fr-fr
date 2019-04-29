---
title: _findnext, _findnext32, _findnext32i64, _findnext64, _findnext64i32, _findnexti64, _wfindnext, _wfindnext32, _wfindnext32i64, _wfindnext64, _wfindnext64i32, _wfindnexti64
ms.date: 11/04/2016
apiname:
- _wfindnext
- _findnext
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
- findnext
- _wfindnext32i64
- _tfindnext64i32
- findnext32
- findnext32i64
- wfindnext64i32
- _wfindnext
- tfindnext64
- findnexti64
- _findnexti64
- _tfindnexti64
- _findnext64i32
- tfindnexti64
- tfindnext32
- _wfindnext64i32
- findnext64i32
- _findnext
- _tfindnext32i64
- _wfindnext64
- wfindnext
- wfindnext32
- tfindnext32i64
- _findnext64
- _tfindnext64
- _wfindnext32
- findnext64
- _findnext32i64
- tfindnext
- wfindnexti64
- tfindnext64i32
- _tfindnext32
- wfindnext32i64
- wfindnext64
- _wfindnexti64
- _tfindnext
- _findnext32
helpviewer_keywords:
- _wfindnexti64 function
- _tfindnext32 function
- wfindnexti64 function
- _wfindnext32i64 function
- findnext32i64 function
- tfindnext64i32 function
- _tfindnext64i32 function
- _findnext function
- findnext64i32 function
- _tfindnext function
- findnext32 function
- tfindnext32 function
- _findnext32 function
- _tfindnext32i64 function
- _wfindnext function
- tfindnext function
- _findnext64 function
- findnext64 function
- _findnext64i32 function
- wfindnext32i64 function
- findnext function
- wfindnext32 function
- _wfindnext64i32 function
- findnexti64 function
- _wfindnext64 function
- _findnext32i64 function
- _findnexti64 function
- _tfindnext64 function
- wfindnext64i32 function
- tfindnexti64 function
- wfindnext64 function
- wfindnext function
- tfindnext64 function
- _wfindnext32 function
- tfindnext32i64 function
- _tfindnexti64 function
ms.assetid: 75d97188-5add-4698-a46c-4c492378f0f8
ms.openlocfilehash: c7df8649625488a83239a19e4afcecea129f9072
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62333727"
---
# <a name="findnext-findnext32-findnext32i64-findnext64-findnext64i32-findnexti64-wfindnext-wfindnext32-wfindnext32i64-wfindnext64-wfindnext64i32-wfindnexti64"></a>_findnext, _findnext32, _findnext32i64, _findnext64, _findnext64i32, _findnexti64, _wfindnext, _wfindnext32, _wfindnext32i64, _wfindnext64, _wfindnext64i32, _wfindnexti64

Rechercher le nom suivant, cas échéant, qui correspond à la *filespec* argument dans un appel précédent à [_findfirst](findfirst-functions.md)et vous devez ensuite modifier le *fileinfo* contenu de la structure en conséquence.

## <a name="syntax"></a>Syntaxe

```C
int _findnext(
   intptr_t handle,
   struct _finddata_t *fileinfo
);
int _findnext32(
   intptr_t handle,
   struct _finddata32_t *fileinfo
);
int _findnext64(
   intptr_t handle,
   struct __finddata64_t *fileinfo
);
int _findnexti64(
   intptr_t handle,
   struct __finddatai64_t *fileinfo
);
int _findnext32i64(
   intptr_t handle,
   struct _finddata32i64_t *fileinfo
);
int _findnext64i32(
   intptr_t handle,
   struct _finddata64i32_t *fileinfo
);
int _wfindnext(
   intptr_t handle,
   struct _wfinddata_t *fileinfo
);
int _wfindnext32(
   intptr_t handle,
   struct _wfinddata32_t *fileinfo
);
int _wfindnext64(
   intptr_t handle,
   struct _wfinddata64_t *fileinfo
);
int _wfindnexti64(
   intptr_t handle,
   struct _wfinddatai64_t *fileinfo
);
int _wfindnext32i64(
   intptr_t handle,
   struct _wfinddatai64_t *fileinfo
);
int _wfindnext64i32(
   intptr_t handle,
   struct _wfinddata64i32_t *fileinfo
);
```

### <a name="parameters"></a>Paramètres

*handle*<br/>
Handle de recherche retournée par un appel précédent à **_findfirst**.

*fileinfo*<br/>
Mémoire tampon des informations du fichier.

## <a name="return-value"></a>Valeur de retour

En cas de réussite, retourne 0. Sinon, retourne -1 et définit **errno** une valeur qui indique la nature de l’échec. Les codes d’erreur possibles sont présentés dans le tableau suivant.

|Valeur de la variable errno|Condition|
|-|-|
| **EINVAL** | Paramètre non valide : *fileinfo* a été **NULL**. Ou bien, le système d’exploitation a retourné une erreur inattendue. |
| **ENOENT** | Aucun autre fichier correspondant n’a été trouvé. |
| **ENOMEM** | Mémoire insuffisante ou dépassé la longueur du nom de fichier **MAX_PATH**. |

Si un paramètre non valide est passé, ces fonctions appellent le gestionnaire de paramètres non valides, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md).

## <a name="remarks"></a>Notes

Vous devez appeler [_findclose](findclose.md) une fois que vous avez terminé d’utiliser le **_findfirst** ou **_findnext** (fonction) (ou toute variante). Cette opération libère les ressources utilisées par ces fonctions dans votre application.

Les variantes de ces fonctions avec le **w** préfixe sont des versions à caractères larges ; sinon, elles sont identiques aux fonctions correspondantes sur un octet.

Les variantes de ces fonctions prennent en charge les types d’heures 32 bits ou 64 bits, ainsi que les tailles de fichiers 32 bits ou 64 bits. Le premier suffixe numérique (**32** ou **64**) indique la taille du temps type utilisé ; le deuxième suffixe est **i32** ou **i64**, indiquant si la taille du fichier est représentée comme un entier 32 bits ou 64 bits. Pour plus d’informations sur les versions qui prennent en charge les tailles de fichiers et les types d’heures 32 bits et 64 bits, consultez le tableau suivant. Les variantes qui utilisent un type d’heure 64 bits permettent d’exprimer les dates de création de fichiers jusqu’au 31 décembre 3000 à 23:59:59 heure UTC, tandis que celles qui utilisent des types d’heure 32 bits représentent uniquement les dates jusqu’au 18 janvier 2038 à 23:59:59, heure UTC. Le 1er janvier 1970 à minuit est la limite inférieure de la plage de dates pour toutes ces fonctions.

À moins que vous ayez une raison spécifique à utiliser les versions qui spécifient la taille au moment explicitement, utilisez **_findnext** ou **_wfindnext** ou, si vous avez besoin prendre en charge des tailles de fichier supérieures à 3 Go, utilisez **_ findnexti64** ou **_wfindnexti64**. Toutes ces fonctions utilisent le type d’heure 64 bits. Dans les versions antérieures, ces fonctions utilisaient un type d’heure 32 bits. S’il s’agit d’une modification avec rupture pour une application, vous pouvez définir **_USE_32BIT_TIME_T** pour obtenir l’ancien comportement. Si **_USE_32BIT_TIME_T** est défini, **_findnext**, **_finnexti64** et les versions Unicode correspondantes utilisent une heure de 32 bits.

### <a name="time-type-and-file-length-type-variations-of-findnext"></a>Variantes de type d’heure et de type de longueur de fichier _findnext

|Fonctions|**_USE_32BIT_TIME_T** défini ?|Type de temps|Type de longueur de fichier|
|---------------|----------------------------------|---------------|----------------------|
|**_findnext**, **_wfindnext**|Non défini|64 bits|32 bits|
|**_findnext**, **_wfindnext**|Défini|32 bits|32 bits|
|**_findnext32**, **_wfindnext32**|Non affecté par la définition de macro|32 bits|32 bits|
|**_findnext64**, **_wfindnext64**|Non affecté par la définition de macro|64 bits|64 bits|
|**_findnexti64**, **_wfindnexti64**|Non défini|64 bits|64 bits|
|**_findnexti64**, **_wfindnexti64**|Défini|32 bits|64 bits|
|**_findnext32i64**, **_wfindnext32i64**|Non affecté par la définition de macro|32 bits|64 bits|
|**_findnext64i32**, **_wfindnext64i32**|Non affecté par la définition de macro|64 bits|32 bits|

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfindnext**|**_findnext**|**_findnext**|**_wfindnext**|
|**_tfindnext32**|**_findnext32**|**_findnext32**|**_wfindnext32**|
|**_tfindnext64**|**_findnext64**|**_findnext64**|**_wfindnext64**|
|**_tfindnexti64**|**_findnexti64**|**_findnexti64**|**_wfindnexti64**|
|**_tfindnext32i64**|**_findnext32i64**|**_findnext32i64**|**_wfindnext32i64**|
|**_tfindnext64i32**|**_findnext64i32**|**_findnext64i32**|**_wfindnext64i32**|

## <a name="requirements"></a>Configuration requise

|Fonction|En-tête requis|
|--------------|---------------------|
|**_findnext**|\<io.h>|
|**_findnext32**|\<io.h>|
|**_findnext64**|\<io.h>|
|**_findnexti64**|\<io.h>|
|**_findnext32i64**|\<io.h>|
|**_findnext64i32**|\<io.h>|
|**_wfindnext**|\<io.h> ou \<wchar.h>|
|**_wfindnext32**|\<io.h> ou \<wchar.h>|
|**_wfindnext64**|\<io.h> ou \<wchar.h>|
|**_wfindnexti64**|\<io.h> ou \<wchar.h>|
|**_wfindnext32i64**|\<io.h> ou \<wchar.h>|
|**_wfindnext64i32**|\<io.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Toutes les versions des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Voir aussi

[Appels système](../../c-runtime-library/system-calls.md)<br/>
[Fonctions de recherche de nom de fichier](../../c-runtime-library/filename-search-functions.md)<br/>
