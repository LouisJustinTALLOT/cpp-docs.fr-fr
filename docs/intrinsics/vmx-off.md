---
title: __vmx_off
ms.date: 11/04/2016
f1_keywords:
- __vmx_off
helpviewer_keywords:
- VMXOFF instruction
- __vmx_off intrinsic
ms.assetid: 78a32d46-9291-406c-b982-a550855aff18
ms.openlocfilehash: 4a01752bd510f9aa8cb159c23e691c9d244145e2
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59023852"
---
# <a name="vmxoff"></a>__vmx_off

**Section spécifique à Microsoft**

Désactive l’opération des extensions (VMX) de machine virtuelle dans le processeur.

## <a name="syntax"></a>Syntaxe

```
void __vmx_off();
```

## <a name="remarks"></a>Notes

La fonction `__vmx_off` est équivalente à l’instruction machine `VMXOFF` . Cette fonction prend en charge l’interaction du moniteur de machines virtuelles d’un hôte avec un système d’exploitation invité et ses applications. Pour plus d’informations, recherchez le document, « Intel Virtualization Technical Specification pour l’IA-32 Intel Architecture, » numéro de document est C97063-002, à la [Intel Corporation](https://software.intel.com/articles/intel-sdm) site.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__vmx_off`|x86, x64|

**Fichier d’en-tête** \<intrin.h >

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[compilateur, intrinsèques](../intrinsics/compiler-intrinsics.md)