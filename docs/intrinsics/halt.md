---
description: 'En savoir plus sur : __halt'
title: __halt
ms.date: 09/02/2019
f1_keywords:
- __halt
- __halt_cpp
helpviewer_keywords:
- __halt intrinsic
- HLT instruction
ms.assetid: a074f44a-101c-45a5-8a5e-cfd223c34002
ms.openlocfilehash: e38478b14b59c910e6d6ac12f9cb69fa369e3459
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336974"
---
# <a name="__halt"></a>__halt

**Spécifique à Microsoft**

Arrête le microprocesseur jusqu’à ce qu’une interruption activée, une interruption non masquable (NMI) ou une réinitialisation se produise.

## <a name="syntax"></a>Syntaxe

```C
void __halt( void );
```

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|
|---------------|------------------|
|`__halt`|x86, x64|

**Fichier d’en-tête** \<intrin.h>

## <a name="remarks"></a>Notes

La `__halt` fonction est équivalente à l' `HLT` instruction machine et est disponible uniquement en mode noyau. Pour plus d’informations, recherchez le document « Guide du développeur de logiciels d’architecture Intel, volume 2 : référence de jeu d’instructions » sur le site [Intel Corporation](https://software.intel.com/articles/intel-sdm) .

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
