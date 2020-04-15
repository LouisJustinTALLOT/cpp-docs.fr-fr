---
title: freopen, _wfreopen
ms.date: 4/2/2020
api_name:
- freopen
- _wfreopen
- _o__wfreopen
- _o_freopen
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
- _wfreopen
- _tfreopen
- freopen
helpviewer_keywords:
- _wfreopen function
- file pointers [C++], reassigning
- _tfreopen function
- freopen function
- tfreopen function
- wfreopen function
ms.assetid: de4b73f8-1043-4d62-98ee-30d2022da885
ms.openlocfilehash: 635775469ed6545abd6da43ba27d496d439f80ee
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345871"
---
# <a name="freopen-_wfreopen"></a>freopen, _wfreopen

Réaffecte un pointeur de fichier. Des versions plus sécurisées de ces fonctions sont disponibles ; consultez [freopen_s, _wfreopen_s](freopen-s-wfreopen-s.md).

## <a name="syntax"></a>Syntaxe

```C
FILE *freopen(
   const char *path,
   const char *mode,
   FILE *stream
);
FILE *_wfreopen(
   const wchar_t *path,
   const wchar_t *mode,
   FILE *stream
);
```

### <a name="parameters"></a>Paramètres

*path*<br/>
Chemin d’accès du nouveau fichier.

*mode*<br/>
Type d'accès autorisé.

*Flux*<br/>
Pointeur désignant la structure **FILE**.

## <a name="return-value"></a>Valeur de retour

Chacune de ces fonctions retourne un pointeur vers le fichier qui vient d'être ouvert. En cas d’erreur, le fichier d’origine est fermé et la fonction renvoie une valeur de pointeur **NULL.** Si *le chemin,* *le mode,* ou *le flux* est un pointeur nul, ou si le nom *de fichier* est une chaîne vide, ces fonctions invoquent le gestionnaire de paramètres invalides, tel que décrit dans la validation [de paramètres](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions **définies errno** à **EINVAL** et retourner **NULL**.

Consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) pour plus d’informations sur ces éléments et autres codes d’erreur.

## <a name="remarks"></a>Notes

Il existe des versions plus sécurisées de ces fonctions ; consultez [freopen_s, _wfreopen_s](freopen-s-wfreopen-s.md).

La fonction **freopen** ferme le fichier actuellement associé au *flux* et réaffecte le *flux* au fichier spécifié par *chemin*. **_wfreopen** est une version à caractère large de **_freopen**; les arguments *de chemin* et *de mode* pour **_wfreopen** sont des cordes de caractère large. **_wfreopen** et **_freopen** se comportent de façon identique autrement.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tfreopen**|**freopen**|**freopen**|**_wfreopen**|

**freopen** est généralement utilisé pour rediriger les fichiers pré-ouverts **stdin**, **stdout**, et **stderr** aux fichiers spécifiés par l’utilisateur. Le nouveau fichier associé au *flux* est ouvert avec *le mode*, qui est une chaîne de caractères spécifiant le type d’accès demandé pour le fichier, comme suit:

|*mode*|Accès|
|-|-|
| **"r"** | Ouvre pour l'accès en lecture. Si le fichier n’existe pas ou ne peut pas être trouvé, l’appel **freopen** échoue. |
| **"w"** | Ouvre un fichier vide pour l'accès en écriture. Si le fichier spécifié existe, son contenu est détruit. |
| **"a"** | S'ouvre pour écriture à la fin du fichier (ajout) sans supprimer le marqueur de fin de fichier (EOF) avant que de nouvelles données soient écrites dans le fichier. Crée le fichier s'il n'existe pas. |
| **"r"** | Ouvre pour l'accès en lecture et en écriture. Le fichier doit exister. |
| **"W"** | Ouvre un fichier vide pour l'accès en lecture et en écriture. Si le fichier existe, son contenu est détruit. |
| **"A"** | S'ouvre pour lecture et ajout. L'opération d'ajout inclut la suppression du marqueur EOF avant que de nouvelles données soient écrites dans le fichier. Le marqueur EOF n'est pas restauré une fois l'écriture terminée. Crée le fichier s'il n'existe pas. |

Utilisez les types **"w"** et **"w"** avec soin, car ils peuvent détruire les fichiers existants.

Lorsqu’un fichier est ouvert avec le type **d’accès** **« a »** ou « a », toutes les opérations d’écriture ont lieu à la fin du fichier. Bien que le pointeur de fichier peut être repositionné à l’aide [de fseek](fseek-fseeki64.md) ou [rembobinage](rewind.md), le pointeur de fichier est toujours déplacé vers la fin du fichier avant toute opération de rédaction est effectuée. Par conséquent, les données existantes ne peuvent pas être écrasées.

