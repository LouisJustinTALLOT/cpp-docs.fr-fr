---
description: 'En savoir plus sur : optimisations guidées par profil'
title: Optimisations guidées par profil
ms.date: 04/23/2019
helpviewer_keywords:
- profile-guided optimizations
- optimization, profile-guided [C++]
ms.assetid: 2225c307-d3ae-42c1-8345-a5a959d132dc
ms.openlocfilehash: cd6a9627de72ef170e88493ef3e2147a0ccc2bc7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97187323"
---
# <a name="profile-guided-optimizations"></a>Optimisations guidées par profil

L’optimisation guidée par profil (PGO) vous permet d’optimiser l’intégralité d’un fichier exécutable, où l’optimiseur utilise les données des séries de tests du fichier. exe ou. dll. Les données représentent les performances probables du programme dans un environnement de production.

Les optimisations guidées par profil sont uniquement disponibles pour les cibles natives x86 ou x64. Les optimisations guidées par profil ne sont pas disponibles pour les fichiers exécutables qui s’exécutent sur le common language runtime. Même si vous générez un assembly avec du code mixte natif et managé (à l’aide de l’option du compilateur **/CLR** ), vous ne pouvez pas utiliser l’optimisation guidée par profil uniquement sur le code natif. Si vous tentez de générer un projet avec ces options définies dans l’IDE, une erreur de génération se produit.

> [!NOTE]
> Les informations collectées à partir des séries de tests de profilage remplacent les optimisations qui seraient autrement appliquées si vous spécifiez **/ob**, **/OS** ou **/OT**. Pour plus d’informations, consultez [/ob (expansion des fonctions inline)](reference/ob-inline-function-expansion.md) et [/OS,/OT (favoriser la taille du code, favoriser la rapidité du code)](reference/os-ot-favor-small-code-favor-fast-code.md).

## <a name="steps-to-optimize-your-app"></a>Étapes d’optimisation de votre application

Pour utiliser l’optimisation guidée par profil, procédez comme suit pour optimiser votre application :

- Compilez un ou plusieurs fichiers de code source avec [/GL](reference/gl-whole-program-optimization.md).

   Chaque module généré avec **/GL** peut être examiné pendant les séries de tests d’optimisation guidée par profil pour capturer le comportement au moment de l’exécution. Chaque module dans une génération d’optimisation guidée par profil n’a pas besoin d’être compilé avec **/GL**. Toutefois, seuls les modules compilés avec **/GL** sont instrumentés et sont disponibles ultérieurement pour les optimisations guidées par profil.

- Liez en utilisant [/LTCG](reference/ltcg-link-time-code-generation.md) et [/GENPROFILE ou/FASTGENPROFILE](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md).

   L’utilisation de **/LTCG** et **/GENPROFILE** ou de **/FASTGENPROFILE** crée un `.pgd` fichier lors de l’exécution de l’application instrumentée. Une fois que les données de série de tests ont été ajoutées au `.pgd` fichier, elles peuvent être utilisées comme entrée pour l’étape de lien suivante (création de l’image optimisée). Lorsque vous spécifiez **/GENPROFILE**, vous pouvez éventuellement ajouter un argument **PGD =**_filename_ pour spécifier un nom ou un emplacement par défaut pour le `.pgd` fichier. La combinaison des options de l’éditeur de liens **/LTCG** et **/GENPROFILE** ou **/FASTGENPROFILE** remplace l’option de l’éditeur de liens **/LTCG : PGINSTRUMENT** déconseillée.

