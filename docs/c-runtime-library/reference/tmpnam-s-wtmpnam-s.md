---
title: tmpnam_s, _wtmpnam_s
ms.date: 11/04/2016
api_name:
- tmpnam_s
- _wtmpnam_s
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
- tmpnam_s
- _wtmpnam_s
- L_tmpnam_s
helpviewer_keywords:
- tmpnam_s function
- file names [C++], creating temporary
- _wtmpnam_s function
- L_tmpnam_s constant
- temporary files, creating
- file names [C++], temporary
- wtmpnam_s function
ms.assetid: e70d76dc-49f5-4aee-bfa2-f1baa2bcd29f
ms.openlocfilehash: 847df0d2369857d009c39b4dd61adce45094899c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70946043"
---
# <a name="tmpnam_s-_wtmpnam_s"></a>tmpnam_s, _wtmpnam_s

Génèrent des noms que vous pouvez utiliser pour créer des fichiers temporaires. Ces versions de [tmpnam et _wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md) intègrent les améliorations de sécurité décrites dans [Fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t tmpnam_s(
   char * str,
   size_t sizeInChars
);
errno_t _wtmpnam_s(
   wchar_t *str,
   size_t sizeInChars
);
template <size_t size>
errno_t tmpnam_s(
   char (&str)[size]
); // C++ only
template <size_t size>
errno_t _wtmpnam_s(
   wchar_t (&str)[size]
); // C++ only
```

### <a name="parameters"></a>Paramètres

*str*<br/>
Pointeur destiné à contenir le nom généré.

*sizeInChars*<br/>
Taille de la mémoire tampon en caractères.

## <a name="return-value"></a>Valeur de retour

Ces deux fonctions retournent 0 en cas de réussite ou un numéro d’erreur en cas d’échec.

### <a name="error-conditions"></a>Conditions d’erreur

|||||
|-|-|-|-|
|*str*|*sizeInChars*|**Valeur de retour**|**Contenu de** *chaîne*|
|**NULL**|any|**EINVAL**|non modifié|
|not **null** (pointe vers une mémoire valide)|trop court|**ERANGE**|non modifié|

Si *Str* a la **valeur null**, le gestionnaire de paramètres non valides est appelé, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions définissent **errno** sur **EINVAL** et retournent **EINVAL**.

## <a name="remarks"></a>Notes

Chacune de ces fonctions retourne le nom d’un fichier qui n’existe pas actuellement. **tmpnam_s** retourne un nom unique dans le répertoire temporaire Windows désigné renvoyé par [GetTempPathW](/windows/win32/api/fileapi/nf-fileapi-gettemppathw). Notez que lorsqu’un nom de fichier est précédé d’une barre oblique inverse et d’aucune information de chemin, comme \fname21, cela indique que le nom est valide pour le répertoire de travail actif.

Pour **tmpnam_s**, vous pouvez stocker ce nom de fichier généré dans *Str*. La longueur maximale d’une chaîne retournée par **tmpnam_s** est **L_tmpnam_s**, définie dans stdio. Manutention. Si *Str* a la **valeur null**, **tmpnam_s** laisse le résultat dans une mémoire tampon statique interne. Par conséquent, tous les appels suivants détruisent cette valeur. Le nom généré par **tmpnam_s** se compose d’un nom de fichier généré par le programme et, après le premier appel à **tmpnam_s**, une extension de fichier de nombres séquentiels dans la base 32 (. 1-. 1vvvvvu, lorsque **TMP_MAX_S** dans stdio. H est **INT_MAX**).

**tmpnam_s** gère automatiquement les arguments de chaîne de caractères multioctets comme il convient, en identifiant les séquences de caractères multioctets en fonction de la page de codes OEM obtenue du système d’exploitation. **_wtmpnam_s** est une version à caractères larges de **tmpnam_s**; l’argument et la valeur de retour de **_wtmpnam_s** sont des chaînes à caractères larges. **_wtmpnam_s** et **tmpnam_s** se comportent de la même manière, sauf que **_wtmpnam_s** ne gère pas les chaînes de caractères multioctets.

En C++, l’utilisation de ces fonctions est simplifiée par les surcharges de modèle ; celles-ci peuvent déduire automatiquement la longueur de la mémoire tampon, ce qui évite d’avoir à spécifier un argument de taille. Pour plus d'informations, consultez [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ttmpnam_s**|**tmpnam_s**|**tmpnam_s**|**_wtmpnam_s**|

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**tmpnam_s**|\<stdio.h>|
|**_wtmpnam_s**|\<stdio.h> ou \<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_tmpnam_s.c
// This program uses tmpnam_s to create a unique filename in the
// current working directory.
//

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   char name1[L_tmpnam_s];
   errno_t err;
   int i;

   for (i = 0; i < 15; i++)
   {
      err = tmpnam_s( name1, L_tmpnam_s );
      if (err)
      {
         printf("Error occurred creating unique filename.\n");
         exit(1);
      }
      else
      {
         printf( "%s is safe to use as a temporary file.\n", name1 );
      }
   }
}
```

```Output
C:\Users\LocalUser\AppData\Local\Temp\u19q8.0 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.1 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.2 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.3 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.4 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.5 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.6 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.7 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.8 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.9 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.a is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.b is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.c is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.d is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.e is safe to use as a temporary file.
```

## <a name="see-also"></a>Voir aussi

[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[malloc](malloc.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[tmpfile_s](tmpfile-s.md)<br/>
