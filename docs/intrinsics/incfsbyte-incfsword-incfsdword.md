---
description: 'En savoir plus sur les éléments suivants : __incfsbyte, __incfsword __incfsdword'
title: __incfsbyte, __incfsword, __incfsdword
ms.date: 09/02/2019
f1_keywords:
- __incfsword
- __incfsbyte_cpp
- __incfsbyte
- __incfsdword
- __incfsword_cpp
- __incfsdword_cpp
helpviewer_keywords:
- __incfsword intrinsic
- __incfsdword intrinsic
- __incfsbyte intrinsic
ms.assetid: 820457fb-e35e-42d3-bcb6-725da3281c64
ms.openlocfilehash: 29d86de51ad282789cb19b72ca953f65af2dc19d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336971"
---
# <a name="__incfsbyte-__incfsword-__incfsdword"></a>__incfsbyte, __incfsword, __incfsdword

**Spécifique à Microsoft**

Ajoutez un à la valeur à un emplacement de mémoire spécifié par un décalage par rapport au début du `FS` segment.

## <a name="syntax"></a>Syntaxe

```C
void __incfsbyte(
   unsigned long Offset
);
void __incfsword(
   unsigned long Offset
);
void __incfsdword(
   unsigned long Offset
);
```

### <a name="parameters"></a>Paramètres

*Décalage*\
dans Offset à partir du début de `FS` .

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|
|---------------|------------------|
|`__incfsbyte`|x86|
|`__incfsword`|x86|
|`__incfsdword`|x86|

**Fichier d’en-tête** \<intrin.h>

## <a name="remarks"></a>Notes

Ces fonctions intrinsèques sont disponibles uniquement en mode noyau et les routines sont uniquement disponibles en tant qu’intrinsèques.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[\__addfsbyte, \_ _addfsword \_ _addfsdword](../intrinsics/addfsbyte-addfsword-addfsdword.md)\
[\__readfsbyte, \_ _readfsdword, \_ _readfsqword, \_ _readfsword](../intrinsics/readfsbyte-readfsdword-readfsqword-readfsword.md)\
[\__writefsbyte, \_ _writefsdword, \_ _writefsqword, \_ _writefsword](../intrinsics/writefsbyte-writefsdword-writefsqword-writefsword.md)\
[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
