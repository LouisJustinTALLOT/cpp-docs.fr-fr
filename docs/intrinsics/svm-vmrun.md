---
title: __svm_vmrun | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __svm_vmrun
dev_langs:
- C++
helpviewer_keywords:
- __svm_vmrun intrinsic
- VMRUN instruction
ms.assetid: ae98a781-fc17-47b2-b40f-86fcebf1867b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3777492212bbff368902acf589f0a3c46ea4ac18
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45718670"
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
  
 Le `__svm_vmrun` fonction est équivalente à la `VMRUN` instruction machine. Cette fonction prend en charge l’interaction du moniteur de machines virtuelles d’un hôte avec un système d’exploitation invité et ses applications. Pour plus d’informations, recherchez dans le document, « manuelle Volume AMD64 Architecture pour le programmeur 2 : programmation du système, « numéro 24593, révision 3.11 ou version ultérieure, à la [corporation d’AMD](https://developer.amd.com/resources/developer-guides-manuals/) site.  
  
## <a name="requirements"></a>Configuration requise  
  
|Intrinsèque|Architecture|  
|---------------|------------------|  
|`__svm_vmrun`|x86, x64|  
  
 **Fichier d’en-tête** \<intrin.h >  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)   
 [__svm_vmsave](../intrinsics/svm-vmsave.md)   
 [__svm_vmload](../intrinsics/svm-vmload.md)