---
title: __outword | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __outword
dev_langs:
- C++
helpviewer_keywords:
- __outword intrinsic
- out instruction
ms.assetid: 995f8834-0f50-4b4f-a7a2-af0e7c371cda
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8f0e827b16b9743cb6bc7fe6906b4c74c3006864
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33331134"
---
# <a name="outword"></a>__outword
**Section spécifique à Microsoft**  
  
 Génère le `out` instruction, qui envoie le mot `Data` le port d’e/s spécifié par `Port`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __outword(   
   unsigned short Port,   
   unsigned short Data   
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 [in] `Port`  
 Le port pour envoyer les données.  
  
 [in] `Data`  
 Les données à envoyer.  
  
## <a name="requirements"></a>Spécifications  
  
|Intrinsèque|Architecture|  
|---------------|------------------|  
|`__outword`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Fichier d’en-tête** \<intrin.h >  
  
## <a name="remarks"></a>Notes  
 Cette routine est disponible uniquement en tant qu'intrinsèque.  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)