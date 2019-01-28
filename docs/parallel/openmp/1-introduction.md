---
title: 1. Introduction
ms.date: 01/16/2019
ms.assetid: c42e72bc-0e31-4b1c-b670-cd82673c0c5a
ms.openlocfilehash: 8c735408bdf9f9a13693bd0ad25df185bb1db42a
ms.sourcegitcommit: 382e247c0f1b4cb7c2dab837b8b6fdff24bff47a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2019
ms.locfileid: "55087273"
---
# <a name="1-introduction"></a>1. Introduction

Ce document spécifie une collection de directives de compilateur, les fonctions de bibliothèque et les variables d’environnement que vous pouvez utiliser pour spécifier le parallélisme de mémoire partagée dans les programmes C et C++. La fonctionnalité décrite dans ce document est collectivement appelée le *OpenMP C/C++ Interface API (Application Program)*. L’objectif de cette spécification est de fournir un modèle de programmation parallèle qui permet à un programme soit portable sur des architectures de mémoire partagée à partir de différents fournisseurs. Compilateurs de nombreux fournisseurs prennent en charge l’API C/C++ OpenMP. Plus d’informations sur OpenMP, y compris le *OpenMP Fortran Application Program Interface*, vous pouvez trouver sur le site web suivant :

[https://www.openmp.org](https://www.openmp.org)

Les directives, les fonctions de bibliothèque et les variables d’environnement définies dans ce document permettent de créer et gérer tout en autorisant la portabilité des programmes parallèles. Les directives étendent le C et C++ séquentiel modèle de programmation avec plusieurs données (SPMD) construit de programme unique, de constructions de partage de travail et de constructions de synchronisation. Ils prennent également en charge le partage et la privatisation de données. Les compilateurs qui prennent en charge les API C++ OpenMP C incluent une option de ligne de commande du compilateur qui active et permet l’interprétation de toutes les directives de compilateur OpenMP.

## <a name="11-scope"></a>1.1 Portée

Cette spécification couvre uniquement parallélisation dirigé par l’utilisateur, dans laquelle vous définissez explicitement les actions que le compilateur et prendre de système d’exécution pour exécuter le programme en parallèle. Les implémentations OpenMP C et C++ ne sont pas requises pour rechercher les dépendances, les conflits, des blocages, des conditions de concurrence ou autres problèmes qui résultent de l’exécution du programme incorrect. Il vous incombe de veiller à ce que l’application en utilisant les constructions OpenMP C et C++ API s’exécute correctement. La parallélisation automatique généré par le compilateur et les directives du compilateur afin de faciliter cette parallélisation ne sont pas abordés dans ce document.

## <a name="12-definition-of-terms"></a>1.2 définition des termes

Les termes suivants sont utilisés dans ce document :

- barrier

  Un point de synchronisation qui doivent atteindre pour tous les threads dans une équipe.  Chaque thread attend jusqu'à ce que tous les threads dans l’équipe arrivent à ce stade. Il existe des obstacles explicites identifiés par les directives et les barrières implicites créées par l’implémentation.

- construct

  Une construction est une instruction. Il se compose d’une directive, suivie d’un bloc structuré. Certaines directives ne font pas partie d’une construction. (Consultez *la directive openmp* dans [annexe C](c-openmp-c-and-cpp-grammar.md)).

- directive

  Un C ou du C++ `#pragma` suivie du `omp` identificateur, d’autres textes et d’une nouvelle ligne. La directive spécifie le comportement du programme.

- étendue dynamique

  Toutes les instructions dans le *étendue lexicale*, ainsi que n’importe quelle instruction à l’intérieur d’une fonction qui est exécutée à la suite de l’exécution des instructions au sein de l’étendue lexicale. Une étendue dynamique est également appelée un *région*.

- étendue lexicale

  Instructions lexicalement contenues dans un *bloc structuré*.

- thread principal

  Le thread qui crée une équipe quand un *région parallèle* est entré.

- région parallèle

  Instructions qui lier à une construction parallèle OpenMP et peuvent être exécutées par plusieurs threads.

- private

  Une variable privée désigne un bloc de stockage qui est unique pour le thread qui effectue la référence. Il existe plusieurs façons de spécifier qu’une variable est privée : une définition dans une région parallèle, un `threadprivate` directive, un `private`, `firstprivate`, `lastprivate`, ou `reduction` clause, ou utilisation de la variable comme un `for`boucle variable de contrôle dans un `for` boucle qui suit immédiatement un `for` ou `parallel for` directive.

- region

  Une étendue dynamique.

- région de série

  Instructions exécutées uniquement par le *maître thread* en dehors de l’étendue dynamique de n’importe quel *région parallèle*.

- Sérialiser

  Exécution d’une construction parallèle avec :

  - une équipe de threads consistant en un seul thread (c'est-à-dire le thread principal pour cette construction parallèle),

  - série ordre d’exécution pour les instructions dans le bloc structuré (l’ordre comme si le bloc ne faisait pas partie d’une construction parallèle), et

  - aucun effet sur la valeur retournée par `omp_in_parallel()` (mis à part les effets de n’importe quel imbriqué constructions parallèles).

- partagés

  Une variable partagée désigne un bloc unique de stockage. Tous les threads qui accèdent à cette variable dans une équipe également accéder à ce bloc unique de stockage.

- bloc structuré

  Un bloc structuré est une instruction (unique ou composée) qui a une seule entrée et une sortie unique. S’il existe un saut dans ou hors d’une instruction, cette instruction est un bloc structuré. (Cette règle inclut un appel à `longjmp`(3C) ou l’utilisation de `throw`, même si un appel à `exit` est autorisée.) Si son exécution toujours commence à l’ouverture `{` et se termine toujours à la fermeture `}`, une instruction composée est un bloc structuré. Une instruction d’expression, une instruction de sélection, une instruction d’itération, ou `try` bloc est un bloc structuré si l’instruction composée correspondante obtenue en le plaçant dans `{` et `}` serait un bloc structuré. Une instruction de saut, une instruction étiquetée ou une instruction de déclaration n’est pas un bloc structuré.

- Équipe

  Un ou plusieurs threads coopérant dans l’exécution d’une construction.

- thread

  Une entité de l’exécution ayant un série flux de contrôle, un ensemble de variables privées et l’accès aux variables partagées.

- variable

  Un identificateur, éventuellement qualifié par espace de noms, qui désigne un objet.

## <a name="13-execution-model"></a>1.3 modèle d’exécution

OpenMP utilise le modèle de bifurcation-jointure de l’exécution en parallèle. Bien que ce modèle de bifurcation-jointure puisse être utile pour résoudre différents problèmes, il est conçu pour les grandes applications basée sur le tableau. OpenMP est destinée à prendre en charge les programmes qui s’exécutent correctement à la fois comme des programmes parallèles (nombre de threads d’exécution et un OpenMP complète prennent en charge de bibliothèque). Il est également pour les programmes qui s’exécutent correctement de manière séquentielles programmes (directives ignorées et une bibliothèque de stubs OpenMP simple). Toutefois, il est possible et autorisés à développer un programme qui ne se comporte pas correctement lors de l’exécution de manière séquentielle. En outre, différents degrés de parallélisme peuvent entraîner des résultats numériques différents en raison de modifications dans l’association d’opérations numériques. Par exemple, une réduction de la série d’addition peut avoir un modèle différent d’associations d’ajout à une réduction en parallèle. Ces différentes associations peuvent changer les résultats de l’addition à virgule flottante.

Un programme écrit avec l’API C/C++ OpenMP commence à s’exécuter en tant qu’un seul thread d’exécution appelé le *maître thread*. Le thread principal s’exécute dans une région série jusqu'à ce que la première construction parallèle est rencontrée. Dans l’API OpenMP C/C++, la `parallel` directive constitue une construction parallèle. Lorsqu’une construction parallèle est rencontrée, le thread principal crée une équipe de threads et le maître devient le maître de l’équipe. Chaque thread dans l’équipe exécute les instructions de l’extension dynamique d’une région parallèle, sauf pour les constructions de partage de travail. Tous les threads de l’équipe doivent rencontrer des constructions de partage de travail dans le même ordre, et un ou plusieurs threads exécute les instructions dans le bloc structuré associé. Le cloisonnement impliqué à la fin d’une construction de partage de travail sans un `nowait` clause est exécutée par tous les threads dans l’équipe.

Si un thread modifie un objet partagé, elle affecte non seulement son propre environnement d’exécution, mais aussi celles des autres threads dans le programme. La modification est garantie être complète, à partir du point de vue d’un autre thread, au point de séquence suivant (comme défini dans la langue de base) uniquement si l’objet est déclaré comme étant volatile. Sinon, la modification est garantie être terminée une fois que tout d’abord la modification des threads. Consultez les autres threads puis (ou simultanément) un `flush` directive qui spécifie l’objet (implicitement ou explicitement). Lorsque le `flush` directives sont implicites par d’autres directives OpenMP ne garantissent pas le classement correct des effets secondaires, il est la responsabilité du programmeur pour fournir supplémentaires, explicite `flush` directives.

À l’achèvement de la construction parallèle, les threads dans l’équipe synchroniser à une barrière implicite, et seul le thread principal continue l’exécution. N’importe quel nombre de constructions parallèle peut être spécifié dans un seul programme. Par conséquent, un programme peut répliquer et joindre autant de fois pendant l’exécution.

L’API C/C++ OpenMP permet aux programmeurs d’utiliser des directives dans les fonctions appelées à partir de constructions parallèles. Les directives qui n’apparaissent pas dans l’étendue lexicale d’une construction parallèle, mais peuvent se trouver dans l’étendue dynamique sont appelés *orphelins* directives. Directives orphelins, les programmeurs qui peuvent d’exécuter des parties principales de leur programme en parallèle, avec uniquement des modifications minimales pour le programme séquentiel. Avec cette fonctionnalité, vous pouvez coder des constructions parallèles à des niveaux supérieurs de l’arborescence des appels programme et utiliser des directives pour contrôler l’exécution dans les fonctions appelées.

Fonctions qui écrivent dans le même fichier de sortie dans lequel les données écrites par différents threads s’affiche dans un ordre non déterministe peuvent entraîner de sortie des appels non synchronisés à C et C++. De même, les appels non synchronisés à entrer des fonctions qui lisent à partir du même fichier peuvent lire les données dans un ordre non déterministe. Utilisation non synchronisée d’e/s, telle que chaque thread accède à un autre fichier, produit les mêmes résultats que l’exécution en série des fonctions d’e/s.

## <a name="14-compliance"></a>1.4 Conformité

Une implémentation de l’API C/C++ OpenMP est *compatibles OpenMP* si il reconnaît et conserve la sémantique de tous les éléments de cette spécification, tels que définis dans les chapitres 1, 2, 3, 4, et concernent l’annexe C. annexes A, B, D, E et F informations uniquement et ne font pas partie de la spécification. Les implémentations qui incluent uniquement un sous-ensemble de l’API ne sont pas compatibles avec OpenMP.

Les API C++ OpenMP C est une extension à la langue de base qui est pris en charge par une implémentation. Si la langue de base ne prend en charge une construction de langage ou une extension qui s’affiche dans ce document, l’implémentation d’OpenMP n’est pas requis pour prendre en charge.

Toutes les fonctions de bibliothèque standard C et C++ et les fonctions intégrées (autrement dit, les fonctions dont le compilateur connaît le spécifique) doit être thread-safe. Non synchronisé l’utilisation des fonctions de thread-safe par différents threads à l’intérieur d’une région parallèle ne produit pas un comportement non défini. Toutefois, le comportement peut-être pas les mêmes que dans une région de série. (Une fonction de génération de nombres aléatoires est un exemple.)

L’API C/C++ OpenMP Spécifie que certains comportements est *défini par l’implémentation.* Une implémentation conforme de OpenMP est nécessaire pour définir et documenter son comportement dans ces cas. Pour obtenir la liste de comportements définis par l’implémentation, consultez [annexe E](e-implementation-defined-behaviors-in-openmp-c-cpp.md).

## <a name="15-normative-references"></a>1.5 références normatives

- ISO/IEC 9899 : 1999, *informations technologie - langages de programmation - C*. Cette spécification de l’API OpenMP fait référence à la norme ISO/IEC 9899 : 1999 comme C99.

- 9899 : 1990 de la norme ISO/IEC, *informations technologie - langages de programmation - C*. Cette spécification de l’API OpenMP appelle 9899 : 1990 de la norme ISO/IEC C90.

- ISO/IEC 14882:1998, *C++ de technologie - langages de programmation - informations*. Cette spécification de l’API OpenMP fait référence à la norme ISO/IEC 14882:1998 en C++.

Lorsque cette spécification de l’API OpenMP fait référence à C, il est fait référence à la langue de base pris en charge par l’implémentation.

## <a name="16-organization"></a>1.6 Organisation

- [Fonctions de bibliothèque du Run-time](3-run-time-library-functions.md)
- [Variables d’environnement](4-environment-variables.md)
- [Comportements définis par l’implémentation dans OpenMP C/C++](e-implementation-defined-behaviors-in-openmp-c-cpp.md)
- [Nouvelles fonctionnalités dans OpenMP C/C++ version 2.0](f-new-features-and-clarifications-in-version-2-0.md)
