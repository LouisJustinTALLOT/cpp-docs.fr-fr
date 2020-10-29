---
title: Étape de build personnalisée, propriétés (Linux C++)
ms.date: 06/07/2019
ms.assetid: 77a9c1fb-7c41-4a9b-9418-18ac17ce4e74
ms.openlocfilehash: 51111b7ff1ab68ecc49b54efdeeef5f95368ab0c
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92924527"
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
