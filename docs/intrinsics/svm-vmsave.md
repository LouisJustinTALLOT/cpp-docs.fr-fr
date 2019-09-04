---
title: __svm_vmsave
ms.date: 09/02/2019
f1_keywords:
- __svm_vmsave
helpviewer_keywords:
- VMSAVE instruction
- __svm_vmsave intrinsic
ms.assetid: 617a60bd-8514-4ba1-8066-bcf4dd481030
ms.openlocfilehash: f91efa7116a8a8e9ebe27c7e5e4e64c4f1533e9d
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219795"
---
# <a name="__svm_vmsave"></a>__svm_vmsave

**Section spécifique à Microsoft**

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

La fonction `__svm_vmsave` est équivalente à l’instruction machine `VMSAVE` . Cette fonction prend en charge l’interaction du moniteur de machines virtuelles d’un hôte avec un système d’exploitation invité et ses applications. Pour plus d’informations, recherchez le document «AMD64 architecture Programmer’s Manual volume 2: Programmation système, «document number 24593, Revision 3,11 ou version ultérieure, sur le site [AMD Corporation](https://developer.amd.com/resources/developer-guides-manuals/) .

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__svm_vmsave`|x86, x64|

**Fichier d’en-tête** \<> Intro. h

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)\
[__svm_vmrun](../intrinsics/svm-vmrun.md)\
[__svm_vmload](../intrinsics/svm-vmload.md)
