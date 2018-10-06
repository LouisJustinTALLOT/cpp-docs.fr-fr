---
title: __halt | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __halt
- __halt_cpp
dev_langs:
- C++
helpviewer_keywords:
- __halt intrinsic
- HLT instruction
ms.assetid: a074f44a-101c-45a5-8a5e-cfd223c34002
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a42575b25040b0dc78bd0199089aaf9575e8de47
ms.sourcegitcommit: a738519aa491a493a8f213971354356c0e6a5f3a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2018
ms.locfileid: "48820622"
---
# <a name="halt"></a>__halt

**Section spécifique à Microsoft**

Arrête le microprocesseur jusqu'à ce qu’une interruption est activée, une interruption non masquable (interruption non programmable) ou une réinitialisation se produit.

## <a name="syntax"></a>Syntaxe

```
void __halt( void );
```

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__halt`|x86, x64|

**Fichier d’en-tête** \<intrin.h >

## <a name="remarks"></a>Notes

Le `__halt` fonction est équivalente à la `HLT` instruction machine et est disponible uniquement en mode noyau. Pour plus d’informations, recherchez dans le document, « manuel du développeur de logiciels Architecture Intel, Volume 2 : référence de jeu d’instructions, » à la [Intel Corporation](https://software.intel.com/articles/intel-sdm) site.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)