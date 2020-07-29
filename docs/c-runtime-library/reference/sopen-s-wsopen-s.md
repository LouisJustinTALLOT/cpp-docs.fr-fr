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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: bddee0b6c5e08e7a7fbae3ca72c3125fa9849c03
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229387"
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

*pfh*<br/>
Handle de fichier ou -1 en cas d'erreur.

*extension*<br/>
Nom du fichier.

*oflag*<br/>
Type d'opérations autorisées.

*shflag*<br/>
Type de partage autorisé.

*pmode*<br/>
Paramètre d'autorisation.

## <a name="return-value"></a>Valeur de retour

Une valeur de retour différente de zéro indique une erreur ; dans ce cas, **errno** est défini sur l’une des valeurs suivantes.

|Valeur de la variable errno|Condition|
|-|-|
| **EACCES** |  Le chemin d'accès donné est un répertoire, ou le fichier est en lecture seule, mais une opération de type « ouvert en écriture » a été tentée. |
| **EEXIST** |  Les indicateurs **_O_CREAT** et **_O_EXCL** ont été spécifiés, mais le *nom de fichier* existe déjà. |
| **EINVAL** |  Argument *Oflag*, *shflag*ou *PMODE* non valide, ou *PFH* ou *filename* était un pointeur null. |
| **EMFILE** | Plus aucun descripteur de fichier disponible. |
| **ENOENT** | Fichier ou chemin d’accès introuvable. |

Si un argument non valide est passé à la fonction, le gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **errno** a la valeur **EINVAL** et **EINVAL** est retourné.

Pour plus d’informations sur ces codes de retour et les autres, consultez [errno, _doserrno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Dans le cas d’une erreur,-1 est retourné via *PFH* (sauf si *PFH* est un pointeur null).

## <a name="remarks"></a>Notes

La fonction **_sopen_s** ouvre le fichier spécifié par *filename* et prépare le fichier pour la lecture ou l’écriture partagée, comme défini par *Oflag* et *shflag*. **_wsopen_s** est une version à caractères larges de **_sopen_s**; l’argument de *nom de fichier* pour **_wsopen_s** est une chaîne de caractères larges. dans le cas contraire, **_wsopen_s** et **_sopen_s** se comportent de la même façon.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tsopen_s**|**_sopen_s**|**_sopen_s**|**_wsopen_s**|

L’expression entière *Oflag* est formée en combinant une ou plusieurs constantes manifestes, qui sont définies dans \<fcntl.h> . Quand au moins deux constantes forment l’argument *Oflag*, elles sont combinées avec l’opérateur or au niveau du bit ( **&#124;** ).

|*Oflag* constante)|Comportement|
|-|-|
| **_O_APPEND** | Déplace le pointeur de fichier à la fin du fichier avant chaque opération d'écriture. |
| **_O_BINARY** | Ouvre le fichier en mode binaire (non traduit). (Pour obtenir une description du mode binaire, consultez [fopen](fopen-wfopen.md).) |
| **_O_CREAT** | Crée un fichier et l'ouvre pour l'accès en écriture. N’a aucun effet si le fichier spécifié par *filename* existe. L’argument *PMODE* est obligatoire lorsque **_O_CREAT** est spécifié. |
| **_O_CREAT** &#124; **_O_SHORT_LIVED** | Crée un fichier temporaire et, dans la mesure du possible, n'effectue pas de vidage sur disque. L’argument *PMODE* est obligatoire lorsque **_O_CREAT** est spécifié. |
| **_O_CREAT** &#124; **_O_TEMPORARY** | Crée un fichier temporaire ; le fichier est supprimé quand le dernier descripteur de fichier est fermé. L’argument *PMODE* est obligatoire lorsque **_O_CREAT** est spécifié. |
| **_O_CREAT** &#124;`_O_EXCL` | Retourne une valeur d’erreur s’il existe un fichier spécifié par *filename* . S’applique uniquement lorsqu’il est utilisé avec **_O_CREAT**. |
| **_O_NOINHERIT** | Empêche la création d'un descripteur de fichier partagé. |
| **_O_RANDOM** | Indique que la mise en cache est optimisée pour, mais non limitée à, l'accès aléatoire à partir du disque. |
| **_O_RDONLY** | Ouvre un fichier pour l'accès en lecture uniquement. Ne peut pas être spécifié avec **_O_RDWR** ou **_O_WRONLY**. |
| **_O_RDWR** | Ouvre un fichier pour l'accès en lecture et en écriture. Ne peut pas être spécifié avec **_O_RDONLY** ou **_O_WRONLY**. |
| **_O_SEQUENTIAL** | Indique que la mise en cache est optimisée pour, mais non limitée à, l'accès séquentiel à partir du disque. |
| **_O_TEXT** | Ouvre un fichier en mode texte (traduit). (Pour plus d’informations, consultez [E/S de fichier en mode texte et binaire](../../c-runtime-library/text-and-binary-mode-file-i-o.md) et [fopen](fopen-wfopen.md).) |
| **_O_TRUNC** | Ouvre un fichier et le tronque à une longueur nulle. Le fichier doit disposer d'une autorisation en écriture. Ne peut pas être spécifié avec **_O_RDONLY**. **_O_TRUNC** utilisé avec **_O_CREAT** ouvre un fichier existant ou crée un fichier. **Remarque :** L’indicateur **_O_TRUNC** détruit le contenu du fichier spécifié. |
| **_O_WRONLY** | Ouvre un fichier pour l'accès en écriture uniquement. Ne peut pas être spécifié avec **_O_RDONLY** ou **_O_RDWR**. |
| **_O_U16TEXT** | Ouvre un fichier en mode Unicode UTF-16. |
| **_O_U8TEXT** | Ouvre un fichier en mode Unicode UTF-8. |
| **_O_WTEXT** | Ouvre un fichier en mode Unicode. |

Pour spécifier le mode d’accès au fichier, vous devez spécifier **_O_RDONLY**, **_O_RDWR**ou **_O_WRONLY**. Il n'y a aucune valeur par défaut pour le mode d'accès.

Lorsqu’un fichier est ouvert en mode Unicode à l’aide de **_O_WTEXT**, **_O_U8TEXT**ou **_O_U16TEXT**, les fonctions d’entrée traduisent les données lues à partir du fichier en données UTF-16 stockées en tant que type **`wchar_t`** . Les fonctions qui écrivent dans un fichier ouvert en mode Unicode attendent des mémoires tampons qui contiennent des données UTF-16 stockées en tant que type **`wchar_t`** . Si le fichier est encodé au format UTF-8, les données UTF-16 sont traduites en UTF-8 lors de leur écriture et le contenu du fichier encodé au format UTF-8 est traduit en UTF-16 lorsqu'il est lu. Toute tentative de lecture ou d'écriture d'une quantité impaire d'octets en mode Unicode provoque une erreur de validation de paramètre. Pour lire ou écrire des données stockées dans votre programme au format UTF-8, utilisez un mode de fichier binaire ou texte au lieu d'un mode Unicode. Vous êtes responsable de toute traduction d'encodage nécessaire.

Si **_sopen_s** est appelé avec **_O_WRONLY**  |  **_O_APPEND** (mode Append) et **_O_WTEXT**, **_O_U16TEXT**ou **_O_U8TEXT**, il tente d’abord d’ouvrir le fichier pour la lecture et l’écriture, de lire la nomenclature, puis de la rouvrir en écriture. Si l'ouverture du fichier pour l'accès en lecture et en écriture échoue, elle ouvre le fichier pour l'accès en écriture uniquement et utilise la valeur par défaut pour le paramètre de mode Unicode.

L’argument *shflag* est une expression constante qui se compose de l’une des constantes manifestes suivantes, qui sont définies dans \<share.h> .

|*shflag* constante)|Comportement|
|-|-|
| **_SH_DENYRW** | Refuse l'accès en lecture et en écriture à un fichier. |
| **_SH_DENYWR** | Refuse l'accès en écriture à un fichier. |
| **_SH_DENYRD** | Refuse l'accès en lecture à un fichier. |
| **_SH_DENYNO** | Autorise l'accès en lecture et en écriture. |

