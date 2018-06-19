---
title: Règles prédéfinies | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- rules, predefined
- NMAKE program, predefined rules
- predefined rules in NMAKE
ms.assetid: 638cdc3f-4aba-4b4f-96e3-ad65b0364f12
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d0a21847bb9363099fa64825b45a90003de053da
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32369758"
---
# <a name="predefined-rules"></a>Règles prédéfinies
Règles d’inférence prédéfinies utilisent les macros de commande et les options fournies par NMAKE.  
  
|Règle|Commande|Par défaut<br /><br /> action|Batch<br /><br /> Règle|La plateforme nmake s’exécute sur|  
|----------|-------------|------------------------|--------------------|----------------------------|  
|. asm.exe|$(AS) $(AFLAGS) $&LT;|ml $<|Non|x86|  
|. asm.obj|$(AS) $(AFLAGS) /c $<|ml /c $<|oui|x86|  
|. asm.exe|$(AS) $(AFLAGS) $&LT;|ml64 $<|Non|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|. asm.obj|$(AS) $(AFLAGS) /c $<|ml64 /c $<|oui|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|. c.exe|$(CC) $(CFLAGS) $&LT;|CL $<|non|toutes les|  
|. c.obj|$(CC) $(CFLAGS) /c $<|cl /c $<|oui|toutes les|  
|. cc.exe|$(CC) $(CFLAGS) $&LT;|CL $<|non|toutes les|  
|. cc.obj|$(CC) $(CFLAGS) /c $<|cl /c $<|oui|toutes les|  
|. cpp.exe|$(CPP) $(CPPFLAGS) $&LT;|CL $<|non|toutes les|  
|. cpp.obj|$(CPP) $(CPPFLAGS) /c $<|cl /c $<|oui|toutes les|  
|. cxx.exe|$(CXX) $(CXXFLAGS) $&LT;|CL $<|non|toutes les|  
|. cxx.obj|$(CXX) $(CXXFLAGS) /c $<|cl /c $<|oui|toutes les|  
|. rc.res|$(RC) $(RFLAGS) /r $<|/r rc $<|Non|toutes les|  
  
## <a name="see-also"></a>Voir aussi  
 [Règles d’inférence](../build/inference-rules.md)