- Profilez l'application.

   À chaque fois qu’une session EXE profilée se termine ou qu’une DLL profilée est déchargée, un `appname!N.pgc` fichier est créé. Un `.pgc` fichier contient des informations sur une série de tests d’application particulière. *appname* est le nom de votre application et *N* est un nombre commençant par 1 qui est incrémenté en fonction du nombre d’autres `appname!N.pgc` fichiers dans le répertoire. Vous pouvez supprimer un `.pgc` fichier si la série de tests ne représente pas un scénario que vous souhaitez optimiser.

   Pendant une série de tests, vous pouvez forcer la fermeture du fichier actuellement ouvert `.pgc` et la création d’un nouveau `.pgc` fichier avec l’utilitaire [pgosweep](pgosweep.md) (par exemple, lorsque la fin d’un scénario de test ne coïncide pas avec l’arrêt de l’application).

   Votre application peut également appeler directement une fonction PGO, [PgoAutoSweep](pgoautosweep.md), pour capturer les données de profil au moment de l’appel sous la forme d’un `.pgc` fichier. Il peut vous offrir un contrôle plus précis du code couvert par les données capturées dans vos `.pgc` fichiers. Pour obtenir un exemple d’utilisation de cette fonction, consultez la documentation [PgoAutoSweep](pgoautosweep.md) .

   Lorsque vous créez votre Build instrumentée, par défaut, la collecte de données est effectuée en mode non thread-safe, ce qui est plus rapide, mais peut être imprécis. En utilisant l’argument **exact** de **/GENPROFILE** ou **/FASTGENPROFILE**, vous pouvez spécifier la collecte des données en mode thread-safe, ce qui est plus précis, mais plus lent. Cette option est également disponible si vous définissez la variable d’environnement [PogoSafeMode](environment-variables-for-profile-guided-optimizations.md#pogosafemode) déconseillée, ou l’option de l’éditeur de liens **/POGOSAFEMODE** déconseillée, lorsque vous créez votre Build instrumentée.

- Liez en utilisant **/LTCG** et **/USEPROFILE**.

   Utilisez les options de l’éditeur de liens **/LTCG** et [/USEPROFILE](reference/useprofile.md) pour créer l’image optimisée. Cette étape prend comme entrée le `.pgd` fichier. Lorsque vous spécifiez **/USEPROFILE**, vous pouvez éventuellement ajouter un argument **PGD =**_filename_ pour spécifier un nom ou un emplacement non défini par défaut pour le `.pgd` fichier. Vous pouvez également spécifier ce nom à l’aide de l’option de l’éditeur de liens **/PGD** déconseillée. La combinaison de **/LTCG** et **/USEPROFILE** remplace les options de l’éditeur de liens **/LTCG : PGOPTIMIZE** et **/LTCG : PGUPDATE** déconseillées.

Il est même possible de créer le fichier exécutable optimisé et de déterminer ultérieurement que le profilage supplémentaire est utile pour créer une image plus optimisée. Si l’image instrumentée et son `.pgd` fichier sont disponibles, vous pouvez effectuer des séries de tests supplémentaires et régénérer l’image optimisée avec le fichier plus récent `.pgd` , en utilisant les mêmes options de l’éditeur de liens **/LTCG** et **/USEPROFILE** .

> [!NOTE]
> Les `.pgc` `.pgd` fichiers et sont des types de fichiers binaires. Si elles sont stockées dans un système de contrôle de code source, évitez toute transformation automatique qui peut être transmise à des fichiers texte.

## <a name="optimizations-performed-by-pgo"></a>Optimisations effectuées par PGO

Les optimisations guidées par profil incluent les vérifications et les améliorations suivantes :

- **Inline** : par exemple, si une fonction appelle fréquemment la fonction b et que la fonction b est relativement petite, les optimisations guidées par profil sont Inline avec la fonction b dans la fonction a.

- **Spéculation virtuelle des appels** : si un appel virtuel, ou un autre appel via un pointeur de fonction, cible souvent une certaine fonction, une optimisation guidée par profil peut insérer un appel direct exécuté de manière conditionnelle à la fonction fréquemment ciblée, et l’appel direct peut être Inline.

- **Enregistrer l’allocation** : l’optimisation basée sur les données de profil entraîne une meilleure allocation des registres.

- **Optimisation** des blocs de base : l’optimisation des blocs de base permet d’insérer dans le même jeu de pages (Localité) des blocs de base couramment exécutés dans un frame donné. Cela réduit le nombre de pages utilisées, ce qui réduit la surcharge de mémoire.

- **Optimisation de la taille/vitesse** : les fonctions dans lesquelles le programme passe le plus de temps d’exécution peuvent être optimisées pour la vitesse.

- **Disposition des fonctions** : selon le graphique des appels et le comportement de l’appelant/appelé profilé, les fonctions qui ont tendance à se trouver le long du même chemin d’exécution sont placées dans la même section.

- **Optimisation des branches conditionnelles** : avec les sondes de valeur, les optimisations guidées par profil peuvent déterminer si une valeur donnée dans une instruction switch est utilisée plus souvent que d’autres valeurs.  Cette valeur peut ensuite être tirée de l’instruction switch.  Il en va de même pour les **`if`** instructions... **`else`** dans lesquelles l’optimiseur peut commander le **`if`** ... de **`else`** sorte que le **`if`** bloc ou soit **`else`** placé en premier, en fonction du bloc qui est plus souvent true.

- **Séparation du code mort** : le code qui n’est pas appelé pendant le profilage est déplacé vers une section spéciale qui est ajoutée à la fin de l’ensemble de sections. En fait, cette section est conservée dans les pages les plus fréquemment utilisées.

- **Séparation du code EH** -étant donné que le code EH n’est exécuté que de façon exceptionnelle, il peut souvent être déplacé vers une section distincte. Elle est déplacée lorsque les optimisations guidées par profil peuvent déterminer que les exceptions se produisent uniquement dans des conditions exceptionnelles.

- Les **intrinsèques de mémoire** , qu’il s’agisse d’étendre ou non un intrinsèque, dépendent du fait qu’il est fréquemment appelé. Un élément intrinsèque peut également être optimisé en fonction de la taille de bloc des déplacements ou des copies.

## <a name="next-steps"></a>Étapes suivantes

En savoir plus sur ces variables d’environnement, fonctions et outils que vous pouvez utiliser dans les optimisations guidées par profil :

[Variables d’environnement pour les optimisations guidées par profil](environment-variables-for-profile-guided-optimizations.md)<br/>
Ces variables ont été utilisées pour spécifier le comportement au moment de l’exécution des scénarios de test. Elles sont désormais dépréciées et remplacées par de nouvelles options de l’éditeur de liens. Ce document vous montre comment passer des variables d’environnement aux options de l’éditeur de liens.

[PgoAutoSweep](pgoautosweep.md)<br/>
Fonction que vous pouvez ajouter à votre application pour fournir un `.pgc` contrôle de capture de données de fichier affiné.

[pgosweep](pgosweep.md)<br/>
Un utilitaire de ligne de commande qui écrit toutes les données de profil dans le `.pgc` fichier, ferme le `.pgc` fichier et ouvre un nouveau `.pgc` fichier.

[pgomgr](pgomgr.md)<br/>
Utilitaire de ligne de commande qui ajoute des données de profil à partir d’un ou de plusieurs `.pgc` fichiers dans le `.pgd` fichier.

[Procédure : Fusionner plusieurs profils PGO en un seul profil](how-to-merge-multiple-pgo-profiles-into-a-single-profile.md)<br/>
Exemples d’utilisation de **pgomgr** .

## <a name="see-also"></a>Voir aussi

[Outils de build MSVC supplémentaires](reference/c-cpp-build-tools.md)