L’argument *PMODE* est toujours requis, contrairement à **_sopen**. Lorsque vous spécifiez **_O_CREAT**, si le fichier n’existe pas, *PMODE* spécifie les paramètres d’autorisation du fichier, qui sont définis quand le nouveau fichier est fermé la première fois. Sinon, *PMODE* est ignoré. *PMODE* est une expression entière qui contient l’une des constantes manifestes, ou les deux, **_S_IWRITE** et **_S_IREAD**, qui sont définis dans \<sys\stat.h> . Quand les deux constantes sont données, elles sont combinées avec l'opérateur OR au niveau du bit. La signification de *PMODE* est la suivante.

|*pmode*|Signification|
|-|-|
| **_S_IREAD** | Lecture autorisée uniquement. |
| **_S_IWRITE** | Écriture autorisée. (En fait, autorise la lecture et l'écriture.) |
| **_S_IREAD** &#124; **_S_IWRITE** | Lecture et écriture autorisées. |

Si l'autorisation d'écriture n'est pas accordée, le fichier est en lecture seule. Dans le système d'exploitation Windows, tous les fichiers sont lisibles ; il est impossible d'accorder une autorisation en écriture seule. Par conséquent, les modes **_S_IWRITE** et **_S_IREAD**  |  **_S_IWRITE** sont équivalents.

**_sopen_s** applique le masque d’autorisation de fichier actuel à *PMODE* avant que les autorisations ne soient définies. (Voir [_umask](umask.md).)

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|En-tête facultatif|
|-------------|---------------------|---------------------|
|**_sopen_s**|\<io.h>|\<fcntl.h>, \<sys\types.h>, \<sys\stat.h>, \<share.h>|
|**_wsopen_s**|\<io.h> ou \<wchar.h>|\<fcntl.h>, \<sys/types.h>, \<sys/stat.h>, \<share.h>|

**_sopen_s** et **_wsopen_s** sont des extensions Microsoft. Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Consultez l’exemple relatif à [_locking](locking.md).

## <a name="see-also"></a>Voir aussi

[E/s de bas niveau](../../c-runtime-library/low-level-i-o.md)<br/>
[_close](close.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_fsopen, _wfsopen](fsopen-wfsopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
