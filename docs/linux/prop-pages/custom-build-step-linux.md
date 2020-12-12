---
description: 'En savoir plus sur : propriétés d’une étape de build personnalisée (Linux C++)'
title: Étape de build personnalisée, propriétés (Linux C++)
ms.date: 06/07/2019
ms.assetid: 77a9c1fb-7c41-4a9b-9418-18ac17ce4e74
ms.openlocfilehash: d8a120d147d107cd96f77556a412aa8ee6636548
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97169773"
---
# <a name="custom-build-step-properties-linux-c"></a>Étape de build personnalisée, propriétés (Linux C++)

::: moniker range="msvc-140"

La prise en charge Linux est disponible dans Visual Studio 2017 et ultérieur.

::: moniker-end

::: moniker range=">=msvc-150"

| Propriété | Description |
|--|--|
| Ligne de commande | Commande à exécuter par l'étape de génération personnalisée. |
| Description | Message qui s'affiche lors de l'exécution de l'étape de génération personnalisée. |
| Sorties | Fichier de sortie généré lors de l'étape de génération personnalisée. Ce paramètre est requis afin que les générations incrémentielles fonctionnent correctement. |
| Dépendances supplémentaires | Liste délimitée par les points-virgules de tous les fichiers d'entrée supplémentaires à utiliser pour l'étape de génération personnalisée. |
| Exécution après et Exécution avant | Ces options définissent le moment de l'exécution de l'étape de génération personnalisée dans le processus de génération, par rapport aux cibles répertoriées. Les cibles le plus souvent répertoriées sont BuildGenerateSources, BuildCompile, et BuildLink, car elles constituent des étapes majeures dans le processus de génération. Les cibles souvent répertoriées sont Midl, CLCompile, et Link. |
| Considérer la sortie en tant que contenu | Cette option est significative uniquement pour les applications du Microsoft Store ou Windows Phone, qui comprennent tous les fichiers de contenu du package .appx. |

::: moniker-end
