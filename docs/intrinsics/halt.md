---
title: __halt
ms.date: 09/02/2019
f1_keywords:
- __halt
- __halt_cpp
helpviewer_keywords:
- __halt intrinsic
- HLT instruction
ms.assetid: a074f44a-101c-45a5-8a5e-cfd223c34002
ms.openlocfilehash: 66f5e05e7673523966ef35ac743fc585930b511c
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222152"
---
# <a name="__halt"></a>__halt

**Section spécifique à Microsoft**

Arrête le microprocesseur jusqu’à ce qu’une interruption activée, une interruption non masquable (NMI) ou une réinitialisation se produise.

## <a name="syntax"></a>Syntaxe

```C
void __halt( void );
```

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__halt`|x86, x64|

**Fichier d’en-tête** \<> Intro. h

## <a name="remarks"></a>Notes

La `__halt` fonction est équivalente à `HLT` l’instruction machine et est disponible uniquement en mode noyau. Pour plus d’informations, recherchez le document «Guide du développeur de logiciels d’architecture Intel, volume 2: Référence du jeu d’instructions, sur le site [Intel Corporation](https://software.intel.com/articles/intel-sdm) .

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
