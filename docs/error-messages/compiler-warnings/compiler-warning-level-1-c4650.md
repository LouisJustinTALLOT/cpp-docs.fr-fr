---
title: Compilateur avertissement (niveau 1) C4650 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4650
dev_langs:
- C++
helpviewer_keywords:
- C4650
ms.assetid: 3190b3e3-dcd6-4846-939b-f900ab652b2a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6cb1c9979141e7958b6c2802aaf321efe41e9570
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33283083"
---
# <a name="compiler-warning-level-1-c4650"></a>Avertissement du compilateur (niveau 1) C4650
informations de débogage pas dans l’en-tête précompilé ; Seuls les symboles globaux de l’en-tête seront disponibles  
  
 Le fichier d’en-tête précompilé n’a pas été compilé avec les informations de débogage symboliques à Microsoft.  
  
 Lorsque lié, le fichier exécutable ou DLL de bibliothèque résultant n’inclura pas les informations de débogage pour les symboles locaux contenus dans l’en-tête précompilé.  
  
 Cet avertissement peut être évité en recompilant le fichier d’en-tête précompilé avec le [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) option de ligne de commande.