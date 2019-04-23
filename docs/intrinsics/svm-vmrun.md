---
title: __svm_vmrun
ms.date: 11/04/2016
f1_keywords:
- __svm_vmrun
helpviewer_keywords:
- __svm_vmrun intrinsic
- VMRUN instruction
ms.assetid: ae98a781-fc17-47b2-b40f-86fcebf1867b
ms.openlocfilehash: 40e53b2ebd54fc109b47f3067e5f89ce50b327de
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59041057"
---
# <a name="svmvmrun"></a>__svm_vmrun

**Section spécifique à Microsoft**

Démarre l’exécution du code d’invité de machine virtuelle qui correspond au bloc de contrôle de machine virtuelle spécifiée (VMCB).

## <a name="syntax"></a>Syntaxe

```
void __svm_vmrun(
   size_t VmcbPhysicalAddress
);
```

#### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*VmcbPhysicalAddress*|[in] L’adresse physique de la VMCB.|

## <a name="remarks"></a>Notes

Le `__svm_vmrun` fonction utilise une quantité minimale d’informations dans le VMCB pour commencer l’exécution du code d’invité de machine virtuelle. Utilisez le [__svm_vmsave](../intrinsics/svm-vmsave.md) ou [__svm_vmload](../intrinsics/svm-vmload.md) fonctionner si vous avez besoin de plus d’informations pour gérer une interruption complexe ou pour basculer vers un autre invité.

La fonction `__svm_vmrun` est équivalente à l’instruction machine `VMRUN` . Cette fonction prend en charge l’interaction du moniteur de machines virtuelles d’un hôte avec un système d’exploitation invité et ses applications. Pour plus d’informations, recherchez dans le document, « manuelle Volume AMD64 Architecture pour le programmeur 2 : Système de programmation, » document nombre 24593, révision 3.11 ou version ultérieure, à la [corporation d’AMD](https://developer.amd.com/resources/developer-guides-manuals/) site.

## <a name="requirements"></a>Configuration requise

|Intrinsèque|Architecture|
|---------------|------------------|
|`__svm_vmrun`|x86, x64|

**Fichier d’en-tête** \<intrin.h >

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)<br/>
[__svm_vmsave](../intrinsics/svm-vmsave.md)<br/>
[__svm_vmload](../intrinsics/svm-vmload.md)