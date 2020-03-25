---
title: Avertissement de ligne de commande D9025
ms.date: 11/04/2016
f1_keywords:
- D9025
helpviewer_keywords:
- D9025
ms.assetid: 6edff72c-1508-46c2-99f4-0e4b3c5e60c9
ms.openlocfilehash: 4afd4d4dc07ffaae6038c025ee371278ebbebea6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80196714"
---
# <a name="command-line-warning-d9025"></a>Avertissement de ligne de commande D9025

substitution de’option1 'par’option2 '

L’option *option1* a été spécifiée, mais elle a été remplacée par *option2*. L’option *option2* a été utilisée.

Si deux options spécifient des directives contradictoires ou incompatibles, la directive spécifiée ou implicite dans l’option la plus éloignée à droite sur la ligne de commande est utilisée.

Si vous recevez cet avertissement lors de la compilation à partir de l’environnement de développement et que vous n’êtes pas certain de l’origine des options en conflit, tenez compte des points suivants :

- Une option peut être spécifiée dans le code ou dans les paramètres de projet du projet. Si vous examinez les pages de [Propriétés de ligne de commande](../../build/reference/command-line-property-pages.md) du compilateur et si vous voyez les options en conflit dans le champ **toutes les options** , les options sont définies dans les pages de propriétés du projet, dans le cas contraire, les options sont définies dans le code source.

   Si les options sont définies dans les pages de propriétés du projet, consultez la page de propriétés du préprocesseur du compilateur (avec le nœud de projet sélectionné dans le Explorateur de solutions).  Si vous ne voyez pas le jeu d’options, vérifiez les paramètres de la page de propriétés du préprocesseur pour chaque fichier de code source (dans Explorateur de solutions) pour vous assurer qu’il n’y est pas ajouté.

   Si les options sont définies dans le code, elles peuvent être définies dans le code ou dans les en-têtes Windows.  Vous pouvez essayer de créer un fichier prétraité ([/p](../../build/reference/p-preprocess-to-a-file.md)) et rechercher le symbole.
