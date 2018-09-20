---
title: __vmx_vmwrite | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __vmx_vmwrite
dev_langs:
- C++
helpviewer_keywords:
- __vmx_vmwrite intrinsic
- VMWRITE instruction
ms.assetid: 88139792-fd3f-4210-97ca-9d84f43a0252
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1a3a503528f5e12fbfafab8cb8e71711ba0650c6
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46396842"
---
# <a name="vmxvmwrite"></a>__vmx_vmwrite

**Section spécifique à Microsoft**

Écrit la valeur spécifiée dans le champ spécifié dans la structure de contrôle de machine virtuelle actuelle (VMCS).

## <a name="syntax"></a>Syntaxe

```
unsigned char __vmx_vmwrite( 
   size_t Field,
   size_t FieldValue
);
```

#### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*Champ*|[in] Le champ VMCS dans lequel écrire.|
|*FieldValue*|[in] Valeur à écrire dans le champ VMCS.|

## <a name="return-value"></a>Valeur de retour

0 de l’opération a réussi.

1. l’opération a échoué avec l’état étendu disponible dans le `VM-instruction error field` de la VMCS actuelle.

2. l’opération a échoué sans état disponible.

## <a name="remarks"></a>Notes

Le `__vmx_vmwrite` fonction est équivalente à la `VMWRITE` instruction machine. La valeur de la `Field` paramètre est un index de champ encodé qui est décrite dans la documentation Intel. Pour plus d’informations, recherchez le document, « Intel Virtualization Technical Specification pour l’IA-32 Intel Architecture, » numéro de document est C97063-002, à la [Intel Corporation](https://software.intel.com/en-us/articles/intel-sdm) de site et recherchez annexe C document.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__vmx_vmwrite`|X64|

**Fichier d’en-tête** \<intrin.h >

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)<br/>
[__vmx_vmread](../intrinsics/vmx-vmread.md)