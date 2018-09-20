---
title: __invlpg | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __invlpg
- __invlpg_cpp
dev_langs:
- C++
helpviewer_keywords:
- invlpg instruction
- __invlpg intrinsic
ms.assetid: 3fb3633f-d9b7-4ec0-9e7f-a7f2fa8ed794
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 01a35d110c56bba6b89c5bf34dedec61bde90794
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46403212"
---
# <a name="invlpg"></a>__invlpg

**Section spécifique à Microsoft**

Génère le x86 `invlpg` instruction, ce qui invalide la mémoire tampon à la lookaside traduction (TLB) pour la page associée de mémoire vers lequel pointé `Address`.

## <a name="syntax"></a>Syntaxe

```
void __invlpg(
   void* Address
);
```

#### <a name="parameters"></a>Paramètres

*Adresse*<br/>
[in] Une adresse 64 bits.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__invlpg`|x86, x64|

**Fichier d’en-tête** \<intrin.h >

## <a name="remarks"></a>Notes

L’intrinsèque `__invlpg` émet une instruction privilégiée et est uniquement disponible en mode noyau avec un niveau de privilège (CPL) égale à 0.

Cette routine est disponible uniquement en tant qu'intrinsèque.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)