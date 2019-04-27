---
title: tmpfile_s
ms.date: 11/04/2016
apiname:
- tmpfile_s
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
- tmpfile_s
helpviewer_keywords:
- temporary files
- tmpfile_s function
- temporary files, creating
ms.assetid: 50879c69-215e-425a-a2a3-8b5467121eae
ms.openlocfilehash: 341e1c8ed6dd20ec7e6a3d71999fb365e45e614a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62155574"
---
# <a name="tmpfiles"></a>tmpfile_s

Crée un fichier temporaire. Il s’agit d’une version de [tmpfile](tmpfile.md) assortie des améliorations de sécurité décrites dans [Fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t tmpfile_s(
   FILE** pFilePtr
);
```

### <a name="parameters"></a>Paramètres

*pFilePtr*<br/>
Adresse d’un pointeur pour stocker l’adresse du pointeur généré désignant un flux.

## <a name="return-value"></a>Valeur de retour

Retourne 0 si l’opération aboutit et un code d’erreur en cas d’échec.

### <a name="error-conditions"></a>Conditions d’erreur

|*pFilePtr*|**Valeur de retour**|**Contents of**  *pFilePtr*|
|----------------|----------------------|---------------------------------|
|**NULL**|**EINVAL**|inchangé|

Si l’erreur de validation de paramètre ci-dessus se produit, le gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **errno** a la valeur **EINVAL** et la valeur de retour est **EINVAL**.

## <a name="remarks"></a>Notes

Le **tmpfile_s** fonction crée un fichier temporaire et place un pointeur vers ce flux de données dans le *pFilePtr* argument. Le fichier temporaire est créé dans le répertoire racine. Pour créer un fichier temporaire dans un répertoire autre que la racine, utilisez [tmpnam_s](tmpnam-s-wtmpnam-s.md) ou [tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md) en association avec [fopen](fopen-wfopen.md).

Si le fichier ne peut pas être ouvert, **tmpfile_s** écrit **NULL** à la *pFilePtr* paramètre. Ce fichier temporaire est automatiquement supprimé quand le fichier est fermé lorsque le programme se termine normalement ou lorsque **_rmtmp** est appelée, en supposant que le répertoire de travail actif ne change pas. Le fichier temporaire est ouvert dans **w + b** mode (lecture/écriture binaire).

Échec peut se produire si vous essayez de plus de **TMP_MAX_S** (voir STDIO. (H) appels avec **tmpfile_s**.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**tmpfile_s**|\<stdio.h>|

Pour plus d’informations sur la compatibilité, voir consultez [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

> [!NOTE]
> Cet exemple peut nécessiter des privilèges d’administrateur pour s’exécuter sur Windows.

```C
// crt_tmpfile_s.c
// This program uses tmpfile_s to create a
// temporary file, then deletes this file with _rmtmp.
//

#include <stdio.h>

int main( void )
{
   FILE *stream;
   char tempstring[] = "String to be written";
   int  i;
   errno_t err;

   // Create temporary files.
   for( i = 1; i <= 3; i++ )
   {
      err = tmpfile_s(&stream);
      if( err )
         perror( "Could not open new temporary file\n" );
      else
         printf( "Temporary file %d was created\n", i );
   }

   // Remove temporary files.
   printf( "%d temporary files deleted\n", _rmtmp() );
}
```

```Output
Temporary file 1 was created
Temporary file 2 was created
Temporary file 3 was created
3 temporary files deleted
```

## <a name="see-also"></a>Voir aussi

[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[_rmtmp](rmtmp.md)<br/>
[_tempnam, _wtempnam, tmpnam, _wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)<br/>
