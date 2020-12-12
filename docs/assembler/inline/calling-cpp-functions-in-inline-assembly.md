---
description: 'En savoir plus sur : appel de fonctions C++ dans un assembly inline'
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
ms.openlocfilehash: 3efd4f00eae5810b287a27546bba3160f479b8f3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97117963"
---
# <a name="calling-c-functions-in-inline-assembly"></a>Appel des fonctions C++ dans l'assembly inline

**Spécifique à Microsoft**

Un **`__asm`** bloc peut appeler uniquement des fonctions C++ globales qui ne sont pas surchargées. Si vous appelez une fonction C++ globale surchargée ou une fonction membre C++, le compilateur génère une erreur.

Vous pouvez également appeler toutes les fonctions déclarées avec une liaison **extern "C"** . Cela permet **`__asm`** à un bloc au sein d’un programme C++ d’appeler les fonctions de la bibliothèque C, car tous les fichiers d’en-tête standard déclarent les fonctions de bibliothèque pour avoir une liaison **extern "C"** .

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Assembleur inline](../../assembler/inline/inline-assembler.md)<br/>
