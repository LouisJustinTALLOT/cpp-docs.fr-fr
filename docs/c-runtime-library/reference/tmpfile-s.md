---
title: tmpfile_s
ms.date: 4/2/2020
api_name:
- tmpfile_s
- _o_tmpfile_s
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
- tmpfile_s
helpviewer_keywords:
- temporary files
- tmpfile_s function
- temporary files, creating
ms.assetid: 50879c69-215e-425a-a2a3-8b5467121eae
ms.openlocfilehash: 48c599887a8a903d52c7dcd46b98046119c9d3ad
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919930"
---
# <a name="tmpfile_s"></a>tmpfile_s

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

### <a name="error-conditions"></a>Conditions d'erreur

|*pFilePtr*|**Valeur de retour**|**Contenu de**  *pFilePtr*|
|----------------|----------------------|---------------------------------|
|**NUL**|**EINVAL**|inchangé|

Si l’erreur de validation de paramètre ci-dessus se produit, le gestionnaire de paramètre non valide est appelé, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, **errno** a la valeur **EINVAL** et la valeur de retour est **EINVAL**.

## <a name="remarks"></a>Notes 

La fonction **tmpfile_s** crée un fichier temporaire et place un pointeur vers ce flux dans l’argument *pFilePtr* . Le fichier temporaire est créé dans le répertoire racine. Pour créer un fichier temporaire dans un répertoire autre que la racine, utilisez [tmpnam_s](tmpnam-s-wtmpnam-s.md) ou [tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md) en association avec [fopen](fopen-wfopen.md).

Si le fichier ne peut pas être ouvert, **tmpfile_s** écrit la **valeur null** dans le paramètre *pFilePtr* . Ce fichier temporaire est automatiquement supprimé lorsque le fichier est fermé, lorsque le programme se termine normalement ou lorsque **_rmtmp** est appelé, en supposant que le répertoire de travail actuel ne change pas. Le fichier temporaire est ouvert dans le mode **w + b** (lecture/écriture binaire).

Une défaillance peut se produire si vous tentez plus de **TMP_MAX_S** (voir stdio. H) appels avec **tmpfile_s**.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**tmpfile_s**|\<stdio.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a> Exemple

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
