---
description: 'En savoir plus sur : _mktemp_s, _wmktemp_s'
title: _mktemp_s, _wmktemp_s
ms.date: 4/2/2020
api_name:
- _mktemp_s
- _wmktemp_s
- _o__mktemp_s
- _o__wmktemp_s
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
- wmktemp_s
- mktemp_s
- _mktemp_s
- _wmktemp_s
helpviewer_keywords:
- _tmktemp_s function
- mktemp_s function
- _wmktemp_s function
- _mktemp_s function
- files [C++], temporary
- tmktemp_s function
- wmktemp_s function
- temporary files [C++]
ms.assetid: 92a7e269-7f3d-4c71-bad6-14bc827a451d
ms.openlocfilehash: c1dcaa7817de70a3478e9bf8014b4ab223837c34
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97114302"
---
# <a name="_mktemp_s-_wmktemp_s"></a>_mktemp_s, _wmktemp_s

Crée un nom de fichier unique. Ces versions de [_mktemp, _wmktemp](mktemp-wmktemp.md) intègrent les améliorations de sécurité décrites dans [Fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t _mktemp_s(
   char *nameTemplate,
   size_t sizeInChars
);
errno_t _wmktemp_s(
   wchar_t *nameTemplate,
   size_t sizeInChars
);
template <size_t size>
errno_t _mktemp_s(
   char (&nameTemplate)[size]
); // C++ only
template <size_t size>
errno_t _wmktemp_s(
   wchar_t (&nameTemplate)[size]
); // C++ only
```

### <a name="parameters"></a>Paramètres

*nameTemplate*<br/>
Modèle de nom de fichier.

*sizeInChars*<br/>
Taille de la mémoire tampon en caractères codés sur un octet dans **_mktemp_s**; caractères larges dans **_wmktemp_s**, y compris la marque de fin null.

## <a name="return-value"></a>Valeur renvoyée

Ces deux fonctions retournent zéro en cas de réussite, sinon un code d’erreur.

### <a name="error-conditions"></a>Conditions d'erreur

|*nameTemplate*|*sizeInChars*|Valeur retournée|Nouvelle valeur dans *nameTemplate*|
|----------------|-------------------|----------------------|-------------------------------|
|**NULL**|n'importe laquelle|**EINVAL**|**NULL**|
|Format incorrect (consultez la section Notes pour obtenir le format approprié)|n'importe laquelle|**EINVAL**|chaîne vide|
|n'importe laquelle|<= nombre de X|**EINVAL**|chaîne vide|

Si l’une des conditions d’erreur ci-dessus se présente, le gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **errno** a la valeur **EINVAL** et les fonctions retournent **EINVAL**.

## <a name="remarks"></a>Notes

La fonction **_mktemp_s** crée un nom de fichier unique en modifiant l’argument *nameTemplate* , de sorte qu’après l’appel, le pointeur *nameTemplate* pointe vers une chaîne contenant le nouveau nom de fichier. **_mktemp_s** gère automatiquement les arguments de chaîne de caractères multioctets si nécessaire, en identifiant les séquences de caractères multioctets en fonction de la page de codes multioctets en cours d’utilisation par le système d’exécution. **_wmktemp_s** est une version à caractères larges de **_mktemp_s**; l’argument de **_wmktemp_s** est une chaîne de caractères larges. autrement, les **_wmktemp_s** et **_mktemp_s** se comportent de la même manière, sauf que **_wmktemp_s** ne gère pas les chaînes de caractères multioctets.

Les versions de la bibliothèque de débogage de ces fonctions remplissent d’abord la mémoire tampon avec 0xFE. Pour désactiver ce comportement, utilisez [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine Tchar.h|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmktemp_s**|**_mktemp_s**|**_mktemp_s**|**_wmktemp_s**|

L’argument *nameTemplate* se présente sous la forme **baseXXXXXX**, où *base* est la partie du nouveau nom de fichier que vous fournissez et chaque X est un espace réservé pour un caractère fourni par **_mktemp_s**. Chaque caractère d’espace réservé dans *nameTemplate* doit être un x majuscule. **_mktemp_s** conserve la *base* et remplace le premier x de fin par un caractère alphabétique. **_mktemp_s** remplace le X de fin suivant par une valeur à cinq chiffres ; Cette valeur est un nombre unique qui identifie le processus appelant, ou dans les programmes multithread, le thread appelant.

Chaque appel réussi à **_mktemp_s** modifie *nameTemplate*. Dans chaque appel suivant du même processus ou thread avec le même argument *nameTemplate* , **_mktemp_s** recherche les noms de fichiers qui correspondent aux noms retournés par **_mktemp_s** dans les appels précédents. Si aucun fichier n’existe pour un nom donné, **_mktemp_s** retourne ce nom. Si des fichiers existent pour tous les noms précédemment retournés, **_mktemp_s** crée un nouveau nom en remplaçant le caractère alphabétique qu’il a utilisé dans le nom précédemment retourné par la lettre minuscule suivante disponible, dans l’ordre, de « a » à « z ». Par exemple, si *base* est :

> **FN**

et la valeur à cinq chiffres fournie par **_mktemp_s** est 12345, le premier nom retourné est :

> **fna12345**

Si ce nom est utilisé pour créer le fichier FNA12345 et que ce fichier existe toujours, le nom suivant retourné sur un appel du même processus ou thread avec la même *base* pour *nameTemplate* est :

> **fnb12345**

Si le fichier FNA12345 n'existe pas, le nom suivant retourné est de nouveau :

> **fna12345**

**_mktemp_s** pouvez créer un maximum de 26 noms de fichiers uniques pour une combinaison donnée de valeurs de *base* et *nameTemplate* . Par conséquent, FNZ12345 est le dernier nom de fichier unique **_mktemp_s** pouvez créer pour les valeurs de *base* et *nameTemplate* utilisées dans cet exemple.

En C++, l’utilisation de ces fonctions est simplifiée par les surcharges de modèle ; les surcharges peuvent déduire la longueur de la mémoire tampon automatiquement (ce qui évite d’avoir à spécifier un argument taille) et peuvent remplacer automatiquement les fonctions plus anciennes et non sécurisées par leurs équivalentes plus récentes et sécurisées. Pour plus d’informations, consultez [Sécuriser les surcharges de modèle](../../c-runtime-library/secure-template-overloads.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_mktemp_s**|\<io.h>|
|**_wmktemp_s**|\<io.h> ou \<wchar.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```cpp
// crt_mktemp_s.cpp
/* The program uses _mktemp to create
* five unique filenames. It opens each filename
* to ensure that the next name is unique.
*/

#include <io.h>
#include <string.h>
#include <stdio.h>

char *fnTemplate = "fnXXXXXX";
char names[5][9];

int main()
{
   int i, err, sizeInChars;
   FILE *fp;

   for( i = 0; i < 5; i++ )
   {
      strcpy_s( names[i], sizeof(names[i]), fnTemplate );
      /* Get the size of the string and add one for the null terminator.*/
      sizeInChars = strnlen(names[i], 9) + 1;
      /* Attempt to find a unique filename: */
      err = _mktemp_s( names[i], sizeInChars );
      if( err != 0 )
         printf( "Problem creating the template" );
      else
      {
         if( fopen_s( &fp, names[i], "w" ) == 0 )
            printf( "Unique filename is %s\n", names[i] );
         else
            printf( "Cannot open %s\n", names[i] );
         fclose( fp );
      }
   }

   return 0;
}
```

### <a name="sample-output"></a>Exemple de sortie

```Output
Unique filename is fna03188
Unique filename is fnb03188
Unique filename is fnc03188
Unique filename is fnd03188
Unique filename is fne03188
```

## <a name="see-also"></a>Voir aussi

[Gestion de fichiers](../../c-runtime-library/file-handling.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_getpid](getpid.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[_tempnam, _wtempnam, tmpnam, _wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)<br/>
[tmpfile_s](tmpfile-s.md)<br/>
