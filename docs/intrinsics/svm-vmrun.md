---
title: __svm_vmrun
ms.date: 09/02/2019
f1_keywords:
- __svm_vmrun
helpviewer_keywords:
- __svm_vmrun intrinsic
- VMRUN instruction
ms.assetid: ae98a781-fc17-47b2-b40f-86fcebf1867b
ms.openlocfilehash: f23df894cc8ad1c270c4c0acbc97cab727e47d93
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219821"
---
# <a name="__svm_vmrun"></a>__svm_vmrun

**Section spécifique à Microsoft**

Démarre l’exécution du code invité de l’ordinateur virtuel qui correspond au bloc de contrôle d’ordinateur virtuel spécifié (VMCB).

## <a name="syntax"></a>Syntaxe

```C
void __svm_vmrun(
   size_t VmcbPhysicalAddress
);
```

### <a name="parameters"></a>Paramètres

*VmcbPhysicalAddress*\
dans Adresse physique du VMCB.

## <a name="remarks"></a>Notes

La `__svm_vmrun` fonction utilise une quantité minimale d’informations dans VMCB pour commencer à exécuter le code invité de l’ordinateur virtuel. Utilisez la fonction [__svm_vmsave](../intrinsics/svm-vmsave.md) ou [__svm_vmload](../intrinsics/svm-vmload.md) si vous avez besoin d’informations supplémentaires pour gérer une interruption complexe, ou pour basculer vers un autre invité.

La fonction `__svm_vmrun` est équivalente à l’instruction machine `VMRUN` . Cette fonction prend en charge l’interaction du moniteur de machines virtuelles d’un hôte avec un système d’exploitation invité et ses applications. Pour plus d’informations, recherchez le document «AMD64 architecture Programmer’s Manual volume 2: Programmation système, «document number 24593, Revision 3,11 ou version ultérieure, sur le site [AMD Corporation](https://developer.amd.com/resources/developer-guides-manuals/) .

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__svm_vmrun`|x86, x64|

**Fichier d’en-tête** \<> Intro. h

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)\
[__svm_vmsave](../intrinsics/svm-vmsave.md)\
[__svm_vmload](../intrinsics/svm-vmload.md)
