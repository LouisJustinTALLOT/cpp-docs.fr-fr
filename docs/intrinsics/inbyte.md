---
description: 'En savoir plus sur : __inbyte'
title: __inbyte
ms.date: 09/02/2019
f1_keywords:
- __inbyte
- __inbyte_cpp
helpviewer_keywords:
- in instruction
- __inbyte intrinsic
ms.assetid: 03b61799-2a08-474d-adc4-2cbf7c81a4d5
ms.openlocfilehash: 77cc1cfb792ffa2f6aef9879820e644372895193
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337022"
---
# <a name="__inbyte"></a>__inbyte

**Spécifique à Microsoft**

Génère l' `in` instruction, en retournant un seul octet lu à partir du port spécifié par `Port` .

## <a name="syntax"></a>Syntaxe

```C
unsigned char __inbyte(
   unsigned short Port
);
```

### <a name="parameters"></a>Paramètres

*Importer*\
dans Port à partir duquel effectuer la lecture.

## <a name="return-value"></a>Valeur retournée

Octet lu à partir du port spécifié.

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|
|---------------|------------------|
|`__inbyte`|x86, x64|

**Fichier d’en-tête** \<intrin.h>

**FIN spécifique à Microsoft**

## <a name="remarks"></a>Notes

Cette routine est disponible uniquement en tant qu'intrinsèque.

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
