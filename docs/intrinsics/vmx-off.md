---
title: __vmx_off
ms.date: 09/02/2019
f1_keywords:
- __vmx_off
helpviewer_keywords:
- VMXOFF instruction
- __vmx_off intrinsic
ms.assetid: 78a32d46-9291-406c-b982-a550855aff18
ms.openlocfilehash: 226b5111c2f4f6771ac75d165c80c3e8ae2336af
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219584"
---
# <a name="__vmx_off"></a>__vmx_off

**Section spécifique à Microsoft**

Désactive l’opération VMX (Virtual Machine extensions) dans le processeur.

## <a name="syntax"></a>Syntaxe

```C
void __vmx_off();
```

## <a name="remarks"></a>Notes

La fonction `__vmx_off` est équivalente à l’instruction machine `VMXOFF` . Cette fonction prend en charge l’interaction du moniteur de machines virtuelles d’un hôte avec un système d’exploitation invité et ses applications. Pour plus d’informations, recherchez le document «Intel Virtualization Technical Specification for the IA-32 Intel architecture», document number est c97063-002, sur le site [Intel Corporation](https://software.intel.com/articles/intel-sdm) .

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__vmx_off`|x86, x64|

**Fichier d’en-tête** \<> Intro. h

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)
