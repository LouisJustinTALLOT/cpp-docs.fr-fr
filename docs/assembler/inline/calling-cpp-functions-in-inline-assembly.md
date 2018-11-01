---
title: Appel des fonctions C++ dans l'assembly inline
ms.date: 08/30/2018
helpviewer_keywords:
- functions [C++], calling in inline assembly
- function calls, C++ functions
- function calls, in inline assembly
- Visual C++, functions
- inline assembly, calling functions
- __asm keyword [C++], calling functions
ms.assetid: 1f0d1eb3-54cf-45d5-838d-958188616b38
ms.openlocfilehash: 666f7b2a59f0d48a14be54a439b6402f2a4d3128
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50458222"
---
# <a name="calling-c-functions-in-inline-assembly"></a>Appel des fonctions C++ dans l'assembly inline

**Section spécifique à Microsoft**

Un bloc `__asm` peut appeler uniquement des fonctions C++ globales qui ne sont pas surchargées. Si vous appelez une fonction C++ globale surchargée ou une fonction membre C++, le compilateur génère une erreur.

Vous pouvez également appeler toutes les fonctions déclarées avec **extern « C »** une liaison. Cela permet une `__asm` bloc au sein d’un programme C++ d’appeler les fonctions de bibliothèque C, étant donné que tous les fichiers d’en-tête standard déclarent les fonctions de bibliothèque pour avoir **extern « C »** une liaison.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Assembleur inline](../../assembler/inline/inline-assembler.md)<br/>