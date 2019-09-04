---
title: __vmx_vmread
ms.date: 09/02/2019
f1_keywords:
- __vmx_vmread
helpviewer_keywords:
- VMREAD instruction
- __vmx_vmread intrinsic
ms.assetid: 08bdd7a0-6435-4ea6-b9a0-f592d870e5aa
ms.openlocfilehash: 409835ac29d6f2e839de62291cc5b142166a465c
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219434"
---
# <a name="__vmx_vmread"></a>__vmx_vmread

**Section spécifique à Microsoft**

Lit un champ spécifié à partir de la structure de contrôle d’ordinateur virtuel en cours (VMCS) et le place à l’emplacement spécifié.

## <a name="syntax"></a>Syntaxe

```C
unsigned char __vmx_vmread(
   size_t Field,
   size_t *FieldValue
);
```

### <a name="parameters"></a>Paramètres

*Case*\
dans Champ VMCS à lire.

*FieldValue*\
dans Pointeur vers l’emplacement où stocker la valeur lue à partir du champ VMCS spécifié par le `Field` paramètre.

## <a name="return-value"></a>Valeur de retour

|`Value`|Signification|
|-----------|-------------|
|0|L’opération a réussi.|
|1|L’opération a échoué avec l’état étendu disponible dans le `VM-instruction error field` de la VMCS actuelle.|
|2|L’opération a échoué sans état disponible.|

## <a name="remarks"></a>Notes

La fonction `__vmx_vmread` est équivalente à l’instruction machine `VMREAD` . La valeur du `Field` paramètre est un index de champ encodé qui est décrit dans la documentation Intel. Pour plus d’informations, recherchez l’annexe C de «caractéristiques techniques de la virtualisation Intel pour l’architecture Intel IA-32», sur le site [Intel Corporation](https://software.intel.com/articles/intel-sdm) .

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__vmx_vmread`|X64|

**Fichier d’en-tête** \<> Intro. h

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)\
[__vmx_vmwrite](../intrinsics/vmx-vmwrite.md)
