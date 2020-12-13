---
description: 'En savoir plus sur : __vmx_vmlaunch'
title: __vmx_vmlaunch
ms.date: 09/02/2019
f1_keywords:
- __vmx_vmlaunch
helpviewer_keywords:
- VMLAUNCH instruction
- __vmx_vmlaunch intrinsic
ms.assetid: 708f7c38-b7c1-4ee7-bfc4-0daeb9cc9360
ms.openlocfilehash: 3f6596e0644250710491ed90036a651c0725a5f9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333542"
---
# <a name="__vmx_vmlaunch"></a>__vmx_vmlaunch

**Spécifique à Microsoft**

Place l’application appelante dans l’état d’opération non racine VMX (machine virtuelle entrée) à l’aide de la structure de contrôle de machine virtuelle (VMCS) actuelle.

## <a name="syntax"></a>Syntaxe

```C
unsigned char __vmx_vmlaunch(void);
```

## <a name="return-value"></a>Valeur de retour

|Valeur|Signification|
|-----------|-------------|
|0|L’opération a réussi.|
|1|L’opération a échoué avec l’état étendu disponible dans le `VM-instruction error field` de la VMCS actuelle.|
|2|L’opération a échoué sans état disponible.|

## <a name="remarks"></a>Notes

Une application peut effectuer une opération d’entrée de machine virtuelle à l’aide de la fonction [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) ou [__vmx_vmresume](../intrinsics/vmx-vmresume.md) . La fonction [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) peut être utilisée uniquement avec un VMCS dont l’état de lancement est `Clear` , et la fonction [__vmx_vmresume](../intrinsics/vmx-vmresume.md) peut être utilisée uniquement avec un VMCS dont l’état de lancement est `Launched` . Par conséquent, utilisez la fonction [__vmx_vmclear](../intrinsics/vmx-vmclear.md) pour définir l’état de lancement d’un VMCS sur `Clear` , puis utilisez la fonction [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) pour votre première opération VM-Enter et la fonction [__vmx_vmresume](../intrinsics/vmx-vmresume.md) pour les opérations d’entrée de machine virtuelle ultérieures.

La fonction `__vmx_vmlaunch` est équivalente à l’instruction machine `VMLAUNCH` . Cette fonction prend en charge l’interaction du moniteur de machines virtuelles d’un hôte avec un système d’exploitation invité et ses applications. Pour plus d’informations, recherchez le document « Intel Virtualization Technical Specification for the IA-32 Intel architecture », document number est c97063-002, sur le site [Intel Corporation](https://software.intel.com/articles/intel-sdm) .

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|
|---------------|------------------|
|`__vmx_vmlaunch`|x64|

**Fichier d’en-tête** \<intrin.h>

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)\
[__vmx_vmresume](../intrinsics/vmx-vmresume.md)\
[__vmx_vmclear](../intrinsics/vmx-vmclear.md)
