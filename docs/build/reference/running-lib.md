---
title: Exécution de LIB
description: Décrit les options de ligne de commande que vous pouvez utiliser avec lib. exe.
ms.date: 02/09/2020
f1_keywords:
- VC.Project.VCLibrarianTool.TargetMachine
- VC.Project.VCLibrarianTool.PrintProgress
- VC.Project.VCLibrarianTool.SuppressStartupBanner
helpviewer_keywords:
- -MACHINE target platform option
- command files, LIB
- MACHINE target platform option
- colon command files
- VERBOSE library manager option
- /NOLOGO library manager option
- dash option specifier
- /MACHINE target platform option
- forward slash option specifier
- -NOLOGO library manager option
- LIB [C++], running LIB
- -VERBOSE library manager option
- /VERBOSE library manager option
- command files
- NOLOGO library manager option
- slash (/)
- semicolon, command files
- / command files
ms.assetid: d54f5c81-7147-4b2c-a8db-68ce6eb1eabd
ms.openlocfilehash: 871b92809f38b4dcbf84de802b1ac9940ea6f1e9
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438941"
---
# <a name="running-lib"></a>Exécution de LIB

Diverses options de ligne de commande peuvent être utilisées pour contrôler LIB.

## <a name="lib-command-line"></a>Ligne de commande LIB

Pour exécuter LIB, tapez la commande `lib`, suivie des options et des noms de fichiers pour la tâche pour laquelle vous utilisez LIB. LIB accepte également l’entrée de ligne de commande dans les fichiers de commandes, qui sont décrits dans la section suivante. LIB n’utilise pas de variable d’environnement.

## <a name="lib-command-files"></a>Fichiers de commandes LIB

Vous pouvez passer des arguments de ligne de commande à LIB dans un fichier de commandes à l’aide de la syntaxe suivante :

> <em>Fichier de commandes</em> **\@lib**

Le fichier *de commande de* fichier est un fichier texte. Aucun espace ou tabulation n’est autorisé entre le signe arobase ( **\@** ) et le nom de fichier. Le nom du *fichier de commandes* n’a pas d’extension par défaut. Spécifiez le nom de fichier complet, y compris toute extension. Les caractères génériques ne peuvent pas être utilisés. Vous pouvez spécifier un chemin d’accès absolu ou relatif avec le nom de fichier.

Dans le fichier de commandes, les arguments peuvent être séparés par des espaces ou des tabulations, comme ils le peuvent sur la ligne de commande. Les arguments peuvent également être séparés par des caractères de saut de ligne. Utilisez un point-virgule ( **;** ) pour marquer un commentaire. LIB ignore tout le texte du point-virgule jusqu’à la fin de la ligne.

Vous pouvez spécifier l’intégralité ou une partie de la ligne de commande dans un fichier de commandes, et vous pouvez utiliser plusieurs fichiers de commandes dans une commande LIB. LIB accepte l’entrée du fichier de commandes comme si elle était spécifiée à cet emplacement sur la ligne de commande. Les fichiers de commandes ne peuvent pas être imbriqués. LIB retourne le contenu des fichiers de commandes, sauf si l’option **/nologo** est utilisée.

## <a name="using-lib-options"></a>Utilisation des options LIB

