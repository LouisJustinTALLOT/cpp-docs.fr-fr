---
title: __vmx_vmptrst
ms.date: 09/02/2019
f1_keywords:
- __vmx_vmptrst
helpviewer_keywords:
- __vmx_vmptrst intrinsic
- VMPTRST instruction
ms.assetid: 8dc66e47-03a0-41b0-8e25-c1485f42817a
ms.openlocfilehash: e559746be9e2a3fe5e81afa4d290265394db3e36
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219486"
---
# <a name="__vmx_vmptrst"></a>__vmx_vmptrst

**Section spécifique à Microsoft**

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

La fonction `__vmx_vmptrst` est équivalente à l’instruction machine `VMPTRST` . Cette fonction prend en charge l’interaction du moniteur de machines virtuelles d’un hôte avec un système d’exploitation invité et ses applications. Pour plus d’informations, recherchez le document «Intel Virtualization Technical Specification for the IA-32 Intel architecture», document number est c97063-002, sur le site [Intel Corporation](https://software.intel.com/articles/intel-sdm) .

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__vmx_vmptrst`|x86, x64|

**Fichier d’en-tête** \<> Intro. h

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)\
[__vmx_vmptrld](../intrinsics/vmx-vmptrld.md)
