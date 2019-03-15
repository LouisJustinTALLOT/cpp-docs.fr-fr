---
title: Options de NMAKE
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, options
ms.assetid: 00ba1aec-ef27-44cf-8d82-c5c095e45bae
ms.openlocfilehash: c60b6d821d8e16e87f86e3b79825aa1dee7867c8
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57825310"
---
# <a name="nmake-options"></a>Options de NMAKE

Options de NMAKE sont décrites dans le tableau suivant. Options sont précédées par une barre oblique (/) ou un tiret (-) et ne sont pas sensible à la casse. Utilisez [! CMDSWITCHES](makefile-preprocessing-directives.md) pour modifier les paramètres d’option dans un makefile ou Tools.ini.

|Option|Objectif|
|------------|-------------|
|/A|Force la génération de toutes les cibles évaluées, même s’il y a pas obsolète en ce qui concerne les objets dépendants. Ne force pas la génération de cibles non liées.|
|/B|Force la génération même si les horodateurs sont égaux. Recommandé uniquement pour les systèmes très rapides (résolution de deux secondes ou moins).|
|/C|Supprime la sortie par défaut, y compris le message de copyright de NMAKE ou les avertissements, les horodateurs et les erreurs NMAKE récupérables. Supprime les avertissements émis par l’option /K.|
|/D|Affiche les horodatages de chacun d’eux évaluée cible et un message et dépendants lorsqu’une cible n’existe pas. Utile avec /P pour le débogage d’un makefile. Utilisez **! CMDSWITCHES** pour définir ou supprimer l’option /D pour une partie d’un makefile.|
|/E|Les causes les variables d’environnement pour remplacer les définitions de macros makefile.|
|/ERRORREPORT[NONE &#124; PROMPT &#124; QUEUE &#124; SEND ]|Si nmake.exe échoue lors de l’exécution, vous pouvez utiliser /ERRORREPORT pour envoyer des informations à Microsoft concernant ces erreurs internes.<br /><br /> Pour plus d’informations sur /ERRORREPORT, consultez [/errorReport (signaler les erreurs du compilateur interne)](errorreport-report-internal-compiler-errors.md).|
|/F *filename*|Spécifie *filename* en tant que makefile. Espaces ou des tabulations peuvent précéder *filename*. Spécifiez /F qu’une seule fois pour chaque makefile. Pour fournir un makefile à partir de l’entrée standard, spécifiez un tiret (-) pour *filename*et de fin d’entrée au clavier avec F6 ou CTRL + Z.|
|/G|Affiche les makefiles inclus avec le ! Directive INCLUDE.  Consultez [Directives de prétraitement Makefile](makefile-preprocessing-directives.md) pour plus d’informations.|
|/HELP, / ?|Affiche un bref résumé de syntaxe de ligne de commande NMAKE.|
|/I|Ignore les codes de sortie à partir de toutes les commandes. Pour définir ou supprimer l’option /I pour une partie d’un makefile, utilisez **! CMDSWITCHES**. Pour ignorer les codes de sortie pour une partie d’un makefile, utilisez un modificateur de commande tiret (-) ou [. Ignorer](dot-directives.md). Remplace /K si les deux sont spécifiés.|
|/K|Poursuit la génération de dépendances non liées, si une commande retourne une erreur. Également émet un avertissement et retourne un code de sortie 1. Par défaut, NMAKE s’arrête si une commande retourne un code de sortie différent de zéro. Avertissements de /K sont supprimés par /C ; /I substitue /K si les deux sont spécifiés.|
|/N|Affiche, mais ne pas exécuter de commandes ; commandes de prétraitement sont exécutées. N’affiche pas les commandes dans les appels récursifs de NMAKE. Utile pour le débogage de makefiles et de contrôle des horodatages. Pour définir ou effacer /N pour une partie d’un makefile, utilisez **! CMDSWITCHES**.|
|/NOLOGO|Supprime le message de copyright de NMAKE.|
|/P|Affiche des informations (définitions de macros, règles d’inférence, cibles, [. SUFFIXES](dot-directives.md) liste) dans la sortie standard, puis exécute la build. Si aucun makefile ou une cible de ligne de commande n’existe, il affiche des informations uniquement. Utiliser avec /D pour déboguer un makefile.|
|/Q|Vérifie les horodatages des cibles ; n’exécute pas la génération. Retourne un code de sortie zéro si toutes les cibles sont à jour et un code de sortie différent de zéro si toutes les cibles ne sont pas. Commandes de prétraitement sont exécutées. Utile lors de l’exécution de NMAKE à partir d’un fichier de commandes.|
|/R|Efface le **. SUFFIXES** répertorier et ignore les règles d’inférence et les macros qui sont définies dans le fichier Tools.ini ou qui sont prédéfinis.|
|/S|Supprime l’affichage des commandes exécutées. Pour supprimer l’affichage dans une partie d’un makefile, utilisez le **\@** modificateur de commande ou [. En mode silencieux](dot-directives.md). Pour définir ou supprimer l’option /S pour une partie d’un makefile, utilisez **! CMDSWITCHES**.|
|/T|Met à jour les horodatages des cibles de ligne de commande (ou la première cible du makefile) et exécute les commandes de prétraitement mais n’exécute pas la génération.|
|/U|Doit être utilisée conjointement avec /N. Fait un dump des fichiers NMAKE inline afin que la sortie /N peut être utilisée comme un fichier de commandes.|
|/X *filename*|Envoie la sortie d’erreur NMAKE vers *filename* au lieu de l’erreur standard. Espaces ou des tabulations peuvent précéder *filename*. Pour envoyer la sortie d’erreur dans la sortie standard, spécifiez un tiret (-) pour *filename*. N’affecte pas la sortie des commandes vers l’erreur standard.|
|/Y|Désactive les règles d’inférence en mode batch. Lorsque cette option est sélectionnée, toutes les règles d’inférence en mode batch sont traitées comme les règles d’inférence ordinaires.|

## <a name="see-also"></a>Voir aussi

[Exécution de NMAKE](running-nmake.md)
