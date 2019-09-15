---
title: gets_s, _getws_s
ms.date: 11/04/2016
api_name:
- _getws_s
- gets_s
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _getws_s
- gets_s
helpviewer_keywords:
- getws_s function
- _getws_s function
- lines, getting
- streams, getting lines
- buffers, avoiding overruns
- buffer overruns
- buffers, buffer overruns
- gets_s function
- standard input, reading from
ms.assetid: 5880c36f-122c-4061-a1a5-aeeced6fe58c
ms.openlocfilehash: f282b4e8de12185a19e07374cf565788dc549136
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70954970"
---
# <a name="gets_s-_getws_s"></a>gets_s, _getws_s

Obtient une ligne du flux **stdin** . Ces versions de [gets, _getws](../../c-runtime-library/gets-getws.md) intègrent des améliorations de sécurité, comme décrit dans [Fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
char *gets_s(
   char *buffer,
   size_t sizeInCharacters
);
wchar_t *_getws_s(
   wchar_t *buffer,
   size_t sizeInCharacters
);
```

```cpp
template <size_t size>
char *gets_s( char (&buffer)[size] ); // C++ only

template <size_t size>
wchar_t *_getws_s( wchar_t (&buffer)[size] ); // C++ only
```

### <a name="parameters"></a>Paramètres

*buffer*<br/>
Emplacement de stockage pour une chaîne entrée.

*sizeInCharacters*<br/>
Taille de la mémoire tampon.

## <a name="return-value"></a>Valeur de retour

Retourne la *mémoire tampon* en cas de réussite. Un pointeur **NULL** indique une condition d’erreur ou de fin de fichier. Utilisez [ferror](ferror.md) ou [feof](feof.md) pour déterminer laquelle des deux s’est produite.

## <a name="remarks"></a>Notes

La fonction **gets_s** lit une ligne dans le flux d’entrée standard **stdin** et la stocke dans la *mémoire tampon*. La ligne se compose de tous les caractères jusqu’à et y compris le premier caractère de saut de ligne (« \n »). **gets_s** remplace ensuite le caractère de saut de ligne par un caractère null (' \ 0 ') avant de retourner la ligne. En revanche, la fonction **fgets_s** conserve le caractère de saut de ligne.

Si le premier caractère lu est le caractère de fin de fichier, un caractère NULL est stocké au début de la *mémoire tampon* et la **valeur null** est retournée.

**_getws_s** est une version à caractères larges de **gets_s**; son argument et sa valeur de retour sont des chaînes à caractères larges.

Si *buffer* a la **valeur null** ou si la valeur de *sizeInCharacters* est inférieure ou égale à zéro, ou si la mémoire tampon est trop petite pour contenir la ligne d’entrée et la marque de fin null, ces fonctions appellent un gestionnaire de paramètres non valides, comme décrit dans [paramètre Validation](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions retournent la **valeur null** et attribuent à errno la valeur **ERANGE**.

En C++, l’utilisation de ces fonctions est simplifiée par les surcharges de modèle ; les surcharges peuvent déduire la longueur de la mémoire tampon automatiquement (ce qui évite d’avoir à spécifier un argument taille) et peuvent remplacer automatiquement les fonctions plus anciennes et non sécurisées par leurs équivalentes plus récentes et sécurisées. Pour plus d'informations, consultez [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_getts_s**|**gets_s**|**gets_s**|**_getws_s**|

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**gets_s**|\<stdio.h>|
|**_getws_s**|\<stdio.h> ou \<wchar.h>|

La console n’est pas prise en charge dans les applications de plateforme Windows universelle (UWP). Les handles de flux standard associés à la console, **stdin**, **stdout**et **stderr**, doivent être redirigés pour que les fonctions runtime C puissent les utiliser dans les applications UWP. Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemples

```C
// crt_gets_s.c
// This program retrieves a string from the stdin and
// prints the same string to the console.

#include <stdio.h>

int main( void )
{
   char line[21]; // room for 20 chars + '\0'
   gets_s( line, 20 );
   printf( "The line entered was: %s\n", line );
}
```

```Input
Hello there!
```

```Output
The line entered was: Hello there!
```

## <a name="see-also"></a>Voir aussi

[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[gets, _getws](../../c-runtime-library/gets-getws.md)<br/>
[fgets, fgetws](fgets-fgetws.md)<br/>
[fputs, fputws](fputs-fputws.md)<br/>
[puts, _putws](puts-putws.md)<br/>
