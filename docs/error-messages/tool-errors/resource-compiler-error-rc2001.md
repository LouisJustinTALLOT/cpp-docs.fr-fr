---
title: Erreur RC2001 du compilateur de ressources
ms.date: 11/04/2016
f1_keywords:
- RC2001
helpviewer_keywords:
- RC2001
ms.assetid: 92bfb4c0-1879-4606-bb9f-ef7368707b4a
ms.openlocfilehash: 35042687b798b53857becdedba57861bd4f41a05
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80191719"
---
# <a name="resource-compiler-error-rc2001"></a>Erreur RC2001 du compilateur de ressources

saut de ligne dans la constante

Une constante de chaîne a été poursuivie sur une deuxième ligne sans une barre oblique inverse ( **\\** ) ou en fermant et en ouvrant des guillemets doubles ( **"** ).

Pour rompre une constante de chaîne qui se trouve sur deux lignes dans le fichier source, effectuez l’une des opérations suivantes :

- Terminez la première ligne par le caractère de continuation de ligne, une barre oblique inverse.

- Fermez la chaîne sur la première ligne avec un guillemet double et ouvrez la chaîne sur la ligne suivante avec un autre guillemet.

Il n’est pas suffisant de terminer la première ligne avec \n, la séquence d’échappement pour incorporer un caractère de saut de ligne dans une constante de chaîne.
