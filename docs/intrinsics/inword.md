---
description: 'En savoir plus sur : __inword'
title: __inword
ms.date: 09/02/2019
f1_keywords:
- __inword_cpp
- __inword
helpviewer_keywords:
- in instruction
- __inword intrinsic
ms.assetid: 5c617edd-6709-40a1-aad2-40d5e39283c6
ms.openlocfilehash: 8e2d698437cdb27a472872cfe24d7d0ab0a3c768
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97167875"
---
# <a name="__inword"></a>__inword

**Spécifique à Microsoft**

Lit les données à partir du port spécifié à l’aide de l' `in` instruction.

## <a name="syntax"></a>Syntaxe

```C
unsigned short __inword(
   unsigned short Port
);
```

### <a name="parameters"></a>Paramètres

*Importer*\
dans Port à partir duquel effectuer la lecture.

## <a name="return-value"></a>Valeur retournée

Mot des données lues.

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|
|---------------|------------------|
|`__inword`|x86, x64|

**Fichier d’en-tête** \<intrin.h>

## <a name="remarks"></a>Notes

Cette routine est disponible uniquement en tant qu'intrinsèque.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
