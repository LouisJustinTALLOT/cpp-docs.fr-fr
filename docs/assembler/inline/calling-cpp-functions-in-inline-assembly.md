---
title: Appel de fonctions C++ dans l’Assembly Inline | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- functions [C++], calling in inline assembly
- function calls, C++ functions
- function calls, in inline assembly
- Visual C++, functions
- inline assembly, calling functions
- __asm keyword [C++], calling functions
ms.assetid: 1f0d1eb3-54cf-45d5-838d-958188616b38
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ffbd8038d240bc2ab0240d172d914790b6ca02ab
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2018
ms.locfileid: "32049621"
---
# <a name="calling-c-functions-in-inline-assembly"></a>Appel des fonctions C++ dans l'assembly inline
## <a name="microsoft-specific"></a>Section spécifique à Microsoft  
 Un bloc `__asm` peut appeler uniquement des fonctions C++ globales qui ne sont pas surchargées. Si vous appelez une fonction C++ globale surchargée ou une fonction membre C++, le compilateur génère une erreur.  
  
 Vous pouvez également appeler toutes les fonctions déclarées avec **extern « C »** une liaison. Cela permet une `__asm` bloc au sein d’un programme C++ d’appeler les fonctions de bibliothèque C, car tous les fichiers d’en-tête standard déclarent les fonctions de bibliothèque d’avoir **extern « C »** une liaison.  
  
 **FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [Assembleur inline](../../assembler/inline/inline-assembler.md)