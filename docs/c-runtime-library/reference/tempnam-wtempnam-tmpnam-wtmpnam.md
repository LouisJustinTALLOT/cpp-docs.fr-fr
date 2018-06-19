---
title: _tempnam, _wtempnam, tmpnam, _wtmpnam | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _wtempnam
- _wtmpnam
- tmpnam
- _tempnam
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
- wtempnam
- _wtmpnam
- wtmpnam
- tmpnam
- _wtempnam
- _tempnam
dev_langs:
- C++
helpviewer_keywords:
- wtempnam function
- file names [C++], creating temporary
- _tempnam function
- ttmpnam function
- tmpnam function
- tempnam function
- wtmpnam function
- temporary files, creating
- file names [C++], temporary
- _ttmpnam function
- _wtmpnam function
- _wtempnam function
ms.assetid: 3ce75f0f-5e30-42a6-9791-8d7cbfe70fca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 55ff069d72d68493eee524ea2f9c012d2fc7f534
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32417011"
---
# <a name="tempnam-wtempnam-tmpnam-wtmpnam"></a>_tempnam, _wtempnam, tmpnam, _wtmpnam

Génèrent des noms que vous pouvez utiliser pour créer des fichiers temporaires. Il existe des versions plus sécurisées de ces fonctions. Consultez [tmpnam_s, _wtmpnam_s](tmpnam-s-wtmpnam-s.md).

## <a name="syntax"></a>Syntaxe

```C
char *_tempnam(
   const char *dir,
   const char *prefix
);
wchar_t *_wtempnam(
   const wchar_t *dir,
   const wchar_t *prefix
);
char *tmpnam(
   char *str
);
wchar_t *_wtmpnam(
   wchar_t *str
);
```

### <a name="parameters"></a>Paramètres

*Préfixe*<br/>
La chaîne qui sera ajouté aux noms retournés par **_tempnam**.

*dir*<br/>
Chemin d’accès utilisé dans le nom de fichier en l’absence de variable d’environnement TMP ou si TMP n’est pas un répertoire valide.

*str*<br/>
Pointeur destiné à contenir le nom généré et qui sera identique à celui retourné par la fonction. Il s’agit d’un moyen pratique d’enregistrer le nom généré.

## <a name="return-value"></a>Valeur de retour

Chacune de ces fonctions retourne un pointeur vers le nom généré ou **NULL** s’il existe un échec. Échec peut se produire si vous essayez de plus de **TMP_MAX** (voir STDIO. H) appels avec **tmpnam** ou si vous utilisez **_tempnam** et il est un nom de répertoire non valide spécifié dans la variable d’environnement TMP et dans le *dir* paramètre.

> [!NOTE]
> Les pointeurs retournés par **tmpnam** et **_wtmpnam** pointent vers les mémoires tampons statiques internes. [free](free.md) ne doit pas être appelé pour libérer ces pointeurs. **libre** doit être appelée pour les pointeurs alloués par **_tempnam** et **_wtempnam**.

## <a name="remarks"></a>Notes

Chacune de ces fonctions retourne le nom d’un fichier qui n’existe pas actuellement. **tmpnam** retourne un nom unique dans le répertoire de travail en cours et **_tempnam** vous permet de générer un nom unique dans un répertoire autre que celui en cours. Notez que lorsqu’un nom de fichier est précédé d’une barre oblique inverse et d’aucune information de chemin, comme \fname21, cela indique que le nom est valide pour le répertoire de travail actif.

Pour **tmpnam**, vous pouvez stocker ce nom de fichier généré dans *str*. Si *str* est **NULL**, puis **tmpnam** laisse le résultat dans un tampon statique interne. Par conséquent, tous les appels suivants détruisent cette valeur. Le nom généré par **tmpnam** se compose d’un nom de fichier généré par le programme et, après le premier appel à **tmpnam**, une extension de fichier de numéros séquentiels dans base 32 (.1-.vvu, lorsque **TMP_MAX**  dans STDIO. H est 32 767).

**_tempnam** générera un nom de fichier unique pour un répertoire choisi par les règles suivantes :

- Si la variable d’environnement TMP est définie avec un nom de répertoire valide, des noms de fichiers uniques sont générés pour le répertoire spécifié par TMP.

