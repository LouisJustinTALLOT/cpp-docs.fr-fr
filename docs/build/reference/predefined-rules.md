---
description: En savoir plus sur les règles prédéfinies
title: Règles prédéfinies
ms.date: 11/04/2016
helpviewer_keywords:
- rules, predefined
- NMAKE program, predefined rules
- predefined rules in NMAKE
ms.assetid: 638cdc3f-4aba-4b4f-96e3-ad65b0364f12
ms.openlocfilehash: 302c649980050764d1bb2f0e9a43b785d0175a09
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97225828"
---
# <a name="predefined-rules"></a>Règles prédéfinies

Les règles d’inférence prédéfinies utilisent les macros de commande et d’options fournies par NMAKE.

|Règle|Commande|Default<br /><br /> action|Batch<br /><br /> Règle|La plateforme NMAKE s’exécute sur|
|----------|-------------|------------------------|--------------------|----------------------------|
|.asm.exe|$ (AS) $ (AFLAGS) $<|ml $<|non|x86|
|. asm. obj|$ (AS) $ (AFLAGS)/c $<|ml/c $<|Oui|x86|
|.asm.exe|$ (AS) $ (AFLAGS) $<|ml64 $<|non|x64|
|. asm. obj|$ (AS) $ (AFLAGS)/c $<|ml64/c $<|Oui|x64|
|.c.exe|$ (CC) $ (CFLAGS) $<|< CL $|non|all|
|. c. obj|$ (CC) $ (CFLAGS)/c $<|cl/c $<|Oui|all|
|.cc.exe|$ (CC) $ (CFLAGS) $<|< CL $|non|all|
|. cc. obj|$ (CC) $ (CFLAGS)/c $<|cl/c $<|Oui|all|
|.cpp.exe|$ (CPP) $ (CPPFLAGS) $<|< CL $|non|all|
|. cpp. obj|$ (CPP) $ (CPPFLAGS)/c $<|cl/c $<|Oui|all|
|.cxx.exe|$ (CXX) $ (CXXFLAGS) $<|< CL $|non|all|
|. cxx. obj|$ (CXX) $ (CXXFLAGS)/c $<|cl/c $<|Oui|all|
|. rc. res|$ (RC) $ (RFLAGS)/r $<|RC/r $<|non|all|

## <a name="see-also"></a>Voir aussi

[Règles d’inférence](inference-rules.md)
