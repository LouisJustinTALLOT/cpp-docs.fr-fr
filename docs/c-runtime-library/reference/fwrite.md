---
title: fwrite
ms.date: 11/04/2016
api_name:
- fwrite
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
- fwrite
helpviewer_keywords:
- streams, writing data to
- fwrite function
ms.assetid: 7afacf3a-72d7-4a50-ba2e-bea1ab9f4124
ms.openlocfilehash: 8149e0f2cbc84c2c28093d86fecd5ff2a9db7aba
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956198"
---
# <a name="fwrite"></a>fwrite

Écrit des données dans un flux.

## <a name="syntax"></a>Syntaxe

```C
size_t fwrite(
   const void *buffer,
   size_t size,
   size_t count,
   FILE *stream
);
```

### <a name="parameters"></a>Paramètres

*buffer*<br/>
Pointeur vers des données à écrire.

*size*<br/>
Taille de l'élément, en octets.

*count*<br/>
Nombre maximal d'éléments à écrire.

*stream*<br/>
Pointeur désignant la structure **FILE**.

## <a name="return-value"></a>Valeur de retour

**fwrite** retourne le nombre d’éléments complets réellement écrits, qui peut être inférieur à *Count* si une erreur se produit. De même, en cas d'erreur, il est impossible de déterminer l'indicateur de position de fichier. Si *Stream* ou *buffer* est un pointeur null, ou si un nombre impair d’octets à écrire est spécifié en mode Unicode, la fonction appelle le gestionnaire de paramètre non valide, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, cette fonction affecte à **errno** la valeur **EINVAL** et retourne 0.

## <a name="remarks"></a>Notes

La **fonction fwrite** écrit dans le *flux*de sortie jusqu’au *nombre* d’éléments, de longueur de *taille* chacun, de la *mémoire tampon* . Le pointeur de fichier associé au *flux* (le cas échéant) est incrémenté du nombre d’octets réellement écrits. Si le *flux* est ouvert en mode texte, chaque saut de ligne est remplacé par une paire retour chariot-saut de ligne. Le remplacement n'a aucun effet sur la valeur de retour.

Lorsque le *flux* est ouvert en mode de traduction Unicode, par exemple, si le *flux* est ouvert en appelant **fopen** et en utilisant un paramètre de mode qui comprend **CCS = Unicode**, **CCS = UTF-16LE**ou **CCS = UTF-8**, ou si le mode est changé en mode de traduction Unicode à l’aide de **_setmode** et d’un paramètre de mode qui inclut **_O_WTEXT**, **_O_U16TEXT**ou **_O_U8TEXT**: la*mémoire tampon* est interprétée comme un pointeur vers un tableau de **wchar_t** qui contient Données UTF-16. Toute tentative d’écriture d’une quantité impaire d’octets dans ce mode provoque une erreur de validation de paramètre.

Comme cette fonction verrouille le thread appelant, il est thread-safe. Pour une version sans verrouillage, consultez **_fwrite_nolock**.

## <a name="requirements"></a>Configuration requise

|Fonction|En-tête requis|
|--------------|---------------------|
|**fwrite**|\<stdio.h>|

Pour plus d’informations sur la compatibilité, voir consultez [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Consultez l’exemple relatif à [fread](fread.md).

## <a name="see-also"></a>Voir aussi

[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[_setmode](setmode.md)<br/>
[fread](fread.md)<br/>
[_fwrite_nolock](fwrite-nolock.md)<br/>
[_write](write.md)<br/>
