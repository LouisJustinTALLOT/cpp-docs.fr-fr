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
ms.openlocfilehash: f16e466ebb5f31231411eaaf9a1a85bfcc46a34d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169576"
---
# <a name="calling-c-functions-in-inline-assembly"></a>Appel des fonctions C++ dans l'assembly inline

**Section spécifique de Microsoft**

Un bloc `__asm` peut appeler uniquement des fonctions C++ globales qui ne sont pas surchargées. Si vous appelez une fonction C++ globale surchargée ou une fonction membre C++, le compilateur génère une erreur.

Vous pouvez également appeler toutes les fonctions déclarées avec une liaison **extern "C"** . Cela permet à un bloc `__asm` dans C++ un programme d’appeler les fonctions de la bibliothèque C, car tous les fichiers d’en-tête standard déclarent les fonctions de bibliothèque pour avoir une liaison **extern "C"** .

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[Assembleur inline](../../assembler/inline/inline-assembler.md)<br/>