Le mode **"a"** ne supprime pas le marqueur EOF avant de passer au fichier. Après l'ajout, la commande MS-DOS TYPE affiche uniquement les données jusqu'au marqueur EOF d'origine, et non les données ajoutées au fichier. Le mode **« a »** supprime le marqueur EOF avant de passer au fichier. Après l'ajout, la commande MS-DOS TYPE affiche toutes les données du fichier. Le mode **« a »** est nécessaire pour passer à un fichier de flux qui est terminé avec le marqueur EOF CTRL-Z.

Lorsque le type **d’accès « r »**, **« w »** ou « **a »** est spécifié, la lecture et l’écriture sont autorisées (le fichier est dit ouvert pour la « mise à jour »). Cependant, quand vous basculez entre lecture et écriture, une opération intermédiaire [fsetpos](fsetpos.md), [fseek](fseek-fseeki64.md) ou [rewind](rewind.md) doit exister. La position actuelle peut être spécifiée pour [l’opération fsetpos](fsetpos.md) ou [fseek,](fseek-fseeki64.md) si désiré. En plus des valeurs ci-dessus, l’un des personnages suivants peut être inclus dans la chaîne de *mode* pour spécifier le mode de traduction pour les nouvelles lignes.

|*modificateur de mode*|Mode de traduction|
|-|-|
| **T** | Ouvrir en mode texte (traduit). |
| **B** | Ouvrez en mode binaire (non traduit); les traductions impliquant des caractères de transport-retour et d’alimentation en ligne sont supprimées. |

En mode texte (traduit), les combinaisons d’alimentation en ligne de retour de transport (CR-LF) sont traduites en caractères d’alimentation en ligne unique (LF) sur l’entrée; Les caractères LF sont traduits en combinaisons CR-LF sur la sortie. De même, Ctrl+Z est interprété comme un caractère de fin de fichier en entrée. Dans les fichiers ouverts pour la lecture ou pour l’écriture et la lecture avec **"a"**, la bibliothèque de temps d’exécution vérifie pour un CTRL-Z à la fin du fichier et le supprime, si possible. Ceci est fait parce que l’utilisation [de fseek](fseek-fseeki64.md) et [ftell](ftell-ftelli64.md) pour se déplacer dans un fichier peut provoquer [fseek](fseek-fseeki64.md) de se comporter incorrectement vers la fin du fichier. **L’option t** est une extension Microsoft qui ne doit pas être utilisée lorsque la portabilité ANSI est souhaitée.

Si **t** ou **b** n’est pas donné en *mode,* le mode de traduction par défaut est défini par la variable globale [_fmode](../../c-runtime-library/fmode.md). Si **t** ou **b** est préfixé à l’argument, la fonction échoue et renvoie **NULL**.

Pour en savoir plus sur les modes texte et binaire, consultez [E/S de fichier en mode texte et binaire](../../c-runtime-library/text-and-binary-mode-file-i-o.md).

## <a name="requirements"></a>Spécifications

|Fonction|En-tête requis|
|--------------|---------------------|
|**freopen**|\<stdio.h>|
|**_wfreopen**|\<stdio.h> ou \<wchar.h>|

La console n’est pas prise en charge dans les applications Universal Windows Platform (UWP). Les poignées de flux standard qui sont associées à la console, **stdin**, **stdout**, et **stderr**, doivent être redirigés avant que les fonctions C run-time peuvent les utiliser dans les applications UWP. Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_freopen.c
// compile with: /W3
// This program reassigns stderr to the file
// named FREOPEN.OUT and writes a line to that file.
#include <stdio.h>
#include <stdlib.h>

FILE *stream;

int main( void )
{
   // Reassign "stderr" to "freopen.out":
   stream = freopen( "freopen.out", "w", stderr ); // C4996
   // Note: freopen is deprecated; consider using freopen_s instead

   if( stream == NULL )
      fprintf( stdout, "error on freopen\n" );
   else
   {
      fprintf( stdout, "successfully reassigned\n" ); fflush( stdout );
      fprintf( stream, "This will go to the file 'freopen.out'\n" );
      fclose( stream );
   }
   system( "type freopen.out" );
}
```

```Output
successfully reassigned
This will go to the file 'freopen.out'
```

## <a name="see-also"></a>Voir aussi

[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[_fileno](fileno.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_setmode](setmode.md)<br/>
