---
description: 'En savoir plus sur les éléments suivants : __readgsbyte, __readgsdword, __readgsqword, __readgsword'
title: __readgsbyte, __readgsdword, __readgsqword, __readgsword
ms.date: 09/02/2019
f1_keywords:
- __readgsbyte
- __readgsdword
- __readgsqword
- __readgsword
helpviewer_keywords:
- __readgsword intrinsic
- __readgsdword intrinsic
- __readgsqword intrinsic
- __readgsbyte intrinsic
ms.assetid: f822632d-854c-4558-a71b-cdfc3eea2236
ms.openlocfilehash: fb1faf0e785f0d0983d7d3611e68a7515298e61c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340968"
---
# <a name="__readgsbyte-__readgsdword-__readgsqword-__readgsword"></a>__readgsbyte, __readgsdword, __readgsqword, __readgsword

**Spécifique à Microsoft**

Lit la mémoire à partir d’un emplacement spécifié par un décalage par rapport au début du segment GS.

## <a name="syntax"></a>Syntaxe

```C
unsigned char __readgsbyte(
   unsigned long Offset
);
unsigned short __readgsword(
   unsigned long Offset
);
unsigned long __readgsdword(
   unsigned long Offset
);
unsigned __int64 __readgsqword(
   unsigned long Offset
);
```

### <a name="parameters"></a>Paramètres

*Décalage*\
dans Offset à partir du début de `GS` à lire à partir de.

## <a name="return-value"></a>Valeur retournée

Contenu de la mémoire de l’octet, du mot, du mot double ou du mot quadruple (comme indiqué par le nom de la fonction appelée) à l’emplacement `GS:[Offset]` .

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|
|---------------|------------------|
|`__readgsbyte`|x64|
|`__readgsdword`|x64|
|`__readgsqword`|x64|
|`__readgsword`|x64|

**Fichier d’en-tête** \<intrin.h>

## <a name="remarks"></a>Notes

Ces routines sont uniquement disponibles en tant qu’intrinsèque.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[__writegsbyte, \_ _writegsdword, \_ _writegsqword, \_ _writegsword](../intrinsics/writegsbyte-writegsdword-writegsqword-writegsword.md)\
[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
