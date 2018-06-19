---
title: tmpnam_s, _wtmpnam_s | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- tmpnam_s
- _wtmpnam_s
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
- tmpnam_s
- _wtmpnam_s
- L_tmpnam_s
dev_langs:
- C++
helpviewer_keywords:
- tmpnam_s function
- file names [C++], creating temporary
- _wtmpnam_s function
- L_tmpnam_s constant
- temporary files, creating
- file names [C++], temporary
- wtmpnam_s function
ms.assetid: e70d76dc-49f5-4aee-bfa2-f1baa2bcd29f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d8c6298c7b66c8967a4e5e23a37c3614edcddf3d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32415523"
---
# <a name="tmpnams-wtmpnams"></a>tmpnam_s, _wtmpnam_s

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
|*str*|*sizeInChars*|**Valeur de retour**|**Contenu de***str* |
|**NULL**|any|**EINVAL**|non modifié|
|Pas **NULL** (pointe vers une mémoire valide)|trop court|**ERANGE**|non modifié|

Si *str* est **NULL**, le Gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions définissent **errno** à **EINVAL** et retourner **EINVAL**.

## <a name="remarks"></a>Notes

Chacune de ces fonctions retourne le nom d’un fichier qui n’existe pas actuellement. **tmpnam_s généraient** retourne un nom unique dans le répertoire de travail actuel. Notez que lorsqu’un nom de fichier est précédé d’une barre oblique inverse et d’aucune information de chemin, comme \fname21, cela indique que le nom est valide pour le répertoire de travail actif.

Pour **tmpnam_s généraient**, vous pouvez stocker ce nom de fichier généré dans *str*. La longueur maximale de la chaîne retournée par **tmpnam_s généraient** est **L_tmpnam_s**, défini dans STDIO. H. Si *str* est **NULL**, puis **tmpnam_s généraient** laisse le résultat dans un tampon statique interne. Par conséquent, tous les appels suivants détruisent cette valeur. Le nom généré par **tmpnam_s généraient** se compose d’un nom de fichier généré par le programme et, après le premier appel à **tmpnam_s généraient**, une extension de fichier de numéros séquentiels dans base 32 (.1-.1vvvvvu, lorsque **TMP _MAX_S** dans STDIO. H est **INT_MAX**).

**tmpnam_s généraient** handles arguments de chaîne de caractères multioctets selon le cas, reconnaissant les séquences de caractères multioctets en fonction de la page de codes OEM obtient automatiquement à partir du système d’exploitation. **_wtmpnam_s** est une version à caractères larges de **tmpnam_s généraient**; la valeur des arguments et de retour de **_wtmpnam_s** sont des chaînes à caractères larges. **_wtmpnam_s** et **tmpnam_s généraient** se comportent de façon identique, sauf que **_wtmpnam_s** ne gère pas les chaînes de caractères multioctets.

En C++, l’utilisation de ces fonctions est simplifiée par les surcharges de modèle ; celles-ci peuvent déduire automatiquement la longueur de la mémoire tampon, ce qui évite d’avoir à spécifier un argument de taille. Pour plus d'informations, consultez [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mappages de routines de texte générique

|Routine TCHAR.H|_UNICODE et _MBCS non définis|_MBCS défini|_UNICODE défini|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ttmpnam_s**|**tmpnam_s**|**tmpnam_s**|**_wtmpnam_s**|

## <a name="requirements"></a>Spécifications

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

## <a name="see-also"></a>Voir aussi

[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[malloc](malloc.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[tmpfile_s](tmpfile-s.md)<br/>
