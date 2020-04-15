---
title: _fread_nolock_s2
ms.date: 4/2/2020
api_name:
- _fread_nolock_s
- _o__fread_nolock_s
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
- _fread_nolock_s
- stdio/_fread_nolock_s
ms.assetid: 5badb9ab-11df-4e17-8162-30bda2a4572e
ms.openlocfilehash: 3fb34a75a0281058a1d70ce41e1ce33b4b1bbb59
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346132"
---
# <a name="_fread_nolock_s"></a>_fread_nolock_s

Lit des données à partir d’un flux de données, sans verrouiller d’autres threads. Cette version de [fread_nolock](fread-nolock.md) est assortie des améliorations de sécurité décrites dans [Fonctionnalités de sécurité dans le CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
size_t _fread_nolock_s(
   void *buffer,
   size_t bufferSize,
   size_t elementSize,
   size_t elementCount,
   FILE *stream
);
```

### <a name="parameters"></a>Paramètres

*buffer*<br/>
Emplacement de stockage des données.

*tamponSize*<br/>
Taille de la mémoire tampon de destination en octets.

*élémentsSize*<br/>
Taille de l’élément à lire en octets.

*élémentCompte*<br/>
Nombre maximal d’éléments à lire.

*Flux*<br/>
Pointeur désignant la structure **FILE**.

## <a name="return-value"></a>Valeur de retour

Consultez [fread_s](fread-s.md).

## <a name="remarks"></a>Notes

Cette fonction est une version non-locking de **fread_s**. Il est identique à **fread_s** sauf qu’il n’est pas protégé contre les interférences par d’autres threads. Elle peut être plus rapide, car elle n’entraîne pas la charge liée au verrouillage des autres threads. Utilisez cette fonction uniquement dans les contextes thread-safe, par exemple avec les applications monothread ou lorsque la portée appelante gère déjà l’isolation des threads.

Par défaut, l’état global de cette fonction est étendue à l’application. Pour changer cela, voir [Global State dans le CRT](../global-state.md).

## <a name="requirements"></a>Spécifications

|Fonction|En-tête requis|
|--------------|---------------------|
|**_fread_nolock_s**|C : \<stdio.h> ; C++ : \<cstdio> ou \<stdio.h>|

Pour plus d’informations sur la compatibilité, consultez [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[fwrite](fwrite.md)<br/>
[_read](read.md)<br/>
