---
title: __svm_vmload
ms.date: 09/02/2019
f1_keywords:
- __svm_vmload
helpviewer_keywords:
- __svm_vmload intrinsic
- VMLOAD instruction
ms.assetid: b46a5592-db76-4ffc-8694-2f3494e28bed
ms.openlocfilehash: da6ca9786b9c7e5041b9a8ca908d567b16176436
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219813"
---
# <a name="__svm_vmload"></a>__svm_vmload

**Section spécifique à Microsoft**

Charge un sous-ensemble de l’état du processeur à partir du bloc de contrôle d’ordinateur virtuel spécifié (VMCB).

## <a name="syntax"></a>Syntaxe

```C
void __svm_vmload(
   size_t VmcbPhysicalAddress
);
```

### <a name="parameters"></a>Paramètres

*VmcbPhysicalAddress*\
dans Adresse physique du VMCB.

## <a name="remarks"></a>Notes

La fonction `__svm_vmload` est équivalente à l’instruction machine `VMLOAD` . Cette fonction prend en charge l’interaction du moniteur de machines virtuelles d’un hôte avec un système d’exploitation invité et ses applications. Pour plus d’informations, recherchez le document «AMD64 architecture Programmer’s Manual volume 2: Programmation système, «document number 24593, Revision 3,11, sur le site [AMD Corporation](https://developer.amd.com/resources/developer-guides-manuals/) .

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__svm_vmload`|x86, x64|

**Fichier d’en-tête** \<> Intro. h

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)\
[__svm_vmrun](../intrinsics/svm-vmrun.md)\
[__svm_vmsave](../intrinsics/svm-vmsave.md)
