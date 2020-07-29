---
title: Coprocesseur à virgule flottante et conventions d’appel
ms.date: 11/04/2016
helpviewer_keywords:
- floating-point numbers [C++]
- floating-point coprocessor
ms.assetid: 3cc6615a-b308-4cf7-9570-83e192a832b3
ms.openlocfilehash: 09358ee36da7e5a86c214789fa7fd0687e9b8825
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231193"
---
# <a name="floating-point-coprocessor-and-calling-conventions"></a>Coprocesseur à virgule flottante et conventions d’appel

Si vous écrivez des routines d’assembly pour le coprocesseur à virgule flottante, vous devez conserver le mot de contrôle à virgule flottante et nettoyer la pile de coprocesseur, sauf si vous retournez une **`float`** **`double`** valeur ou (que votre fonction doit retourner dans St (0)).

## <a name="see-also"></a>Voir aussi

[Conventions d’appel](../cpp/calling-conventions.md)
