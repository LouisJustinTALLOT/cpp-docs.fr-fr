---
description: 'En savoir plus sur : __vmx_vmresume'
title: __vmx_vmresume
ms.date: 09/02/2019
f1_keywords:
- __vmx_vmresume
helpviewer_keywords:
- __vmx_vmresume intrinsic
- VMRESUME instruction
ms.assetid: 233fe1b6-c727-493a-a484-1b2363732281
ms.openlocfilehash: 35c1ca7eeca847b14d16c451752a186c63a59749
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97343776"
---
# <a name="__vmx_vmresume"></a>__vmx_vmresume

**Spécifique à Microsoft**

Reprend l’opération non racine VMX à l’aide de la structure de contrôle de machine virtuelle actuelle (VMCS, Virtual Machine Control Structure).

## <a name="syntax"></a>Syntaxe

```C
unsigned char __vmx_vmresume(
   void);
```

## <a name="return-value"></a>Valeur de retour

|Valeur|Signification|
|-----------|-------------|
|0|L’opération a réussi.|
|1|L’opération a échoué avec l’état étendu disponible dans le `VM-instruction error field` de la VMCS actuelle.|
|2|L’opération a échoué sans état disponible.|

## <a name="remarks"></a>Notes

Une application peut effectuer une opération VM-enter à l’aide de la fonction [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) ou `__vmx_vmresume` . La fonction `__vmx_vmlaunch` peut être utilisée seulement avec une VMCS dont l’état de lancement est `Clear`, et la fonction `__vmx_vmresume` peut être utilisée seulement avec une VMCS dont l’état de lancement est `Launched`. Par conséquent, utilisez la fonction [__vmx_vmclear](../intrinsics/vmx-vmclear.md) pour définir l’état de lancement d’une VMCS sur `Clear`, puis utilisez la fonction `__vmx_vmlaunch` pour votre première opération VM-enter et la fonction `__vmx_vmresume` pour les opérations VM-enter ultérieures.

La fonction `__vmx_vmresume` est équivalente à l’instruction machine `VMRESUME` . Cette fonction prend en charge l’interaction du moniteur de machines virtuelles d’un hôte avec un système d’exploitation invité et ses applications. Pour plus d’informations, recherchez le document PDF « Intel Virtualization Technical Specification for the IA-32 Intel Architecture », dont le numéro de document est C97063-002, sur le site d’ [Intel Corporation](https://software.intel.com/articles/intel-sdm) .

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|
|---------------|------------------|
|`__vmx_vmresume`|x64|

**Fichier d’en-tête** \<intrin.h>

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)\
[__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md)\
[__vmx_vmclear](../intrinsics/vmx-vmclear.md)
