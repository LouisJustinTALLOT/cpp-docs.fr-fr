---
title: __vmx_vmwrite
ms.date: 11/04/2016
f1_keywords:
- __vmx_vmwrite
helpviewer_keywords:
- __vmx_vmwrite intrinsic
- VMWRITE instruction
ms.assetid: 88139792-fd3f-4210-97ca-9d84f43a0252
ms.openlocfilehash: c5c6e0edcb3136986cfd8e05f3d5217b3d021fa7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50529244"
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

La fonction `__vmx_vmwrite` est équivalente à l’instruction machine `VMWRITE` . La valeur de la `Field` paramètre est un index de champ encodé qui est décrite dans la documentation Intel. Pour plus d’informations, recherchez le document, « Intel Virtualization Technical Specification pour l’IA-32 Intel Architecture, » numéro de document est C97063-002, à la [Intel Corporation](https://software.intel.com/articles/intel-sdm) de site et recherchez annexe C document.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__vmx_vmwrite`|X64|

**Fichier d’en-tête** \<intrin.h >

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)<br/>
[__vmx_vmread](../intrinsics/vmx-vmread.md)