---
description: 'En savoir plus sur : __vmx_off'
title: __vmx_off
ms.date: 09/02/2019
f1_keywords:
- __vmx_off
helpviewer_keywords:
- VMXOFF instruction
- __vmx_off intrinsic
ms.assetid: 78a32d46-9291-406c-b982-a550855aff18
ms.openlocfilehash: d36b9079165dd68b207658d6141bdf11bd9747cb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333588"
---
# <a name="__vmx_off"></a>__vmx_off

**Spécifique à Microsoft**

Désactive l’opération VMX (Virtual Machine extensions) dans le processeur.

## <a name="syntax"></a>Syntaxe

```C
void __vmx_off();
```

## <a name="remarks"></a>Notes

La fonction `__vmx_off` est équivalente à l’instruction machine `VMXOFF` . Cette fonction prend en charge l’interaction du moniteur de machines virtuelles d’un hôte avec un système d’exploitation invité et ses applications. Pour plus d’informations, recherchez le document « Intel Virtualization Technical Specification for the IA-32 Intel architecture », document number est c97063-002, sur le site [Intel Corporation](https://software.intel.com/articles/intel-sdm) .

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|
|---------------|------------------|
|`__vmx_off`|x86, x64|

**Fichier d’en-tête** \<intrin.h>

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
