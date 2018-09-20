---
title: Tableau, répertorier et mapper les Classes | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.mfc
dev_langs:
- C++
helpviewer_keywords:
- arrays [MFC], classes
- list classes [MFC]
- collection classes [MFC], maps
- map classes [MFC]
- collection classes [MFC], lists
ms.assetid: 81a13a7f-0c2c-4efd-b6bb-b4e624a0743d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a8d044f8844fdf46969342d1b4fc5cf2f007c041
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46436336"
---
# <a name="array-list-and-map-classes"></a>Classes de tableaux, listes et mappages

Pour gérer des agrégats de données, la bibliothèque de classes fournit un groupe de classes de collection (tableaux, listes et mappages) pouvant contenir différents types d’objets et types prédéfinis. Les collections sont dimensionnées de manière dynamique. Ces classes peuvent être utilisées dans n'importe quel programme écrit pour Windows ou non. Toutefois, elles sont plus utiles pour implémenter les structures de données qui définissent les classes de votre document dans le framework d'application. Vous pouvez facilement dériver les classes de collection spécialisées à partir de ces éléments, ou vous pouvez les créer en fonction des classes du modèle. Pour plus d’informations sur ces approches, consultez l’article [Collections](../mfc/collections.md). Pour obtenir la liste des classes de collection de modèle, consultez l’article [Classes de modèle pour les tableaux, listes et mappages](../mfc/template-classes-for-arrays-lists-and-maps.md).

Les tableaux sont des structures de données unidimensionnelles stockées en mémoire de manière contiguë. Ils prennent en charge l'accès aléatoire très rapide (RAM) puisque l'adresse mémoire d'un élément donné peut être calculée en multipliant l'index de l'élément par la taille d'un élément et en ajoutant le résultat à l'adresse de base du tableau. Les tableaux sont très coûteux si vous devez insérer des éléments dans le tableau, puisque le tableau entier après l'élément inséré doit être déplacé pour libérer de l'espace pour l'élément à insérer. Les tableaux peuvent être développés et réduits selon les besoins.

Les listes sont similaires aux tableaux mais elles sont stockées différemment. Chaque élément d'une liste inclut également un pointeur vers les éléments précédents et suivants, ce qui en fait une liste doublement liée. Il est très rapide d'ajouter ou de supprimer des éléments car cela implique seulement de modifier quelques pointeurs. Toutefois, la recherche d'une liste peut être coûteuse puisque toutes les recherches doivent commencer à l'une des fins de la liste.

Les mappages lient une valeur clé à une valeur de données. Par exemple, la clé d'un mappage peut être une chaîne et les données peuvent correspondre à des pointeurs au sein d'une liste. Vous demanderiez au mappage de vous donner le pointeur associé à une chaîne spécifique. Les recherches de mappage sont rapides car les mappages utilisent des tables de hachage pour les recherches de clés. Ajouter et supprimer des éléments est aussi rapide. Les mappages sont souvent utilisés avec d'autres structures de données en tant qu'index auxiliaires. MFC utilise un type spécial de mappage appelé un [table des messages](../mfc/mapping-messages.md) pour mapper les messages Windows à un pointeur vers la fonction de gestionnaire pour ce message.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../mfc/class-library-overview.md)

