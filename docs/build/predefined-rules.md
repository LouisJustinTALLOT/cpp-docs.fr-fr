---
title: Des règles prédéfinies | Microsoft Docs
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
ms.openlocfilehash: 5a34d3d0a601b2e160f988e0fed34a630612d839
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45719249"
---
# <a name="predefined-rules"></a>Règles prédéfinies

Règles d’inférence prédéfinies utilisent les macros de commande et les options fournies par NMAKE.

|Règle|Commande|Par défaut<br /><br /> action|Batch<br /><br /> Règle|Plateforme nmake s’exécute sur|
|----------|-------------|------------------------|--------------------|----------------------------|
|. asm.exe|$(AS) $(AFLAGS) $&LT;|ml $<|Non|x86|
|. asm.obj|$(AS) $(AFLAGS) /c $<|ml /c $<|oui|x86|
|. asm.exe|$(AS) $(AFLAGS) $&LT;|ml64 $<|Non|X64|
|. asm.obj|$(AS) $(AFLAGS) /c $<|ml64 /c $<|oui|X64|
|. c.exe|$(CC) $(CFLAGS) $&LT;|CL $<|non|all|
|. c.obj|$(CC) $(CFLAGS) /c $<|cl /c $<|oui|all|
|. cc.exe|$(CC) $(CFLAGS) $&LT;|CL $<|non|all|
|. cc.obj|$(CC) $(CFLAGS) /c $<|cl /c $<|oui|all|
|. cpp.exe|$(CPP) $(CPPFLAGS) $&LT;|CL $<|non|all|
|. cpp.obj|$(CPP) $(CPPFLAGS) /c $<|cl /c $<|oui|all|
|. cxx.exe|$(CXX) $(CXXFLAGS) $&LT;|CL $<|non|all|
|. cxx.obj|$(CXX) $(CXXFLAGS) /c $<|cl /c $<|oui|all|
|. rc.res|$(RC) $(RFLAGS) /r $<|/r rc $<|Non|all|

## <a name="see-also"></a>Voir aussi

[Règles d’inférence](../build/inference-rules.md)