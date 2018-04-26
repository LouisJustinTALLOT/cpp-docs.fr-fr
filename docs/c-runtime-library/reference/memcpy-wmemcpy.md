---
title: memcpy, wmemcpy | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- memcpy
- wmemcpy
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
apitype: DLLExport
f1_keywords:
- wmemcpy
- memcpy
dev_langs:
- C++
helpviewer_keywords:
- wmemcpy function
- memcpy function
ms.assetid: 34abb90b-bffb-46dc-a2f3-a5e9940839d6
caps.latest.revision: 21
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a31ada40bfab599b6da41da268bf79792f8ebf20
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2018
---
# <a name="memcpy-wmemcpy"></a>memcpy, wmemcpy

Copie des octets entre les mémoires tampon. Des versions plus sécurisées de ces fonctions sont disponibles ; consultez [memcpy_s, wmemcpy_s](memcpy-s-wmemcpy-s.md).

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

*dest*<br/>
Nouvelle mémoire tampon.

*src*<br/>
Mémoire tampon à partir de laquelle effectuer la copie.

*count*<br/>
Nombre de caractères à copier.

## <a name="return-value"></a>Valeur de retour

La valeur de *dest*.

## <a name="remarks"></a>Notes

**memcpy** copies *nombre* octets à partir de *src* à *dest*; **wmemcpy** copies *nombre* caractères larges (sur deux octets). Si la source et la destination se chevauchent, le comportement de **memcpy** n’est pas défini. Utilisez **memmove** pour gérer les régions qui se chevauche.

> [!IMPORTANT]
> Assurez-vous que la mémoire tampon de destination est d'une taille identique ou supérieure à celle de la mémoire tampon source. Pour plus d’informations, consultez [Solutions contre les dépassements de mémoire tampon](http://msdn.microsoft.com/library/windows/desktop/ms717795).

> [!IMPORTANT]
> Étant donné qu’autant dépassements de mémoire tampon et les failles de sécurité potentielles par conséquent, ont été détectées pour une utilisation incorrecte de **memcpy**, cette fonction est répertoriée parmi les fonctions « bannies » par le cycle de vie de développement de sécurité (SDL).  Vous remarquerez peut-être que certaines classes de bibliothèque VC ++ continuent à utiliser **memcpy**.  En outre, vous pouvez observer que l’optimiseur du compilateur VC ++ émet parfois des appels à **memcpy**.  Le produit Visual C++ est développé conformément au processus SDL, et l'utilisation de cette fonction bannie a donc été évaluée avec attention.  Dans le cas de son utilisation dans des bibliothèques, les appels ont été examinés avec soin pour garantir que les dépassements de mémoire tampon ne seront pas autorisés via ces appels.  Dans le cas le compilateur, certains modèles de code sont parfois reconnus comme étant identiques au modèle de **memcpy**et sont donc remplacés par un appel à la fonction.  Dans ce cas, l’utilisation de **memcpy** n’est pas plus risquée que l’original instructions auraient été ; elles ont simplement été optimisées à un appel à la performance réglées **memcpy** (fonction).  Tout comme l'utilisation de fonctions CRT « sécurisées » ne garantit pas la sécurité (elles rendent simplement plus compliquée une utilisation risquée), l'utilisation de fonctions « bannies » ne signifie pas qu'il y a danger à coup sûr (elles nécessitent seulement un examen plus attentif pour garantir la sécurité).
>
> Étant donné que **memcpy** utilisation par les bibliothèques du compilateur VC ++ a été examinée avec soin, ces appels sont autorisés dans du code qui est conforme à SDL.  **memcpy** appels introduites dans le code source d’applications sont conformes à SDL seulement quand cette utilisation a été vérifiée par des experts en sécurité.

Le **memcpy** et **wmemcpy** fonctions seront déconseillées seulement si la constante **_CRT_SECURE_DEPRECATE_MEMORY** est défini avant l’instruction d’inclusion dans l’ordre de les fonctions déconseillées, comme dans l’exemple ci-dessous :

```C
#define _CRT_SECURE_DEPRECATE_MEMORY
#include <memory.h>
```

ou

```C
#define _CRT_SECURE_DEPRECATE_MEMORY
#include <wchar.h>
```

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**memcpy**|\<memory.h> ou \<string.h>|
|**wmemcpy**|\<wchar.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

Consultez [memmove](memmove-wmemmove.md) pour obtenir un exemple montrant comment utiliser **memcpy**.

## <a name="see-also"></a>Voir aussi

[Manipulation de la mémoire tampon](../../c-runtime-library/buffer-manipulation.md)<br/>
[_memccpy](memccpy.md)<br/>
[memchr, wmemchr](memchr-wmemchr.md)<br/>
[memcmp, wmemcmp](memcmp-wmemcmp.md)<br/>
[memmove, wmemmove](memmove-wmemmove.md)<br/>
[memset, wmemset](memset-wmemset.md)<br/>
[strcpy_s, wcscpy_s, _mbscpy_s](strcpy-s-wcscpy-s-mbscpy-s.md)<br/>
[strncpy_s, _strncpy_s_l, wcsncpy_s, _wcsncpy_s_l, _mbsncpy_s, _mbsncpy_s_l](strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)<br/>
