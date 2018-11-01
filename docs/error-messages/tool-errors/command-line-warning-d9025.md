---
title: Avertissement de ligne de commande D9025
ms.date: 11/04/2016
f1_keywords:
- D9025
helpviewer_keywords:
- D9025
ms.assetid: 6edff72c-1508-46c2-99f4-0e4b3c5e60c9
ms.openlocfilehash: fb9ab3152efe565501e91fbad5ebb279c4396968
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50652424"
---
# <a name="command-line-warning-d9025"></a>Avertissement de ligne de commande D9025

substitution de 'option1' par 'option2'

Le *option1* option a été spécifiée mais a ensuite été substituée par *option2*. Le *option2* option a été utilisée.

Si deux options spécifient des directives contradictoires ou incompatibles, la directive spécifiée ou implicite dans l’option plus à droite sur la ligne de commande est utilisée.

Si vous obtenez cet avertissement lors de la compilation à partir de l’environnement de développement et que vous ne savez pas d'où viennent les options en conflit, considérez les points suivants :

- Une option peut être spécifiée dans le code ou dans les paramètres de projet du projet. Si vous examinez du compilateur [Pages de propriétés de ligne de commande](../../ide/command-line-property-pages.md) et si vous voyez les options en conflit dans le **toutes les Options** champ ensuite les options sont définies dans les pages de propriétés du projet, sinon, les options sont définies dans le code source.

   Si les options sont définies dans les pages de propriétés du projet, recherchez sur la page de propriétés préprocesseur du compilateur (avec le nœud du projet sélectionné dans l’Explorateur de solutions).  Si vous ne voyez pas l’option définie ici, vérifiez les paramètres de page de propriétés préprocesseur pour chaque fichier de code source (dans l’Explorateur de solutions) pour vous assurer qu’il n'est pas y ajouté.

   Si les options sont définies dans le code peut être définie dans le code ou dans les en-têtes windows.  Vous pouvez essayer de créer un fichier prétraité ([/P](../../build/reference/p-preprocess-to-a-file.md)) et d’y rechercher le symbole.