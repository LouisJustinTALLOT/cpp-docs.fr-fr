---
title: __vmx_vmptrld | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __vmx_vmptrld
dev_langs:
- C++
helpviewer_keywords:
- __vmx_vmptrld intrinsic
- VMPTRLD instruction
ms.assetid: 95c9ec5b-1a81-41ba-983e-327bd6a65fcb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4f3304106662d290a208545061bf9f71b7f30c10
ms.sourcegitcommit: a738519aa491a493a8f213971354356c0e6a5f3a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2018
ms.locfileid: "48820943"
---
# <a name="vmxvmptrld"></a>__vmx_vmptrld

**Section spécifique à Microsoft**

Charge le pointeur à la structure de contrôle de machine virtuelle actuelle (VMCS) à partir de l’adresse spécifiée.

## <a name="syntax"></a>Syntaxe

```
int __vmx_vmptrld( 
   unsigned __int64 *VmcsPhysicalAddress 
);
```

#### <a name="parameters"></a>Paramètres

[in] *`VmcsPhysicalAddress` l’adresse où se trouve le pointeur de la VMCS.

## <a name="return-value"></a>Valeur de retour

0 de l’opération a réussi.

1. l’opération a échoué avec l’état étendu disponible dans le `VM-instruction error field` de la VMCS actuelle.

2. l’opération a échoué sans état disponible.

## <a name="remarks"></a>Notes

Le pointeur de la VMCS est une adresse physique 64 bits.

Le `__vmx_vmptrld` fonction est équivalente à la `VMPTRLD` instruction machine. Cette fonction prend en charge l’interaction du moniteur de machines virtuelles d’un hôte avec un système d’exploitation invité et ses applications. Pour plus d’informations, recherchez le document, « Intel Virtualization Technical Specification pour l’IA-32 Intel Architecture, » numéro de document est C97063-002, à la [Intel Corporation](https://software.intel.com/articles/intel-sdm) site.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__vmx_vmptrld`|X64|

**Fichier d’en-tête** \<intrin.h >

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)<br/>
[__vmx_vmptrst](../intrinsics/vmx-vmptrst.md)