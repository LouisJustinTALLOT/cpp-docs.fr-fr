---
title: C++versions release-Visual Studio
ms.date: 12/10/2018
helpviewer_keywords:
- debugging [C++], release builds
- release builds
- debug builds, converting to release build
ms.assetid: fa9a78fa-f4b5-4722-baf4-aec655c4ff0f
ms.openlocfilehash: 46ae5e0f3d545f0e3e004f612314ab416b270fd8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168822"
---
# <a name="release-builds"></a>Versions release

Une version Release utilise des optimisations. Lorsque vous utilisez des optimisations pour créer une version Release, le compilateur ne génère pas d’informations de débogage symboliques. L’absence d’informations de débogage symboliques, ainsi que le fait que le code n’est pas généré pour les appels TRACE et Assert, signifie que la taille de votre fichier exécutable est réduite et sera donc plus rapide.

## <a name="in-this-section"></a>Contenu de cette section

[Problèmes courants lors de la création d’une version Release](common-problems-when-creating-a-release-build.md)<br/>
[Résolution de problèmes liés à la version Release](fixing-release-build-problems.md)<br/>
[Utilisation de VERIFY au lieu d’ASSERT](using-verify-instead-of-assert.md)<br/>
[Utilisation de la version debug pour vérifier les remplacements de mémoire](using-the-debug-build-to-check-for-memory-overwrite.md)<br/>
[Guide pratique pour déboguer une version Release](how-to-debug-a-release-build.md)<br/>
[Vérification des remplacements de mémoire](checking-for-memory-overwrites.md)<br/>
[Optimisation du code](optimizing-your-code.md)

## <a name="see-also"></a>Voir aussi

[Référence de la génération C/C++](reference/c-cpp-building-reference.md)
