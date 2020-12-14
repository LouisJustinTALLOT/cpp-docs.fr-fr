---
description: 'En savoir plus sur : coprocesseur à virgule flottante et conventions d’appel'
title: Coprocesseur à virgule flottante et conventions d’appel
ms.date: 11/04/2016
helpviewer_keywords:
- floating-point numbers [C++]
- floating-point coprocessor
ms.assetid: 3cc6615a-b308-4cf7-9570-83e192a832b3
ms.openlocfilehash: 2f68671783b8a556e787aa6637b9b5c2e5799485
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97242546"
---
# <a name="floating-point-coprocessor-and-calling-conventions"></a>Coprocesseur à virgule flottante et conventions d’appel

Si vous écrivez des routines d’assembly pour le coprocesseur à virgule flottante, vous devez conserver le mot de contrôle à virgule flottante et nettoyer la pile de coprocesseur, sauf si vous retournez une **`float`** **`double`** valeur ou (que votre fonction doit retourner dans St (0)).

## <a name="see-also"></a>Voir aussi

[Conventions d’appel](../cpp/calling-conventions.md)
