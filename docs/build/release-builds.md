---
title: Versions de C++ - Visual Studio
ms.date: 12/10/2018
helpviewer_keywords:
- debugging [C++], release builds
- release builds
- debug builds, converting to release build
ms.assetid: fa9a78fa-f4b5-4722-baf4-aec655c4ff0f
ms.openlocfilehash: 6167c024ae76952573475a815f24d2cf4be01119
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57826145"
---
# <a name="release-builds"></a>Versions release

Une version Release utilise des optimisations. Lorsque vous utilisez des optimisations pour créer une version Release, le compilateur ne génère pas les informations de débogage symboliques. L’absence d’informations de débogage symboliques, ainsi que le fait que le code n’est pas généré pour la TRACE et ASSERT appelle, signifie que la taille de votre fichier exécutable est réduite et n’est donc plus rapidement.

## <a name="in-this-section"></a>Dans cette section

[Problèmes courants lors de la création d’une version Release](common-problems-when-creating-a-release-build.md)<br/>
[Résolution de problèmes liés à la version Release](fixing-release-build-problems.md)<br/>
[Utilisation de VERIFY au lieu d’ASSERT](using-verify-instead-of-assert.md)<br/>
[Utilisation de la version debug pour vérifier les remplacements de mémoire](using-the-debug-build-to-check-for-memory-overwrite.md)<br/>
[Guide pratique pour déboguer une version Release](how-to-debug-a-release-build.md)<br/>
[Vérification des remplacements de mémoire](checking-for-memory-overwrites.md)<br/>
[Optimisation du code](optimizing-your-code.md)<br/>

## <a name="see-also"></a>Voir aussi

[Référence de la génération C/C++](reference/c-cpp-building-reference.md)