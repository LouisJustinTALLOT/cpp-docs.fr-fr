---
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
ms.openlocfilehash: 278f1de33a7e01c5893217ddd8aaa22e68cf0c94
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222351"
---
# <a name="__readgsbyte-__readgsdword-__readgsqword-__readgsword"></a>__readgsbyte, __readgsdword, __readgsqword, __readgsword

**Section spécifique à Microsoft**

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

## <a name="return-value"></a>Valeur de retour

Contenu de la mémoire de l’octet, du mot, du mot double ou du mot quadruple (comme indiqué par le nom de la fonction appelée `GS:[Offset]`) à l’emplacement.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__readgsbyte`|X64|
|`__readgsdword`|X64|
|`__readgsqword`|X64|
|`__readgsword`|X64|

**Fichier d’en-tête** \<> Intro. h

## <a name="remarks"></a>Notes

Ces routines sont uniquement disponibles en tant qu’intrinsèque.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[__writegsbyte, \__writegsdword, \__writegsqword, \__writegsword](../intrinsics/writegsbyte-writegsdword-writegsqword-writegsword.md)\
[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
