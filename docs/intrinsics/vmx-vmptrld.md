---
title: __vmx_vmptrld
ms.date: 09/02/2019
f1_keywords:
- __vmx_vmptrld
helpviewer_keywords:
- __vmx_vmptrld intrinsic
- VMPTRLD instruction
ms.assetid: 95c9ec5b-1a81-41ba-983e-327bd6a65fcb
ms.openlocfilehash: 79b5a8b34b652ae1f011e89c793a7157c9e435ee
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219497"
---
# <a name="__vmx_vmptrld"></a>__vmx_vmptrld

**Section spécifique à Microsoft**

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

## <a name="return-value"></a>Valeur de retour

entre
L’opération a réussi.

1,0
L’opération a échoué avec l’état étendu disponible dans le `VM-instruction error field` de la VMCS actuelle.

2
L’opération a échoué sans état disponible.

## <a name="remarks"></a>Notes

Le pointeur VMCS est une adresse physique 64 bits.

La fonction `__vmx_vmptrld` est équivalente à l’instruction machine `VMPTRLD` . Cette fonction prend en charge l’interaction du moniteur de machines virtuelles d’un hôte avec un système d’exploitation invité et ses applications. Pour plus d’informations, recherchez le document «Intel Virtualization Technical Specification for the IA-32 Intel architecture», document number est c97063-002, sur le site [Intel Corporation](https://software.intel.com/articles/intel-sdm) .

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__vmx_vmptrld`|X64|

**Fichier d’en-tête** \<> Intro. h

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)\
[__vmx_vmptrst](../intrinsics/vmx-vmptrst.md)
