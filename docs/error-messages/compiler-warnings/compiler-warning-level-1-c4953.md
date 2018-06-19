---
title: Compilateur avertissement (niveau 1) C4953 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4953
dev_langs:
- C++
helpviewer_keywords:
- C4953
ms.assetid: 3c4f6ac6-3976-41ab-8a27-3c41d7472ea7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0af5a16ebbf7851eceb2f2cd355f953b14c4bd38
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33293060"
---
# <a name="compiler-warning-level-1-c4953"></a>Avertissement du compilateur (niveau 1) C4953
'function' Inline a été modifié depuis le rassemblement des données de profil ; données de profil non utilisées  
  
 Quand vous avez utilisé [/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md), le compilateur a détecté un module d’entrée qui a été recompilé après `/LTCG:PGINSTRUMENT` et qui possède une fonction (***function***) qui a été modifiée et dans laquelle des séries de tests existantes ont identifié la fonction comme candidate à l’incorporation (inlining). Toutefois, en raison de la recompilation du module, la fonction ne sera plus candidate à l’incorporation (inlining).  
  
 Cet avertissement possède un caractère informatif. Pour résoudre cet avertissement, exécutez `/LTCG:PGINSTRUMENT`, relancez toutes les séries de tests, puis exécutez `/LTCG:PGOPTIMIZE`.  
  
 Si `/LTCG:PGOPTIMIZE` avait été utilisé, cet avertissement aurait été remplacé par une erreur.