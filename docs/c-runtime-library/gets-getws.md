---
description: 'En savoir plus sur : obtient, _getws'
title: gets, _getws
ms.date: 4/2/2020
api_name:
- _getws
- gets
- _o__getws
- _o_gets
api_location:
- msvcr80.dll
- msvcr90.dll
- msvcr120.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcrt.dll
- msvcr100.dll
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _getts
- gets
- _getws
helpviewer_keywords:
- getws function
- getts function
- _getws function
- lines, getting
- streams, getting lines
- _getts function
- gets function
- standard input, reading from
ms.assetid: 1ec2dd4b-f801-48ea-97c2-892590f16024
ms.openlocfilehash: cb2bf89bfcec8e10e05fa479cd7c9d78d9c6d80e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97181720"
---
# <a name="gets-_getws"></a>gets, _getws

Obtient une ligne du flux `stdin` Des versions plus sécurisées de ces fonctions sont disponibles. Consultez [gets_s, _getws_s](../c-runtime-library/reference/gets-s-getws-s.md).

> [!IMPORTANT]
> Ces fonctions sont obsolètes. Depuis Visual Studio 2015, elles ne sont pas disponibles dans la bibliothèque CRT. Les versions sécurisées de ces fonctions, gets_s et getws_s, sont toujours disponibles. Pour plus d’informations sur ces fonctions alternatives, consultez [gets_s, _getws_s](../c-runtime-library/reference/gets-s-getws-s.md).

> [!IMPORTANT]
> Cette API ne peut pas être utilisée dans les applications qui s'exécutent dans le Windows Runtime. Pour plus d’informations, consultez [Fonctions CRT non prises en charge dans les applications de la plateforme Windows universelle](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```
char *gets(
   char *buffer
);
wchar_t *_getws(
   wchar_t *buffer
);
template <size_t size>
char *gets(
   char (&buffer)[size]
); // C++ only
template <size_t size>
wchar_t *_getws(
   wchar_t (&buffer)[size]
); // C++ only
```

#### <a name="parameters"></a>Paramètres

*mémoire tampon*<br/>
Emplacement de stockage pour une chaîne entrée.

## <a name="return-value"></a>Valeur renvoyée

Retourne son argument en cas de réussite. Un pointeur **NULL** indique une condition d’erreur ou de fin de fichier. Utilisez [ferror](../c-runtime-library/reference/ferror.md) ou [feof](../c-runtime-library/reference/feof.md) pour déterminer laquelle des deux s’est produite. Si `buffer` a la valeur **NULL** ou est une chaîne vide, ces fonctions appellent le gestionnaire de paramètres non valides, comme décrit dans [Validation de paramètre](../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions retournent **NULL** et affectent à errno la valeur `EINVAL`.

## <a name="remarks"></a>Notes

La fonction `gets` lit une ligne dans le flux d’entrée standard `stdin` et la stocke dans `buffer`. La ligne se compose de tous les caractères jusqu’à et y compris le premier caractère de saut de ligne (« \n »). `gets` remplace ensuite le caractère de saut de ligne par un caractère null (« \0 ») avant de retourner la ligne. En revanche, la fonction `fgets` conserve le caractère de saut de ligne. `_getws` est une version à caractères larges de `gets`; son argument et sa valeur de retour sont des chaînes à caractères larges.

> [!IMPORTANT]
> Comme il n’existe aucun moyen de limiter le nombre de caractères lus par gets, une entrée non approuvée peut facilement provoquer des dépassements de la mémoire tampon. Utilisez `fgets` à la place.

En C++, ces fonctions ont des surcharges de modèle qui appellent les équivalents plus récents et sécurisés de ces fonctions. Pour plus d’informations, consultez [Sécuriser les surcharges de modèle](../c-runtime-library/secure-template-overloads.md).

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](global-state.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|`_getts`|`gets`|`gets`|`_getws`|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|`gets`|\<stdio.h>|
|`_getws`|\<stdio.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```c
// crt_gets.c
// compile with: /WX /W3

#include <stdio.h>

int main( void )
{
   char line[21]; // room for 20 chars + '\0'
   gets( line );  // C4996
   // Danger: No way to limit input to 20 chars.
   // Consider using gets_s instead.
   printf( "The line entered was: %s\n", line );
}
```

Notez qu’une entrée de plus de 20 caractères entraînera le dépassement de la mémoire tampon de ligne et presque certainement le blocage du programme.

```Output

Hello there!The line entered was: Hello there!
```

## <a name="see-also"></a>Voir aussi

[E/S de flux](../c-runtime-library/stream-i-o.md)<br/>
[fgets, fgetws](../c-runtime-library/reference/fgets-fgetws.md)<br/>
[fputs, fputws](../c-runtime-library/reference/fputs-fputws.md)<br/>
[puts, _putws](../c-runtime-library/reference/puts-putws.md)
