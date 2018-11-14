---
title: freopen, _wfreopen
ms.date: 11/04/2016
apiname:
- freopen
- _wfreopen
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
ms.openlocfilehash: 4c570837bddea1f5e986ae5f767279ab2637ea21
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51332502"
---
# <a name="freopen-wfreopen"></a>freopen, _wfreopen

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

*flux de données*<br/>
Pointeur désignant la structure **FILE**.

## <a name="return-value"></a>Valeur de retour

Chacune de ces fonctions retourne un pointeur vers le fichier qui vient d'être ouvert. Si une erreur se produit, le fichier d’origine est fermé et la fonction retourne un **NULL** valeur de pointeur. Si *chemin d’accès*, *mode*, ou *flux* est un pointeur null, ou si *filename* est une chaîne vide, ces fonctions appellent le paramètre non valide Gestionnaire, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions définissent **errno** à **EINVAL** et retourner **NULL**.

Pour plus d’informations sur ces codes d’erreur et les autres, consultez [_doserrno, errno, _sys_errlist et _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Notes

Il existe des versions plus sécurisées de ces fonctions ; consultez [freopen_s, _wfreopen_s](freopen-s-wfreopen-s.md).

Le **freopen** fonction ferme le fichier actuellement associé *flux* et réaffecte *flux* dans le fichier spécifié par *chemin d’accès*. **_wfreopen** est une version à caractères larges de **_freopen**; le *chemin d’accès* et *mode* arguments à **_wfreopen** sont chaînes à caractères larges. **_wfreopen** et **_freopen** se comportent de façon identique dans le cas contraire.

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tfreopen**|**freopen**|**freopen**|**_wfreopen**|

**freopen** est généralement utilisé pour rediriger les fichiers pré-ouverts **stdin**, **stdout**, et **stderr** vers les fichiers spécifiés par l’utilisateur. Le nouveau fichier associé *flux* est ouvert avec *mode*, qui est une chaîne de caractères spécifiant le type d’accès demandé pour le fichier, comme suit :

|*mode*|Accès|
|-|-|
| **"r"** | Ouvre pour l'accès en lecture. Si le fichier n’existe pas ou est introuvable, la **freopen** appeler échoue. |
| **"w"** | Ouvre un fichier vide pour l'accès en écriture. Si le fichier spécifié existe, son contenu est détruit. |
| **"a"** | S'ouvre pour écriture à la fin du fichier (ajout) sans supprimer le marqueur de fin de fichier (EOF) avant que de nouvelles données soient écrites dans le fichier. Crée le fichier s'il n'existe pas. |
| **"r+"** | Ouvre pour l'accès en lecture et en écriture. Le fichier doit exister. |
| **"w+"** | Ouvre un fichier vide pour l'accès en lecture et en écriture. Si le fichier existe, son contenu est détruit. |
| **"a+"** | S'ouvre pour lecture et ajout. L'opération d'ajout inclut la suppression du marqueur EOF avant que de nouvelles données soient écrites dans le fichier. Le marqueur EOF n'est pas restauré une fois l'écriture terminée. Crée le fichier s'il n'existe pas. |

Utilisez le **« w »** et **« w + »** types avec précaution, car ils peuvent détruire les fichiers existants.

Quand un fichier est ouvert avec le **« a »** ou **« a + »** type, d’accès toutes les opérations ont lieu à la fin du fichier d’écriture. Bien que le pointeur de fichier peut être repositionné à l’aide de [fseek](fseek-fseeki64.md) ou [rewind](rewind.md), le pointeur de fichier est toujours redéplacé à la fin du fichier avant toute opération d’écriture. Par conséquent, les données existantes ne peuvent pas être remplacées.

Le **« a »** mode ne supprime pas le marqueur EOF avant d’ajouter au fichier. Après l'ajout, la commande MS-DOS TYPE affiche uniquement les données jusqu'au marqueur EOF d'origine, et non les données ajoutées au fichier. Le **« a + »** mode ne supprime pas le marqueur EOF avant d’ajouter au fichier. Après l'ajout, la commande MS-DOS TYPE affiche toutes les données du fichier. Le **« a + »** mode est obligatoire pour ajouter des données dans un fichier de flux de données qui se termine par le marqueur EOF CTRL + Z.

Lorsque le **« r + »**, **« w + »**, ou **« a + »** type d’accès est spécifié, la lecture et l’écriture sont autorisées (le fichier est réputé être ouvert pour « update »). Cependant, quand vous basculez entre lecture et écriture, une opération intermédiaire [fsetpos](fsetpos.md), [fseek](fseek-fseeki64.md) ou [rewind](rewind.md) doit exister. La position actuelle peut être spécifiée pour le [fsetpos](fsetpos.md) ou [fseek](fseek-fseeki64.md) opération, si vous le souhaitez. Outre les valeurs ci-dessus, un des caractères suivants peut-être être inclus dans le *mode* chaîne pour spécifier le mode de traduction pour les nouvelles lignes.

|*mode* modificateur|Mode de traduction|
|-|-|
| **t** | Ouvrir en mode texte (traduit). |
| **b** | Ouvrir en mode binaire (non traduit) ; les traductions implique la suppression des caractères de retour chariot et de saut de ligne. |

En mode texte (traduit), les combinaisons de sauts de ligne (CR-LF) de chariot sont traduites en caractères de saut de ligne (LF) unique d’entrée ; Les caractères de saut de ligne sont traduits en combinaisons retour chariot / saut de ligne en sortie. De même, Ctrl+Z est interprété comme un caractère de fin de fichier en entrée. Dans les fichiers ouverts en lecture ou de lecture et écriture avec **« a + »**, la bibliothèque runtime recherche un CTRL + Z à la fin du fichier et le supprime, si possible. En effet à l’aide de [fseek](fseek-fseeki64.md) et [ftell](ftell-ftelli64.md) pour se déplacer dans un fichier risque de [fseek](fseek-fseeki64.md) au comportement incorrect vers la fin du fichier. Le **t** option est une extension Microsoft qui ne doit pas être utilisée lorsque la portabilité ANSI est souhaitée.

Si **t** ou **b** n’est pas spécifié dans *mode*, le mode de traduction par défaut est défini par la variable globale [_fmode](../../c-runtime-library/fmode.md). Si **t** ou **b** est préfixé à l’argument, la fonction échoue et le retourne **NULL**.

Pour en savoir plus sur les modes texte et binaire, consultez [E/S de fichier en mode texte et binaire](../../c-runtime-library/text-and-binary-mode-file-i-o.md).

## <a name="requirements"></a>Configuration requise

|Fonction|En-tête requis|
|--------------|---------------------|
|**freopen**|\<stdio.h>|
|**_wfreopen**|\<stdio.h> ou \<wchar.h>|

La console n’est pas pris en charge dans les applications Universal Windows Platform (UWP). Les handles de flux standard qui sont associés à la console, **stdin**, **stdout**, et **stderr**, doivent être redirigés pour que les fonctions runtime C de les utiliser dans les applications UWP . Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

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
