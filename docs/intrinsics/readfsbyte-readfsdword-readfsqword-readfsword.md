---
description: 'En savoir plus sur les éléments suivants : __readfsbyte, __readfsdword, __readfsqword, __readfsword'
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
ms.openlocfilehash: 2b733ced12045253c78e823379c10a5e70f65143
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340981"
---
# <a name="__readfsbyte-__readfsdword-__readfsqword-__readfsword"></a>__readfsbyte, __readfsdword, __readfsqword, __readfsword

**Spécifique à Microsoft**

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

## <a name="return-value"></a>Valeur retournée

Contenu de la mémoire de l’octet, du mot, du mot double ou de mot quadruple (comme indiqué par le nom de la fonction appelée) à l’emplacement `FS:[Offset]` .

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|
|---------------|------------------|
|`__readfsbyte`|x86|
|`__readfsdword`|x86|
|`__readfsqword`|x86|
|`__readfsword`|x86|

**Fichier d’en-tête** \<intrin.h>

## <a name="remarks"></a>Notes

Ces routines sont disponibles uniquement comme intrinsèques.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[__writefsbyte, \_ _writefsdword, \_ _writefsqword, \_ _writefsword](../intrinsics/writefsbyte-writefsdword-writefsqword-writefsword.md)\
[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
