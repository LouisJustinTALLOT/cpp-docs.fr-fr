---
title: Erreur de ligne de commande D8016
ms.date: 11/04/2016
f1_keywords:
- D8016
helpviewer_keywords:
- D8016
ms.assetid: eec51312-7471-4f92-94b2-d517cafc8ef5
ms.openlocfilehash: 1bdef16b14488be86aff880db7c049f4bcddcdb5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80196961"
---
# <a name="command-line-error-d8016"></a>Erreur de ligne de commande D8016

les options de ligne de commande’option1 'et’option2 'sont incompatibles

Les options de ligne de commande ne peuvent pas être spécifiées en même temps.

Vérifiez les variables d’environnement, telles que CL, pour les spécifications de l’option.

**/CLR** implique **/EHa**, et vous ne pouvez pas spécifier d’autre option du compilateur **/Eh** avec **/CLR**. Pour plus d'informations, consultez [/clr (Common Language Runtime Compilation)](../../build/reference/clr-common-language-runtime-compilation.md).

Vous pouvez obtenir D8016 après la mise à jour C++ d’un projet Visual 6,0 : le processus de l’Assistant Mise à jour du projet peut activer **/RTC** pour chaque fichier de code source dans le projet, qui remplace le paramètre **/RTC** pour le projet.  Pour résoudre ce cas, remplacez le paramètre **/RTC** pour chaque fichier de code source du projet par le paramètre par défaut, ce qui signifie que le paramètre du projet pour **/RTC** sera appliqué pour chaque fichier.

Pour plus d’informations sur la modification du paramètre de propriété **/RTC** [, consultez/RTC (vérifications des erreurs au moment de l’exécution)](../../build/reference/rtc-run-time-error-checks.md) .
