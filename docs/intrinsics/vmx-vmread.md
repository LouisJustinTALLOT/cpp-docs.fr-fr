---
title: __vmx_vmread
ms.date: 11/04/2016
f1_keywords:
- __vmx_vmread
helpviewer_keywords:
- VMREAD instruction
- __vmx_vmread intrinsic
ms.assetid: 08bdd7a0-6435-4ea6-b9a0-f592d870e5aa
ms.openlocfilehash: 5c7b72ba3bf1bd60324704b774bcedaf5612240f
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59028384"
---
# <a name="vmxvmread"></a>__vmx_vmread

**Section spécifique à Microsoft**

Lit un champ spécifié à partir de la structure de contrôle de machine virtuelle actuelle (VMCS) et le place dans l’emplacement spécifié.

## <a name="syntax"></a>Syntaxe

```
unsigned char __vmx_vmread(
   size_t Field,
   size_t *FieldValue
);
```

#### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*Champ*|[in] Le champ VMCS à lire.|
|*FieldValue*|[in] Un pointeur vers l’emplacement pour stocker la valeur lire à partir du champ VMCS spécifié par le `Field` paramètre.|

## <a name="return-value"></a>Valeur de retour

|Value|Signification|
|-----------|-------------|
|0|L’opération a réussi.|
|1|L’opération a échoué avec l’état étendu disponible dans le `VM-instruction error field` de la VMCS actuelle.|
|2|L’opération a échoué sans état disponible.|

## <a name="remarks"></a>Notes

La fonction `__vmx_vmread` est équivalente à l’instruction machine `VMREAD` . La valeur de la `Field` paramètre est un index de champ encodé qui est décrite dans la documentation Intel. Pour plus d’informations, recherchez le document, « Intel Virtualization Technical Specification pour l’IA-32 Intel Architecture, » numéro de document est C97063-002, à la [Intel Corporation](https://software.intel.com/articles/intel-sdm) de site, puis consultez l’annexe C de ce document .

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__vmx_vmread`|X64|

**Fichier d’en-tête** \<intrin.h >

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[compilateur, intrinsèques](../intrinsics/compiler-intrinsics.md)<br/>
[__vmx_vmwrite](../intrinsics/vmx-vmwrite.md)