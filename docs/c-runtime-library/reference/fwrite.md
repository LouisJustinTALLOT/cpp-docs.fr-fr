---
title: fwrite
ms.date: 4/2/2020
api_name:
- fwrite
- _o_fwrite
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: a5bd6da3c8d16189f7ff0db744901e03513acc21
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345392"
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

*Taille*<br/>
Taille de l'élément, en octets.

*count*<br/>
Nombre maximal d'éléments à écrire.

*Flux*<br/>
Pointeur désignant la structure **FILE**.

## <a name="return-value"></a>Valeur de retour

**fwrite** renvoie le nombre d’éléments complets réellement écrits, qui peuvent être moins que *compter* si une erreur se produit. De même, en cas d'erreur, il est impossible de déterminer l'indicateur de position de fichier. Si le *flux* ou le *tampon* est un pointeur nul, ou si un nombre impair d’octets à écrire est spécifié en mode Unicode, la fonction invoque le gestionnaire de paramètres invalides, tel que décrit dans [la validation de paramètres](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, cette fonction définit **errno** à **EINVAL** et renvoie 0.

## <a name="remarks"></a>Notes

La fonction **fwrite** écrit jusqu’à *compter* les éléments, de longueur de *taille* chacun, de *tampon* au *flux*de sortie . Le pointeur de fichier associé au *flux* (s’il y en a un) est incrémenté par le nombre d’octets réellement écrits. Si *le flux* est ouvert en mode texte, chaque flux de ligne est remplacé par une paire d’alimentation de retour de voiture. Le remplacement n'a aucun effet sur la valeur de retour.

Lorsque *le flux* est ouvert en mode de traduction Unicode, par exemple, si le *flux* est ouvert en appelant **fopen** et en utilisant un paramètre de mode qui inclut **ccs-UNICODE**, **ccs-UTF-16LE**, ou **ccs-UTF-8**, ou si le mode est changé en mode de traduction Unicode en utilisant **_setmode** et un paramètre de mode qui comprend **_O_WTEXT**, **_O_U16TEXT**, ou **_O_U8TEXT**-*tampon* est interprété comme un pointeur à un tableau de **wchar_t** qui contient des données UTF-16. Toute tentative d'écriture d'une quantité impaire d'octets dans ce mode provoque une erreur de validation de paramètre.

Comme cette fonction verrouille le thread appelant, il est thread-safe. Pour une version non-locking, voir **_fwrite_nolock**.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Fonction|En-tête requis|
|--------------|---------------------|
|**fwrite**|\<stdio.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Consultez l’exemple relatif à [fread](fread.md).

## <a name="see-also"></a>Voir aussi

[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[_setmode](setmode.md)<br/>
[fread](fread.md)<br/>
[_fwrite_nolock](fwrite-nolock.md)<br/>
[_write](write.md)<br/>
