---
title: __readfsbyte, __readfsdword, __readfsqword, __readfsword
ms.date: 09/02/2019
f1_keywords:
- __readfsword
- __readfsdword
- __readfsbyte
- __readfsqword
helpviewer_keywords:
- __readfsword intrinsic
- readfsword intrinsic
- __readfsdword intrinsic
- readfsbyte intrinsic
- __readfsbyte intrinsic
- readfsdword intrinsic
- readfsqword intrinsic
- __readfsqword intrinsic
ms.assetid: f6ee7203-4179-402c-a464-0746c84ce6ac
ms.openlocfilehash: 30040b33fe8c686bc0cda585c525ae2926cdf314
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222362"
---
# <a name="__readfsbyte-__readfsdword-__readfsqword-__readfsword"></a>__readfsbyte, __readfsdword, __readfsqword, __readfsword

**Section spécifique à Microsoft**

Lit la mémoire à partir d’un emplacement spécifié par un décalage par rapport au début du segment FS.

## <a name="syntax"></a>Syntaxe

```C
unsigned char __readfsbyte(
   unsigned long Offset
);
unsigned short __readfsword(
   unsigned long Offset
);
unsigned long __readfsdword(
   unsigned long Offset
);
unsigned __int64 __readfsqword(
   unsigned long Offset
);
```

### <a name="parameters"></a>Paramètres

*Décalage*\
dans Offset à partir du début de `FS` à lire à partir de.

## <a name="return-value"></a>Valeur de retour

Contenu de la mémoire de l’octet, du mot, du mot double ou de mot quadruple (comme indiqué par le nom de la fonction `FS:[Offset]`appelée) à l’emplacement.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__readfsbyte`|x86|
|`__readfsdword`|x86|
|`__readfsqword`|x86|
|`__readfsword`|x86|

**Fichier d’en-tête** \<> Intro. h

## <a name="remarks"></a>Notes

Ces routines sont disponibles uniquement comme intrinsèques.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[__writefsbyte, \__writefsdword, \__writefsqword, \__writefsword](../intrinsics/writefsbyte-writefsdword-writefsqword-writefsword.md)\
[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
