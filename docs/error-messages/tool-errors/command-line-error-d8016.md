---
title: Erreur de ligne de commande D8016
ms.date: 11/04/2016
f1_keywords:
- D8016
helpviewer_keywords:
- D8016
ms.assetid: eec51312-7471-4f92-94b2-d517cafc8ef5
ms.openlocfilehash: c1e2e3e28f8556416f58d68f8ef1df4b220bc54c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399965"
---
# <a name="command-line-error-d8016"></a>Erreur de ligne de commande D8016

options de ligne de commande 'option1' et 'option2' sont incompatibles

Les options de ligne de commande ne peut pas être spécifiées ensemble.

Vérifiez les variables d’environnement, telles que CL, spécifications d’option.

**/ CLR** implique **/EHa**, et vous ne pouvez pas spécifier n’importe quel autre **/EH** option du compilateur avec **/CLR**. Pour plus d’informations, consultez l’article [/clr (Compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).

Vous pouvez obtenir D8016 après la mise à jour un projet Visual C++ 6.0 : le processus d’Assistant de mise à jour de projet peut activer **/RTC** pour chaque fichier de code source dans le projet, ce qui substitue le **/RTC** pour le projet.  Pour résoudre, modifiez le **/RTC** définition pour chaque fichier de code source dans le projet pour le paramètre par défaut, ce qui signifie que le paramètre de projet pour **/RTC** sera appliquée pour chaque fichier.

Consultez [/RTC (vérifications des erreurs au moment de l’exécution)](../../build/reference/rtc-run-time-error-checks.md) pour plus d’informations sur la modification de la **/RTC** paramètre de propriété.