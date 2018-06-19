---
title: Optimisations guidées par profil | Documents Microsoft
ms.custom: ''
ms.date: 03/14/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- profile-guided optimizations
- optimization, profile-guided [C++]
ms.assetid: 2225c307-d3ae-42c1-8345-a5a959d132dc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c7d6de281097232b1b8abc10a103af9c186e3550
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379404"
---
# <a name="profile-guided-optimizations"></a>Optimisations guidées par profil

L'optimisation guidée par profil vous permet d'optimiser un fichier de sortie alors que l'optimiseur utilise les données de séries de tests du fichier .exe ou .dll. Les données représentent la manière dont le programme est susceptible de s'exécuter dans un environnement de production.

Optimisations guidées par profil sont uniquement disponibles pour les cibles natives x86 ou x64. Optimisations guidées par profil ne sont pas disponibles pour les fichiers de sortie qui s’exécutent sur le common language runtime. Même si vous produisez un assembly avec du code natif et managé mixte (à l’aide de la **/CLR** option du compilateur), vous ne pouvez pas utiliser l’optimisation guidée par profil sur le code natif uniquement. Si vous tentez de générer un projet avec ces options dans l’IDE, une erreur de build se produit.

> [!NOTE]
> Les informations collectées à partir des séries de tests de profilage remplacent les optimisations qui seraient en vigueur si vous spécifiez **/Ob**, **/Os**, ou **/Ot**. Pour plus d’informations, consultez [/Ob (Expansion des fonctions Inline)](../../build/reference/ob-inline-function-expansion.md) et [/Os, /Ot (favoriser la taille du Code, favoriser la vitesse du Code)](../../build/reference/os-ot-favor-small-code-favor-fast-code.md).

## <a name="steps-to-optimize-your-app"></a>Étapes pour optimiser votre application

Pour utiliser l’optimisation guidée par profil, suivez ces étapes pour optimiser votre application :

- Compilez un ou plusieurs fichiers de code source avec [/GL](../../build/reference/gl-whole-program-optimization.md).

   Chaque module généré avec **/GL** peut être examiné pendant les séries de tests de l’optimisation guidée par profil pour capturer le comportement d’exécution. Chaque module dans une build de l’optimisation guidée par profil ne devra pas être compilé avec **/GL**. Toutefois, seuls les modules compilés avec **/GL** sont instrumentées et disponibles ultérieurement pour les optimisations guidées par profil.

