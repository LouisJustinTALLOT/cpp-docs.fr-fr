---
title: __vmx_vmptrst
ms.date: 11/04/2016
f1_keywords:
- __vmx_vmptrst
helpviewer_keywords:
- __vmx_vmptrst intrinsic
- VMPTRST instruction
ms.assetid: 8dc66e47-03a0-41b0-8e25-c1485f42817a
ms.openlocfilehash: 4d7e2ed29daac276c9b6cba07a727371a212fd4a
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51331891"
---
# <a name="vmxvmptrst"></a>__vmx_vmptrst

**Section spécifique à Microsoft**

Stocke le pointeur vers la structure de contrôle de machine virtuelle actuelle (VMCS) à l’adresse spécifiée.

## <a name="syntax"></a>Syntaxe

```
void __vmx_vmptrst(
   unsigned __int64 *VmcsPhysicalAddress
);
```

### <a name="parameters"></a>Paramètres

*VmcsPhysicalAddress*<br/>
[in] L’adresse où se trouve le pointeur de la VMCS actuels.

## <a name="remarks"></a>Notes

Le pointeur de la VMCS est une adresse physique 64 bits.

La fonction `__vmx_vmptrst` est équivalente à l’instruction machine `VMPTRST` . Cette fonction prend en charge l’interaction du moniteur de machines virtuelles d’un hôte avec un système d’exploitation invité et ses applications. Pour plus d’informations, recherchez le document, « Intel Virtualization Technical Specification pour l’IA-32 Intel Architecture, » numéro de document est C97063-002, à la [Intel Corporation](https://software.intel.com/articles/intel-sdm) site.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__vmx_vmptrst`|x86, x64|

**Fichier d’en-tête** \<intrin.h >

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)<br/>
[__vmx_vmptrld](../intrinsics/vmx-vmptrld.md)