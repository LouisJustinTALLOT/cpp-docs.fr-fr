---
title: Fichiers et flux | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- files [C++]
- streams
ms.assetid: f61e712b-eac9-4c28-bb18-97c3786ef387
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ca0850f0e798067ba48b59a1c2585b8ba87c5451
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46062174"
---
# <a name="files-and-streams"></a>Fichiers et flux

Un programme communique avec l'environnement cible en lisant et en écrivant dans des fichiers. Un fichier peut être :

- Un jeu de données que vous pouvez lire et écrire à plusieurs reprises.

- Un flux d'octets générés par un programme (tel qu'un pipeline).

- Un flux d'octets reçus ou envoyés à un périphérique.

Les deux derniers éléments sont des fichiers interactifs. Les fichiers sont généralement le principal moyen d'interaction avec un programme. Vous manipulez tous ces types de fichiers à peu près de la même manière en appelant des fonctions de la bibliothèque. Vous incluez l'en-tête standard STDIO.H pour déclarer la plupart de ces fonctions.

Pour pouvoir exécuter un grand nombre d'opérations sur un fichier, celui-ci doit être ouvert. L'ouverture d'un fichier l'associe à un flux, une structure de données dans la bibliothèque C standard qui ne tient pas compte de nombreuses différences entre les fichiers de différents types. La bibliothèque gère l'état de chaque flux dans un objet de type FILE.

L'environnement cible ouvre trois fichiers avant le démarrage du programme. Vous pouvez ouvrir un fichier en appelant la fonction de bibliothèque [fopen, _wfopen](../c-runtime-library/reference/fopen-wfopen.md) avec deux arguments. (La fonction `fopen` a été déconseillée, utilisez [fopen_s, _wfopen_s](../c-runtime-library/reference/fopen-s-wfopen-s.md) à la place.) Le premier argument est un nom de fichier. Le deuxième argument est une chaîne C, qui indique :

- Si vous prévoyez de lire les données du fichier, d'y écrire des données ou les deux.

- Si vous envisagez de générer un nouveau contenu pour le fichier (ou de créer un fichier s'il n'existait pas précédemment) ou de laisser le contenu existant en place.

- Si l'écriture dans un fichier peut modifier le contenu existant ou doit uniquement ajouter des octets à la fin du fichier.

- Si vous voulez manipuler un flux de texte ou un flux binaire.

Une fois le fichier ouvert, vous pouvez déterminer si le flux est orienté octet (un flux d'octets) ou orienté large (un flux large). Un flux est initialement indépendant. L'appel de certaines fonctions pour s'exécuter sur le flux le rend orienté octet, alors que certaines autres fonctions le rendent orienté large. Une fois établi, un flux gère son orientation jusqu'à ce qu'il soit fermé par un appel à [fclose](../c-runtime-library/reference/fclose-fcloseall.md) ou [freopen](../c-runtime-library/reference/freopen-wfreopen.md).

© 1989-2001 par P.J. Plauger et Jim Brodie. Tous droits réservés.

## <a name="see-also"></a>Voir aussi

[Flux texte et binaires](../c-runtime-library/text-and-binary-streams.md)<br/>
[Flux d’octets et flux larges](../c-runtime-library/byte-and-wide-streams.md)<br/>
[Contrôle des flux](../c-runtime-library/controlling-streams.md)<br/>
[États de flux](../c-runtime-library/stream-states.md)