---
title: 1.2 définition des termes | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: fcaa8eb8-bbbf-4a24-ad0e-e299c442db79
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e95ad940aac14892ac14e8d56ba64f49d0bbf7c0
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46423830"
---
# <a name="12-definition-of-terms"></a>1.2 Définition des termes

Les termes suivants sont utilisés dans ce document :

- barrier

   Un point de synchronisation qui doit être accessible par tous les threads dans une équipe.  Chaque thread attend jusqu'à ce que tous les threads dans l’équipe arrivent à ce stade. Il existe des obstacles explicites identifiés par les directives et les barrières implicites créées par l’implémentation.

- construct

   Une construction est une instruction. Il se compose d’une directive et le bloc structuré suivant. Notez que certaines directives ne font pas partie d’une construction. (Consultez *la directive openmp* dans [annexe C](../../parallel/openmp/c-openmp-c-and-cpp-grammar.md)).

- directive

   Un C ou du C++ **#pragma** suivie de la **omp** identificateur, d’autres textes et d’une nouvelle ligne. La directive spécifie le comportement du programme.

- étendue dynamique

   Toutes les instructions dans le *étendue lexicale*, ainsi que n’importe quelle instruction à l’intérieur d’une fonction qui est exécutée à la suite de l’exécution des instructions au sein de l’étendue lexicale. Une étendue dynamique est également appelée un *région*.

- étendue lexicale

   Instructions lexicalement contenues dans un *bloc structuré*.

-  thread principal

   Le thread qui crée une équipe quand un *région parallèle* est entré.

- région parallèle

   Instructions qui peuvent être exécutées par plusieurs threads et les lier à une construction parallèle OpenMP.

- private

   Une variable privée désigne un bloc de stockage qui est unique pour le thread qui effectue la référence. Notez qu’il existe plusieurs façons de spécifier qu’une variable est privée : une définition dans une région parallèle, un **threadprivate** directive, un **privé**, **firstprivate**, **lastprivate**, ou **réduction** clause, ou utilisation de la variable comme un **pour**variable de contrôle de boucle dans un **pour** boucle qui suit immédiatement un **pour** ou **parallèles pour** la directive.

- region

   Une étendue dynamique.

- région de série

   Instructions exécutées uniquement par le *maître thread* en dehors de l’étendue dynamique de n’importe quel *région parallèle*.

- Sérialiser

   Pour exécuter une construction parallèle avec une équipe de threads consistant en un seul thread (c'est-à-dire le thread principal pour cette construction parallèle), série ordre d’exécution pour les instructions dans le bloc structuré (le même ordre comme si le bloc n’ont pas été partie d’une construction parallèle) et sans aucune incidence sur la valeur retournée par **omp_in_parallel()** (mis à part les effets de n’importe quel imbriqué constructions parallèles).

- partagés

   Une variable partagée désigne un bloc unique de stockage. Tous les threads dans une équipe qui accèdent à cette variable accède à ce bloc unique de stockage.

- bloc structuré

   Un bloc structuré est une instruction (unique ou composée) qui a une seule entrée et une sortie unique. Aucune instruction n’est un bloc structuré s’il existe un saut dans ou hors de cette instruction (y compris un appel à **longjmp**(3C) ou l’utilisation de **lever**, mais un appel à **quitter** est autorisée). Une instruction composée est un bloc structuré si son exécution toujours commence à l’ouverture **{** et se termine toujours à la fermeture **}**. Une instruction d’expression, une instruction de sélection, une instruction d’itération, ou **essayez** bloc est un bloc structuré si l’instruction composée correspondante obtenue en le plaçant dans **{** et **}** serait un bloc structuré. Une instruction de saut, une instruction étiquetée ou une instruction de déclaration n’est pas un bloc structuré.

-  Équipe

   Un ou plusieurs threads coopérant dans l’exécution d’une construction.

- thread

   Une entité de l’exécution ayant un série flux de contrôle, un ensemble de variables privées et l’accès aux variables partagées.

- variable

   Un identificateur, éventuellement qualifié par espace de noms, qui désigne un objet.
