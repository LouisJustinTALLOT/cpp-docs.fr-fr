---
title: _fread_nolock_s2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
apiname:
- _fread_nolock_s
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
- _fread_nolock_s
- stdio/_fread_nolock_s
dev_langs:
- C++
ms.assetid: 5badb9ab-11df-4e17-8162-30bda2a4572e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: db0cd82d251595be586b46fb66a0f0262484e2f8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="freadnolocks"></a>_fread_nolock_s

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

*BufferSize*<br/>
Taille de la mémoire tampon de destination en octets.

*elementSize*<br/>
Taille de l’élément à lire en octets.

*valeur d’elementCount*<br/>
Nombre maximal d’éléments à lire.

*Flux de données*<br/>
Pointeur désignant la structure **FILE**.

## <a name="return-value"></a>Valeur de retour

Consultez [fread_s](fread-s.md).

## <a name="remarks"></a>Notes

Cette fonction est une version sans verrouillage de **fread_s**. Il est identique à **fread_s** , sauf qu’il n’est pas protégé contre les interférences par d’autres threads. Elle peut être plus rapide, car elle n’entraîne pas la charge liée au verrouillage des autres threads. Utilisez cette fonction uniquement dans les contextes thread-safe, par exemple avec les applications monothread ou lorsque la portée appelante gère déjà l’isolation des threads.

## <a name="requirements"></a>Spécifications

|Fonction|En-tête requis|
|--------------|---------------------|
|**_fread_nolock_s**|C : \<stdio.h> ; C++ : \<cstdio> ou \<stdio.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Voir aussi

[E/S de flux](../../c-runtime-library/stream-i-o.md)<br/>
[fwrite](fwrite.md)<br/>
[_read](read.md)<br/>
