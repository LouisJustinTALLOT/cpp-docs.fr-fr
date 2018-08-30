---
title: Compilateur avertissement (niveau 1) C4952 | Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4952
dev_langs:
- C++
helpviewer_keywords:
- C4952
ms.assetid: 593324f0-5cfe-42fb-b221-2f71308765dd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f62f4c18380d89eb516a5fa49ef63e92ab79a6f2
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43207149"
---
# <a name="compiler-warning-level-1-c4952"></a>Avertissement du compilateur (niveau 1) C4952

> «*fonction*' : aucune donnée de profil trouvée dans la base de données du programme '*fichier_pgd*»

Lorsque vous utilisez [/LTCG : PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md), le compilateur a détecté un module d’entrée qui a été recompilé après `/LTCG:PGINSTRUMENT` et possède une nouvelle fonction (*fonction*) présent.

Cet avertissement possède un caractère informatif. Pour résoudre cet avertissement, exécutez `/LTCG:PGINSTRUMENT`, relancez toutes les séries de tests, puis exécutez `/LTCG:PGOPTIMIZE`.

Si `/LTCG:PGOPTIMIZE` avait été utilisé, cet avertissement aurait été remplacé par une erreur.