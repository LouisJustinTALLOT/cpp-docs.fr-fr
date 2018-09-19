---
title: Erreur de ligne de commande D8016 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- D8016
dev_langs:
- C++
helpviewer_keywords:
- D8016
ms.assetid: eec51312-7471-4f92-94b2-d517cafc8ef5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0ee16542b2f0cf9842e351813ed2e0b0d22cccaa
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46056987"
---
# <a name="command-line-error-d8016"></a>Erreur de ligne de commande D8016

options de ligne de commande 'option1' et 'option2' sont incompatibles

Les options de ligne de commande ne peut pas être spécifiées ensemble.

Vérifiez les variables d’environnement, telles que CL, spécifications d’option.

**/ CLR** implique **/EHa**, et vous ne pouvez pas spécifier n’importe quel autre **/EH** option du compilateur avec **/CLR**. Pour plus d’informations, consultez l’article [/clr (Compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).

Vous pouvez obtenir D8016 après la mise à jour un projet Visual C++ 6.0 : le processus d’Assistant de mise à jour de projet peut activer **/RTC** pour chaque fichier de code source dans le projet, ce qui substitue le **/RTC** pour le projet.  Pour résoudre, modifiez le **/RTC** définition pour chaque fichier de code source dans le projet pour le paramètre par défaut, ce qui signifie que le paramètre de projet pour **/RTC** sera appliquée pour chaque fichier.

Consultez [/RTC (vérifications des erreurs au moment de l’exécution)](../../build/reference/rtc-run-time-error-checks.md) pour plus d’informations sur la modification de la **/RTC** paramètre de propriété.