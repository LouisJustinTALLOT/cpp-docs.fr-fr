---
description: 'En savoir plus sur : _tempnam, _wtempnam, tmpnam, _wtmpnam'
title: _tempnam, _wtempnam, tmpnam, _wtmpnam
ms.date: 11/04/2016
api_name:
- _wtempnam
- _wtmpnam
- tmpnam
- _tempnam
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
- wtempnam
- _wtmpnam
- wtmpnam
- tmpnam
- _wtempnam
- _tempnam
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
ms.openlocfilehash: ee127a7d3ee59ec697dc0032fefb04b84b839c4d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97326194"
---
# <a name="_tempnam-_wtempnam-tmpnam-_wtmpnam"></a>_tempnam, _wtempnam, tmpnam, _wtmpnam

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

*prefix*<br/>
Chaîne qui sera précédée des noms retournés par **_tempnam**.

*dir*<br/>
Chemin d’accès utilisé dans le nom de fichier en l’absence de variable d’environnement TMP ou si TMP n’est pas un répertoire valide.

*str*<br/>
Pointeur destiné à contenir le nom généré et qui sera identique à celui retourné par la fonction. Il s’agit d’un moyen pratique d’enregistrer le nom généré.

## <a name="return-value"></a>Valeur renvoyée

Chacune de ces fonctions retourne un pointeur vers le nom généré ou **null** en cas d’échec. Une défaillance peut se produire si vous tentez plus de **TMP_MAX** (voir stdio. H) appelle avec **tmpnam** ou si vous utilisez **_tempnam** et qu’un nom de répertoire non valide est spécifié dans la variable d’environnement TMP et dans le paramètre *dir* .

> [!NOTE]
> Les pointeurs retournés par **tmpnam** et **_wtmpnam** pointent vers des mémoires tampon statiques internes. [free](free.md) ne doit pas être appelé pour libérer ces pointeurs. **Free** doit être appelé pour les pointeurs alloués par **_tempnam** et **_wtempnam**.

## <a name="remarks"></a>Notes

Chacune de ces fonctions retourne le nom d’un fichier qui n’existe pas actuellement. **tmpnam** retourne un nom unique dans le répertoire temporaire Windows désigné renvoyé par [GetTempPathW](/windows/win32/api/fileapi/nf-fileapi-gettemppathw). **\_ tempnam** génère un nom unique dans un répertoire autre que celui désigné. Notez que lorsqu’un nom de fichier est précédé d’une barre oblique inverse et d’aucune information de chemin, comme \fname21, cela indique que le nom est valide pour le répertoire de travail actif.

Pour **tmpnam**, vous pouvez stocker ce nom de fichier généré dans *Str*. Si *Str* a la **valeur null**, **tmpnam** laisse le résultat dans une mémoire tampon statique interne. Par conséquent, tous les appels suivants détruisent cette valeur. Le nom généré par **tmpnam** se compose d’un nom de fichier généré par le programme et, après le premier appel à **tmpnam**, une extension de fichier de nombres séquentiels dans la base 32 (. 1-4. vvu, lorsque **TMP_MAX** dans stdio. H est 32 767).

**_tempnam** générera un nom de fichier unique pour un répertoire choisi par les règles suivantes :

- Si la variable d’environnement TMP est définie avec un nom de répertoire valide, des noms de fichiers uniques sont générés pour le répertoire spécifié par TMP.

- Si la variable d’environnement TMP n’est pas définie ou si elle est définie sur le nom d’un répertoire qui n’existe pas, **_tempnam** utilise le paramètre *dir* comme chemin d’accès pour lequel elle génère des noms uniques.

- Si la variable d’environnement TMP n’est pas définie ou si elle est définie sur le nom d’un répertoire qui n’existe pas, et si *dir* a la valeur **null** ou est défini sur le nom d’un répertoire qui n’existe pas, **_tempnam** utilisera le répertoire de travail actuel pour générer des noms uniques. Actuellement, si TMP et *dir* spécifient tous deux des noms de répertoires qui n’existent pas, l’appel de la fonction **_tempnam** échoue.

