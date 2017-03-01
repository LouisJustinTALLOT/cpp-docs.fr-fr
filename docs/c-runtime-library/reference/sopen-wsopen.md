---
title: _sopen, _wsopen | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _sopen
- _wsopen
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
- _wsopen
- wsopen
- _sopen
- _tsopen
dev_langs:
- C++
helpviewer_keywords:
- sopen function
- sharing files
- opening files, for sharing
- _sopen function
- wsopen function
- files [C++], opening
- files [C++], sharing
- _wsopen function
ms.assetid: a9d4cccf-06e9-414d-96fa-453fca88cc1f
caps.latest.revision: 21
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: c8b8418394c4ebcc5ff13d97e2b7b28929982c79
ms.lasthandoff: 02/24/2017

---
# <a name="sopen-wsopen"></a>_sopen, _wsopen
Ouvre un fichier pour le partage. Il existe des versions plus sécurisées de ces fonctions. Consultez [_sopen_s, _wsopen_s](../../c-runtime-library/reference/sopen-s-wsopen-s.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _sopen(  
   const char *filename,  
   int oflag,  
   int shflag [,  
   int pmode ]   
);  
int _wsopen(  
   const wchar_t *filename,  
   int oflag,  
   int shflag [,  
   int pmode ]   
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `filename`  
 Nom du fichier.  
  
 `oflag`  
 Type d'opérations autorisées.  
  
 `shflag`  
 Type de partage autorisé.  
  
 `pmode`  
 Paramètre d'autorisation.  
  
## <a name="return-value"></a>Valeur de retour  
 Chacune de ces fonctions retourne un descripteur de fichier pour le fichier ouvert.  
  
 Si `filename` ou `oflag` est un pointeur `NULL` ou si `oflag` ou `shflag` ne se trouve pas dans une plage de valeurs valide, le gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l'exécution est autorisée à se poursuivre, ces fonctions retournent -1 et affectent à `errno` l'une des valeurs suivantes.  
  
 `EACCES`  
 Le chemin d'accès donné est un répertoire, ou le fichier est en lecture seule, mais une opération de type « ouvert en écriture » a été tentée.  
  
 `EEXIST`  
Les indicateurs  `_O_CREAT` et `_O_EXCL` ont été spécifiés, mais `filename` existe déjà.  
  
 `EINVAL`  
 Argument `oflag` ou `shflag` non valide.  
  
 `EMFILE`  
 Aucun autre descripteur de fichier n'est disponible.  
  
 `ENOENT`  
 Fichier ou chemin d'accès introuvable.  
  
 Pour plus d’informations sur ces codes de retour et les autres, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Notes  
 La fonction `_sopen` ouvre le fichier spécifié par `filename` et prépare le fichier pour la lecture ou l'écriture partagée, comme défini par `oflag` et `shflag`. `_wsopen` est une version à caractères larges de `_sopen` ; l'argument `filename` de `_wsopen` est une chaîne à caractères larges. Sinon, `_wsopen` et `_sopen` se comportent de la même façon.  
  
### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique  
  
|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tsopen`|`_sopen`|`_sopen`|`_wsopen`|  
  
 L’expression entière `oflag` est constituée en combinant une ou plusieurs des constantes manifestes suivantes, qui sont définies dans \<fcntl.h>. Quand plusieurs constantes forment l’argument `oflag`, elles sont combinées avec l’opérateur OR au niveau du bit ( `|` ).  
  
 `_O_APPEND`  
 Repositionne un pointeur de fichier à la fin du fichier avant chaque opération d'écriture.  
  
 `_O_BINARY`  
 Ouvre un fichier en mode binaire (non traduit). (Pour obtenir une description du mode binaire, consultez [fopen](../../c-runtime-library/reference/fopen-wfopen.md).)  
  
 `_O_CREAT`  
 Crée un fichier et l'ouvre pour l'accès en écriture. N'a aucun effet si le fichier spécifié par `filename` existe. L'argument `pmode` est obligatoire quand `_O_CREAT` est spécifié.  
  
 `_O_CREAT | _O_SHORT_LIVED`  
 Crée un fichier temporaire et, dans la mesure du possible, n'effectue pas de vidage sur disque. L'argument `pmode` est obligatoire quand `_O_CREAT` est spécifié.  
  
 `_O_CREAT | _O_TEMPORARY`  
 Crée un fichier temporaire ; le fichier est supprimé quand le dernier descripteur de fichier est fermé. L'argument `pmode` est obligatoire quand `_O_CREAT` est spécifié.  
  
 `_O_CREAT | _O_EXCL`  
 Retourne une valeur d'erreur s'il existe un fichier spécifié par `filename`. Applicable uniquement en cas d'utilisation avec `_O_CREAT`.  
  
 `_O_NOINHERIT`  
 Empêche la création d'un descripteur de fichier partagé.  
  
 `_O_RANDOM`  
 Spécifie l'accès principalement aléatoire à partir du disque.  
  
 `_O_RDONLY`  
 Ouvre un fichier pour l'accès en lecture uniquement. Ne peut pas être spécifié avec `_O_RDWR` ou `_O_WRONLY`.  
  
 `_O_RDWR`  
 Ouvre un fichier pour l'accès en lecture et en écriture. Ne peut pas être spécifié avec `_O_RDONLY` ou `_O_WRONLY`.  
  
 `_O_SEQUENTIAL`  
 Spécifie l'accès principalement séquentiel à partir du disque.  
  
 `_O_TEXT`  
 Ouvre un fichier en mode texte (traduit). (Pour plus d’informations, consultez [E/S de fichier en mode texte et binaire](../../c-runtime-library/text-and-binary-mode-file-i-o.md) et [fopen](../../c-runtime-library/reference/fopen-wfopen.md).)  
  
 `_O_TRUNC`  
 Ouvre un fichier et le tronque à une longueur nulle. Le fichier doit disposer d'une autorisation en écriture. Ne peut pas être spécifié avec `_O_RDONLY`. `_O_TRUNC` utilisé avec `_O_CREAT` ouvre un fichier existant ou crée un fichier.  
  
> [!NOTE]
>  L'indicateur `_O_TRUNC` détruit le contenu du fichier spécifié.  
  
 `_O_WRONLY`  
 Ouvre un fichier pour l'accès en écriture uniquement. Ne peut pas être spécifié avec `_O_RDONLY` ou `_O_RDWR`.  
  
 `_O_U16TEXT`  
 Ouvre un fichier en mode Unicode UTF-16.  
  
 `_O_U8TEXT`  
 Ouvre un fichier en mode Unicode UTF-8.  
  
 `_O_WTEXT`  
 Ouvre un fichier en mode Unicode.  
  
 Pour spécifier le mode d'accès aux fichiers, vous devez spécifier `_O_RDONLY`, `_O_RDWR` ou `_O_WRONLY`. Il n'y a aucune valeur par défaut pour le mode d'accès.  
  
 Quand un fichier est ouvert en mode Unicode à l'aide d'`_O_WTEXT`, `_O_U8TEXT` ou `_O_U16TEXT`, les fonctions d'entrée traduisent les données qui sont lues à partir du fichier en données UTF-16 stockées comme type `wchar_t`. Les fonctions qui écrivent dans un fichier ouvert en mode Unicode attendent des mémoires tampons qui contiennent des données UTF-16 stockées comme type `wchar_t`. Si le fichier est encodé au format UTF-8, les données UTF-16 sont traduites en UTF-8 lors de leur écriture et le contenu du fichier encodé au format UTF-8 est traduit en UTF-16 lorsqu'il est lu. Toute tentative de lecture ou d'écriture d'une quantité impaire d'octets en mode Unicode provoque une erreur de validation de paramètre. Pour lire ou écrire des données stockées dans votre programme au format UTF-8, utilisez un mode de fichier binaire ou texte au lieu d'un mode Unicode. Vous êtes responsable de toute traduction d'encodage nécessaire.  
  
 Si `_sopen` est appelée avec `_O_WRONLY | _O_APPEND` (mode Append) et `_O_WTEXT`, `_O_U16TEXT` ou `_O_U8TEXT`, elle tente d'abord d'ouvrir le fichier pour la lecture et l'écriture, de lire la marque BOM, puis de le rouvrir pour l'accès en écriture uniquement. Si l'ouverture du fichier pour l'accès en lecture et en écriture échoue, elle ouvre le fichier pour l'accès en écriture uniquement et utilise la valeur par défaut pour le paramètre de mode Unicode.  
  
 L’argument `shflag` est une expression constante constituée de l’une des constantes manifestes suivantes, qui sont définies dans \<share.h>.  
  
 `_SH_DENYRW`  
 Refuse l'accès en lecture et en écriture à un fichier.  
  
 `_SH_DENYWR`  
 Refuse l'accès en écriture à un fichier.  
  
 `_SH_DENYRD`  
 Refuse l'accès en lecture à un fichier.  
  
 `_SH_DENYNO`  
 Autorise l'accès en lecture et en écriture.  
  
 L'argument `pmode` est obligatoire uniquement quand `_O_CREAT` est spécifié. Si le fichier n'existe pas, `pmode` spécifie les paramètres d'autorisation du fichier, qui sont définis quand le nouveau fichier est fermé pour la première fois. Sinon, `pmode` est ignoré. `pmode` est une expression entière qui contient l’une des constantes manifestes `_S_IWRITE` et `_S_IREAD` (ou les deux), qui sont définies dans \<sys\stat.h>. Quand les deux constantes sont données, elles sont combinées avec l'opérateur OR au niveau du bit. La signification de `pmode` est la suivante.  
  
 `_S_IWRITE`  
 Écriture autorisée.  
  
 `_S_IREAD`  
 Lecture autorisée.  
  
 `_S_IREAD | _S_IWRITE`  
 Lecture et écriture autorisées.  
  
 Si l'autorisation d'écriture n'est pas accordée, le fichier est en lecture seule. Dans le système d'exploitation Windows, tous les fichiers sont lisibles ; il est impossible d'accorder une autorisation en écriture seule. Par conséquent, les modes `_S_IWRITE` et `_S_IREAD | _S_IWRITE` sont équivalents.  
  
 `_sopen` applique le masque d'autorisation de fichier actif à `pmode` avant que les autorisations soient définies. (Voir [_umask](../../c-runtime-library/reference/umask.md).)  
  
## <a name="requirements"></a>Spécifications  
  
|Routine|En-tête requis|En-tête facultatif|  
|-------------|---------------------|---------------------|  
|`_sopen`|\<io.h>|\<fcntl.h>, \<sys\types.h>, \<sys\stat.h>, \<share.h>|  
|`_wsopen`|\<io.h> ou \<wchar.h>|\<fcntl.h>, \<sys\types.h>, \<sys\stat.h>, \<share.h>|  
  
 Pour plus d’informations sur la compatibilité, consultez [Compatibilité](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Exemple  
 Consultez l’exemple relatif à [_locking](../../c-runtime-library/reference/locking.md).  
  
## <a name="net-framework-equivalent"></a>Équivalent .NET Framework  
 Non applicable. Pour appeler la fonction C standard, utilisez `PInvoke`. Pour plus d’informations, consultez [Exemples d’appel de plateforme](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f).  
  
## <a name="see-also"></a>Voir aussi  
 [E/S de bas niveau](../../c-runtime-library/low-level-i-o.md)   
 [_close](../../c-runtime-library/reference/close.md)   
 [_creat, _wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
 [fopen, _wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [_fsopen, _wfsopen](../../c-runtime-library/reference/fsopen-wfsopen.md)   
 [_open, _wopen](../../c-runtime-library/reference/open-wopen.md)
