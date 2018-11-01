---
title: Règles prédéfinies
ms.date: 11/04/2016
helpviewer_keywords:
- rules, predefined
- NMAKE program, predefined rules
- predefined rules in NMAKE
ms.assetid: 638cdc3f-4aba-4b4f-96e3-ad65b0364f12
ms.openlocfilehash: b4b8ca7b0126ca42b2144aa094e7f766f6344b2a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50609688"
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