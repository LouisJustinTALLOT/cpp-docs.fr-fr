---
title: Appel des fonctions C++ dans l’Assembly Inline | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
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
ms.openlocfilehash: 4717ae24dc1a0b6f51f7a00f68f6569c2f988c65
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43678942"
---
# <a name="calling-c-functions-in-inline-assembly"></a>Appel des fonctions C++ dans l'assembly inline

**Section spécifique à Microsoft**

Un bloc `__asm` peut appeler uniquement des fonctions C++ globales qui ne sont pas surchargées. Si vous appelez une fonction C++ globale surchargée ou une fonction membre C++, le compilateur génère une erreur.

Vous pouvez également appeler toutes les fonctions déclarées avec **extern « C »** une liaison. Cela permet une `__asm` bloc au sein d’un programme C++ d’appeler les fonctions de bibliothèque C, étant donné que tous les fichiers d’en-tête standard déclarent les fonctions de bibliothèque pour avoir **extern « C »** une liaison.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Assembleur inline](../../assembler/inline/inline-assembler.md)<br/>