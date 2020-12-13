---
description: 'En savoir plus sur les éléments suivants : __writefsbyte, __writefsdword, __writefsqword, __writefsword'
title: __writefsbyte, __writefsdword, __writefsqword, __writefsword
ms.date: 09/02/2019
f1_keywords:
- __writefsword
- __writefsbyte
- __writefsqword
- __writefsdword
helpviewer_keywords:
- writefsbyte intrinsic
- __writefsword intrinsic
- writefsqword intrinsic
- writefsdword intrinsic
- __writefsdword intrinsic
- __writefsqword intrinsic
- __writefsbyte intrinsic
- writefsword intrinsic
ms.assetid: 23ac6e8e-bc91-4e90-a4c6-da02993637ad
ms.openlocfilehash: cde85cd7fea5b65ced127da96033ecc5b1f4f058
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97136056"
---
# <a name="__writefsbyte-__writefsdword-__writefsqword-__writefsword"></a>__writefsbyte, __writefsdword, __writefsqword, __writefsword

**Spécifique à Microsoft**

Écrire de la mémoire dans un emplacement spécifié par un décalage par rapport au début du segment FS.

## <a name="syntax"></a>Syntaxe

```C
void __writefsbyte(
   unsigned long Offset,
   unsigned char Data
);
void __writefsword(
   unsigned long Offset,
   unsigned short Data
);
void __writefsdword(
   unsigned long Offset,
   unsigned long Data
);
void __writefsqword(
   unsigned long Offset,
   unsigned __int64 Data
);
```

### <a name="parameters"></a>Paramètres

*Décalage*\
dans Offset à partir du début des FS à écrire.

*Données*\
dans Valeur à écrire.

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|
|---------------|------------------|
|`__writefsbyte`|x86|
|`__writefsword`|x86|
|`__writefsdword`|x86|
|`__writefsqword`|x86|

**Fichier d’en-tête** \<intrin.h>

## <a name="remarks"></a>Notes

Ces routines sont disponibles uniquement comme intrinsèques.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[__readfsbyte, \_ _readfsdword, \_ _readfsqword, \_ _readfsword](../intrinsics/readfsbyte-readfsdword-readfsqword-readfsword.md)\
[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
