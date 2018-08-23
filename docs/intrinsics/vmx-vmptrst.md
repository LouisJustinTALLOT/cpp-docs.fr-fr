---
title: __vmx_vmptrst | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __vmx_vmptrst
dev_langs:
- C++
helpviewer_keywords:
- __vmx_vmptrst intrinsic
- VMPTRST instruction
ms.assetid: 8dc66e47-03a0-41b0-8e25-c1485f42817a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e2997ed93de7291c22ae4f147bdd2392b71385e6
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2018
ms.locfileid: "42541031"
---
# <a name="vmxvmptrst"></a>__vmx_vmptrst
**Section spécifique à Microsoft**  
  
 Stocke le pointeur vers la structure de contrôle de machine virtuelle actuelle (VMCS) à l’adresse spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __vmx_vmptrst(   
   unsigned __int64 *VmcsPhysicalAddress   
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 [in] *`VmcsPhysicalAddress`  
 L’adresse où se trouve le pointeur de la VMCS actuels.  
  
## <a name="remarks"></a>Notes  
 Le pointeur de la VMCS est une adresse physique 64 bits.  
  
 Le `__vmx_vmptrst` fonction est équivalente à la `VMPTRST` instruction machine. Cette fonction prend en charge l’interaction du moniteur de machines virtuelles d’un hôte avec un système d’exploitation invité et ses applications. Pour plus d’informations, recherchez le document, « Intel Virtualization Technical Specification pour l’IA-32 Intel Architecture, » numéro de document est C97063-002, à la [Intel Corporation](http://go.microsoft.com/fwlink/p/?linkid=127) site.  
  
## <a name="requirements"></a>Configuration requise  
  
|Intrinsèque|Architecture|  
|---------------|------------------|  
|`__vmx_vmptrst`|x86, x64|  
  
 **Fichier d’en-tête** \<intrin.h >  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)   
 [__vmx_vmptrld](../intrinsics/vmx-vmptrld.md)