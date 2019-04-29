---
title: Optimisations guidées par profil
ms.date: 04/23/2019
helpviewer_keywords:
- profile-guided optimizations
- optimization, profile-guided [C++]
ms.assetid: 2225c307-d3ae-42c1-8345-a5a959d132dc
ms.openlocfilehash: 46619e77861b6a3a78d74ce6c6d9173a3a5f270f
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2019
ms.locfileid: "64341153"
---
# <a name="profile-guided-optimizations"></a>Optimisations guidées par profil

Optimisation guidée par profil (PGO) vous permet d’optimiser un fichier exécutable entière, où l’optimiseur utilise les données de séries de tests du fichier .exe ou .dll. Les données représentent la performance probable du programme dans un environnement de production.

Optimisations guidées par profil sont uniquement disponibles pour les cibles natives x86 ou x64. Optimisations guidées par profil ne sont pas disponibles pour les fichiers exécutables qui s’exécutent sur le common language runtime. Même si vous produisez un assembly avec du code natif et managé mixte (à l’aide de la **/CLR** option du compilateur), vous ne pouvez pas utiliser l’optimisation guidée par profil sur le code natif uniquement. Si vous essayez de générer un projet avec ces options dans l’IDE, une erreur de build se produit.

> [!NOTE]
> Les informations collectées à partir des séries de tests de profilage remplacent les optimisations qui seraient en vigueur si vous spécifiez **/Ob**, **/Os**, ou **/Ot**. Pour plus d’informations, consultez [/Ob (Expansion des fonctions Inline)](reference/ob-inline-function-expansion.md) et [/Os, /Ot (favoriser la taille du Code, favoriser la vitesse du Code)](reference/os-ot-favor-small-code-favor-fast-code.md).

## <a name="steps-to-optimize-your-app"></a>Étapes d’optimisation de votre application

Pour utiliser l’optimisation guidée par profil, suivez ces étapes pour optimiser votre application :

- Compilez un ou plusieurs fichiers de code source avec [/GL](reference/gl-whole-program-optimization.md).

   Chaque module généré avec **/GL** peuvent être examinés pendant les séries de tests d’optimisation guidée par profil pour capturer le comportement au moment de l’exécution. Chaque module dans une génération à optimisation guidée par profil ne doit pas être compilé avec **/GL**. Toutefois, seuls les modules compilés avec **/GL** instrumentés et disponibles ultérieurement pour les optimisations guidées par profil.

- Établissez une liaison avec [/LTCG](reference/ltcg-link-time-code-generation.md) et [/GENPROFILE ou /fastgenprofile](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md).

   L’utilisation simultanée **/LTCG** et **/genprofile** ou **/fastgenprofile** crée un `.pgd` fichier lors de l’exécution de l’application instrumentée. Une fois que les données de série de tests sont ajoutées à la `.pgd` fichier, il peut être utilisé en tant qu’entrée à l’étape suivante de lien (création de l’image optimisée). Lorsque vous spécifiez **/genprofile**, vous pouvez éventuellement ajouter un **PGD =**_filename_ argument pour spécifier un nom de non défini par défaut ou un emplacement pour le `.pgd` fichier. La combinaison de **/LTCG** et **/genprofile** ou **/fastgenprofile** les options de l’éditeur de liens remplace déconseillées **/LTCG : PGINSTRUMENT** option de l’éditeur de liens.

