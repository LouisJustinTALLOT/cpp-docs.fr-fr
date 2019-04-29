---
title: fwrite
ms.date: 11/04/2016
apiname:
- fwrite
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
- fwrite
helpviewer_keywords:
- streams, writing data to
- fwrite function
ms.assetid: 7afacf3a-72d7-4a50-ba2e-bea1ab9f4124
ms.openlocfilehash: b4d6b9ce4fb66ee545f52946e28e4984d9e4f924
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62287545"
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

**fwrite** retourne le nombre d’intégral éléments réellement écrits, ce qui peut être inférieur à *nombre* si une erreur se produit. De même, en cas d'erreur, il est impossible de déterminer l'indicateur de position de fichier. Si *flux* ou *tampon* est un pointeur null, ou si un nombre impair d’octets à écrire est spécifié en mode Unicode, la fonction appelle le Gestionnaire de paramètre non valide, comme décrit dans [ Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, cette fonction affecte **errno** à **EINVAL** et retourne 0.

## <a name="remarks"></a>Notes

Le **fwrite** fonction écrit jusqu'à *nombre* éléments, de *taille* longueur chaque, à partir de *tampon* à la sortie *flux*. Le pointeur de fichier associé *flux* (le cas échéant) est incrémenté par le nombre d’octets réellement écrits. Si *flux* est ouvert en mode texte, chaque saut de ligne est remplacé par un retour chariot - saut de ligne paire. Le remplacement n'a aucun effet sur la valeur de retour.

Lorsque *flux* est ouvert en mode de traduction Unicode, par exemple, si *flux* est ouverte en appelant **fopen** et à l’aide d’un paramètre de mode qui inclut **ccs = UNICODE**, **ccs = UTF-16LE**, ou **ccs = UTF-8**, ou si le mode est modifié pour un mode de traduction Unicode à l’aide de **_setmode** et un mode paramètre qui inclut **_O_WTEXT**, **_O_U16TEXT**, ou **_O_U8TEXT**—*tampon* est interprété comme un pointeur vers un tableau de **wchar_t** qui contient les données UTF-16. Toute tentative d’écriture d’une quantité impaire d’octets dans ce mode provoque une erreur de validation de paramètre.

Comme cette fonction verrouille le thread appelant, il est thread-safe. Pour obtenir une version sans verrouillage, consultez **_fwrite_nolock**.

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
