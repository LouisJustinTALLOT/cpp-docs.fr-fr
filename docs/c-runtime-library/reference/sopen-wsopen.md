---
title: _sopen, _wsopen
ms.date: 11/04/2016
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
ms.openlocfilehash: 4bb728b8e48190eb01e47dc9cd7de65a350f612d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50626129"
---
# <a name="sopen-wsopen"></a>_sopen, _wsopen

Ouvre un fichier pour le partage. Des versions plus sécurisées de ces fonctions sont disponibles : consultez [_sopen_s, _wsopen_s](sopen-s-wsopen-s.md).

## <a name="syntax"></a>Syntaxe

```C
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

### <a name="parameters"></a>Paramètres

*filename*<br/>
Nom du fichier.

*oflag*<br/>
Type d'opérations autorisées.

*shflag*<br/>
Type de partage autorisé.

*pmode*<br/>
Paramètre d'autorisation.

## <a name="return-value"></a>Valeur de retour

Chacune de ces fonctions retourne un descripteur de fichier pour le fichier ouvert.

Si *filename* ou *oflag* est un **NULL** pointeur, ou si *oflag* ou *shflag* n’est pas dans un valide plage de valeurs, le Gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions retournent -1 et la valeur **errno** à une des valeurs suivantes.

|Valeur de la variable errno|Condition|
|-|-|
**EACCES**|Le chemin d'accès donné est un répertoire, ou le fichier est en lecture seule, mais une opération de type « ouvert en écriture » a été tentée.
**EEXIST**|**_O_CREAT** et **_O_EXCL** indicateurs ont été spécifiées, mais *filename* existe déjà.
**EINVAL**|Non valide *oflag* ou *shflag* argument.
**EMFILE**|Aucun autre descripteur de fichier n'est disponible.
**ENOENT**|Fichier ou chemin d'accès introuvable.

Pour plus d'informations sur ces codes de retour et autres, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

Le **_sopen** fonction ouvre le fichier spécifié par *filename* et prépare le fichier en lecture partagée ou d’écriture, comme défini par *oflag* et *shflag* . **_wsopen** est une version à caractères larges de **_sopen**; le *filename* l’argument de **_wsopen** est une chaîne de caractères larges. **_wsopen** et **_sopen** se comportent de façon identique dans le cas contraire.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tsopen**|**_sopen**|**_sopen**|**_wsopen**|

L’expression d’entier *oflag* est formé en combinant une ou plusieurs des constantes manifestes suivantes, qui sont définies dans \<fcntl.h >. Quand deux ou plusieurs constantes forment l’argument *oflag*, elles sont combinées avec l’opérateur OR au niveau du bit ( **&#124;** ).

|*oflag* constante|Comportement|
|-|-|
**_O_APPEND**|Déplace le pointeur de fichier à la fin du fichier avant chaque opération d'écriture.
**_O_BINARY**|Ouvre le fichier en mode binaire (non traduit). (Pour obtenir une description du mode binaire, consultez [fopen](fopen-wfopen.md).)
**_O_CREAT**|Crée un fichier et l'ouvre pour l'accès en écriture. N’a aucun effet si le fichier spécifié par *filename* existe. Le *pmode* argument est requis quand **_O_CREAT** est spécifié.
**_O_CREAT** &AMP;#124; **_O_SHORT_LIVED**|Crée un fichier temporaire et, dans la mesure du possible, n'effectue pas de vidage sur disque. Le *pmode* argument est requis quand **_O_CREAT** est spécifié.
**_O_CREAT** &AMP;#124; **_O_TEMPORARY**|Crée un fichier temporaire ; le fichier est supprimé quand le dernier descripteur de fichier est fermé. Le *pmode* argument est requis quand **_O_CREAT** est spécifié.
**_O_CREAT**&AMP;#124; ` _O_EXCL`|Retourne une valeur d’erreur si un fichier spécifié par *filename* existe. S’applique uniquement lorsque utilisé avec **_O_CREAT**.
**_O_NOINHERIT**|Empêche la création d'un descripteur de fichier partagé.
**_O_RANDOM**|Indique que la mise en cache est optimisée pour, mais non limitée à, l'accès aléatoire à partir du disque.
**_O_RDONLY**|Ouvre un fichier pour l'accès en lecture uniquement. Ne peut pas être spécifié avec **_O_RDWR** ou **_O_WRONLY**.
**_O_RDWR**|Ouvre un fichier pour l'accès en lecture et en écriture. Ne peut pas être spécifié avec **_O_RDONLY** ou **_O_WRONLY**.
**_O_SEQUENTIAL**|Indique que la mise en cache est optimisée pour, mais non limitée à, l'accès séquentiel à partir du disque.
**_O_TEXT**|Ouvre un fichier en mode texte (traduit). (Pour plus d’informations, consultez [E/S de fichier en mode texte et binaire](../../c-runtime-library/text-and-binary-mode-file-i-o.md) et [fopen](fopen-wfopen.md).)
**_O_TRUNC**|Ouvre un fichier et le tronque à une longueur nulle. Le fichier doit disposer d'une autorisation en écriture. Ne peut pas être spécifié avec **_O_RDONLY**. **_O_TRUNC** utilisé avec **_O_CREAT** ouvre un fichier existant ou crée un fichier. **Remarque :** le **_O_TRUNC** indicateur détruit le contenu du fichier spécifié.
**_O_WRONLY**|Ouvre un fichier pour l'accès en écriture uniquement. Ne peut pas être spécifié avec **_O_RDONLY** ou **_O_RDWR**.
**_O_U16TEXT**|Ouvre un fichier en mode Unicode UTF-16.
**_O_U8TEXT**|Ouvre un fichier en mode Unicode UTF-8.
**_O_WTEXT**|Ouvre un fichier en mode Unicode.

Pour spécifier le mode d’accès de fichier, vous devez spécifier soit **_O_RDONLY**, **_O_RDWR**, ou **_O_WRONLY**. Il n'y a aucune valeur par défaut pour le mode d'accès.

Quand un fichier est ouvert en mode Unicode à l’aide de **_O_WTEXT**, **_O_U8TEXT**, ou **_O_U16TEXT**, d’entrée fonctions traduisent les données lues à partir du fichier en données UTF-16 stockées en tant que type **wchar_t**. Fonctions qui écrivent dans un fichier ouvert en mode Unicode attendent des mémoires tampons qui contiennent des données UTF-16 stockées comme type **wchar_t**. Si le fichier est encodé au format UTF-8, les données UTF-16 sont traduites en UTF-8 lors de leur écriture et le contenu du fichier encodé au format UTF-8 est traduit en UTF-16 lorsqu'il est lu. Toute tentative de lecture ou d'écriture d'une quantité impaire d'octets en mode Unicode provoque une erreur de validation de paramètre. Pour lire ou écrire des données stockées dans votre programme au format UTF-8, utilisez un mode de fichier binaire ou texte au lieu d'un mode Unicode. Vous êtes responsable de toute traduction d'encodage nécessaire.

Si **_sopen** est appelée avec **_O_WRONLY** | **_O_APPEND** (mode append) et **_O_WTEXT**, **_O_ U16TEXT**, ou **_O_U8TEXT**, il tente d’abord d’ouvrir le fichier pour lecture et écriture, lire la marque BOM, puis rouvrez-la pour un accès en écriture uniquement. Si l'ouverture du fichier pour l'accès en lecture et en écriture échoue, elle ouvre le fichier pour l'accès en écriture uniquement et utilise la valeur par défaut pour le paramètre de mode Unicode.

L’argument *shflag* est une expression constante constituée de l’une des constantes manifestes suivantes, qui sont définies dans \<share.h >.

|*shflag* constante|Comportement|
|-|-|
**_SH_DENYRW**|Refuse l'accès en lecture et en écriture à un fichier.
**_SH_DENYWR**|Refuse l'accès en écriture à un fichier.
**_SH_DENYRD**|Refuse l'accès en lecture à un fichier.
**_SH_DENYNO**|Autorise l'accès en lecture et en écriture.

Le *pmode* argument est requis uniquement lorsque **_O_CREAT** est spécifié. Si le fichier n’existe pas, *pmode* spécifie les paramètres d’autorisation du fichier, qui sont définis quand le nouveau fichier est fermé pour la première fois. Sinon, *pmode* est ignoré. *pmode* est une expression d’entier qui contient tout ou partie des constantes manifestes **_S_IWRITE** et **_S_IREAD**, qui sont définies dans \<sys\stat.h >. Quand les deux constantes sont données, elles sont combinées avec l'opérateur OR au niveau du bit. La signification de *pmode* se présente comme suit.

|*pmode*|Signification|
|-|-|
**_S_IREAD**|Lecture autorisée uniquement.
**_S_IWRITE**|Écriture autorisée. (En fait, autorise la lecture et l'écriture.)
**_S_IREAD** &AMP;#124; **_S_IWRITE**|Lecture et écriture autorisées.

Si l'autorisation d'écriture n'est pas accordée, le fichier est en lecture seule. Dans le système d'exploitation Windows, tous les fichiers sont lisibles ; il est impossible d'accorder une autorisation en écriture seule. Par conséquent, les modes **_S_IWRITE** et **_S_IREAD** | **_S_IWRITE** sont équivalentes.

**_sopen** applique le masque d’autorisation de fichier actuelle à *pmode* avant que les autorisations sont définies. (Voir [_umask](umask.md).)

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|En-tête facultatif|
|-------------|---------------------|---------------------|
|**_sopen**|\<io.h>|\<fcntl.h>, \<sys\types.h>, \<sys\stat.h>, \<share.h>|
|**_wsopen**|\<io.h> ou \<wchar.h>|\<fcntl.h>, \<sys\types.h>, \<sys\stat.h>, \<share.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Consultez l’exemple relatif à [_locking](locking.md).

## <a name="see-also"></a>Voir aussi

[E/S de bas niveau](../../c-runtime-library/low-level-i-o.md)<br/>
[_close](close.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_fsopen, _wfsopen](fsopen-wfsopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