- Profilez l'application.

   Met fin à une session EXE profilée chaque fois, ou une DLL profilée est déchargée, un `appname!N.pgc` fichier est créé. Un `.pgc` fichier contient des informations sur une série de tests application particulière. *appname* est le nom de votre application, et *N* est un nombre commençant par 1 qui est incrémenté selon le nombre d’autres `appname!N.pgc` fichiers dans le répertoire. Vous pouvez supprimer un `.pgc` fichier si la série de tests ne représentent pas un scénario que vous souhaitez optimiser.

   Pendant une série de tests, vous pouvez forcer la fermeture d’actuellement ouvert `.pgc` fichier et la création d’un nouveau `.pgc` de fichiers avec le [pgosweep](pgosweep.md) utility (par exemple, lors de la fin d’un scénario de test ne coïncide avec l’application arrêt).

   Votre application peut également appeler directement une fonction PGO, [PgoAutoSweep](pgoautosweep.md), pour capturer les données de profil au moment de l’appel comme un `.pgc` fichier. Il peut vous donner un contrôle plus précis sur le code couvert par les données capturées dans votre `.pgc` fichiers. Pour obtenir un exemple montrant comment utiliser cette fonction, consultez le [PgoAutoSweep](pgoautosweep.md) documentation.

   Lorsque vous créez votre build instrumentée, par défaut, la collecte de données est effectuée en mode thread-safe, ce qui est plus rapide mais peut être imprécise. À l’aide de la **EXACT** l’argument de **/genprofile** ou **/fastgenprofile**, vous pouvez spécifier la collecte de données en mode thread-safe, ce qui est plus précis, mais plus lente. Cette option est également disponible si vous définissez déconseillées [PogoSafeMode](environment-variables-for-profile-guided-optimizations.md#pogosafemode) variable d’environnement ou déconseillées **/POGOSAFEMODE** option de l’éditeur de liens, lorsque vous créez votre build instrumentée.

- Établissez une liaison avec **/LTCG** et **/USEPROFILE**.

   Utilisez à la fois le **/LTCG** et [/USEPROFILE](reference/useprofile.md) les options de l’éditeur de liens pour créer l’image optimisée. Cette étape prend comme entrée le `.pgd` fichier. Lorsque vous spécifiez **/USEPROFILE**, vous pouvez éventuellement ajouter un **PGD =**_filename_ argument pour spécifier un nom de celle par défaut ou un emplacement pour le `.pgd` fichier. Vous pouvez également spécifier ce nom à l’aide de déconseillées **/PGD** option de l’éditeur de liens. La combinaison de **/LTCG** et **/USEPROFILE** remplace déconseillées **/LTCG : PGOPTIMIZE** et **/LTCG : PGUPDATE** les options de l’éditeur de liens.

Il est même possible de créer le fichier exécutable optimisé et de déterminer ultérieurement qu’un profilage supplémentaire serait utile pour créer une image plus optimisée. Si l’image instrumentée et son `.pgd` fichier sont disponibles, vous pouvez effectuer des séries de tests supplémentaires et régénérer l’image optimisée avec la plus récente `.pgd` fichier, à l’aide de la même **/LTCG** et **/USEPROFILE** les options de l’éditeur de liens.

## <a name="optimizations-performed-by-pgo"></a>Optimisations effectuées par PGO

Les optimisations guidées par profil incluent ces vérifications et les améliorations :

- **Incorporation (inlining)** , par exemple, si une fonction A appelle fréquemment une fonction B, et la fonction B est relativement petite, puis guidée par profil optimisations fonction inline B dans la fonction A.

- **Spéculation sur les appels virtuels** -si un appel virtuel, ou un autre appel via un pointeur fonction, cible fréquemment une certaine fonction, une optimisation guidée par profil peut insérer un appel direct exécuté conditionnellement à la fonction fréquemment ciblée, et l’appel direct peut être inline.

- **Allocation des registres** -optimisation basée sur les données de profil entraîne une meilleure allocation des registres.

- **Optimisation des blocs de base** -optimisation des blocs de base permet de placer les blocs de base fréquemment qui s’exécutent temporellement dans un frame donné à placer dans le même ensemble de pages (localité). Elle réduit le nombre de pages utilisées, ce qui réduit la surcharge de mémoire.

- **Optimisation de la taille/vitesse** -fonctions auxquelles le programme consacre le plus de temps d’exécution peuvent être optimisés pour la vitesse.

- **Disposition des fonctions** - basé sur le graphique des appels et de profiler le comportement appelant/appelé, les fonctions qui ont tendance à suivre le même chemin d’accès d’exécution sont placées dans la même section.

- **Optimisation des branches conditionnelles** : en testant les valeurs, guidées par profil optimisations peuvent trouver si une valeur donnée dans une instruction switch est utilisée plus souvent que d’autres valeurs.  Cette valeur peut ensuite être tirée de l’instruction switch.  Mais elle peuvent être accomplie avec `if`... `else` instructions où l’optimiseur peut organiser les `if`... `else` donc que soit le `if` ou `else` bloc est placé en premier, selon le bloc qui est le plus souvent true.

- **Séparation du Code mort** -Code qui n’est pas appelé pendant le profilage est déplacé vers une section spéciale qui est ajoutée à la fin de l’ensemble des sections. Il permet de conserver efficacement cette section en dehors des pages utilisées fréquemment.

- **Séparation du Code EH** -code EH, car est exécutée uniquement à titre exceptionnel, il peut souvent être déplacé vers une section distincte. Il est déplacé lorsque les optimisations guidées par profil peuvent déterminer que les exceptions se produisent uniquement dans des conditions exceptionnelles.

- **Intrinsèques mémoire** : Si vous développez un élément intrinsèque ou non dépend de si elle est appelée fréquemment. Un élément intrinsèque peut également être optimisé en fonction de la taille de bloc des déplacements ou des copies.

## <a name="next-steps"></a>Étapes suivantes

En savoir plus sur ces variables d’environnement, les fonctions et les outils que vous pouvez utiliser dans les optimisations guidées par profil :

[Variables d’environnement pour les optimisations guidées par profil](environment-variables-for-profile-guided-optimizations.md)<br/>
Ces variables ont été utilisées pour spécifier le comportement au moment de l’exécution de scénarios de test. Elles sont désormais déconseillés et remplacés par nouvelles options de l’éditeur de liens. Ce document vous montre comment déplacer des variables d’environnement pour les options de l’éditeur de liens.

[PgoAutoSweep](pgoautosweep.md)<br/>
Une fonction que vous pouvez ajouter à votre application pour fournir affinée `.pgc` contrôle de capture de données de fichier.

[pgosweep](pgosweep.md)<br/>
Un utilitaire de ligne de commande qui écrit toutes les données de profil pour le `.pgc` de fichiers, se ferme le `.pgc` de fichiers et ouvre une nouvelle `.pgc` fichier.

[pgomgr](pgomgr.md)<br/>
Un utilitaire de ligne de commande qui ajoute des données de profil à partir d’un ou plusieurs `.pgc` les fichiers vers le `.pgd` fichier.

[Guide pratique pour Fusionner plusieurs profils PGO en un seul profil](how-to-merge-multiple-pgo-profiles-into-a-single-profile.md)<br/>
Exemples de **pgomgr** utilisation.

## <a name="see-also"></a>Voir aussi

[Outils de build MSVC supplémentaires](reference/c-cpp-build-tools.md)
