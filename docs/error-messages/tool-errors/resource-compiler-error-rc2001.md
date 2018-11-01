---
title: 'Erreur RC2001 du compilateur de ressources '
ms.date: 11/04/2016
f1_keywords:
- RC2001
helpviewer_keywords:
- RC2001
ms.assetid: 92bfb4c0-1879-4606-bb9f-ef7368707b4a
ms.openlocfilehash: f4755e04a744d94636b4b37aaf727e0d733008ef
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50602109"
---
# <a name="resource-compiler-error-rc2001"></a>Erreur RC2001 du compilateur de ressources 

saut de ligne dans la constante

Constante de chaîne se poursuivie sur une seconde ligne, sans utilisation d’une barre oblique inverse (**\\**) ou ouverture et fermeture des guillemets doubles (**»**).

Pour interrompre une constante de chaîne qui se trouve sur deux lignes dans le fichier source, effectuez l’une des opérations suivantes :

- La première ligne par le caractère de continuation de ligne, une barre oblique inverse de fin.

- Fermez la chaîne sur la première ligne avec un guillemet double et ouvrez la chaîne sur la ligne suivante avec un autre guillemet.

Il n’est pas suffisante pour terminer la première ligne par \n, la séquence d’échappement pour incorporer un caractère de saut de ligne dans une constante de chaîne.