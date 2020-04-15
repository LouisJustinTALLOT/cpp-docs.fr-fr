---
title: _sopen_s, _wsopen_s
ms.date: 4/2/2020
api_name:
- _sopen_s
- _wsopen_s
- _o__sopen_s
- _o__wsopen_s
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
- _sopen_s
- wsopen_s
- _wsopen_s
- sopen_s
helpviewer_keywords:
- sopen_s function
- _wsopen_s function
- wsopen_s function
- opening files, for sharing
- files [C++], opening
- _sopen_s function
- files [C++], sharing
ms.assetid: 059a0084-d08c-4973-9174-55e391b72aa2
ms.openlocfilehash: 81feacae0e4608512e7325c57e7f2b96bcf2cdde
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81356503"
---
# <a name="_sopen_s-_wsopen_s"></a>_sopen_s, _wsopen_s

Ouvre un fichier pour le partage. Ces versions de [_sopen et _wsopen](sopen-wsopen.md) intègrent les améliorations de sécurité décrites dans [Fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t _sopen_s(
   int* pfh,
   const char *filename,
   int oflag,
   int shflag,
   int pmode
);
errno_t _wsopen_s(
   int* pfh,
   const wchar_t *filename,
   int oflag,
   int shflag,
   int pmode,
);
```

### <a name="parameters"></a>Paramètres

*pfh pfh*<br/>
Handle de fichier ou -1 en cas d'erreur.

*Fichier*<br/>
Nom du fichier.

*Oflag*<br/>
Type d'opérations autorisées.

*shflag*<br/>
Type de partage autorisé.

*pmode*<br/>
Paramètre d'autorisation.

## <a name="return-value"></a>Valeur de retour

Une valeur de retour non zéro indique une erreur; dans ce **cas, errno** est réglé sur l’une des valeurs suivantes.

|Valeur de la variable errno|Condition|
|-|-|
| **LES EACCES** |  Le chemin d'accès donné est un répertoire, ou le fichier est en lecture seule, mais une opération de type « ouvert en écriture » a été tentée. |
| **EEXIST** |  **_O_CREAT** et **_O_EXCL** drapeaux ont été spécifiés, mais *le nom de fichier* existe déjà. |
| **EINVAL (EN)** |  Invalide *oflag*, *shflag*, ou *pmode* argument, ou *pfh* ou *nom de fichier* était un pointeur nul. |
| **EMFILE** | Plus aucun descripteur de fichier disponible. |
| **ENOENT (ENOENT)** | Fichier ou chemin d’accès introuvable. |

Si un argument non valide est passé à la fonction, le gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution se poursuit, **errno** est réglé sur **EINVAL** et **EINVAL** est retourné.

Pour plus d’informations sur ces codes de retour et les autres, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Dans le cas d’une erreur, -1 est retourné par *pfh* (sauf *pfh* est un pointeur nul).

## <a name="remarks"></a>Notes

La fonction **_sopen_s** ouvre le fichier spécifié par *nom de fichier* et prépare le fichier pour la lecture ou l’écriture partagée, tel que défini par *oflag* et *shflag*. **_wsopen_s** est une version à caractère large de **_sopen_s**; l’argument *du nom de fichier* pour **_wsopen_s** est une chaîne de caractère large. **_wsopen_s** et **_sopen_s** se comportent de façon identique autrement.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tsopen_s**|**_sopen_s**|**_sopen_s**|**_wsopen_s**|

L’expression integer *delag* est formée en combinant une ou \<plusieurs constantes manifestes, qui sont définies en fcntl.h>. Lorsque deux constantes ou plus forment *l’argument delag*, ils sont combinés avec l’opérateur bitwise-OR ( **&#124;** ).

|*delag* constante|Comportement|
|-|-|
| **_O_APPEND** | Déplace le pointeur de fichier à la fin du fichier avant chaque opération d'écriture. |
| **_O_BINARY** | Ouvre le fichier en mode binaire (non traduit). (Pour obtenir une description du mode binaire, consultez [fopen](fopen-wfopen.md).) |
| **_O_CREAT** | Crée un fichier et l'ouvre pour l'accès en écriture. N’a aucun effet si le fichier spécifié par *nom de fichier* existe. *L’argument du pmode* est requis lorsque **_O_CREAT** est spécifiée. |
| **_O_SHORT_LIVED _O_CREAT** &#124; **_O_SHORT_LIVED** | Crée un fichier temporaire et, dans la mesure du possible, n'effectue pas de vidage sur disque. *L’argument du pmode* est requis lorsque **_O_CREAT** est spécifiée. |
| **_O_CREAT** **&#124; _O_TEMPORARY** | Crée un fichier temporaire ; le fichier est supprimé quand le dernier descripteur de fichier est fermé. *L’argument du pmode* est requis lorsque **_O_CREAT** est spécifiée. |
| **_O_CREAT** &#124;`_O_EXCL` | Renvoie une valeur d’erreur si un fichier spécifié par *nom de fichier* existe. Ne s’applique que lorsqu’il est utilisé avec **_O_CREAT**. |
| **_O_NOINHERIT** | Empêche la création d'un descripteur de fichier partagé. |
| **_O_RANDOM** | Indique que la mise en cache est optimisée pour, mais non limitée à, l'accès aléatoire à partir du disque. |
| **_O_RDONLY** | Ouvre un fichier pour l'accès en lecture uniquement. Impossible de préciser avec **_O_RDWR** ou **_O_WRONLY**. |
| **_O_RDWR** | Ouvre un fichier pour l'accès en lecture et en écriture. Impossible de préciser avec **_O_RDONLY** ou **_O_WRONLY**. |
| **_O_SEQUENTIAL** | Indique que la mise en cache est optimisée pour, mais non limitée à, l'accès séquentiel à partir du disque. |
| **_O_TEXT** | Ouvre un fichier en mode texte (traduit). (Pour plus d’informations, consultez [E/S de fichier en mode texte et binaire](../../c-runtime-library/text-and-binary-mode-file-i-o.md) et [fopen](fopen-wfopen.md).) |
| **_O_TRUNC** | Ouvre un fichier et le tronque à une longueur nulle. Le fichier doit disposer d'une autorisation en écriture. Impossible de préciser avec **_O_RDONLY**. **_O_TRUNC** utilisé avec **_O_CREAT** ouvre un fichier existant ou crée un fichier. **Note:** Le **drapeau _O_TRUNC** détruit le contenu du fichier spécifié. |
| **_O_WRONLY** | Ouvre un fichier pour l'accès en écriture uniquement. Impossible de préciser avec **_O_RDONLY** ou **_O_RDWR**. |
| **_O_U16TEXT** | Ouvre un fichier en mode Unicode UTF-16. |
| **_O_U8TEXT** | Ouvre un fichier en mode Unicode UTF-8. |
| **_O_WTEXT** | Ouvre un fichier en mode Unicode. |

Pour spécifier le mode d’accès au fichier, vous devez spécifier **soit _O_RDONLY**, **_O_RDWR,** ou **_O_WRONLY**. Il n'y a aucune valeur par défaut pour le mode d'accès.

Lorsqu’un fichier est ouvert en mode Unicode en utilisant **_O_WTEXT**, **_O_U8TEXT**, ou **_O_U16TEXT**, les fonctions d’entrée traduisent les données qui sont lues à partir du fichier en données UTF-16 stockées sous forme de type **wchar_t**. Les fonctions qui écrivent à un fichier ouvert en mode Unicode s’attendent à des tampons qui contiennent des données UTF-16 stockées sous forme de type **wchar_t**. Si le fichier est encodé au format UTF-8, les données UTF-16 sont traduites en UTF-8 lors de leur écriture et le contenu du fichier encodé au format UTF-8 est traduit en UTF-16 lorsqu'il est lu. Toute tentative de lecture ou d'écriture d'une quantité impaire d'octets en mode Unicode provoque une erreur de validation de paramètre. Pour lire ou écrire des données stockées dans votre programme au format UTF-8, utilisez un mode de fichier binaire ou texte au lieu d'un mode Unicode. Vous êtes responsable de toute traduction d'encodage nécessaire.

Si **_sopen_s** est appelé avec **_O_WRONLY** | **_O_APPEND** (mode annexe) et **_O_WTEXT**, **_O_U16TEXT**, ou **_O_U8TEXT**, il essaie d’abord d’ouvrir le fichier pour la lecture et l’écriture, lire le BOM, puis le rouvrir pour l’écriture seulement. Si l'ouverture du fichier pour l'accès en lecture et en écriture échoue, elle ouvre le fichier pour l'accès en écriture uniquement et utilise la valeur par défaut pour le paramètre de mode Unicode.

*L’argument shflag* est une expression constante qui se compose de \<l’une des constantes manifestes suivantes, qui sont définies en share.h>.

|*shflag* constante|Comportement|
|-|-|
| **_SH_DENYRW** | Refuse l'accès en lecture et en écriture à un fichier. |
| **_SH_DENYWR** | Refuse l'accès en écriture à un fichier. |
| **_SH_DENYRD** | Refuse l'accès en lecture à un fichier. |
| **_SH_DENYNO** | Autorise l'accès en lecture et en écriture. |

*L’argument de pmode* est toujours exigé, contrairement à **_sopen**. Lorsque vous spécifiez **_O_CREAT**, si le fichier n’existe pas, *pmode* spécifie les paramètres d’autorisation du fichier, qui sont définis lorsque le nouveau fichier est fermé la première fois. Sinon, *pmode* est ignoré. *pmode* est une expression integer qui contient l’une ou les deux constantes manifestes **_S_IWRITE** et **_S_IREAD**, qui sont définies en \<sys-stat.h>. Quand les deux constantes sont données, elles sont combinées avec l'opérateur OR au niveau du bit. Le sens du *pmode* est le suivant.

|*pmode*|Signification|
|-|-|
| **_S_IREAD** | Lecture autorisée uniquement. |
| **_S_IWRITE** | Écriture autorisée. (En fait, autorise la lecture et l'écriture.) |
| **_S_IREAD** **_S_IWRITE** &#124; | Lecture et écriture autorisées. |

Si l'autorisation d'écriture n'est pas accordée, le fichier est en lecture seule. Dans le système d'exploitation Windows, tous les fichiers sont lisibles ; il est impossible d'accorder une autorisation en écriture seule. Par conséquent, les modes **_S_IWRITE** et **_S_IREAD** | **_S_IWRITE** sont équivalents.

**_sopen_s** applique le masque actuel d’autorisation de fichier à *pmode* avant que les autorisations soient définies. (Voir [_umask](umask.md).)

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|En-tête facultatif|
|-------------|---------------------|---------------------|
|**_sopen_s**|\<io.h>|\<fcntl.h>, \<sys\types.h>, \<sys\stat.h>, \<share.h>|
|**_wsopen_s**|\<io.h> ou \<wchar.h>|\<fcntl.h>, \<sys/types.h>, \<sys/stat.h>, \<share.h>|

**_sopen_s** et **_wsopen_s** sont des extensions Microsoft. Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Consultez l’exemple relatif à [_locking](locking.md).

## <a name="see-also"></a>Voir aussi

[E/S niveau bas](../../c-runtime-library/low-level-i-o.md)<br/>
[_close](close.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_fsopen, _wfsopen](fsopen-wfsopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
