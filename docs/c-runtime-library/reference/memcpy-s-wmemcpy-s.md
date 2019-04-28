---
title: memcpy_s, wmemcpy_s
ms.date: 11/04/2016
apiname:
- memcpy_s
- wmemcpy_s
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
- wmemcpy_s
- memcpy_s
helpviewer_keywords:
- memcpy_s function
- wmemcpy_s function
ms.assetid: 5504e20a-83d9-4063-91fc-3f55f7dabe99
ms.openlocfilehash: 802d75307096e649df15b1864b99699fba92a3a1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62285329"
---
# <a name="memcpys-wmemcpys"></a>memcpy_s, wmemcpy_s

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

## <a name="return-value"></a>Valeur de retour

Zéro si l'opération a réussi ; code d'erreur en cas de échec.

### <a name="error-conditions"></a>Conditions d’erreur

|*dest*|*destSize*|*src*|*count*|Valeur de retour|Contenu de *dest*|
|------------|----------------|-----------|---|------------------|------------------------|
|any|any|any|0|0|Non modifiée|
|**NULL**|any|any|Différent de zéro|**EINVAL**|Non modifiée|
|any|any|**NULL**|Différent de zéro|**EINVAL**|*dest* est remis à zéro|
|any|< *count*|any|Différent de zéro|**ERANGE**|*dest* est remis à zéro|

## <a name="remarks"></a>Notes

**memcpy_s** copies *nombre* octets à partir de *src* à *dest*; **wmemcpy_s** copies *nombre* caractères larges (sur deux octets). Si la source et la destination se chevauchent, le comportement de **memcpy_s** n’est pas défini. Utilisez **memmove_s** pour gérer les régions qui se chevauchent.

Ces fonctions valident leurs paramètres. Si *nombre* est différente de zéro et *dest* ou *src* est un pointeur null, ou *destSize* est inférieure à *nombre*, ces fonctions appellent le Gestionnaire de paramètre non valide, comme décrit dans [Validation de paramètre](../../c-runtime-library/parameter-validation.md). Si l’exécution est autorisée à se poursuivre, ces fonctions retournent **EINVAL** ou **ERANGE** et définissez **errno** à la valeur de retour.

## <a name="requirements"></a>Configuration requise

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
