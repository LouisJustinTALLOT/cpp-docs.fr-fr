---
title: 1. Introduction
ms.date: 01/16/2019
ms.assetid: c42e72bc-0e31-4b1c-b670-cd82673c0c5a
ms.openlocfilehash: e2857565f7838ae45ff88ea53ba714e1418116ff
ms.sourcegitcommit: f2a135d69a2a8ef1777da60c53d58fe06980c997
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2020
ms.locfileid: "87521172"
---
# <a name="1-introduction"></a>1. Introduction

Ce document spécifie une collection de directives de compilateur, de fonctions de bibliothèque et de variables d’environnement que vous pouvez utiliser pour spécifier le parallélisme de mémoire partagée dans les programmes C et C++. La fonctionnalité décrite dans ce document est collectivement connue sous le nom d' *interface de programmation d’applications (API) OpenMP C/C++*. L’objectif de cette spécification est de fournir un modèle de programmation parallèle qui permet à un programme d’être portable sur des architectures de mémoire partagée de différents fournisseurs. Les compilateurs de nombreux fournisseurs prennent en charge l’API C/C++ OpenMP. Vous trouverez plus d’informations sur OpenMP, y compris l' *interface du programme d’application Fortran OpenMP*, sur le site Web suivant :

[https://www.openmp.org](https://www.openmp.org)

Les directives, les fonctions de bibliothèque et les variables d’environnement définies dans ce document vous permettent de créer et de gérer des programmes parallèles tout en autorisant la portabilité. Les directives étendent le modèle de programmation séquentielle C et C++ à l’aide de constructions de données à programme unique (SPMD), de constructions de partage de travail et de constructions de synchronisation. Ils prennent également en charge le partage et la privatisation des données. Les compilateurs qui prennent en charge l’API C et C++ OpenMP incluent une option de ligne de commande pour le compilateur qui active et autorise l’interprétation de toutes les directives de compilateur OpenMP.

## <a name="11-scope"></a>1.1 Portée

Cette spécification couvre uniquement la parallélisation dirigée par l’utilisateur, dans laquelle vous définissez explicitement les actions que le compilateur et le système d’exécution prennent pour exécuter le programme en parallèle. Les implémentations d’OpenMP C et C++ ne sont pas requises pour vérifier les dépendances, les conflits, les blocages, les conditions de concurrence ou d’autres problèmes qui entraînent une exécution incorrecte du programme. Vous êtes chargé de vérifier que l’application qui utilise les constructions de l’API C et C++ OpenMP s’exécute correctement. Les directives et la parallélisation automatiques générées par le compilateur au compilateur pour faciliter cette parallélisation ne sont pas abordées dans ce document.

## <a name="12-definition-of-terms"></a>1,2 définition des termes

Les termes suivants sont utilisés dans ce document :

- barrier

  Point de synchronisation que tous les threads d’une équipe doivent atteindre.  Chaque thread attend que tous les threads de l’équipe arrivent à ce stade. Il existe des barrières explicites identifiées par les directives et les barrières implicites créées par l’implémentation.

- construct

  Une construction est une instruction. Il se compose d’une directive, suivie d’un bloc structuré. Certaines directives ne font pas partie d’une construction. (Consultez *OpenMP-directive* dans [l’annexe C](c-openmp-c-and-cpp-grammar.md)).

- directive

  C ou C++ `#pragma` suivi de l' `omp` identificateur, d’un autre texte et d’une nouvelle ligne. La directive spécifie le comportement du programme.

- étendue dynamique

  Toutes les instructions dans l' *étendue lexicale*, plus toute instruction à l’intérieur d’une fonction exécutée à la suite de l’exécution d’instructions dans l’étendue lexicale. Une étendue dynamique est également appelée une *région*.

- étendue lexicale

  Les instructions sont détenues lexicalement au sein d’un *bloc structuré*.

- thread principal

  Thread qui crée une équipe lorsqu’une *région parallèle* est entrée.

- région parallèle

  Les instructions qui créent une liaison à une construction parallèle OpenMP et peuvent être exécutées par de nombreux threads.

- private

  Une variable privée désigne un bloc de stockage propre au thread qui fait la référence. Il existe plusieurs façons de spécifier qu’une variable est privée : une définition dans une région parallèle, une `threadprivate` directive, une `private` `firstprivate` clause,,, `lastprivate` ou `reduction` , ou utiliser la variable en tant que **`for`** variable de contrôle de boucle dans une **`for`** boucle immédiatement après une `for` `parallel for` directive ou.

- region

  Une étendue dynamique.

- région série

  Instructions exécutées uniquement par le *thread principal* en dehors de l’étendue dynamique d’une *région parallèle*.

- serialize

  Pour exécuter une construction parallèle avec :

  - une équipe de threads composée d’un seul thread (qui est le thread principal pour cette construction parallèle),

  - ordre d’exécution séquentiel des instructions dans le bloc structuré (le même ordre que si le bloc ne fait pas partie d’une construction parallèle), et

  - aucun effet sur la valeur retournée par `omp_in_parallel()` (à l’exception des effets de toutes les constructions parallèles imbriquées).

- partagés

  Une variable partagée désigne un bloc de stockage unique. Tous les threads d’une équipe qui accèdent à cette variable accèdent également à ce bloc de stockage unique.

- bloc structuré

  Un bloc structuré est une instruction (simple ou composée) qui a une seule entrée et une seule sortie. S’il y a un saut dans une instruction, cette instruction est un bloc structuré. (Cette règle comprend un appel à `longjmp` (3C) ou l’utilisation de `throw` , bien qu’un appel à `exit` soit autorisé.) Si son exécution commence toujours à l’ouverture `{` et se termine toujours à la fermeture `}` , une instruction composée est un bloc structuré. Une instruction d’expression, une instruction de sélection, une instruction d’itération ou un **`try`** bloc est un bloc structuré si l’instruction composée correspondante obtenue en la mettant dans `{` et `}` serait un bloc structuré. Une instruction de saut, une instruction étiquetée ou une instruction de déclaration n’est pas un bloc structuré.

- team

  Un ou plusieurs threads coopèrent dans l’exécution d’une construction.

- thread

  Entité d’exécution ayant un contrôle de workflow série, un ensemble de variables privées et un accès aux variables partagées.

- variable

  Identificateur, éventuellement qualifié par des noms d’espaces de noms, qui désigne un objet.

## <a name="13-execution-model"></a>1,3 modèle d’exécution

OpenMP utilise le modèle de bifurcation-jointure de l’exécution parallèle. Bien que ce modèle de bifurcation-jointure puisse être utile pour la résolution de divers problèmes, il est adapté aux applications de grande taille. OpenMP est conçu pour prendre en charge les programmes qui s’exécutent correctement à la fois en tant que programmes parallèles (nombreux threads d’exécution et bibliothèque de prise en charge OpenMP complète). C’est également le cas pour les programmes qui s’exécutent correctement en tant que programmes séquentiels (directives ignorées et une simple bibliothèque de stubs OpenMP). Toutefois, il est possible et autorisé à développer un programme qui ne se comporte pas correctement lorsqu’il est exécuté de façon séquentielle. En outre, différents degrés de parallélisme peuvent entraîner des résultats numériques différents en raison des modifications apportées à l’Association des opérations numériques. Par exemple, une réduction de l’addition en série peut avoir un modèle d’associations d’addition différent de celui d’une réduction parallèle. Ces différentes associations peuvent modifier les résultats de l’addition à virgule flottante.

Un programme écrit avec l’API C/C++ OpenMP commence l’exécution comme un thread unique d’exécution appelé le *thread principal*. Le thread principal s’exécute dans une région de série jusqu’à ce que la première construction parallèle soit rencontrée. Dans l’API C/C++ OpenMP, la `parallel` directive constitue une construction parallèle. Lorsqu’une construction parallèle est rencontrée, le thread principal crée une équipe de threads, et le maître devient maître de l’équipe. Chaque thread de l’équipe exécute les instructions dans l’étendue dynamique d’une région parallèle, à l’exception des constructions de partage de travail. Tous les threads de l’équipe doivent rencontrer des constructions de partage de travail dans le même ordre, et un ou plusieurs threads exécutent les instructions dans le bloc structuré associé. La barrière impliquée à la fin d’une construction de partage de travail sans `nowait` clause est exécutée par tous les threads de l’équipe.

Si un thread modifie un objet partagé, il affecte non seulement son propre environnement d’exécution, mais également ceux des autres threads du programme. La modification est garantie pour être effectuée, du point de vue d’un autre thread, au point de séquence suivant (tel que défini dans la langue de base) uniquement si l’objet est déclaré comme volatile. Dans le cas contraire, la modification est garantie après la première modification du thread. Les autres threads (ou simultanément) voient une `flush` directive qui spécifie l’objet (implicitement ou explicitement). Lorsque les `flush` directives qui sont implicites par d’autres directives OpenMP ne garantissent pas le bon ordre des effets secondaires, il incombe au programmeur de fournir des directives explicites supplémentaires `flush` .

À la fin de la construction parallèle, les threads de l’équipe se synchronisent à un cloisonnement implicite, et seul le thread principal continue l’exécution. N’importe quel nombre de constructions parallèles peut être spécifié dans un programme unique. Par conséquent, un programme peut créer des branches et les joindre plusieurs fois pendant l’exécution.

L’API C/C++ OpenMP permet aux programmeurs d’utiliser des directives dans les fonctions appelées à partir de constructions parallèles. Les directives qui n’apparaissent pas dans l’étendue lexicale d’une construction parallèle mais peuvent se trouver dans l’étendue dynamique sont appelées directives *orphelines* . Avec les directives orphelines, les programmeurs peuvent exécuter des parties majeures de leur programme en parallèle, avec uniquement des modifications minimes du programme séquentiel. Avec cette fonctionnalité, vous pouvez coder des constructions parallèles aux niveaux supérieurs de l’arborescence des appels du programme et utiliser des directives pour contrôler l’exécution dans toutes les fonctions appelées.

Les appels non synchronisés aux fonctions de sortie C et C++ qui écrivent dans le même fichier peuvent générer une sortie dans laquelle les données écrites par différents threads s’affichent dans un ordre non déterministe. De même, les appels non synchronisés aux fonctions d’entrée qui lisent à partir du même fichier peuvent lire les données dans un ordre non déterministe. Utilisation non synchronisée des e/s, de telle sorte que chaque thread accède à un fichier différent, produit les mêmes résultats que l’exécution en série des fonctions d’e/s.

## <a name="14-compliance"></a>1.4 Conformité

Une implémentation de l’API C/C++ OpenMP est *conforme à la norme OpenMP* si elle reconnaît et conserve la sémantique de tous les éléments de cette spécification, comme indiqué dans les chapitres 1, 2, 3, 4 et annexe C. les annexes A, B, D, E et F sont fournies à titre d’information uniquement et ne font pas partie de la spécification. Les implémentations qui incluent uniquement un sous-ensemble de l’API ne sont pas conformes à OpenMP.

L’API C et C++ OpenMP est une extension du langage de base pris en charge par une implémentation. Si la langue de base ne prend pas en charge une construction ou une extension de langage qui apparaît dans ce document, l’implémentation OpenMP n’est pas nécessaire pour la prendre en charge.

Toutes les fonctions de la bibliothèque C et C++ standard et les fonctions intégrées (autrement dit, les fonctions dont le compilateur a des connaissances spécifiques) doivent être thread-safe. L’utilisation non synchronisée de fonctions thread-safe par différents threads à l’intérieur d’une région parallèle ne produit pas un comportement indéfini. Toutefois, le comportement peut ne pas être le même que dans une région de série. (Une fonction de génération de nombres aléatoires est un exemple.)

L’API C/C++ OpenMP spécifie que certains comportements sont *définis par l’implémentation.* Une implémentation OpenMP conforme est requise pour définir et documenter son comportement dans ces cas. Pour obtenir la liste des comportements définis par l’implémentation, consultez [l’annexe E](e-implementation-defined-behaviors-in-openmp-c-cpp.md).

## <a name="15-normative-references"></a>1,5 Références normatives

- ISO/IEC 9899:1999, *technologies de l’information-Langages de programmation-C*. Cette spécification de l’API OpenMP fait référence à la norme ISO/IEC 9899:1999 en tant que C99.

- ISO/IEC 9899:1990, *technologies de l’information-Langages de programmation-C*. Cette spécification de l’API OpenMP fait référence à la norme ISO/IEC 9899:1990 en tant que C90.

- ISO/IEC 14882:1998, *technologies de l’information-Langages de programmation-C++*. Cette spécification de l’API OpenMP fait référence à la norme ISO/IEC 14882:1998 en tant que C++.

Lorsque cette spécification d’API OpenMP fait référence à C, il est fait référence à la langue de base prise en charge par l’implémentation.

## <a name="16-organization"></a>1.6 Organisation

- [Fonctions de la bibliothèque du runtime](3-run-time-library-functions.md)
- [Variables d’environnement](4-environment-variables.md)
- [Comportements définis par l’implémentation dans OpenMP C/C++](e-implementation-defined-behaviors-in-openmp-c-cpp.md)
- [Nouvelles fonctionnalités de la version C/C++ OpenMP 2,0](f-new-features-and-clarifications-in-version-2-0.md)
