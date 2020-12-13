---
description: 'En savoir plus sur : __svm_vmsave'
title: __svm_vmsave
ms.date: 09/02/2019
f1_keywords:
- __svm_vmsave
helpviewer_keywords:
- VMSAVE instruction
- __svm_vmsave intrinsic
ms.assetid: 617a60bd-8514-4ba1-8066-bcf4dd481030
ms.openlocfilehash: 5c0e4eb5f2d4c0f73921572811b070c8f87a2673
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333678"
---
# <a name="__svm_vmsave"></a>__svm_vmsave

**Spécifique à Microsoft**

Stocke un sous-ensemble de l’état du processeur dans le bloc de contrôle d’ordinateur virtuel spécifié (VMCB).

## <a name="syntax"></a>Syntaxe

```C
void __svm_vmsave(
   size_t VmcbPhysicalAddress
);
```

### <a name="parameters"></a>Paramètres

*VmcbPhysicalAddress*\
dans Adresse physique du VMCB.

## <a name="remarks"></a>Notes

La fonction `__svm_vmsave` est équivalente à l’instruction machine `VMSAVE` . Cette fonction prend en charge l’interaction du moniteur de machines virtuelles d’un hôte avec un système d’exploitation invité et ses applications. Pour plus d’informations, recherchez le document « AMD64 architecture Programmer’s Manual volume 2 : System Programming », numéro de document 24593, Revision 3,11 ou version ultérieure, sur le site [AMD Corporation](https://developer.amd.com/resources/developer-guides-manuals/) .

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|
|---------------|------------------|
|`__svm_vmsave`|x86, x64|

**Fichier d’en-tête** \<intrin.h>

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)\
[__svm_vmrun](../intrinsics/svm-vmrun.md)\
[__svm_vmload](../intrinsics/svm-vmload.md)
