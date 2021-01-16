---
description: 'En savoir plus sur les éléments suivants : memcpy, wmemcpy'
title: memcpy, wmemcpy
ms.date: 1/14/2021
api_name:
- memcpy
- wmemcpy
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
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wmemcpy
- memcpy
helpviewer_keywords:
- wmemcpy function
- memcpy function
ms.assetid: 34abb90b-bffb-46dc-a2f3-a5e9940839d6
ms.openlocfilehash: 49b08877f63bf0d331dcc40e2885b375fe6d1ee7
ms.sourcegitcommit: 1cd8f8a75fd036ffa57bc70f3ca869042d8019d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/15/2021
ms.locfileid: "98243136"
---
# <a name="memcpy-wmemcpy"></a>`memcpy`, `wmemcpy`

Copie des octets entre les mémoires tampon. Des versions plus sécurisées de ces fonctions sont disponibles ; consultez [ `memcpy_s` , `wmemcpy_s` ](memcpy-s-wmemcpy-s.md).

## <a name="syntax"></a>Syntaxe

```C
void *memcpy(
   void *dest,
   const void *src,
   size_t count
);
wchar_t *wmemcpy(
   wchar_t *dest,
   const wchar_t *src,
   size_t count
);
```

### <a name="parameters"></a>Paramètres

*`dest`*\
Nouvelle mémoire tampon.

*`src`*\
Mémoire tampon à partir de laquelle effectuer la copie.

*`count`*\
Nombre de caractères à copier.

## <a name="return-value"></a>Valeur renvoyée

Valeur de *`dest`* .

## <a name="remarks"></a>Remarques

**`memcpy`** copie les *`count`* octets de *`src`* vers *`dest`* ; copie les **`wmemcpy`** *`count`* caractères larges (deux octets). Si la source et la destination se chevauchent, le comportement de **`memcpy`** n’est pas défini. Utilisez **`memmove`** pour gérer les régions qui se chevauchent.

> [!IMPORTANT]
> Assurez-vous que la mémoire tampon de destination est d'une taille identique ou supérieure à celle de la mémoire tampon source. Pour plus d’informations, consultez [Solutions contre les dépassements de mémoire tampon](/windows/win32/SecBP/avoiding-buffer-overruns).

> [!IMPORTANT]
> Étant donné qu’un grand nombre de dépassements de mémoire tampon, et donc des failles de sécurité potentielles, ont été suivis pour une utilisation incorrecte de **`memcpy`** , cette fonction est indiquée parmi les fonctions « interdites » par le cycle de vie de développement de la sécurité (SDL).  Vous pouvez remarquer que certaines classes de bibliothèque VC + + continuent à utiliser **`memcpy`** .  En outre, vous pouvez remarquer que l’optimiseur du compilateur VC + + émet parfois des appels à **`memcpy`** .  Le produit Visual C++ est développé conformément au processus SDL, et l'utilisation de cette fonction bannie a donc été évaluée avec attention.  Dans le cas de son utilisation dans des bibliothèques, les appels ont été examinés avec soin pour garantir que les dépassements de mémoire tampon ne seront pas autorisés via ces appels.  Dans le cas du compilateur, certains modèles de code sont parfois reconnus comme étant identiques au modèle de **`memcpy`** et sont donc remplacés par un appel à la fonction.  Dans ce cas, l’utilisation de **`memcpy`** n’est pas plus risquée que les instructions d’origine auraient été. elles ont simplement été optimisées pour un appel à la fonction avec optimisation des performances **`memcpy`** .  Tout comme l’utilisation de fonctions CRT « sécurisées » ne garantit pas la sécurité (elles compliquent simplement la protection), l’utilisation de fonctions « interdites » ne garantit pas le danger (elles nécessitent simplement un examen plus approfondi pour garantir la sécurité).
>
> Étant donné que l' **`memcpy`** utilisation par le compilateur et les bibliothèques VC + + a été examinée avec soin, ces appels sont autorisés dans du code qui est autrement conforme à SDL.  **`memcpy`** les appels introduits dans le code source de l’application sont uniquement conformes à SDL quand cette utilisation a été examinée par des experts en sécurité.

Les **`memcpy`** **`wmemcpy`** fonctions et seront dépréciées uniquement si la constante **`_CRT_SECURE_DEPRECATE_MEMORY`** est définie avant l’instruction d’inclusion pour que les fonctions soient dépréciées, comme dans l’exemple ci-dessous :

```C
#define _CRT_SECURE_DEPRECATE_MEMORY
#include <memory.h>
```

ou

```C
#define _CRT_SECURE_DEPRECATE_MEMORY
#include <wchar.h>
```

## <a name="requirements"></a>Configuration requise

|Routine|En-tête requis|
|-------------|---------------------|
|**`memcpy`**|`<memory.h>` ou `<string.h>`|
|**`wmemcpy`**|`<wchar.h>`|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

[`memmove`](memmove-wmemmove.md)Pour obtenir un exemple d’utilisation de **`memcpy`** , consultez.

## <a name="see-also"></a>Voir aussi

[Manipulation de la mémoire tampon](../../c-runtime-library/buffer-manipulation.md)\
[`_memccpy`](memccpy.md)\
[`memchr`, `wmemchr`](memchr-wmemchr.md)\
[`memcmp`, `wmemcmp`](memcmp-wmemcmp.md)\
[`memmove`, `wmemmove`](memmove-wmemmove.md)\
[`memset`, `wmemset`](memset-wmemset.md)\
[`strcpy_s`, `wcscpy_s`, `_mbscpy_s`](strcpy-s-wcscpy-s-mbscpy-s.md)\
[`strncpy_s`, `_strncpy_s_l`, `wcsncpy_s`, `_wcsncpy_s_l`, `_mbsncpy_s`, `_mbsncpy_s_l`](strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)\
