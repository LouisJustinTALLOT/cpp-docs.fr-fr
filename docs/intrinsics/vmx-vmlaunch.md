---
title: __vmx_vmlaunch
ms.date: 09/02/2019
f1_keywords:
- __vmx_vmlaunch
helpviewer_keywords:
- VMLAUNCH instruction
- __vmx_vmlaunch intrinsic
ms.assetid: 708f7c38-b7c1-4ee7-bfc4-0daeb9cc9360
ms.openlocfilehash: 8d78e5181fdd43e10431e12d0cf540c8c9c2e719
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219548"
---
# <a name="__vmx_vmlaunch"></a>__vmx_vmlaunch

**Section spécifique à Microsoft**

Place l’application appelante dans l’état d’opération non racine VMX (machine virtuelle entrée) à l’aide de la structure de contrôle de machine virtuelle (VMCS) actuelle.

## <a name="syntax"></a>Syntaxe

```C
unsigned char __vmx_vmlaunch(void);
```

## <a name="return-value"></a>Valeur de retour

|`Value`|Signification|
|-----------|-------------|
|0|L’opération a réussi.|
|1|L’opération a échoué avec l’état étendu disponible dans le `VM-instruction error field` de la VMCS actuelle.|
|2|L’opération a échoué sans état disponible.|

## <a name="remarks"></a>Notes

Une application peut effectuer une opération d’entrée de machine virtuelle à l’aide de la fonction [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) ou [__vmx_vmresume](../intrinsics/vmx-vmresume.md) . La fonction [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) peut être utilisée uniquement avec un VMCS dont l’état de `Clear`lancement est, et la fonction [__vmx_vmresume](../intrinsics/vmx-vmresume.md) peut être utilisée uniquement avec un VMCS dont l' `Launched`état de lancement est. Par conséquent, utilisez la fonction [__vmx_vmclear](../intrinsics/vmx-vmclear.md) pour définir l’état de lancement d’un `Clear`VMCS sur, puis utilisez la fonction [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) pour votre première opération VM-Enter et la fonction [__vmx_vmresume](../intrinsics/vmx-vmresume.md) pour la machine virtuelle suivante-Enter traitements.

La fonction `__vmx_vmlaunch` est équivalente à l’instruction machine `VMLAUNCH` . Cette fonction prend en charge l’interaction du moniteur de machines virtuelles d’un hôte avec un système d’exploitation invité et ses applications. Pour plus d’informations, recherchez le document «Intel Virtualization Technical Specification for the IA-32 Intel architecture», document number est c97063-002, sur le site [Intel Corporation](https://software.intel.com/articles/intel-sdm) .

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__vmx_vmlaunch`|X64|

**Fichier d’en-tête** \<> Intro. h

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)\
[__vmx_vmresume](../intrinsics/vmx-vmresume.md)\
[__vmx_vmclear](../intrinsics/vmx-vmclear.md)
