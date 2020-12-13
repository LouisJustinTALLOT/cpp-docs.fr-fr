---
description: 'En savoir plus sur : __vmx_vmptrst'
title: __vmx_vmptrst
ms.date: 09/02/2019
f1_keywords:
- __vmx_vmptrst
helpviewer_keywords:
- __vmx_vmptrst intrinsic
- VMPTRST instruction
ms.assetid: 8dc66e47-03a0-41b0-8e25-c1485f42817a
ms.openlocfilehash: 216da453acf5c04e4189271185567841327571ec
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333519"
---
# <a name="__vmx_vmptrst"></a>__vmx_vmptrst

**Spécifique à Microsoft**

Stocke le pointeur vers la structure de contrôle de machine virtuelle (VMCS) actuelle à l’adresse spécifiée.

## <a name="syntax"></a>Syntaxe

```C
void __vmx_vmptrst(
   unsigned __int64 *VmcsPhysicalAddress
);
```

### <a name="parameters"></a>Paramètres

*VmcsPhysicalAddress*\
dans Adresse où le pointeur VMCS actuel est stocké.

## <a name="remarks"></a>Notes

Le pointeur VMCS est une adresse physique 64 bits.

La fonction `__vmx_vmptrst` est équivalente à l’instruction machine `VMPTRST` . Cette fonction prend en charge l’interaction du moniteur de machines virtuelles d’un hôte avec un système d’exploitation invité et ses applications. Pour plus d’informations, recherchez le document « Intel Virtualization Technical Specification for the IA-32 Intel architecture », document number est c97063-002, sur le site [Intel Corporation](https://software.intel.com/articles/intel-sdm) .

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|
|---------------|------------------|
|`__vmx_vmptrst`|x86, x64|

**Fichier d’en-tête** \<intrin.h>

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)\
[__vmx_vmptrld](../intrinsics/vmx-vmptrld.md)
