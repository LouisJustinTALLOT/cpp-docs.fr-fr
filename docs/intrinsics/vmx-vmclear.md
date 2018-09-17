---
title: __vmx_vmclear | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __vmx_vmclear
dev_langs:
- C++
helpviewer_keywords:
- VMCLEAR instruction
- __vmx_vmclear intrinsic
ms.assetid: e3eb98e4-50fc-4c93-9bac-340fd1f0a466
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fd5661a2b6aa257c91babcc3d17b1babb0b4d2c2
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45707159"
---
# <a name="vmxvmclear"></a>__vmx_vmclear
**Section spécifique à Microsoft**  
  
 Initialise la structure de contrôle de machine virtuelle spécifiée (VMCS) et définit son état de lancement `Clear`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
unsigned char __vmx_vmclear(  
   unsigned __int64 *VmcsPhysicalAddress  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|*VmcsPhysicalAddress*|[in] Pointeur vers un emplacement de mémoire 64 bits qui contient l’adresse physique de la VMCS à effacer.|  
  
## <a name="return-value"></a>Valeur de retour  
  
|Value|Signification|  
|-----------|-------------|  
|0|L’opération a réussi.|  
|1|L’opération a échoué avec l’état étendu disponible dans le `VM-instruction error field` de la VMCS actuelle.|  
|2|L’opération a échoué sans état disponible.|  
  
## <a name="remarks"></a>Notes  
 Une application peut effectuer une opération VM-enter à l’aide du [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) ou [__vmx_vmresume](../intrinsics/vmx-vmresume.md) (fonction). Le [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) fonction peut être utilisée uniquement avec une VMCS dont l’état de lancement est `Clear`et le [__vmx_vmresume](../intrinsics/vmx-vmresume.md) fonction peut être utilisée uniquement avec une VMCS dont l’état de lancement est `Launched`. Par conséquent, utilisez le [__vmx_vmclear](../intrinsics/vmx-vmclear.md) fonction permettant de définir l’état de lancement d’une VMCS sur `Clear`. Utilisez le [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) (fonction) pour votre première opération VM-enter et la [__vmx_vmresume](../intrinsics/vmx-vmresume.md) (fonction) pour les opérations VM-enter ultérieures.  
  
 Le `__vmx_vmclear` fonction est équivalente à la `VMCLEAR` instruction machine. Cette fonction prend en charge l’interaction du moniteur de machines virtuelles d’un hôte avec un système d’exploitation invité et ses applications. Pour plus d’informations, recherchez le document, « Intel Virtualization Technical Specification pour l’IA-32 Intel Architecture, » numéro de document est C97063-002, à la [Intel Corporation](https://software.intel.com/en-us/articles/intel-sdm) site.  
  
## <a name="requirements"></a>Configuration requise  
  
|Intrinsèque|Architecture|  
|---------------|------------------|  
|`__vmx_vmclear`|X64|  
  
 **Fichier d’en-tête** \<intrin.h >  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)   
 [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md)   
 [__vmx_vmresume](../intrinsics/vmx-vmresume.md)