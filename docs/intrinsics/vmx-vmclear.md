---
title: __vmx_vmclear
ms.date: 09/02/2019
f1_keywords:
- __vmx_vmclear
helpviewer_keywords:
- VMCLEAR instruction
- __vmx_vmclear intrinsic
ms.assetid: e3eb98e4-50fc-4c93-9bac-340fd1f0a466
ms.openlocfilehash: 3b5807402cf0a9d8a9ef1ded1d112d22a801633e
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219539"
---
# <a name="__vmx_vmclear"></a>__vmx_vmclear

**Section spécifique à Microsoft**

Initialise la structure de contrôle d’ordinateur virtuel (VMCS) spécifiée et définit son état de `Clear`lancement sur.

## <a name="syntax"></a>Syntaxe

```C
unsigned char __vmx_vmclear(
   unsigned __int64 *VmcsPhysicalAddress
);
```

### <a name="parameters"></a>Paramètres

*VmcsPhysicalAddress*\
dans Pointeur vers un emplacement de mémoire 64 bits qui contient l’adresse physique du VMCS à effacer.

## <a name="return-value"></a>Valeur de retour

|`Value`|Signification|
|-----------|-------------|
|0|L’opération a réussi.|
|1|L’opération a échoué avec l’état étendu disponible dans le `VM-instruction error field` de la VMCS actuelle.|
|2|L’opération a échoué sans état disponible.|

## <a name="remarks"></a>Notes

Une application peut effectuer une opération d’entrée de machine virtuelle à l’aide de la fonction [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) ou [__vmx_vmresume](../intrinsics/vmx-vmresume.md) . La fonction [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) peut être utilisée uniquement avec un VMCS dont l’état de `Clear`lancement est, et la fonction [__vmx_vmresume](../intrinsics/vmx-vmresume.md) peut être utilisée uniquement avec un VMCS dont l' `Launched`état de lancement est. Par conséquent, utilisez la fonction [__vmx_vmclear](../intrinsics/vmx-vmclear.md) pour définir l’état de lancement d’un `Clear`VMCS sur. Utilisez la fonction [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) pour votre première opération VM-Enter et la fonction [__vmx_vmresume](../intrinsics/vmx-vmresume.md) pour les opérations d’entrée de machine virtuelle ultérieures.

La fonction `__vmx_vmclear` est équivalente à l’instruction machine `VMCLEAR` . Cette fonction prend en charge l’interaction du moniteur de machines virtuelles d’un hôte avec un système d’exploitation invité et ses applications. Pour plus d’informations, recherchez le document «Intel Virtualization Technical Specification for the IA-32 Intel architecture», document number est c97063-002, sur le site [Intel Corporation](https://software.intel.com/articles/intel-sdm) .

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__vmx_vmclear`|X64|

**Fichier d’en-tête** \<> Intro. h

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)\
[__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md)\
[__vmx_vmresume](../intrinsics/vmx-vmresume.md)