- Si la variable d’environnement TMP n’est pas définie ou si elle est définie sur le nom d’un répertoire qui n’existe pas, **_tempnam** utilisera le *dir* paramètre en tant que le chemin d’accès pour lesquels il génère des noms uniques.

- Si la variable d’environnement TMP n’est pas définie ou si elle est définie sur le nom d’un répertoire qui n’existe pas et si *dir* est **NULL** ou le nom d’un répertoire qui n’existe pas, la valeur **_ tempnam** utilisera le répertoire de travail en cours pour générer des noms uniques. Actuellement, si les deux TMP et *dir* spécifier des noms de répertoires qui n’existent pas, le **_tempnam** appel de fonction échoue.

Le nom retourné par **_tempnam** sera une concaténation de *préfixe* et un numéro séquentiel, qui permet de combiner pour créer un nom de fichier unique pour le répertoire spécifié. **_tempnam** génère des noms de fichiers qui ont pas d’extension. **_tempnam** utilise [malloc](malloc.md) d’allocation d’espace pour le nom de fichier ; le programme est responsable de la libération de cet espace lorsqu’il n’est plus nécessaire.

**_tempnam** et **tmpnam** handle d’arguments de chaîne de caractères multioctets selon le cas, reconnaissant les séquences de caractères multioctets en fonction de la page de codes OEM obtient automatiquement à partir du système d’exploitation. **_wtempnam** est une version à caractères larges de **_tempnam**; les arguments et la valeur de retour de **_wtempnam** sont des chaînes à caractères larges. **_wtempnam** et **_tempnam** se comportent de façon identique, sauf que **_wtempnam** ne gère pas les chaînes de caractères multioctets. **_wtmpnam** est une version à caractères larges de **tmpnam**; la valeur des arguments et de retour de **_wtmpnam** sont des chaînes à caractères larges. **_wtmpnam** et **tmpnam** se comportent de façon identique, sauf que **_wtmpnam** ne gère pas les chaînes de caractères multioctets.

Si **_DEBUG** et **_CRTDBG_MAP_ALLOC** sont définies, **_tempnam** et **_wtempnam** sont remplacés par les appels à [_tempnam _dbg et _wtempnam_dbg](tempnam-dbg-wtempnam-dbg.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ttmpnam**|**tmpnam**|**tmpnam**|**_wtmpnam**|
|**_ttempnam**|**_tempnam**|**_tempnam**|**_wtempnam**|

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_tempnam**|\<stdio.h>|
|**_wtempnam**, **_wtmpnam**|\<stdio.h> ou \<wchar.h>|
|**tmpnam**|\<stdio.h>|

Pour plus d’informations sur la compatibilité, voir consultez [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_tempnam.c
// compile with: /W3
// This program uses tmpnam to create a unique filename in the
// current working directory, then uses _tempnam to create
// a unique filename with a prefix of stq.

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   char* name1 = NULL;
   char* name2 = NULL;

   // Create a temporary filename for the current working directory:
   if( ( name1 = tmpnam( NULL ) ) != NULL ) // C4996
   // Note: tmpnam is deprecated; consider using tmpnam_s instead
      printf( "%s is safe to use as a temporary file.\n", name1 );
   else
      printf( "Cannot create a unique filename\n" );

   // Create a temporary filename in temporary directory with the
   // prefix "stq". The actual destination directory may vary
   // depending on the state of the TMP environment variable and
   // the global variable P_tmpdir.

   if( ( name2 = _tempnam( "c:\\tmp", "stq" ) ) != NULL )
      printf( "%s is safe to use as a temporary file.\n", name2 );
   else
      printf( "Cannot create a unique filename\n" );

   // When name2 is no longer needed :
   if(name2)
     free(name2);

}
```

```Output
\s1gk. is safe to use as a temporary file.
C:\DOCUME~1\user\LOCALS~1\Temp\2\stq2 is safe to use as a temporary file.
```

## <a name="see-also"></a>Voir aussi

[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[malloc](malloc.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[tmpfile](tmpfile.md)<br/>
[tmpfile_s](tmpfile-s.md)<br/>
