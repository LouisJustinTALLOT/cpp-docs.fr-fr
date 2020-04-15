---
title: freopen_s, _wfreopen_s
ms.date: 4/2/2020
api_name:
- _wfreopen_s
- freopen_s
- _o__wfreopen_s
- _o_freopen_s
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
- freopen_s
- _tfreopen_s
- _wfreopen_s
helpviewer_keywords:
- _tfreopen_s function
- _wfreopen_s function
- file pointers [C++], reassigning
- tfreopen_s function
- wfreopen_s function
- freopen_s function
ms.assetid: ad25a4da-6ad4-476b-a86d-660b221ca84d
ms.openlocfilehash: a24e34ead905d2f704bfbf4d829064c656272e97
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345919"
---
# <a name="freopen_s-_wfreopen_s"></a>freopen_s, _wfreopen_s

Réaffecte un pointeur de fichier. Ces versions de [freopen, _wfreopen](freopen-wfreopen.md) intègrent des améliorations de sécurité, comme décrit dans [Fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t freopen(
   FILE** pFile,
   const char *path,
   const char *mode,
   FILE *stream
);
errno_t _wfreopen(
   FILE** pFile,
   const wchar_t *path,
   const wchar_t *mode,
   FILE *stream
);
```

### <a name="parameters"></a>Paramètres

*pFile (en)*<br/>
Pointeur vers le pointeur de fichier devant être fourni par l'appel.

*path*<br/>
Chemin d’accès du nouveau fichier.

*mode*<br/>
Type d'accès autorisé.

*Flux*<br/>
Pointeur désignant la structure **FILE**.

## <a name="return-value"></a>Valeur de retour

Chacune de ces fonctions retourne un code d'erreur. Si une erreur se produit, le fichier d'origine est fermé.

## <a name="remarks"></a>Notes

La fonction **freopen_s** ferme le fichier actuellement associé au *flux* et réaffecte le *flux* au fichier spécifié par *chemin*. **_wfreopen_s** est une version à caractère large de **_freopen_s**; les arguments *de chemin* et *de mode* pour **_wfreopen_s** sont des cordes de caractère large. **_wfreopen_s** et **_freopen_s** se comportent de façon identique autrement.

Si l’un des *PFile*, *chemin*, *mode*, ou *flux* sont **NULL**, ou si *le chemin* est une chaîne vide, ces fonctions invoquent le gestionnaire de paramètres invalides, comme décrit dans La validation [de paramètres](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions **définies errno** à **EINVAL** et retourner **EINVAL**.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tfreopen_s**|**freopen_s**|**freopen_s**|**_wfreopen_s**|

**freopen_s** est généralement utilisé pour rediriger les fichiers pré-ouverts **stdin**, **stdout**, et **stderr** vers les fichiers spécifiés par l’utilisateur. Le nouveau fichier associé au *flux* est ouvert avec *le mode*, qui est une chaîne de caractères spécifiant le type d’accès demandé pour le fichier, comme suit:

|*mode*|Accès|
|-|-|
| **"r"** | Ouvre pour l'accès en lecture. Si le fichier n’existe pas ou ne peut pas être trouvé, **l’freopen_s** appel échoue. |
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
|**freopen_s**|\<stdio.h>|
|**_wfreopen_s**|\<stdio.h> ou \<wchar.h>|

La console n’est pas prise en charge dans les applications Universal Windows Platform (UWP). Les poignées de flux standard qui sont associées à la console, **stdin**, **stdout**, et **stderr**, doivent être redirigés avant que les fonctions C run-time peuvent les utiliser dans les applications UWP. Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_freopen_s.c
// This program reassigns stderr to the file
// named FREOPEN.OUT and writes a line to that file.

#include <stdio.h>
#include <stdlib.h>

FILE *stream;

int main( void )
{
   errno_t err;
   // Reassign "stderr" to "freopen.out":
   err = freopen_s( &stream, "freopen.out", "w", stderr );

   if( err != 0 )
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
[freopen, _wfreopen](freopen-wfreopen.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[_fileno](fileno.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_setmode](setmode.md)<br/>
