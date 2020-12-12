---
description: 'En savoir plus sur : versions release'
title: Builds de version C++-Visual Studio
ms.date: 12/10/2018
helpviewer_keywords:
- debugging [C++], release builds
- release builds
- debug builds, converting to release build
ms.assetid: fa9a78fa-f4b5-4722-baf4-aec655c4ff0f
ms.openlocfilehash: 7168fd50421835edc82d0599b22deb9214e28869
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97273785"
---
# <a name="release-builds"></a>Versions release

Une version Release utilise des optimisations. Lorsque vous utilisez des optimisations pour créer une version Release, le compilateur ne génère pas d’informations de débogage symboliques. L’absence d’informations de débogage symboliques, ainsi que le fait que le code n’est pas généré pour les appels TRACE et Assert, signifie que la taille de votre fichier exécutable est réduite et sera donc plus rapide.

## <a name="in-this-section"></a>Dans cette section

[Problèmes courants lors de la création d’une version Release](common-problems-when-creating-a-release-build.md)<br/>
[Résolution des problèmes de version Release](fixing-release-build-problems.md)<br/>
[Utilisation de VERIFY au lieu d’Assert](using-verify-instead-of-assert.md)<br/>
[Utilisation de la version Debug pour vérifier le remplacement de mémoire](using-the-debug-build-to-check-for-memory-overwrite.md)<br/>
[Comment : déboguer une version Release](how-to-debug-a-release-build.md)<br/>
[Vérification des remplacements de mémoire](checking-for-memory-overwrites.md)<br/>
[Optimisation de votre code](optimizing-your-code.md)

## <a name="see-also"></a>Voir aussi

[Référence à la génération C/C++](reference/c-cpp-building-reference.md)
