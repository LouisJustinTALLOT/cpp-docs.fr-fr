---
description: 'En savoir plus sur : __invlpg'
title: __invlpg
ms.date: 09/02/2019
f1_keywords:
- __invlpg
- __invlpg_cpp
helpviewer_keywords:
- invlpg instruction
- __invlpg intrinsic
ms.assetid: 3fb3633f-d9b7-4ec0-9e7f-a7f2fa8ed794
ms.openlocfilehash: 16d8f51c8bf36ea94be7b1325ee5bed256c29693
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97167901"
---
# <a name="__invlpg"></a>__invlpg

**Spécifique à Microsoft**

Génère l' `invlpg` instruction x86, qui invalide la mémoire tampon de traduction (TLB) pour la page associée à la mémoire vers laquelle pointe l' *adresse*.

## <a name="syntax"></a>Syntaxe

```C
void __invlpg(
   void* Address
);
```

### <a name="parameters"></a>Paramètres

*-*\
dans Adresse 64 bits.

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|
|---------------|------------------|
|`__invlpg`|x86, x64|

**Fichier d’en-tête** \<intrin.h>

## <a name="remarks"></a>Notes

L’intrinsèque `__invlpg` émet une instruction privilégiée et est disponible uniquement en mode noyau avec un niveau de privilège (CPL) de 0.

Cette routine est disponible uniquement en tant qu'intrinsèque.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
