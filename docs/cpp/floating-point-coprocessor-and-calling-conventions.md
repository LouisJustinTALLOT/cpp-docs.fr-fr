---
title: Coprocesseur à virgule flottante et conventions d’appel
ms.date: 11/04/2016
helpviewer_keywords:
- floating-point numbers [C++]
- floating-point coprocessor
ms.assetid: 3cc6615a-b308-4cf7-9570-83e192a832b3
ms.openlocfilehash: c70dd3b049ca353acc8a504df52b2c61feaf1974
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188618"
---
# <a name="floating-point-coprocessor-and-calling-conventions"></a>Coprocesseur à virgule flottante et conventions d’appel

Si vous écrivez des routines d’assembly pour le coprocesseur à virgule flottante, vous devez conserver le mot de contrôle à virgule flottante et nettoyer la pile de coprocesseur, sauf si vous retournez une valeur **float** ou **double** (que votre fonction doit retourner dans St (0)).

## <a name="see-also"></a>Voir aussi

[Conventions d’appel](../cpp/calling-conventions.md)
