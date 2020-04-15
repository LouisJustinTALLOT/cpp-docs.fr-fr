---
title: memmove_s, wmemmove_s
ms.date: 4/2/2020
api_name:
- wmemmove_s
- memmove_s
- _o_wmemmove_s
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
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wmemmove_s
- memmove_s
helpviewer_keywords:
- wmemmove_s function
- memmove_s function
ms.assetid: a17619e4-1307-4bb0-98c6-77f8c68dab2d
ms.openlocfilehash: baec33046f891f64c04adeccf21f41d3eec7b814
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81333155"
---
# <a name="memmove_s-wmemmove_s"></a>memmove_s, wmemmove_s

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

*nombreOfElements*<br/>
Taille de la mémoire tampon de destination.

*src*<br/>
Objet source.

*count*<br/>
Nombre d’octets **(memmove_s**) ou de caractères (**wmemmove_s**) à copier.

## <a name="return-value"></a>Valeur de retour

Zéro si l’opération a réussi ; code d’erreur en cas de échec.

### <a name="error-conditions"></a>Conditions d'erreur

|*dest*|*nombreOfElements*|*src*|Valeur retournée|Contenu de *dest*|
|------------|------------------------|-----------|------------------|------------------------|
|**Null**|n'importe laquelle|n'importe laquelle|**EINVAL (EN)**|non modifié|
|n'importe laquelle|n'importe laquelle|**Null**|**EINVAL (EN)**|non modifié|
|n'importe laquelle|< *Compter*|n'importe laquelle|**ERANGE**|non modifié|

## <a name="remarks"></a>Notes

Les copies *comptent* les octets des personnages de *src* à *dest*. Si certaines régions de la zone source et le chevauchement de la destination, **memmove_s** s’assure que les octets de source d’origine dans la région qui se chevauchent sont copiés avant d’être écrasés.

Si *le dest* ou si *le src* est un pointeur nul, ou si la chaîne de destination est trop petite, ces fonctions invoquent un gestionnaire de paramètre invalide, tel que décrit dans [la validation de paramètres](../../c-runtime-library/parameter-validation.md) . Si l’exécution est autorisée à se poursuivre, ces fonctions renvoient **EINVAL** et **placent errno** à **EINVAL**.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

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

### <a name="output"></a>Output

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
