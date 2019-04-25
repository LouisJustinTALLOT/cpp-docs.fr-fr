---
title: Erreur des outils Éditeur de liens LNK1318
ms.date: 05/29/2018
f1_keywords:
- LNK1318
helpviewer_keywords:
- LNK1318
ms.openlocfilehash: 8ed6489a27d4c0e117f7f18281ff188f40936e0a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160989"
---
# <a name="linker-tools-error-lnk1318"></a>Erreur des outils Éditeur de liens LNK1318

> Erreur PDB inattendue ; *provoquer* '*détails*'

L’éditeur de liens a rencontré une erreur inattendue lors de l’ouverture, de lecture ou écriture dans un fichier PDB.

Ce message d’erreur est généré pour les problèmes rares dans les fichiers PDB. Le *provoquer* et *détails* représentent les informations disponibles à l’éditeur de liens lors de la défaillance s’est produite. Cela ne seront peut-être pas très utile, comme les erreurs courantes lors du traitement des fichiers PDB ont des messages d’erreur distincts et plus informatif.

Étant donné que la source de l’erreur est rare, uniquement les conseils générique est disponible pour résoudre ce problème :

- Effectuer une opération de nettoyage dans vos répertoires de build, puis effectuez une génération complète de votre solution.

- Redémarrez votre ordinateur, ou recherchez les processus de mspdbsrv.exe isolée ou suspendue et les arrêter dans TaskManager.

- Désactiver les vérifications antivirus dans vos répertoires de projet.

- Utilisez le [/Zf](../../build/reference/zf.md) option du compilateur si vous utilisez [/MP](../../build/reference/mp-build-with-multiple-processes.md) processus de génération avec MSBuild, ou un autre parallèle.

- Tentez une génération à l’aide de l’ensemble d’outils hébergé 64 bits.

- Sérialiser la liaison pour atténuer les problèmes de lien parallèles si nécessaire. Cette erreur peut être provoquée si mspdbsrv.exe est lancée par une instance de liaison et est arrêtée avant une autre instance de liaison est effectuée à l’utiliser. L’inconvénient de ce correctif est que vos builds de projet peuvent prendre beaucoup plus de temps.