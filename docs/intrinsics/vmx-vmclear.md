---
description: 'En savoir plus sur : __vmx_vmclear'
title: __vmx_vmclear
ms.date: 09/02/2019
f1_keywords:
- __vmx_vmclear
helpviewer_keywords:
- VMCLEAR instruction
- __vmx_vmclear intrinsic
ms.assetid: e3eb98e4-50fc-4c93-9bac-340fd1f0a466
ms.openlocfilehash: 2eec5c1189c6a798246a6dabfc731fb0166bc14a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333566"
---
# <a name="__vmx_vmclear"></a>__vmx_vmclear

**Spécifique à Microsoft**

Initialise la structure de contrôle d’ordinateur virtuel (VMCS) spécifiée et définit son état de lancement sur `Clear` .

## <a name="syntax"></a>Syntaxe

```C
unsigned char __vmx_vmclear(
   unsigned __int64 *VmcsPhysicalAddress
);
```

### <a name="parameters"></a>Paramètres

*VmcsPhysicalAddress*\
dans Pointeur vers un emplacement de mémoire 64 bits qui contient l’adresse physique du VMCS à effacer.

## <a name="return-value"></a>Valeur retournée

|Valeur|Signification|
|-----------|-------------|
|0|L’opération a réussi.|
|1|L’opération a échoué avec l’état étendu disponible dans le `VM-instruction error field` de la VMCS actuelle.|
|2|L’opération a échoué sans état disponible.|

## <a name="remarks"></a>Notes

Une application peut effectuer une opération d’entrée de machine virtuelle à l’aide de la fonction [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) ou [__vmx_vmresume](../intrinsics/vmx-vmresume.md) . La fonction [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) peut être utilisée uniquement avec un VMCS dont l’état de lancement est `Clear` , et la fonction [__vmx_vmresume](../intrinsics/vmx-vmresume.md) peut être utilisée uniquement avec un VMCS dont l’état de lancement est `Launched` . Par conséquent, utilisez la fonction [__vmx_vmclear](../intrinsics/vmx-vmclear.md) pour définir l’état de lancement d’un VMCS sur `Clear` . Utilisez la fonction [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) pour votre première opération VM-Enter et la fonction [__vmx_vmresume](../intrinsics/vmx-vmresume.md) pour les opérations d’entrée de machine virtuelle ultérieures.

La fonction `__vmx_vmclear` est équivalente à l’instruction machine `VMCLEAR` . Cette fonction prend en charge l’interaction du moniteur de machines virtuelles d’un hôte avec un système d’exploitation invité et ses applications. Pour plus d’informations, recherchez le document « Intel Virtualization Technical Specification for the IA-32 Intel architecture », document number est c97063-002, sur le site [Intel Corporation](https://software.intel.com/articles/intel-sdm) .

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|
|---------------|------------------|
|`__vmx_vmclear`|x64|

**Fichier d’en-tête** \<intrin.h>

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)\
[__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md)\
[__vmx_vmresume](../intrinsics/vmx-vmresume.md)
