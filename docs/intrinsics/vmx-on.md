---
title: __vmx_on
ms.date: 09/02/2019
f1_keywords:
- __vmx_on
helpviewer_keywords:
- VMXON instruction
- __vmx_on intrinsic
ms.assetid: 16804991-6a75-4adf-8ec2-bc95acfa4801
ms.openlocfilehash: b6041711d9b6806362b856475151f2c4f63750cb
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219579"
---
# <a name="__vmx_on"></a>__vmx_on

**Section spécifique à Microsoft**

Active l’opération des extensions de machine virtuelle (VMX) dans le processeur.

## <a name="syntax"></a>Syntaxe

```C
unsigned char __vmx_on(
   unsigned __int64 *VmsSupportPhysicalAddress
);
```

### <a name="parameters"></a>Paramètres

*VmsSupportPhysicalAddress*\
dans Pointeur vers une adresse physique 64 bits qui pointe vers une structure de contrôle de machine virtuelle (VMCS).

## <a name="return-value"></a>Valeur de retour

|Valeur|Signification|
|-----------|-------------|
|0|L’opération a réussi.|
|1|L’opération a échoué avec l’état étendu disponible dans le `VM-instruction error field` de la VMCS actuelle.|
|2|L’opération a échoué sans état disponible.|

## <a name="remarks"></a>Notes

La `__vmx_on` fonction correspond à l' `VMXON` instruction machine. Cette fonction prend en charge l’interaction du moniteur de machines virtuelles d’un hôte avec un système d’exploitation invité et ses applications. Pour plus d’informations, recherchez le document «Intel Virtualization Technical Specification for the IA-32 Intel architecture», document number est c97063-002, sur le site [Intel Corporation](https://software.intel.com/articles/intel-sdm) .

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__vmx_on`|X64|

**Fichier d’en-tête** \<> Intro. h

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
