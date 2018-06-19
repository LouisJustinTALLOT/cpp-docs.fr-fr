---
title: Étape de build personnalisée, propriétés (Linux C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/17/2017
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: Linux
ms.topic: conceptual
ms.assetid: 77a9c1fb-7c41-4a9b-9418-18ac17ce4e74
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: 0ec787826a09379732ac00fa858d32f05cf8025b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33326070"
---
# <a name="custom-build-step-properties-linux-c"></a>Étape de build personnalisée, propriétés (Linux C++)

Propriété | Description
--- | ---
Ligne de commande | Commande à exécuter par l'étape de génération personnalisée.
Description | Message qui s'affiche lors de l'exécution de l'étape de génération personnalisée.
Sorties | Fichier de sortie généré lors de l'étape de génération personnalisée. Ce paramètre est requis afin que les générations incrémentielles fonctionnent correctement.
Dépendances supplémentaires | Liste délimitée par les points-virgules de tous les fichiers d'entrée supplémentaires à utiliser pour l'étape de génération personnalisée.
Exécutez après et exécutez avant | Ces options définissent le moment de l'exécution de l'étape de génération personnalisée dans le processus de génération, par rapport aux cibles répertoriées. Les cibles le plus souvent répertoriées sont BuildGenerateSources, BuildCompile, et BuildLink, car elles constituent des étapes majeures dans le processus de génération. Les cibles souvent répertoriées sont Midl, CLCompile, et Link.
Considérer la sortie en tant que contenu | Cette option est significative uniquement pour les applications du Microsoft Store ou Windows Phone, qui comprennent tous les fichiers de contenu du package .appx.