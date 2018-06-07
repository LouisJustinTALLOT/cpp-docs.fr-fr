---
title: LNK1318 d’erreur des outils Éditeur de liens | Documents Microsoft
ms.custom: ''
ms.date: 05/29/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1318
dev_langs:
- C++
helpviewer_keywords:
- LNK1318
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 364c819c6ec2bf6e1195011eced6e6ad1699877b
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34570686"
---
# <a name="linker-tools-error-lnk1318"></a>L’éditeur de liens outils erreur LNK1318

> Erreur inattendue PDB ; *provoquer* '*détails*'

L’éditeur de liens a rencontré une erreur inattendue lors de l’ouverture, la lecture ou écriture dans un fichier PDB.

Ce message d’erreur est généré pour des problèmes rares dans des fichiers PDB. Le *provoquer* et *détails* représentent les informations disponibles pour l’éditeur de liens lors de la défaillance s’est produite. Cela ne seront peut-être pas très utile, comme les erreurs courantes lors du traitement de fichiers PDB ont des messages d’erreur distincts et plus informatif.

Étant donné que la source de l’erreur est rare, uniquement les conseils générique est disponible pour résoudre ce problème :

- Effectuer une opération de nettoyage dans vos répertoires de build, puis effectuez une génération complète de votre solution.

- Redémarrez votre ordinateur, ou recherchez les processus de mspdbsrv.exe perdus ou bloqués et éliminer dans TaskManager.

- Désactiver les vérifications antivirues dans vos répertoires de projet.

- Utilisez le [/Zf](../../build/reference/zf.md) option du compilateur si vous utilisez [/MP](../../build/reference/mp-build-with-multiple-processes.md) processus de génération avec MSBuild ou un autre parallèle.

- Tentez une génération à l’aide de l’ensemble d’outils hébergé 64 bits.

- Sérialiser la liaison pour atténuer les problèmes de liaison parallèle si nécessaire. Cette erreur peut être provoquée si mspdbsrv.exe est lancée par une instance de liaison et est arrêté avant de procéder à une autre instance de liaison à l’utiliser. L’inconvénient de ce correctif est que vos builds de projet peuvent prendre beaucoup plus de temps.