---
title: Erreur des outils Éditeur de liens LNK1318
ms.date: 05/29/2018
f1_keywords:
- LNK1318
helpviewer_keywords:
- LNK1318
ms.openlocfilehash: a61c11a9cbb25fea6fddc0bf1c5c4c2a7af1cf4f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183577"
---
# <a name="linker-tools-error-lnk1318"></a>Erreur des outils Éditeur de liens LNK1318

> Erreur PDB inattendue ; *cause* «*Détails*»

L’éditeur de liens a rencontré une erreur inattendue lors de l’ouverture, de la lecture ou de l’écriture dans un fichier PDB.

Ce message d’erreur est généré pour les problèmes rares dans les fichiers PDB. La *cause* et les *Détails* représentent les informations disponibles pour l’éditeur de liens lorsque l’échec s’est produit. Cela peut ne pas être très utile, car des erreurs courantes lors du traitement des fichiers PDB contiennent des messages d’erreur plus explicites et plus informatifs.

Étant donné que la source de l’erreur n’est pas courante, il n’existe que des conseils génériques pour la résolution de ce problème :

- Effectuez une opération de nettoyage dans vos répertoires de build, puis effectuez une génération complète de votre solution.

- Redémarrez votre ordinateur, ou recherchez les processus mspdbsrv. exe isolés ou bloqués, puis supprimez-les dans TaskManager.

- Désactivez les vérifications antivirus dans les répertoires de votre projet.

- Utilisez l’option de compilateur [/ZF](../../build/reference/zf.md) si vous utilisez [/MP](../../build/reference/mp-build-with-multiple-processes.md) avec MSBuild ou un autre processus de génération parallèle.

- Essayez de générer à l’aide de l’ensemble d’outils hébergé 64 bits.

- Sérialisez la liaison pour atténuer les problèmes de liaison parallèle, si nécessaire. Cette erreur peut être provoquée si mspdbsrv. exe est lancé par une instance de Link et s’arrête avant qu’une autre instance de Link ne l’utilise. L’inconvénient de ce correctif est que l’exécution de votre projet peut prendre beaucoup plus de temps.
