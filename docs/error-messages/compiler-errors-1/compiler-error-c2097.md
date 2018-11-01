---
title: Erreur du compilateur C2097
ms.date: 11/04/2016
f1_keywords:
- C2097
helpviewer_keywords:
- C2097
ms.assetid: 7e5b2fd4-f61c-4b8a-b265-93e987a04bd3
ms.openlocfilehash: 8b50221997dcf2fb60ee2b82ed630dd325a38145
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50676588"
---
# <a name="compiler-error-c2097"></a>Erreur du compilateur C2097

initialisation non conforme

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes

1. Initialisation d’une variable à l’aide d’une valeur non constante.

1. Initialisation d’une adresse courte avec une adresse longue.

1. Initialisation d’une structure locale, une union ou un tableau avec une expression non constante lors de la compilation avec **/Za**.

1. Initialisation avec une expression contenant un opérateur virgule.

1. Initialisation avec une expression qui n’est ni constante ni symbolique.