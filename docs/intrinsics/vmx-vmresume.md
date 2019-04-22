---
title: __vmx_vmresume
ms.date: 11/04/2016
f1_keywords:
- __vmx_vmresume
helpviewer_keywords:
- __vmx_vmresume intrinsic
- VMRESUME instruction
ms.assetid: 233fe1b6-c727-493a-a484-1b2363732281
ms.openlocfilehash: d2bfe9a8f98b8a03a82768177217d70674708c39
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59040591"
---
# <a name="vmxvmresume"></a>__vmx_vmresume

**Section spécifique à Microsoft**

Reprend l’opération non racine VMX à l’aide de la structure de contrôle de machine virtuelle actuelle (VMCS, Virtual Machine Control Structure).

## <a name="syntax"></a>Syntaxe

```
unsigned char __vmx_vmresume(
   void);
```

## <a name="return-value"></a>Valeur de retour

|Value|Signification|
|-----------|-------------|
|0|L’opération a réussi.|
|1|L’opération a échoué avec l’état étendu disponible dans le `VM-instruction error field` de la VMCS actuelle.|
|2|L’opération a échoué sans état disponible.|

## <a name="remarks"></a>Notes

Une application peut effectuer une opération VM-enter à l’aide de la fonction [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) ou `__vmx_vmresume` . La fonction `__vmx_vmlaunch` peut être utilisée seulement avec une VMCS dont l’état de lancement est `Clear`, et la fonction `__vmx_vmresume` peut être utilisée seulement avec une VMCS dont l’état de lancement est `Launched`. Par conséquent, utilisez la fonction [__vmx_vmclear](../intrinsics/vmx-vmclear.md) pour définir l’état de lancement d’une VMCS sur `Clear`, puis utilisez la fonction `__vmx_vmlaunch` pour votre première opération VM-enter et la fonction `__vmx_vmresume` pour les opérations VM-enter ultérieures.

La fonction `__vmx_vmresume` est équivalente à l’instruction machine `VMRESUME` . Cette fonction prend en charge l’interaction du moniteur de machines virtuelles d’un hôte avec un système d’exploitation invité et ses applications. Pour plus d’informations, recherchez le document PDF « Intel Virtualization Technical Specification for the IA-32 Intel Architecture », dont le numéro de document est C97063-002, sur le site d’ [Intel Corporation](https://software.intel.com/articles/intel-sdm) .

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__vmx_vmresume`|X64|

**Fichier d’en-tête** \<intrin.h >

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)<br/>
[__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md)<br/>
[__vmx_vmclear](../intrinsics/vmx-vmclear.md)