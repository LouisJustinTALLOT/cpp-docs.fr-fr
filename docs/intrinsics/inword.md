---
title: __inword
ms.date: 09/02/2019
f1_keywords:
- __inword_cpp
- __inword
helpviewer_keywords:
- in instruction
- __inword intrinsic
ms.assetid: 5c617edd-6709-40a1-aad2-40d5e39283c6
ms.openlocfilehash: 7daaf1abd5089716061f118e30e9534e5c5c18ee
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440978"
---
# <a name="__inword"></a>__inword

**Section spécifique de Microsoft**

Lit les données à partir du port spécifié à l’aide de l’instruction `in`.

## <a name="syntax"></a>Syntaxe

```C
unsigned short __inword(
   unsigned short Port
);
```

### <a name="parameters"></a>Paramètres

\ de *port*
dans Port à partir duquel effectuer la lecture.

## <a name="return-value"></a>Valeur retournée

Mot des données lues.

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|
|---------------|------------------|
|`__inword`|x86, x64|

**Fichier d’en-tête** \<Intro. h >

## <a name="remarks"></a>Notes

Cette routine est disponible uniquement en tant qu'intrinsèque.

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
