---
title: Compilateur avertissement (niveau 1) C4627 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4627
dev_langs:
- C++
helpviewer_keywords:
- C4627
ms.assetid: 8840f3e6-b496-423a-8635-eb55d5f854a2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dcde9e6707465fd95dbcb10e073a852624f0de0a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33284184"
---
# <a name="compiler-warning-level-1-c4627"></a>Avertissement du compilateur (niveau 1) C4627
'\<identificateur >': ignoré lors de la recherche une utilisation d’en-tête précompilé  
  
 Lors de la recherche de l’emplacement où un en-tête précompilé est utilisé, le compilateur a rencontré un `#include` directive pour le  *\<identificateur >* fichier include. Le compilateur ignore le `#include` directive, mais il émet l’avertissement **C4627** si l’en-tête précompilé ne contient pas déjà le  *\<identificateur >* fichier include.  
  
## <a name="see-also"></a>Voir aussi  
 [Création de fichiers d’en-tête précompilé](../../build/reference/creating-precompiled-header-files.md)