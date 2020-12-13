---
description: 'En savoir plus sur : __svm_vmrun'
title: __svm_vmrun
ms.date: 09/02/2019
f1_keywords:
- __svm_vmrun
helpviewer_keywords:
- __svm_vmrun intrinsic
- VMRUN instruction
ms.assetid: ae98a781-fc17-47b2-b40f-86fcebf1867b
ms.openlocfilehash: c01716e496513aa11132fdfc95235a39c7277279
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333700"
---
# <a name="__svm_vmrun"></a>__svm_vmrun

**Spécifique à Microsoft**

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

La fonction `__svm_vmrun` est équivalente à l’instruction machine `VMRUN` . Cette fonction prend en charge l’interaction du moniteur de machines virtuelles d’un hôte avec un système d’exploitation invité et ses applications. Pour plus d’informations, recherchez le document « AMD64 architecture Programmer’s Manual volume 2 : System Programming », numéro de document 24593, Revision 3,11 ou version ultérieure, sur le site [AMD Corporation](https://developer.amd.com/resources/developer-guides-manuals/) .

## <a name="requirements"></a>Spécifications

|Intrinsic|Architecture|
|---------------|------------------|
|`__svm_vmrun`|x86, x64|

**Fichier d’en-tête** \<intrin.h>

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)\
[__svm_vmsave](../intrinsics/svm-vmsave.md)\
[__svm_vmload](../intrinsics/svm-vmload.md)
