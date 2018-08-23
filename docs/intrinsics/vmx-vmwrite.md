---
title: __vmx_vmwrite | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __vmx_vmwrite
dev_langs:
- C++
helpviewer_keywords:
- __vmx_vmwrite intrinsic
- VMWRITE instruction
ms.assetid: 88139792-fd3f-4210-97ca-9d84f43a0252
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ec022fe2d317ec38bc1d9b06f459b9efc7818c92
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2018
ms.locfileid: "42541752"
---
# <a name="vmxvmwrite"></a>__vmx_vmwrite
**Section spécifique à Microsoft**  
  
 Écrit la valeur spécifiée dans le champ spécifié dans la structure de contrôle de machine virtuelle actuelle (VMCS).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
unsigned char __vmx_vmwrite(   
   size_t Field,  
   size_t FieldValue  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|[in] `Field`|Le champ VMCS dans lequel écrire.|  
|[in] `FieldValue`|Valeur à écrire dans le champ VMCS.|  
  
## <a name="return-value"></a>Valeur de retour  
 0  
 L’opération a réussi.  
  
 1  
 L’opération a échoué avec l’état étendu disponible dans le `VM-instruction error field` de la VMCS actuelle.  
  
 2  
 L’opération a échoué sans état disponible.  
  
## <a name="remarks"></a>Notes  
 Le `__vmx_vmwrite` fonction est équivalente à la `VMWRITE` instruction machine. La valeur de la `Field` paramètre est un index de champ encodé qui est décrite dans la documentation Intel. Pour plus d’informations, recherchez le document, « Intel Virtualization Technical Specification pour l’IA-32 Intel Architecture, » numéro de document est C97063-002, à la [Intel Corporation](http://go.microsoft.com/fwlink/p/?linkid=127) de site et recherchez annexe C document.  
  
## <a name="requirements"></a>Configuration requise  
  
|Intrinsèque|Architecture|  
|---------------|------------------|  
|`__vmx_vmwrite`|X64|  
  
 **Fichier d’en-tête** \<intrin.h >  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)   
 [__vmx_vmread](../intrinsics/vmx-vmread.md)