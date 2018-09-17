---
title: __svm_invlpga | Microsoft Docs
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
ms.openlocfilehash: c2f962ec4a348cca7ffdf43852cb01d673f3fb18
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45706600"
---
# <a name="svminvlpga"></a>__svm_invlpga
**Section spécifique à Microsoft**  
  
 Invalide l’entrée de mappage d’adresse dans la mémoire tampon de l’ordinateur traduction ITLB. Les paramètres spécifient l’adresse virtuelle et l’identificateur d’espace d’adresse de la page à invalider.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __svm_invlpga(  
     void *Va,  
     int ASID);  
```  
  
#### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|*Évaluation des vulnérabilités*|[in] L’adresse virtuelle de la page à invalider.|  
|*ASID*|[in] L’identificateur d’espace adresse (ASID) de la page à invalider.|  
  
## <a name="remarks"></a>Notes  
 Le `__svm_invlpga` fonction est équivalente à la `INVLPGA` instruction machine. Cette fonction prend en charge l’interaction du moniteur de machines virtuelles d’un hôte avec un système d’exploitation invité et ses applications. Pour plus d’informations, recherchez dans le document, « manuelle Volume AMD64 Architecture pour le programmeur 2 : programmation du système, « 24593, révision 3.11, de numéro de document sur le [corporation d’AMD](https://developer.amd.com/resources/developer-guides-manuals/) site.  
  
## <a name="requirements"></a>Configuration requise  
  
|Intrinsèque|Architecture|  
|---------------|------------------|  
|`__svm_invlpga`|x86, x64|  
  
 **Fichier d’en-tête** \<intrin.h >  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)