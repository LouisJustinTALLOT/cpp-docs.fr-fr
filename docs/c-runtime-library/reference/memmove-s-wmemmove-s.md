---
title: memmove_s, wmemmove_s
ms.date: 11/04/2016
apiname:
- wmemmove_s
- memmove_s
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
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- wmemmove_s
- memmove_s
helpviewer_keywords:
- wmemmove_s function
- memmove_s function
ms.assetid: a17619e4-1307-4bb0-98c6-77f8c68dab2d
ms.openlocfilehash: 28d879a205790d1f132caca1022d0740e317c342
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62285144"
---
# <a name="memmoves-wmemmoves"></a>memmove_s, wmemmove_s

Déplace une mémoire tampon vers une autre Ces versions de [memmove, wmemmove](memmove-wmemmove.md) intègrent les améliorations de sécurité décrites dans [Fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t memmove_s(
   void *dest,
   size_t numberOfElements,
   const void *src,
   size_t count
);
errno_t wmemmove_s(
   wchar_t *dest,
   size_t numberOfElements,
   const wchar_t *src,
   size_t count
);
```

### <a name="parameters"></a>Paramètres

*dest*<br/>
Objet de destination.

*numberOfElements*<br/>
Taille de la mémoire tampon de destination.

*src*<br/>
Objet source.

*count*<br/>
Nombre d’octets (**memmove_s**) ou de caractères (**wmemmove_s**) à copier.

## <a name="return-value"></a>Valeur de retour

Zéro si l’opération a réussi ; code d’erreur en cas de échec.

### <a name="error-conditions"></a>Conditions d’erreur

|*dest*|*numberOfElements*|*src*|Valeur de retour|Contenu de *dest*|
|------------|------------------------|-----------|------------------|------------------------|
|**NULL**|any|any|**EINVAL**|non modifié|
|any|any|**NULL**|**EINVAL**|non modifié|
|any|< *count*|any|**ERANGE**|non modifié|

## <a name="remarks"></a>Notes

Copies *nombre* octets de caractères à partir de *src* à *dest*. Si certaines régions de la zone source et la destination se chevauchent, **memmove_s** garantit que les octets source d’origine dans la région de chevauchement sont copiés avant d’être remplacés.

Si *dest* ou si *src* est un pointeur null, ou si la chaîne de destination est trop petite, ces fonctions appellent un gestionnaire de paramètre non valide, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md) . Si l’exécution est autorisée à se poursuivre, ces fonctions retournent **EINVAL** et définissez **errno** à **EINVAL**.

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**memmove_s**|\<string.h>|
|**wmemmove_s**|\<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_memmove_s.c
//
// The program demonstrates the
// memmove_s function which works as expected
// for moving overlapping regions.

#include <stdio.h>
#include <string.h>

int main()
{
   char str[] = "0123456789";

   printf("Before: %s\n", str);

   // Move six bytes from the start of the string
   // to a new position shifted by one byte. To protect against
   // buffer overrun, the secure version of memmove requires the
   // the length of the destination string to be specified.

   memmove_s((str + 1), strnlen(str + 1, 10), str, 6);

   printf_s(" After: %s\n", str);
}
```

### <a name="output"></a>Sortie

```Output
Before: 0123456789
After: 0012345789
```

## <a name="see-also"></a>Voir aussi

[Manipulation de la mémoire tampon](../../c-runtime-library/buffer-manipulation.md)<br/>
[_memccpy](memccpy.md)<br/>
[memcpy, wmemcpy](memcpy-wmemcpy.md)<br/>
[strcpy_s, wcscpy_s, _mbscpy_s](strcpy-s-wcscpy-s-mbscpy-s.md)<br/>
[strcpy, wcscpy, _mbscpy](strcpy-wcscpy-mbscpy.md)<br/>
[strncpy_s, _strncpy_s_l, wcsncpy_s, _wcsncpy_s_l, _mbsncpy_s, _mbsncpy_s_l](strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)<br/>
[strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)<br/>
