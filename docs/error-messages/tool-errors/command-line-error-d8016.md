---
description: 'En savoir plus sur : erreur Command-Line D8016'
title: Erreur de ligne de commande D8016
ms.date: 11/04/2016
f1_keywords:
- D8016
helpviewer_keywords:
- D8016
ms.assetid: eec51312-7471-4f92-94b2-d517cafc8ef5
ms.openlocfilehash: 2f340cb7574177536310343dc9761058b7b9bc08
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97115714"
---
# <a name="command-line-error-d8016"></a>Erreur de ligne de commande D8016

les options de ligne de commande’option1 'et’option2 'sont incompatibles

Les options de ligne de commande ne peuvent pas être spécifiées en même temps.

Vérifiez les variables d’environnement, telles que CL, pour les spécifications de l’option.

**/CLR** implique **/EHa**, et vous ne pouvez pas spécifier d’autre option du compilateur **/Eh** avec **/CLR**. Pour plus d’informations, consultez [/clr (compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).

Vous pouvez obtenir D8016 après la mise à jour d’un projet Visual C++ 6,0 : le processus de l’Assistant Mise à jour de projet peut activer **/RTC** pour chaque fichier de code source dans le projet, qui remplace le paramètre **/RTC** pour le projet.  Pour résoudre ce cas, remplacez le paramètre **/RTC** pour chaque fichier de code source du projet par le paramètre par défaut, ce qui signifie que le paramètre du projet pour **/RTC** sera appliqué pour chaque fichier.

Pour plus d’informations sur la modification du paramètre de propriété **/RTC** [, consultez/RTC (vérifications des erreurs au moment de l’exécution)](../../build/reference/rtc-run-time-error-checks.md) .
