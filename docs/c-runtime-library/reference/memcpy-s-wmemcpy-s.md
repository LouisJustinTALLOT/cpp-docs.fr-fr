---
description: 'En savoir plus sur : memcpy_s, wmemcpy_s'
title: memcpy_s, wmemcpy_s
ms.date: 4/2/2020
api_name:
- memcpy_s
- wmemcpy_s
- _o_memcpy_s
- _o_wmemcpy_s
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wmemcpy_s
- memcpy_s
helpviewer_keywords:
- memcpy_s function
- wmemcpy_s function
ms.assetid: 5504e20a-83d9-4063-91fc-3f55f7dabe99
ms.openlocfilehash: 77c71e594d9a3853438987e85e43700d1f467718
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97304738"
---
# <a name="memcpy_s-wmemcpy_s"></a>memcpy_s, wmemcpy_s

Copie des octets entre les mémoires tampon. Ces versions de [memcpy, wmemcpy](memcpy-wmemcpy.md) intègrent les améliorations de sécurité décrites dans [Fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t memcpy_s(
   void *dest,
   size_t destSize,
   const void *src,
   size_t count
);
errno_t wmemcpy_s(
   wchar_t *dest,
   size_t destSize,
   const wchar_t *src,
   size_t count
);
```

### <a name="parameters"></a>Paramètres

*dest*<br/>
Nouvelle mémoire tampon.

*destSize*<br/>
Taille de la mémoire tampon de destination, en octets dans le cas de memcpy_s et en caractères larges (wchar_t) dans le cas de wmemcpy_s.

*src*<br/>
Mémoire tampon à partir de laquelle effectuer la copie.

*count*<br/>
Nombre de caractères à copier.

## <a name="return-value"></a>Valeur renvoyée

Zéro si l'opération a réussi ; code d'erreur en cas de échec.

### <a name="error-conditions"></a>Conditions d'erreur

|*dest*|*destSize*|*src*|*count*|Valeur retournée|Contenu de *dest*|
|------------|----------------|-----------|---|------------------|------------------------|
|n'importe laquelle|n'importe laquelle|n'importe laquelle|0|0|Non modifiée|
|**NULL**|n'importe laquelle|n'importe laquelle|Différent de zéro|**EINVAL**|Non modifiée|
|n'importe laquelle|n'importe laquelle|**NULL**|Différent de zéro|**EINVAL**|*dest* est mis à zéro|
|n'importe laquelle|< *saut*|n'importe laquelle|Différent de zéro|**ERANGE**|*dest* est mis à zéro|

## <a name="remarks"></a>Notes

**memcpy_s** copie le *nombre* d’octets de *src* vers *dest*; **wmemcpy_s** copie le *nombre* de caractères larges (deux octets). Si la source et la destination se chevauchent, le comportement de **memcpy_s** n’est pas défini. Utilisez **memmove_s** pour gérer les régions qui se chevauchent.

Ces fonctions valident leurs paramètres. Si *Count* n’est pas égal à zéro et que *dest* ou *src* est un pointeur null, ou que *destSize* est inférieur à *Count*, ces fonctions appellent le gestionnaire de paramètres non valides, comme décrit dans [validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions retournent **EINVAL** ou **ERANGE** et attribuent à **errno** la valeur de retour.

Par défaut, l’état global de cette fonction est limité à l’application. Pour modifier cette valeur, consultez [état global dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**memcpy_s**|\<memory.h> ou \<string.h>|
|**wmemcpy_s**|\<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```C
// crt_memcpy_s.c
// Copy memory in a more secure way.

#include <memory.h>
#include <stdio.h>

int main()
{
   int a1[10], a2[100], i;
   errno_t err;

   // Populate a2 with squares of integers
   for (i = 0; i < 100; i++)
   {
      a2[i] = i*i;
   }

   // Tell memcpy_s to copy 10 ints (40 bytes), giving
   // the size of the a1 array (also 40 bytes).
   err = memcpy_s(a1, sizeof(a1), a2, 10 * sizeof (int) );
   if (err)
   {
      printf("Error executing memcpy_s.\n");
   }
   else
   {
     for (i = 0; i < 10; i++)
       printf("%d ", a1[i]);
   }
   printf("\n");
}
```

```Output
0 1 4 9 16 25 36 49 64 81
```

## <a name="see-also"></a>Voir aussi

[Manipulation de la mémoire tampon](../../c-runtime-library/buffer-manipulation.md)<br/>
[_memccpy](memccpy.md)<br/>
[memchr, wmemchr](memchr-wmemchr.md)<br/>
[memcmp, wmemcmp](memcmp-wmemcmp.md)<br/>
[memmove, wmemmove](memmove-wmemmove.md)<br/>
[memset, wmemset](memset-wmemset.md)<br/>
[strcpy, wcscpy, _mbscpy](strcpy-wcscpy-mbscpy.md)<br/>
[strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)<br/>
[strncpy_s, _strncpy_s_l, wcsncpy_s, _wcsncpy_s_l, _mbsncpy_s, _mbsncpy_s_l](strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)<br/>
