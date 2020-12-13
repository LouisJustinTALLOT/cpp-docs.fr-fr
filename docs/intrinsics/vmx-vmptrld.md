---
description: 'En savoir plus sur : __vmx_vmptrld'
title: __vmx_vmptrld
ms.date: 09/02/2019
f1_keywords:
- __vmx_vmptrld
helpviewer_keywords:
- __vmx_vmptrld intrinsic
- VMPTRLD instruction
ms.assetid: 95c9ec5b-1a81-41ba-983e-327bd6a65fcb
ms.openlocfilehash: 850311e4423940ebd34a203e6d43ec961b3258f4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333535"
---
# <a name="__vmx_vmptrld"></a>__vmx_vmptrld

**Spécifique à Microsoft**

Charge le pointeur vers la structure de contrôle de machine virtuelle (VMCS) actuelle à partir de l’adresse spécifiée.

## <a name="syntax"></a>Syntaxe

```C
int __vmx_vmptrld(
   unsigned __int64 *VmcsPhysicalAddress
);
```

### <a name="parameters"></a>Paramètres

*VmcsPhysicalAddress*\
dans Adresse où le pointeur VMCS est stocké.

## <a name="return-value"></a>Valeur retournée

entre
L’opération a réussi.

1,0
L’opération a échoué avec l’état étendu disponible dans le `VM-instruction error field` de la VMCS actuelle.

2
L’opération a échoué sans état disponible.

## <a name="remarks"></a>Notes

Le pointeur VMCS est une adresse physique 64 bits.

La fonction `__vmx_vmptrld` est équivalente à l’instruction machine `VMPTRLD` . Cette fonction prend en charge l’interaction du moniteur de machines virtuelles d’un hôte avec un système d’exploitation invité et ses applications. Pour plus d’informations, recherchez le document « Intel Virtualization Technical Specification for the IA-32 Intel architecture », document number est c97063-002, sur le site [Intel Corporation](https://software.intel.com/articles/intel-sdm) .

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|
|---------------|------------------|
|`__vmx_vmptrld`|x64|

**Fichier d’en-tête** \<intrin.h>

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)\
[__vmx_vmptrst](../intrinsics/vmx-vmptrst.md)
