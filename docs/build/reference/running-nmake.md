---
title: Exécution de NMAKE
ms.date: 10/29/2019
helpviewer_keywords:
- targets, building
- response files, NMAKE
- targets
- command files
- NMAKE program, targets
- NMAKE program, running
- command files, NMAKE
ms.assetid: 0421104d-8b7b-4bf3-86c1-928d9b7c1a8c
ms.openlocfilehash: ed56b7cd69b683caa84f184d9d72e70aac12add3
ms.sourcegitcommit: 6ed1bc5b26dc60a780c1fc5f2f19d57ba1dc47d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73144542"
---
# <a name="running-nmake"></a>Exécution de NMAKE

## <a name="syntax"></a>Syntaxe

> **NMAKE** [*option* ...] [*macros* ...] [*cibles* ...] [ **\@** _fichier de commandes_ ...]

## <a name="remarks"></a>Notes

NMAKE génère uniquement les *cibles* spécifiées ou, si aucun n’est spécifié, la première cible dans le Makefile. La première cible Makefile peut être une [pseudocible](description-blocks.md#pseudotargets) qui crée d’autres cibles. NMAKE utilise les Makefiles spécifiés avec **/f**, ou si **/f** n’est pas spécifié, il s’agit du fichier Makefile dans le répertoire actif. Si aucun Makefile n’est spécifié, il utilise des règles d’inférence pour générer des *cibles*de ligne de commande.

Le fichier texte de *fichier de commandes* (ou fichier réponse) contient une entrée de ligne de commande. D’autres entrées peuvent précéder ou suivre \@*fichier de commandes*. Un chemin d’accès est autorisé. Dans *le fichier de commandes*, les sauts de ligne sont traités comme des espaces. Placez les définitions de macro entre guillemets si elles contiennent des espaces.

## <a name="nmake-options"></a>Options de NMAKE

Les options NMAKE sont décrites dans le tableau suivant. Les options sont précédées d’une barre oblique (`/`) ou d’un tiret (`-`), et ne respectent pas la casse. Utilisez [`!CMDSWITCHES`](makefile-preprocessing-directives.md) pour modifier les paramètres d’option dans un Makefile ou dans Tools. ini.

| Option | Fonction |
| ------------ | ------------- |
| **/A** | Force la génération de toutes les cibles évaluées, même si elles ne sont pas obsolètes par rapport aux dépendants. Ne force pas les builds de cibles non associées. |
| **/B** | Force la génération même si les horodateurs sont égaux. Recommandé uniquement pour les systèmes rapides (résolution de deux secondes ou moins). |
| **/C** | Supprime la sortie par défaut, y compris les erreurs ou avertissements NMAKE non mortels, les horodateurs et le message de Copyright NMAKE. Supprime les avertissements émis par **/k**. |
| **/D** | Affiche les horodateurs de chaque cible et dépendant évalués, ainsi qu’un message lorsqu’une cible n’existe pas. Utile avec **/p** pour déboguer un Makefile. Utilisez `!CMDSWITCHES` pour définir ou effacer **/d** dans le cadre d’un Makefile. |
| **/E** | Fait en sorte que les variables d’environnement remplacent les définitions de macros Makefile. |
| **/errorreport** [ **aucune** &#124; **invite** &#124; de **file d’attente d'** &#124; **envoi** ] | Si NMAKE. exe échoue au moment de l’exécution, vous pouvez utiliser **/errorreport** pour envoyer des informations à Microsoft sur ces erreurs internes.<br /><br /> Pour plus d’informations, consultez l’article [/errorReport (Signaler les erreurs internes du compilateur)](errorreport-report-internal-compiler-errors.md). |
| **/F** *nom de fichier* | Spécifie *filename* comme Makefile. Les espaces ou les tabulations peuvent précéder le *nom de fichier*. Spécifiez **/f** une fois pour chaque Makefile. Pour fournir un Makefile à partir d’une entrée standard, spécifiez un tiret (`-`) pour le *nom de fichier*et terminez l’entrée au clavier par **F6** ou **Ctrl + Z**. |
| **/G** | Affiche les Makefiles inclus dans la directive `!INCLUDE`. Pour plus d’informations, consultez [directives de prétraitement](makefile-preprocessing-directives.md)d’un Makefile. |
| **/Help**, **/ ?** | Affiche un bref résumé de la syntaxe de la ligne de commande NMAKE. |
| **/I** | Ignore les codes de sortie de toutes les commandes. Pour définir ou effacer **/i** pour une partie d’un Makefile, utilisez `!CMDSWITCHES`. Pour ignorer les codes de sortie dans une partie d’un Makefile, utilisez un modificateur de commande Dash (`-`) ou [`.IGNORE`](dot-directives.md). Remplace **/k** si les deux sont spécifiés. |
| **/K** | Poursuit la génération de dépendances non liées, si une commande retourne une erreur. Émet également un avertissement et retourne un code de sortie de 1. Par défaut, NMAKE s’arrête si une commande retourne un code de sortie différent de zéro. Les avertissements de **/k** sont supprimés par **/c**; **/I** remplace **/k** si les deux sont spécifiés. |
| **/N** | Affiche, mais n’exécute pas les commandes ; les commandes de prétraitement sont exécutées. N’affiche pas les commandes dans les appels NMAKE récursifs. Utile pour déboguer les makefiles et vérifier les horodateurs. Pour définir ou effacer **/n** dans le cadre d’un Makefile, utilisez `!CMDSWITCHES`. |
| **/NOLOGO** | Supprime le message de copyright de NMAKE. |
| **/P** | Affiche des informations (définitions de macro, règles d’inférence, cibles, liste de [`.SUFFIXES`](dot-directives.md) ) à la sortie standard, puis exécute la Build. S’il n’existe aucun Makefile ou cible de ligne de commande, il affiche uniquement des informations. Utilisez avec **/d** pour déboguer un Makefile. |
| **/Q** | Vérifie les horodateurs des cibles ; n’exécute pas la Build. Retourne un code de sortie zéro si toutes les cibles sont à jour, et un code de sortie différent de zéro si une cible est obsolète. Les commandes de prétraitement sont exécutées. Utile lors de l’exécution de NMAKE à partir d’un fichier de commandes. |
| **/R** | Efface la liste `.SUFFIXES` et ignore les règles d’inférence et les macros définies dans le fichier Tools. ini ou prédéfinies. |
| **Commutateur** | Supprime l’affichage des commandes exécutées. Pour supprimer l’affichage dans une partie d’un Makefile, utilisez le modificateur de commande **\@** ou [`.SILENT`](dot-directives.md). Pour définir ou effacer **/s** dans le cadre d’un Makefile, utilisez `!CMDSWITCHES`. |
| **Commutateur** | Met à jour les horodateurs des cibles de ligne de commande (ou de la première cible Makefile) et exécute les commandes de prétraitement, mais n’exécute pas la génération. |
| **/U** | Doit être utilisé conjointement avec **/n**. Fait un dump des fichiers NMAKE Inline afin que la sortie **/n** puisse être utilisée comme fichier de commandes. |
| **/X** *nom du fichier* | Envoie la sortie d’erreur NMAKE au *nom de fichier* au lieu de l’erreur standard. Les espaces ou les tabulations peuvent précéder le *nom de fichier*. Pour envoyer la sortie d’erreur vers la sortie standard, spécifiez un tiret (`-`) pour *filename*. N’affecte pas la sortie des commandes à l’erreur standard. |
| **/Y** | Désactive les règles d’inférence en mode batch. Lorsque cette option est sélectionnée, toutes les règles d’inférence en mode batch sont traitées comme des règles d’inférence régulières. |

## <a name="toolsini-and-nmake"></a>Tools.ini et NMAKE

NMAKE lit Tools. ini avant de lire les Makefiles, sauf si **/r** est utilisé. Il recherche d’abord Tools. ini dans le répertoire actif, puis dans le répertoire spécifié par la variable d’environnement INIT. La section relative aux paramètres NMAKE du fichier d’initialisation commence par `[NMAKE]` et peut contenir des informations sur les Makefiles. Spécifiez un commentaire sur une ligne distincte commençant par un signe dièse (`#`).

## <a name="exit-codes-from-nmake"></a>Codes de sortie de NMAKE

NMAKE retourne les codes de sortie suivants :

| Code | Signification |
| ---------- | ------------- |
| 0 | Aucune erreur (peut-être un avertissement) |
| 1 | Build incomplète (émis uniquement quand l’utilisation de **/k** est utilisée) |
| 2 | Erreur de programme, peut-être provoquée par l’un des problèmes suivants :<br /> -Erreur de syntaxe dans le Makefile<br /> -Code d’erreur ou de sortie d’une commande<br /> -Interruption par l’utilisateur |
| 4 | Erreur système : mémoire insuffisante |
| 255 | La cible n’est pas à jour (émis uniquement lorsque **/q** est utilisé) |

## <a name="see-also"></a>Voir aussi

[NMAKE, référence](nmake-reference.md)
