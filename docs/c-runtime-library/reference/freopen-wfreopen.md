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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 435211b246f9943588aeef2005e501a9eac59c6b
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82916345"
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

*train*<br/>
Pointeur désignant la structure **FILE**.

## <a name="return-value"></a>Valeur de retour

Chacune de ces fonctions retourne un pointeur vers le fichier qui vient d'être ouvert. Si une erreur se produit, le fichier d’origine est fermé et la fonction retourne une valeur de pointeur **null** . Si *path*, *mode*ou *Stream* est un pointeur null, ou si *filename* est une chaîne vide, ces fonctions appellent le gestionnaire de paramètres non valides, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions attribuent à **errno** la valeur **EINVAL** et retournent la **valeur null**.

Consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) pour plus d’informations sur ces éléments et autres codes d’erreur.

## <a name="remarks"></a>Notes 

Il existe des versions plus sécurisées de ces fonctions ; consultez [freopen_s, _wfreopen_s](freopen-s-wfreopen-s.md).

La fonction **freopen** ferme le fichier actuellement associé au *flux* et réaffecte le *flux* au fichier spécifié par le *chemin d’accès*. **_wfreopen** est une version à caractères larges de **_freopen**; les arguments *path* et *mode* de **_wfreopen** sont des chaînes à caractères larges. dans le cas contraire, **_wfreopen** et **_freopen** se comportent de la même façon.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tfreopen**|**freopen**|**freopen**|**_wfreopen**|

**freopen** est généralement utilisé pour rediriger les fichiers **stdin**, **stdout**et **stderr** des fichiers préalablement ouverts vers des fichiers spécifiés par l’utilisateur. Le nouveau fichier associé à *Stream* est ouvert en *mode*, qui est une chaîne de caractères spécifiant le type d’accès demandé pour le fichier, comme suit :

|*mode*|Accès|
|-|-|
| **r** | Ouvre pour l'accès en lecture. Si le fichier n’existe pas ou est introuvable, l’appel **freopen** échoue. |
| **s** | Ouvre un fichier vide pour l'accès en écriture. Si le fichier spécifié existe, son contenu est détruit. |
| **un** | S'ouvre pour écriture à la fin du fichier (ajout) sans supprimer le marqueur de fin de fichier (EOF) avant que de nouvelles données soient écrites dans le fichier. Crée le fichier s'il n'existe pas. |
| **"r +"** | Ouvre pour l'accès en lecture et en écriture. Le fichier doit exister. |
| **"w +"** | Ouvre un fichier vide pour l'accès en lecture et en écriture. Si le fichier existe, son contenu est détruit. |
| **"a +"** | S'ouvre pour lecture et ajout. L'opération d'ajout inclut la suppression du marqueur EOF avant que de nouvelles données soient écrites dans le fichier. Le marqueur EOF n'est pas restauré une fois l'écriture terminée. Crée le fichier s'il n'existe pas. |

Utilisez les types **« w »** et **« w + »** avec précaution, car ils peuvent détruire les fichiers existants.

Lorsqu’un fichier est ouvert avec le type d’accès **« a »** ou **« a + »** , toutes les opérations d’écriture se produisent à la fin du fichier. Même si le pointeur de fichier peut être repositionné à l’aide de [fseek](fseek-fseeki64.md) ou [rembobiner](rewind.md), le pointeur de fichier est toujours redéplacé à la fin du fichier avant toute opération d’écriture. Par conséquent, les données existantes ne peuvent pas être remplacées.

Le mode **« a »** ne supprime pas le marqueur EOF avant l’ajout au fichier. Après l'ajout, la commande MS-DOS TYPE affiche uniquement les données jusqu'au marqueur EOF d'origine, et non les données ajoutées au fichier. Le mode **« a + »** supprime le marqueur EOF avant d’ajouter au fichier. Après l'ajout, la commande MS-DOS TYPE affiche toutes les données du fichier. Le mode **« a + »** est requis pour l’ajout à un fichier de flux qui se termine par le marqueur EOF Ctrl + Z.

Quand le type d’accès **"r +"**, **"w +"** ou **"a +"** est spécifié, la lecture et l’écriture sont autorisées (le fichier est dit ouvert pour "mettre à jour"). Cependant, quand vous basculez entre lecture et écriture, une opération intermédiaire [fsetpos](fsetpos.md), [fseek](fseek-fseeki64.md) ou [rewind](rewind.md) doit exister. La position actuelle peut être spécifiée pour l’opération [fsetpos](fsetpos.md) ou [fseek](fseek-fseeki64.md) , si vous le souhaitez. Outre les valeurs ci-dessus, l’un des caractères suivants peut être inclus dans la chaîne de *mode* pour spécifier le mode de traduction pour les nouvelles lignes.

|modificateur de *mode*|Mode de traduction|
|-|-|
| **t** | Ouvrir en mode texte (traduit). |
| **p** | Ouvrir en mode binaire (non traduit); les traductions qui impliquent des caractères de retour chariot et de saut de ligne sont supprimées. |

En mode texte (traduit), les combinaisons retour chariot-saut de ligne sont traduites en caractères de saut de ligne unique (LF) à l’entrée ; Les caractères de saut de ligne sont traduits en combinaisons CR-LF en sortie. De même, Ctrl+Z est interprété comme un caractère de fin de fichier en entrée. Dans les fichiers ouverts en lecture ou pour l’écriture et la lecture avec **« a + »**, la bibliothèque Runtime recherche un Ctrl + Z à la fin du fichier et le supprime, si possible. Cela est dû au fait que l’utilisation de [fseek](fseek-fseeki64.md) et [ftell](ftell-ftelli64.md) pour se déplacer dans un fichier peut entraîner un comportement incorrect de [fseek](fseek-fseeki64.md) vers la fin du fichier. L’option **t** est une extension Microsoft qui ne doit pas être utilisée là où la portabilité ANSI est souhaitée.

Si **t** ou **b** n’est pas spécifié en *mode*, le mode de traduction par défaut est défini par la variable globale [_fmode](../../c-runtime-library/fmode.md). Si **t** ou **b** est préfixé à l’argument, la fonction échoue et retourne la **valeur null**.

Pour en savoir plus sur les modes texte et binaire, consultez [E/S de fichier en mode texte et binaire](../../c-runtime-library/text-and-binary-mode-file-i-o.md).

## <a name="requirements"></a>Spécifications

|Function|En-tête requis|
|--------------|---------------------|
|**freopen**|\<stdio.h>|
|**_wfreopen**|\<stdio.h> ou \<wchar.h>|

La console n’est pas prise en charge dans les applications de plateforme Windows universelle (UWP). Les handles de flux standard associés à la console, **stdin**, **stdout**et **stderr**, doivent être redirigés pour que les fonctions runtime C puissent les utiliser dans les applications UWP. Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

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
