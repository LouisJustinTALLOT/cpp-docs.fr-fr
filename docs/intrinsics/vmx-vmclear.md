---
title: __vmx_vmclear
ms.date: 11/04/2016
f1_keywords:
- __vmx_vmclear
helpviewer_keywords:
- VMCLEAR instruction
- __vmx_vmclear intrinsic
ms.assetid: e3eb98e4-50fc-4c93-9bac-340fd1f0a466
ms.openlocfilehash: 17e3e5c91a58894b25fc6b2a72f7d0056fa88119
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59036535"
---
# <a name="vmxvmclear"></a>__vmx_vmclear

**Section spécifique à Microsoft**

Initialise la structure de contrôle de machine virtuelle spécifiée (VMCS) et définit son état de lancement `Clear`.

## <a name="syntax"></a>Syntaxe

```
unsigned char __vmx_vmclear(
   unsigned __int64 *VmcsPhysicalAddress
);
```

#### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*VmcsPhysicalAddress*|[in] Pointeur vers un emplacement de mémoire 64 bits qui contient l’adresse physique de la VMCS à effacer.|

## <a name="return-value"></a>Valeur de retour

|Value|Signification|
|-----------|-------------|
|0|L’opération a réussi.|
|1|L’opération a échoué avec l’état étendu disponible dans le `VM-instruction error field` de la VMCS actuelle.|
|2|L’opération a échoué sans état disponible.|

## <a name="remarks"></a>Notes

Une application peut effectuer une opération VM-enter à l’aide du [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) ou [__vmx_vmresume](../intrinsics/vmx-vmresume.md) (fonction). Le [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) fonction peut être utilisée uniquement avec une VMCS dont l’état de lancement est `Clear`et le [__vmx_vmresume](../intrinsics/vmx-vmresume.md) fonction peut être utilisée uniquement avec une VMCS dont l’état de lancement est `Launched`. Par conséquent, utilisez le [__vmx_vmclear](../intrinsics/vmx-vmclear.md) fonction permettant de définir l’état de lancement d’une VMCS sur `Clear`. Utilisez le [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) (fonction) pour votre première opération VM-enter et la [__vmx_vmresume](../intrinsics/vmx-vmresume.md) (fonction) pour les opérations VM-enter ultérieures.

La fonction `__vmx_vmclear` est équivalente à l’instruction machine `VMCLEAR` . Cette fonction prend en charge l’interaction du moniteur de machines virtuelles d’un hôte avec un système d’exploitation invité et ses applications. Pour plus d’informations, recherchez le document, « Intel Virtualization Technical Specification pour l’IA-32 Intel Architecture, » numéro de document est C97063-002, à la [Intel Corporation](https://software.intel.com/articles/intel-sdm) site.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__vmx_vmclear`|X64|

**Fichier d’en-tête** \<intrin.h >

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[compilateur, intrinsèques](../intrinsics/compiler-intrinsics.md)<br/>
[__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md)<br/>
[__vmx_vmresume](../intrinsics/vmx-vmresume.md)