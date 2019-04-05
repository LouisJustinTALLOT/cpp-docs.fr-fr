---
title: __invlpg
ms.date: 11/04/2016
f1_keywords:
- __invlpg
- __invlpg_cpp
helpviewer_keywords:
- invlpg instruction
- __invlpg intrinsic
ms.assetid: 3fb3633f-d9b7-4ec0-9e7f-a7f2fa8ed794
ms.openlocfilehash: b4f941baae9f03ed288a99d59e2b06262962e339
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59023312"
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

[compilateur, intrinsèques](../intrinsics/compiler-intrinsics.md)