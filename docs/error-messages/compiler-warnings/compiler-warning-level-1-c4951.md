---
title: Compilateur avertissement (niveau 1) C4951 | Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4951
dev_langs:
- C++
helpviewer_keywords:
- C4951
ms.assetid: 669d8bb7-5efa-4ba9-99db-4e65addbf054
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e26c4bc176a54f063a3f9bce2faf451a9c0406f0
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43204233"
---
# <a name="compiler-warning-level-1-c4951"></a>Avertissement du compilateur (niveau 1) C4951

> «*fonction*' a été modifié depuis les données de profil, données de profil de fonction non utilisées

Une fonction d’un module d’entrée a été remplacée par [/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md), de sorte que les données de profil ne sont plus valides. Le module d’entrée a été recompilé après **/LTCG : PGINSTRUMENT** et possède une fonction (*fonction*) avec un autre flux de contrôle qu’était dans le module au moment de la  **/LTCG : PGINSTRUMENT** opération.

Cet avertissement est à caractère informatif. Pour résoudre cet avertissement, exécutez **/LTCG:PGINSTRUMENT**, relancez toutes les séries de tests, puis exécutez **/LTCG:PGOPTIMIZE**.

Si **/LTCG:PGOPTIMIZE** avait été utilisé, cet avertissement aurait été remplacé par une erreur.