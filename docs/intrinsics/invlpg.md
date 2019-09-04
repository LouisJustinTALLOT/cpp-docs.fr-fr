---
title: __invlpg
ms.date: 09/02/2019
f1_keywords:
- __invlpg
- __invlpg_cpp
helpviewer_keywords:
- invlpg instruction
- __invlpg intrinsic
ms.assetid: 3fb3633f-d9b7-4ec0-9e7f-a7f2fa8ed794
ms.openlocfilehash: ba8bd81498f805992336b0dc4163fe18fa157a2c
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221898"
---
# <a name="__invlpg"></a>__invlpg

**Section spécifique à Microsoft**

Génère l’instruction `invlpg` x86, qui invalide la mémoire tampon de traduction (TLB) pour la page associée à la mémoire vers laquelle pointe l' *adresse*.

## <a name="syntax"></a>Syntaxe

```C
void __invlpg(
   void* Address
);
```

### <a name="parameters"></a>Paramètres

*-* \
dans Adresse 64 bits.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__invlpg`|x86, x64|

**Fichier d’en-tête** \<> Intro. h

## <a name="remarks"></a>Notes

L’intrinsèque `__invlpg` émet une instruction privilégiée et est disponible uniquement en mode noyau avec un niveau de privilège (CPL) de 0.

Cette routine est disponible uniquement en tant qu'intrinsèque.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
