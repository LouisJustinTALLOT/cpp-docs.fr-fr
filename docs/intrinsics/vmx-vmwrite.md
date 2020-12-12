---
description: 'En savoir plus sur : __vmx_vmwrite'
title: __vmx_vmwrite
ms.date: 09/02/2019
f1_keywords:
- __vmx_vmwrite
helpviewer_keywords:
- __vmx_vmwrite intrinsic
- VMWRITE instruction
ms.assetid: 88139792-fd3f-4210-97ca-9d84f43a0252
ms.openlocfilehash: d8902d51b05fa96faf22cbb6d80400e1f67c5f3e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97257301"
---
# <a name="__vmx_vmwrite"></a>__vmx_vmwrite

**Spécifique à Microsoft**

Écrit la valeur spécifiée dans le champ spécifié dans la structure de contrôle d’ordinateur virtuel en cours (VMCS).

## <a name="syntax"></a>Syntaxe

```C
unsigned char __vmx_vmwrite(
   size_t Field,
   size_t FieldValue
);
```

### <a name="parameters"></a>Paramètres

*Case*\
dans Champ VMCS à écrire.

*FieldValue*\
dans Valeur à écrire dans le champ VMCS.

## <a name="return-value"></a>Valeur retournée

entre
L’opération a réussi.

1,0
L’opération a échoué avec l’état étendu disponible dans le `VM-instruction error field` de la VMCS actuelle.

2
L’opération a échoué sans état disponible.

## <a name="remarks"></a>Notes

La fonction `__vmx_vmwrite` est équivalente à l’instruction machine `VMWRITE` . La valeur du `Field` paramètre est un index de champ encodé qui est décrit dans la documentation Intel. Pour plus d’informations, recherchez l’annexe C de « caractéristiques techniques de la virtualisation Intel pour l’architecture Intel IA-32 », sur le site [Intel Corporation](https://software.intel.com/articles/intel-sdm) .

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|
|---------------|------------------|
|`__vmx_vmwrite`|x64|

**Fichier d’en-tête** \<intrin.h>

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)\
[__vmx_vmread](../intrinsics/vmx-vmread.md)
