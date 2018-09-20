---
title: __vmx_on | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __vmx_on
dev_langs:
- C++
helpviewer_keywords:
- VMXON instruction
- __vmx_on intrinsic
ms.assetid: 16804991-6a75-4adf-8ec2-bc95acfa4801
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 21ac0eb53b75aece9d717b85b9625a69741a2be9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46379753"
---
# <a name="vmxon"></a>__vmx_on

**Section spécifique à Microsoft**

Active l’opération des extensions (VMX) de machine virtuelle dans le processeur.

## <a name="syntax"></a>Syntaxe

```
unsigned char __vmx_on(
   unsigned __int64 *VmsSupportPhysicalAddress
);
```

#### <a name="parameters"></a>Paramètres

*VmsSupportPhysicalAddress*<br/>
[in] Pointeur vers une adresse physique 64 bits qui pointe vers une structure de contrôle de la machine virtuelle (VMCS).

## <a name="return-value"></a>Valeur de retour

|Value|Signification|
|-----------|-------------|
|0|L’opération a réussi.|
|1|L’opération a échoué avec l’état étendu disponible dans le `VM-instruction error field` de la VMCS actuelle.|
|2|L’opération a échoué sans état disponible.|

## <a name="remarks"></a>Notes

Le `__vmx_on` fonction correspond à la `VMXON` instruction machine. Cette fonction prend en charge l’interaction du moniteur de machines virtuelles d’un hôte avec un système d’exploitation invité et ses applications. Pour plus d’informations, recherchez le document, « Intel Virtualization Technical Specification pour l’IA-32 Intel Architecture, » numéro de document est C97063-002, à la [Intel Corporation](https://software.intel.com/en-us/articles/intel-sdm) site.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__vmx_on`|X64|

**Fichier d’en-tête** \<intrin.h >

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)