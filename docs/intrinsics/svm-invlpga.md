---
title: __svm_invlpga | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __svm_invlpga
dev_langs:
- C++
helpviewer_keywords:
- __svm_invlpga intrinsic
- INVLPGA instruction
ms.assetid: aa6578ce-8278-464b-8815-a0fc45330915
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2e48fc39fd972387ee9fbbe587dc53bf61f2ae59
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33330393"
---
# <a name="svminvlpga"></a>__svm_invlpga
**Section spécifique à Microsoft**  
  
 Invalide l’entrée de mappage d’adresse dans la mémoire tampon de lecture parallèle de conversion de l’ordinateur. Les paramètres spécifient l’adresse virtuelle et l’identificateur d’espace d’adresse de la page à invalider.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __svm_invlpga(  
     void *Va,  
     int ASID);  
```  
  
#### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|[in] `Va`|L’adresse virtuelle de la page à invalider.|  
|[in] `ASID`|L’identificateur d’espace adresse (ASID) de la page à invalider.|  
  
## <a name="remarks"></a>Notes  
 Le `__svm_invlpga` fonction est équivalente à la `INVLPGA` instruction machine. Cette fonction prend en charge l’interaction du moniteur de machines virtuelles d’un hôte avec un système d’exploitation invité et ses applications. Pour plus d’informations, recherchez le document, « de Volume manuelle AMD64 Architecture programmeur 2 : programmation du système, « numéro 24593, 3.11, de révision du document à la [corporation d’AMD](http://go.microsoft.com/fwlink/p/?linkid=23746) site.  
  
## <a name="requirements"></a>Spécifications  
  
|Intrinsèque|Architecture|  
|---------------|------------------|  
|`__svm_invlpga`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Fichier d’en-tête** \<intrin.h >  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)