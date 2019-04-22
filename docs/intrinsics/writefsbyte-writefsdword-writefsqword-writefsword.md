---
title: __writefsbyte, __writefsdword, __writefsqword, __writefsword
ms.date: 11/04/2016
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
ms.openlocfilehash: 6461ef730760298e3159e4ac70dbbdf7bd827092
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59025773"
---
# <a name="writefsbyte-writefsdword-writefsqword-writefsword"></a>__writefsbyte, __writefsdword, __writefsqword, __writefsword

**Section spécifique à Microsoft**

Écrire la mémoire à un emplacement spécifié par un décalage par rapport au début du segment FS.

## <a name="syntax"></a>Syntaxe

```
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

#### <a name="parameters"></a>Paramètres

*Offset*<br/>
[in] Le décalage entre le début du FS à écrire dans.

*Données*<br/>
[in] Valeur à écrire.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__writefsbyte`|x86|
|`__writefsword`|x86|
|`__writefsdword`|x86|
|`__writefsqword`|x86|

**Fichier d’en-tête** \<intrin.h >

## <a name="remarks"></a>Notes

Ces routines sont disponibles uniquement sous forme de fonctions intrinsèques.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[__readfsbyte, \__readfsdword, \__readfsqword, \__readfsword](../intrinsics/readfsbyte-readfsdword-readfsqword-readfsword.md)<br/>
[compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)