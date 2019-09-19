---
title: __vmx_vmwrite
ms.date: 09/02/2019
f1_keywords:
- __vmx_vmwrite
helpviewer_keywords:
- __vmx_vmwrite intrinsic
- VMWRITE instruction
ms.assetid: 88139792-fd3f-4210-97ca-9d84f43a0252
ms.openlocfilehash: cdc5590858f160db24bf75ef11c8f20b204a3152
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219395"
---
# <a name="__vmx_vmwrite"></a>__vmx_vmwrite

**Section spécifique à Microsoft**

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

## <a name="return-value"></a>Valeur de retour

0\
L’opération a réussi.

1\
L’opération a échoué avec l’état étendu disponible dans le `VM-instruction error field` de la VMCS actuelle.

2\
L’opération a échoué sans état disponible.

## <a name="remarks"></a>Notes

La fonction `__vmx_vmwrite` est équivalente à l’instruction machine `VMWRITE` . La valeur du `Field` paramètre est un index de champ encodé qui est décrit dans la documentation Intel. Pour plus d’informations, recherchez l’annexe C de «caractéristiques techniques de la virtualisation Intel pour l’architecture Intel IA-32», sur le site [Intel Corporation](https://software.intel.com/articles/intel-sdm) .

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__vmx_vmwrite`|X64|

**Fichier d’en-tête** \<> Intro. h

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)\
[__vmx_vmread](../intrinsics/vmx-vmread.md)