- Lier à l’aide de [LTCG](../../build/reference/ltcg-link-time-code-generation.md) et [/GENPROFILE ou /fastgenprofile](../../build/reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md).

   L’utilisation des deux **LTCG** et **/genprofile** ou **/fastgenprofile** crée un fichier .pgd lors de l’exécution de l’application instrumentée. Une fois les données de série de tests ajoutées au fichier .pgd, elles peuvent être utilisées en entrée pour la prochaine étape de liaison (création de l'image optimisée). Lors de la spécification **/genprofile**, vous pouvez éventuellement ajouter un **PGD =**_nom de fichier_ argument pour spécifier un autre nom ou emplacement pour le fichier .pgd. La combinaison de **LTCG** et **/genprofile** ou **/FASTGENPROFILE** les options de l’éditeur de liens remplace déconseillées **/LTCG : PGINSTRUMENT** option de l’éditeur de liens.

- Profilez l'application.

   Chaque fois qu’une session EXE profilée se termine ou une DLL profilée est déchargée, un *appname*! # .pgc fichier est créé. Un fichier .pgc contient des informations sur une série de tests d'application particulière. # est un nombre commençant par 1 qui est incrémenté selon le nombre d’autres *appname*! # .pgc des fichiers dans le répertoire. Vous pouvez supprimer un fichier .pgc si la série de tests ne représente pas un scénario que vous souhaitez optimiser.

   Pendant une série de tests, vous pouvez forcer la fermeture du fichier .pgc actuellement ouvert et la création d’un nouveau fichier .pgc avec le [pgosweep](../../build/reference/pgosweep.md) utilitaire (par exemple, lorsque la fin d’un scénario de test ne coïncide pas avec l’arrêt de l’application).

   Votre application peut appeler directement une fonction PGO, [PgoAutoSweep](pgoautosweep.md), pour capturer les données de profil au moment de l’appel comme un fichier .pgc. Cela peut vous donner un contrôle plus précis du code couvert par les données capturées dans vos fichiers .pgc. Pour obtenir un exemple montrant comment utiliser cette fonction, consultez le [PgoAutoSweep](pgoautosweep.md) documentation.

   Lorsque vous créez votre build instrumentée, par défaut, la collecte de données est effectuée en mode thread-safe, ce qui est plus rapide, mais ne peut pas être totalement exact. À l’aide de la **EXACT** argument **/genprofile** ou **/fastgenprofile**, vous pouvez spécifier la collecte de données en mode thread-safe, ce qui est plus précis, mais il est plus lent. Cette option est également disponible si vous définissez déconseillées [PogoSafeMode](environment-variables-for-profile-guided-optimizations.md#pogosafemode) variable d’environnement ou déconseillées **/POGOSAFEMODE** option de l’éditeur de liens, lorsque vous créez votre build instrumentée.

- Lier à l’aide de **LTCG** et **/useprofile**.

   Utilisez à la fois le **LTCG** et [/useprofile](useprofile.md) les options de l’éditeur de liens pour créer l’image optimisée. Cette étape accepte en entrée le fichier .pgd. Lorsque vous spécifiez **/useprofile**, vous pouvez éventuellement ajouter un **PGD =**_nom de fichier_ argument pour spécifier un nom de celui par défaut ou un emplacement pour le fichier .pgd. Vous pouvez également spécifier ce nom à l’aide de déconseillées **/PGD** option de l’éditeur de liens. La combinaison de **LTCG** et **/useprofile** remplace déconseillées **/LTCG : PGOPTIMIZE** et **/LTCG : PGUPDATE** les options de l’éditeur de liens.

Il est même possible de créer le fichier de sortie optimisé et de déterminer ultérieurement qu'un profilage supplémentaire serait utile pour créer une image plus optimisée. Si l’image instrumentée et son fichier .pgd sont disponibles, vous pouvez effectuer des séries de tests supplémentaires et régénérer l’image optimisée avec le fichier .pgd plus récent, à l’aide de la même **LTCG** et **/useprofile** les options de l’éditeur de liens .

## <a name="optimizations-performed-by-pgo"></a>Optimisations effectuées par PGO

Vous trouverez ci-dessous une liste des optimisations guidées par profil :

- **Incorporation (inlining)** , par exemple, s’il existe une fonction A que fréquemment appelle la fonction B et la fonction B est relativement petite, puis les optimisations guidées par profil seront fonction inline B dans la fonction A.

- **Spéculation sur les appels virtuels** -si un appel virtuel, ou un autre appel via un pointeur fonction, cible fréquemment une certaine fonction, une optimisation guidée par profil peut insérer un appel direct exécuté conditionnellement à la fonction fréquemment ciblée, et l’appel direct peut être inline.

- **Allocation des registres** - optimisation avec les données de profil entraîne une meilleure allocation des registres.

- **Optimisation des blocs de base** -optimisation des blocs de base permet des blocs de base fréquemment exécutées qui s’exécutent temporellement dans un frame donné à être placé dans le même jeu de pages (localité). Cela réduit le nombre de pages utilisées, ce qui réduit au maximum la surcharge de la mémoire.

- **Optimisation de la taille/vitesse** -fonctions auxquelles le programme consacre beaucoup de temps peuvent être optimisées pour la vitesse.

- **Disposition des fonctions** - basé sur le graphique des appels et profiler le comportement des appelants/appelés, les fonctions qui ont tendance à être sur le même chemin d’exécution sont placées dans la même section.

- **Optimisation des branches conditionnelles** : en testant les valeurs, guidées par profil optimisations peuvent rechercher si une valeur donnée dans une instruction switch est utilisée plus souvent que d’autres valeurs.  Cette valeur peut ensuite être tirée de l’instruction switch.  La même opération peut être effectuée avec des instructions if/else dans lesquelles l'optimiseur peut organiser les instructions if/else afin que le bloc if ou else soit placé en premier selon le bloc qui est le plus souvent true.

- **Séparation du Code mort** -Code qui n’est pas appelé pendant le profilage est déplacé vers une section spéciale ajoutée à la fin de l’ensemble des sections. Cela permet de conserver efficacement cette section en dehors des pages utilisées fréquemment.

- **Séparation du Code EH** -le code EH, en cours d’exécution exceptionnellement, peut souvent être déplacé vers une section distincte lorsque les optimisations guidées par profil peuvent déterminer que les exceptions se produisent uniquement dans des conditions exceptionnelles.

- **Intrinsèques mémoire** -l’expansion d’éléments intrinsèques peut être conseillée s’il peut être déterminé si un élément intrinsèque est fréquemment appelé. Un élément intrinsèque peut également être optimisé en fonction de la taille de bloc des déplacements ou des copies.

Si vous utilisez Visual Studio 2013, vous pouvez utiliser automatisé [guidée par profil plug-in optimisation](../../build/reference/profile-guided-optimization-in-the-performance-and-diagnostics-hub.md) de Visual C++ dans le Hub performances et Diagnostics pour simplifier et rationaliser le processus d’optimisation dans Visual Studio. Ce plug-in n’est pas disponible dans les versions ultérieures de Visual Studio.

## <a name="next-steps"></a>Étapes suivantes

En savoir plus sur ces variables d’environnement, les fonctions et les outils que vous pouvez utiliser dans les optimisations guidées par profil :

[Variables d’environnement pour les optimisations guidées par profil](../../build/reference/environment-variables-for-profile-guided-optimizations.md)<br/>
Ces variables peuvent être utilisées pour spécifier le comportement au moment de l’exécution de scénarios de test. Ils ont été déconseillées en faveur de nouvelles options de l’éditeur de liens ; Lisez ceci pour vous aider à déplacer les variables d’environnement pour les options de l’éditeur de liens.

[PgoAutoSweep](pgoautosweep.md)<br/>
Une fonction, vous pouvez ajouter à votre application pour fournir le contrôle de capture de données de fichier .pgc affinée.

[pgosweep](../../build/reference/pgosweep.md)<br/>
Utilitaire de ligne de commande qui écrit toutes les données de profil dans le fichier .pgc, ferme le fichier .pgc et ouvre un nouveau fichier .pgc.

[pgomgr](../../build/reference/pgomgr.md)<br/>
Utilitaire de ligne de commande qui ajoute des données de profil à partir d’un ou plusieurs fichiers .pgc au fichier .pgd.

[Comment : fusionner plusieurs profils PGO en un seul profil](../../build/reference/how-to-merge-multiple-pgo-profiles-into-a-single-profile.md) exemples de **pgomgr** utilisation.

## <a name="see-also"></a>Voir aussi

[Outils de génération C/C++](../../build/reference/c-cpp-build-tools.md)
