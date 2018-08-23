---
title: __vmx_vmread | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __vmx_vmread
dev_langs:
- C++
helpviewer_keywords:
- VMREAD instruction
- __vmx_vmread intrinsic
ms.assetid: 08bdd7a0-6435-4ea6-b9a0-f592d870e5aa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eee9c82487159b9233999d17ff36c4aad3ef6445
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2018
ms.locfileid: "42545812"
---
# <a name="vmxvmread"></a>__vmx_vmread
**Section spécifique à Microsoft**  
  
 Lit un champ spécifié à partir de la structure de contrôle de machine virtuelle actuelle (VMCS) et le place dans l’emplacement spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
unsigned char __vmx_vmread(  
   size_t Field,  
   size_t *FieldValue  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|[in] `Field`|Le champ VMCS à lire.|  
|[in] `FieldValue`|Un pointeur vers l’emplacement pour stocker la valeur lire à partir du champ VMCS spécifié par le `Field` paramètre.|  
  
## <a name="return-value"></a>Valeur de retour  
  
|Value|Signification|  
|-----------|-------------|  
|0|L’opération a réussi.|  
|1|L’opération a échoué avec l’état étendu disponible dans le `VM-instruction error field` de la VMCS actuelle.|  
|2|L’opération a échoué sans état disponible.|  
  
## <a name="remarks"></a>Notes  
 Le `__vmx_vmread` fonction est équivalente à la `VMREAD` instruction machine. La valeur de la `Field` paramètre est un index de champ encodé qui est décrite dans la documentation Intel. Pour plus d’informations, recherchez le document, « Intel Virtualization Technical Specification pour l’IA-32 Intel Architecture, » numéro de document est C97063-002, à la [Intel Corporation](http://go.microsoft.com/fwlink/p/?linkid=127) de site, puis consultez l’annexe C de ce document .  
  
## <a name="requirements"></a>Configuration requise  
  
|Intrinsèque|Architecture|  
|---------------|------------------|  
|`__vmx_vmread`|X64|  
  
 **Fichier d’en-tête** \<intrin.h >  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)   
 [__vmx_vmwrite](../intrinsics/vmx-vmwrite.md)