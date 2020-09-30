---
title: Erreur irrécupérable C1049
description: Décrit l’erreur irrécupérable du compilateur C1049, un argument numérique non valide et explique comment la résoudre.
ms.date: 11/04/2019
f1_keywords:
- C1049
helpviewer_keywords:
- C1049
ms.openlocfilehash: 9b3cbe5d081e32680e5408fc4a6ddcd932db77a2
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91503268"
---
# <a name="fatal-error-c1049"></a>Erreur irrécupérable C1049

> argument numérique non valide '*value*'

Le CL.EXE analyseur de ligne de commande a trouvé une *valeur* où il attendait un argument numérique.

Une erreur C1049 peut se produire lorsque le compilateur ne trouve pas d’argument numérique pour l’une des options de compilateur suivantes :

[/constexpr : profondeur](../../build/reference/constexpr-control-constexpr-evaluation.md)\
[/constexpr : suivi des traces](../../build/reference/constexpr-control-constexpr-evaluation.md)\
[/constexpr : étapes](../../build/reference/constexpr-control-constexpr-evaluation.md)

Les options du compilateur de ligne de commande qui attendent un argument numérique peuvent également signaler `Command line error D8004` , `Command line error D8021` ,, `Command line warning D9002` `Command line warning D9014` ou `Command line warning D9024` .

Pour résoudre cette erreur, examinez la ligne de commande à la recherche d’arguments introuvables ou manquants. Vérifiez qu’il n’y a pas d’espace blanc inattendu entre les options et les arguments. La dernière ligne de commande peut être générée par des macros, des variables d’environnement ou d’autres opérations du système de génération. C’est pourquoi il est important d’examiner la ligne de commande réelle passée au compilateur.

- Dans les fichiers de commandes ou les Makefiles, vous pouvez utiliser une commande **echo** pour signaler la ligne de commande réelle.

- Dans Visual Studio, ouvrez la boîte de dialogue **pages de propriétés** de votre projet. Sur la page **Propriétés de configuration**  >  **C/C++**  >  **général** , affectez la valeur **non**à la propriété supprimer la **bannière de démarrage** . Choisissez **OK** pour enregistrer vos modifications. La fenêtre **sortie** affiche maintenant la ligne de commande lors de la génération, juste après la ligne de copyright.

D’autres systèmes de génération peuvent avoir des fichiers journaux ou des options détaillées pour voir les commandes réelles utilisées. Pour plus d’informations, consultez la documentation de votre système de génération.