Une option se compose d’un spécificateur d’option, qui est un tiret ( **-** ) ou une barre oblique ( **/** ), suivi du nom de l’option. Les noms d’options ne peuvent pas être abrégés. Certaines options prennent un argument, spécifié après un signe deux-points ( **:** ). Aucun espace ou onglet n’est autorisé dans une spécification d’option. Utilisez un ou plusieurs espaces ou tabulations pour séparer les spécifications de l’option sur la ligne de commande. Les noms des options et leurs arguments de mot clé ou de nom de fichier ne respectent pas la casse, mais les identificateurs utilisés comme arguments respectent la casse. LIB traite les options dans l’ordre spécifié sur la ligne de commande et dans les fichiers de commandes. Si une option est répétée avec des arguments différents, le dernier à traiter est prioritaire.

Les options suivantes s’appliquent à tous les modes de LIB :

> **/Errorreport** \[**aucune** &#124; **invite** &#124; de la **file d’attente d'** &#124; **envoi**]

L’option/ERRORREPORT est déconseillée. À compter de Windows Vista, le rapport d’erreurs est contrôlé par les paramètres d' [rapport d’erreurs Windows (WER)](/windows/win32/wer/windows-error-reporting) .

> **/LINKREPRO :** _chemin d’accès au répertoire_ \
> **/LINKREPROTARGET :** _nom de fichier_

Pour aider Microsoft à diagnostiquer les incidents lib. exe et les erreurs internes, vous pouvez utiliser l’option [/LINKREPRO](linkrepro.md) . Cette option génère une *reproduction de lien*, un ensemble d’artefacts de build qui permettent à Microsoft de reproduire un problème qui se produit pendant les opérations de la bibliothèque. L’option [/LINKREPROTARGET](linkreprotarget.md) peut être utilisée avec l’option **/LINKREPRO** . Il génère uniquement des artefacts de reproduction de lien lorsque lib. exe génère le fichier spécifié. Pour plus d’informations, consultez Guide pratique [pour signaler un problème avec C++ l’ensemble d’outils Microsoft](../../overview/how-to-report-a-problem-with-the-visual-cpp-toolset.md).

> **/LTCG**

« LTCG » représente la *génération de code durant l’édition de liens*. Cette fonctionnalité nécessite une collaboration entre le compilateur ([CL. exe](compiler-options.md)), lib et l’éditeur de liens ([Link](linker-options.md)). Ensemble, ils peuvent optimiser le code au-delà de ce que n’importe quel composant peut faire lui-même.

L’option **/LTCG** de lib spécifie que les entrées de cl. exe incluent les fichiers objets générés à l’aide de l’option du compilateur [/GL](gl-whole-program-optimization.md) . Si LIB rencontre de telles entrées et que **/LTCG** n’est pas spécifié, il redémarre avec/LTCG activé après l’affichage d’un message d’information. En d’autres termes, il n’est pas nécessaire de définir cette option explicitement, mais elle accélère les performances de génération. Cela est dû au fait que LIB n’a pas à redémarrer lui-même.

Dans le processus de génération, la sortie de LIB est envoyée à LINK. LINK possède sa propre option **/LTCG** distincte. Il est utilisé pour effectuer diverses optimisations, notamment l’optimisation de l’ensemble du programme et l’instrumentation de l’optimisation guidée par profil (PGO). Pour plus d’informations sur l’option de lien, consultez [/LTCG](ltcg-link-time-code-generation.md).

> **/MACHINE**

Spécifie la plateforme cible pour le programme. En règle générale, vous n’avez pas besoin de spécifier **/machine**. LIB déduit le type d’ordinateur à partir des fichiers. obj. Toutefois, dans certains cas, LIB ne peut pas déterminer le type d’ordinateur et émet un message d’erreur. Si une telle erreur se produit, spécifiez **/machine**. En mode **/extract** , cette option est réservée à la vérification. Utilisez `lib /?` sur la ligne de commande pour afficher les types d’ordinateur disponibles.

> **/NOLOGO**

Supprime l’affichage du message de copyright et du numéro de version LIB et empêche l’écho des fichiers de commandes.

> **/VERBOSE**

Affiche des détails sur la progression de la session, y compris les noms des fichiers. obj en cours d’ajout. Les informations sont envoyées vers la sortie standard et peuvent être redirigées vers un fichier.

> **/WX**[ **: no**]

Considérer les avertissements comme des erreurs. Pour plus d’informations, consultez l’article [/WX (Traiter les avertissements de l’Éditeur de liens comme des erreurs)](wx-treat-linker-warnings-as-errors.md).

D’autres options s’appliquent uniquement à des modes spécifiques de LIB. Ces options sont décrites dans les sections décrivant chaque mode.

## <a name="see-also"></a>Voir aussi

[Référence LIB](lib-reference.md)
