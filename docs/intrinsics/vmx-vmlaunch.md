---
title: __vmx_vmlaunch | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- __vmx_vmlaunch
dev_langs:
- C++
helpviewer_keywords:
- VMLAUNCH instruction
- __vmx_vmlaunch intrinsic
ms.assetid: 708f7c38-b7c1-4ee7-bfc4-0daeb9cc9360
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 14b7328ad2d9cfebb7416241bad3ca1e5081f2cf
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/23/2018
---
# <a name="vmxvmlaunch"></a>__vmx_vmlaunch
**Section spécifique à Microsoft**  
  
 Place l’application appelante dans un état d’opération non racine VMX (entrée de la machine virtuelle) à l’aide de la structure de contrôle de machine virtuelle actuelle (VMCS).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
unsigned char __vmx_vmlaunch(  
   void);  
```  
  
## <a name="return-value"></a>Valeur de retour  
  
|Value|Signification|  
|-----------|-------------|  
|0|L’opération a réussi.|  
|1|L’opération a échoué avec l’état étendu disponible dans le `VM-instruction error field` de la VMCS actuelle.|  
|2|L’opération a échoué sans état disponible.|  
  
## <a name="remarks"></a>Notes  
 Une application peut effectuer une opération VM-enter à l’aide du [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) ou [__vmx_vmresume](../intrinsics/vmx-vmresume.md) (fonction). Le [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) fonction peut être utilisée uniquement avec une VMCS dont l’état de lancement est `Clear`et le [__vmx_vmresume](../intrinsics/vmx-vmresume.md) fonction peut être utilisée uniquement avec une VMCS dont l’état de lancement est `Launched`. Par conséquent, utilisez le [__vmx_vmclear](../intrinsics/vmx-vmclear.md) fonction pour définir l’état de lancement d’une VMCS sur `Clear`, puis utilisez le [__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md) fonction pour votre première opération VM-enter et la [__vmx_vmresume](../intrinsics/vmx-vmresume.md) fonction pour les opérations VM-enter ultérieures.  
  
 Le `__vmx_vmlaunch` fonction est équivalente à la `VMLAUNCH` instruction machine. Cette fonction prend en charge l’interaction du moniteur de machines virtuelles d’un hôte avec un système d’exploitation invité et ses applications. Pour plus d’informations, recherchez le document, « Intel virtualisation technique spécification pour l’Architecture IA-32 Intel, » document numéro est C97063-002, sur le [Intel Corporation](http://go.microsoft.com/fwlink/p/?linkid=127) site.  
  
## <a name="requirements"></a>Configuration requise  
  
|Intrinsèque|Architecture|  
|---------------|------------------|  
|`__vmx_vmlaunch`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Fichier d’en-tête** \<intrin.h >  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)   
 [__vmx_vmresume](../intrinsics/vmx-vmresume.md)   
 [__vmx_vmclear](../intrinsics/vmx-vmclear.md)