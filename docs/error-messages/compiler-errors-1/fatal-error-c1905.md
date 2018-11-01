---
title: Erreur irrécupérable C1905
ms.date: 11/04/2016
f1_keywords:
- C1905
helpviewer_keywords:
- C1905
ms.assetid: fefc6769-477f-45a2-9878-6f0a5f42472c
ms.openlocfilehash: 3fb4db30d91e0dd8c9dbeeebca46210122e5ff07
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50663150"
---
# <a name="fatal-error-c1905"></a>Erreur irrécupérable C1905

Front-end et back end non compatibles (doivent cibler le même processeur)

Cette erreur se produit lorsqu’un fichier .obj est généré par un compilateur frontal (C1.dll) ciblant un processeur, telles que x86, ARM ou x64, mais il est lu par un serveur principal (C2.dll) qui cible un processeur différent.

Pour résoudre ce problème, assurez-vous d'utiliser un compilateur frontal et un compilateur principal qui correspondent. Il s'agit du paramétrage par défaut pour les projets créés dans Visual Studio. Cette erreur peut se produire si vous avez modifié le fichier projet et utilisé des chemins d'accès aux outils de compilateur différents. Si vous n'avez pas spécifiquement défini de chemin d'accès pour les outils du compilateur, cette erreur peut survenir si votre installation de Visual Studio est endommagée. Par exemple, vous pouvez avoir copié les fichiers .dll du compilateur d'un emplacement à un autre. Utilisez **programmes et fonctionnalités** dans le panneau de configuration Windows pour réparer ou réinstaller Visual Studio.