---
title: __inbyte
ms.date: 09/02/2019
f1_keywords:
- __inbyte
- __inbyte_cpp
helpviewer_keywords:
- in instruction
- __inbyte intrinsic
ms.assetid: 03b61799-2a08-474d-adc4-2cbf7c81a4d5
ms.openlocfilehash: f0036763ed7315a54fbfe6dcc873b46b52f0730c
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222137"
---
# <a name="__inbyte"></a>__inbyte

**Section spécifique à Microsoft**

Génère l' `in` instruction, en retournant un seul octet lu à partir du `Port`port spécifié par.

## <a name="syntax"></a>Syntaxe

```C
unsigned char __inbyte(
   unsigned short Port
);
```

### <a name="parameters"></a>Paramètres

*Importer*\
dans Port à partir duquel effectuer la lecture.

## <a name="return-value"></a>Valeur de retour

Octet lu à partir du port spécifié.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__inbyte`|x86, x64|

**Fichier d’en-tête** \<> Intro. h

**FIN de la section spécifique à Microsoft**

## <a name="remarks"></a>Notes

Cette routine est disponible uniquement en tant qu'intrinsèque.

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
