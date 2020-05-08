---
title: _findnext, _findnext32, _findnext32i64, _findnext64, _findnext64i32, _findnexti64, _wfindnext, _wfindnext32, _wfindnext32i64, _wfindnext64, _wfindnext64i32, _wfindnexti64
ms.date: 4/2/2020
api_name:
- _findnext
- _findnext32
- _findnext32i64
- _findnext64
- _findnext64i32
- _findnexti64
- _wfindnext
- _wfindnext32
- _wfindnext32i64
- _wfindnext64
- _wfindnext64i32
- _wfindnexti64
- _o__findnext32
- _o__findnext32i64
- _o__findnext64
- _o__findnext64i32
- _o__wfindnext32
- _o__wfindnext32i64
- _o__wfindnext64
- _o__wfindnext64i32
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: acb680db3b07b0f600b758401f1270deccf03da7
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82911665"
---
# <a name="_findnext-_findnext32-_findnext32i64-_findnext64-_findnext64i32-_findnexti64-_wfindnext-_wfindnext32-_wfindnext32i64-_wfindnext64-_wfindnext64i32-_wfindnexti64"></a>_findnext, _findnext32, _findnext32i64, _findnext64, _findnext64i32, _findnexti64, _wfindnext, _wfindnext32, _wfindnext32i64, _wfindnext64, _wfindnext64i32, _wfindnexti64

Recherchez le nom suivant, le cas échéant, qui correspond à l’argument de *spécification* de contenu dans un appel précédent à [_findfirst](findfirst-functions.md), puis modifiez le contenu de la structure *FileInfo* en conséquence.

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

*traitée*<br/>
Handle de recherche retourné par un appel précédent à **_findfirst**.

*FileInfo*<br/>
Mémoire tampon des informations du fichier.

## <a name="return-value"></a>Valeur de retour

En cas de réussite, retourne 0. Sinon, retourne-1 et définit **errno** sur une valeur indiquant la nature de l’échec. Les codes d’erreur possibles sont présentés dans le tableau suivant.

|Valeur de la variable errno|Condition|
|-|-|
| **EINVAL** | Paramètre non valide : *FileInfo* était **null**. Ou bien, le système d’exploitation a retourné une erreur inattendue. |
| **ENOENT** | Aucun autre fichier correspondant n’a été trouvé. |
| **ENOMEM** | La mémoire est insuffisante ou la longueur du nom de fichier est dépassée **MAX_PATH**. |

Si un paramètre non valide est passé, ces fonctions appellent le gestionnaire de paramètres non valides, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md).

## <a name="remarks"></a>Notes 

Vous devez appeler [_findclose](findclose.md) une fois que vous avez terminé d’utiliser la fonction **_findfirst** ou **_findnext** (ou toute variante). Cette opération libère les ressources utilisées par ces fonctions dans votre application.

Les variantes de ces fonctions avec le préfixe **w** sont des versions à caractères larges ; dans le cas contraire, ils sont identiques aux fonctions sur un octet correspondantes.

Les variantes de ces fonctions prennent en charge les types d’heures 32 bits ou 64 bits, ainsi que les tailles de fichiers 32 bits ou 64 bits. Le premier suffixe numérique (**32** ou **64**) indique la taille du type d’heure utilisé ; le deuxième suffixe est soit **i32** , soit **I64**, indiquant si la taille du fichier est représentée sous la forme d’un entier 32 bits ou 64 bits. Pour plus d’informations sur les versions qui prennent en charge les tailles de fichiers et les types d’heures 32 bits et 64 bits, consultez le tableau suivant. Les variantes qui utilisent un type d’heure 64 bits permettent d’exprimer les dates de création de fichiers jusqu’au 31 décembre 3000 à 23:59:59 heure UTC, tandis que celles qui utilisent des types d’heure 32 bits représentent uniquement les dates jusqu’au 18 janvier 2038 à 23:59:59, heure UTC. Le 1er janvier 1970 à minuit est la limite inférieure de la plage de dates pour toutes ces fonctions.

À moins que vous n’ayez une raison particulière d’utiliser les versions qui spécifient la taille de l’heure de manière explicite, utilisez **_findnext** ou **_wfindnext** ou, si vous devez prendre en charge des tailles de fichier supérieures à 3 Go, utilisez **_findnexti64** ou **_wfindnexti64**. Toutes ces fonctions utilisent le type d’heure 64 bits. Dans les versions antérieures, ces fonctions utilisaient un type d’heure 32 bits. S’il s’agit d’une modification avec rupture pour une application, vous pouvez définir **_USE_32BIT_TIME_T** pour obtenir l’ancien comportement. Si **_USE_32BIT_TIME_T** est défini, **_findnext**, **_finnexti64** et leurs versions Unicode correspondantes utilisent une heure de 32 bits.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

### <a name="time-type-and-file-length-type-variations-of-_findnext"></a>Variantes de type d’heure et de type de longueur de fichier _findnext

|Fonctions|**_USE_32BIT_TIME_T** défini ?|Type d’heure|Type de longueur de fichier|
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

## <a name="requirements"></a>Spécifications

|Function|En-tête requis|
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

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliothèques

Toutes les versions des [bibliothèques Runtime C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Voir aussi

[Appels système](../../c-runtime-library/system-calls.md)<br/>
[Fonctions de recherche de nom de fichier](../../c-runtime-library/filename-search-functions.md)<br/>
