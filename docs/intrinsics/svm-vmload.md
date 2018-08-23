---
title: __svm_vmload | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __svm_vmload
dev_langs:
- C++
helpviewer_keywords:
- __svm_vmload intrinsic
- VMLOAD instruction
ms.assetid: b46a5592-db76-4ffc-8694-2f3494e28bed
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7ff94cddb6c286fa651b1ba728238e0d38ab3b17
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2018
ms.locfileid: "42541029"
---
# <a name="svmvmload"></a>__svm_vmload
**Section spécifique à Microsoft**  
  
 Charge un sous-ensemble de l’état du processeur à partir du bloc de contrôle de machine virtuelle spécifiée (VMCB).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __svm_vmload(  
   size_t VmcbPhysicalAddress  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|[in] `VmcbPhysicalAddress`|L’adresse physique de la VMCB.|  
  
## <a name="remarks"></a>Notes  
 Le `__svm_vmload` fonction est équivalente à la `VMLOAD` instruction machine. Cette fonction prend en charge l’interaction du moniteur de machines virtuelles d’un hôte avec un système d’exploitation invité et ses applications. Pour plus d’informations, recherchez dans le document, « manuelle Volume AMD64 Architecture pour le programmeur 2 : programmation du système, « 24593, révision 3.11, de numéro de document sur le [corporation d’AMD](http://go.microsoft.com/fwlink/p/?linkid=23746) site.  
  
## <a name="requirements"></a>Configuration requise  
  
|Intrinsèque|Architecture|  
|---------------|------------------|  
|`__svm_vmload`|x86, x64|  
  
 **Fichier d’en-tête** \<intrin.h >  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)   
 [__svm_vmrun](../intrinsics/svm-vmrun.md)   
 [__svm_vmsave](../intrinsics/svm-vmsave.md)