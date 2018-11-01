---
title: Coprocesseur à virgule flottante et conventions d’appel
ms.date: 11/04/2016
helpviewer_keywords:
- floating-point numbers [C++]
- floating-point coprocessor
ms.assetid: 3cc6615a-b308-4cf7-9570-83e192a832b3
ms.openlocfilehash: 7e9184d66bde26ab0e2b345f8f10c2e28619fd2b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50625107"
---
# <a name="floating-point-coprocessor-and-calling-conventions"></a>Coprocesseur à virgule flottante et conventions d’appel

Si vous écrivez des routines pour flottante point coprocesseur assembly, vous devez conserver flottante pointez le mot de contrôle et de nettoyer la pile de coprocesseur, sauf si vous retournez un **float** ou **double** valeur (laquelle votre fonction doit retourner dans ST(0)).

## <a name="see-also"></a>Voir aussi

[Conventions d’appel](../cpp/calling-conventions.md)