Le nom retourné par **_tempnam** sera une concaténation de *préfixe* et un nombre séquentiel, qui sera combiné pour créer un nom de fichier unique pour le répertoire spécifié. **_tempnam** génère des noms de fichiers qui n’ont pas d’extension. **_tempnam** utilise [malloc](malloc.md) pour allouer de l’espace pour le nom de fichier ; le programme est chargé de libérer cet espace lorsqu’il n’est plus nécessaire.

**_tempnam** et **tmpnam** gèrent automatiquement les arguments de chaîne de caractères multioctets comme il convient, en identifiant les séquences de caractères multioctets en fonction de la page de codes OEM obtenue du système d’exploitation. **_wtempnam** est une version à caractères larges de **_tempnam**; les arguments et la valeur de retour de **_wtempnam** sont des chaînes à caractères larges. **_wtempnam** et **_tempnam** se comportent de la même manière, sauf que **_wtempnam** ne gère pas les chaînes de caractères multioctets. **_wtmpnam** est une version à caractères larges de **tmpnam**; l’argument et la valeur de retour de **_wtmpnam** sont des chaînes à caractères larges. **_wtmpnam** et **tmpnam** se comportent de la même manière, sauf que **_wtmpnam** ne gère pas les chaînes de caractères multioctets.

Si **_DEBUG** et **_CRTDBG_MAP_ALLOC** sont définis, **_tempnam** et **_wtempnam** sont remplacés par des appels à [_tempnam_dbg et _wtempnam_dbg](tempnam-dbg-wtempnam-dbg.md).

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

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_tempnam.c
// compile with: /W3
// This program uses tmpnam to create a unique filename in the
// temporary directory, and _tempname to create a unique filename
// in C:\\tmp.

#include <stdio.h>
#include <stdlib.h>

int main(void)
{
   char * name1 = NULL;
   char * name2 = NULL;
   char * name3 = NULL;

   // Create a temporary filename for the current working directory:
   if ((name1 = tmpnam(NULL)) != NULL) { // C4996
   // Note: tmpnam is deprecated; consider using tmpnam_s instead
      printf("%s is safe to use as a temporary file.\n", name1);
   } else {
      printf("Cannot create a unique filename\n");
   }

   // Create a temporary filename in temporary directory with the
   // prefix "stq". The actual destination directory may vary
   // depending on the state of the TMP environment variable and
   // the global variable P_tmpdir.

   if ((name2 = _tempnam("c:\\tmp", "stq")) != NULL) {
      printf("%s is safe to use as a temporary file.\n", name2);
   } else {
      printf("Cannot create a unique filename\n");
   }

   // When name2 is no longer needed:
   if (name2) {
      free(name2);
   }

   // Unset TMP environment variable, then create a temporary filename in C:\tmp.
   if (_putenv("TMP=") != 0) {
      printf("Could not remove TMP environment variable.\n");
   }

   // With TMP unset, we will use C:\tmp as the temporary directory.
   // Create a temporary filename in C:\tmp with prefix "stq".
   if ((name3 = _tempnam("c:\\tmp", "stq")) != NULL) {
      printf("%s is safe to use as a temporary file.\n", name3);
   }
   else {
      printf("Cannot create a unique filename\n");
   }

   // When name3 is no longer needed:
   if (name3) {
      free(name3);
   }

   return 0;
}
```

```Output
C:\Users\LocalUser\AppData\Local\Temp\sriw.0 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\stq2 is safe to use as a temporary file.
c:\tmp\stq3 is safe to use as a temporary file.
```

## <a name="see-also"></a>Voir aussi

[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[malloc](malloc.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[tmpfile](tmpfile.md)<br/>
[tmpfile_s](tmpfile-s.md)<br/>
