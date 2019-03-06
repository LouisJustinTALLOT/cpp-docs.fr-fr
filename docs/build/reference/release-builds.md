---
title: Versions release
ms.date: 11/04/2016
helpviewer_keywords:
- debugging [C++], release builds
- release builds
- debug builds, converting to release build
ms.assetid: fa9a78fa-f4b5-4722-baf4-aec655c4ff0f
ms.openlocfilehash: 346beace1979871cfd9bf4ee0d487e7f85a26eaa
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57426093"
---
# <a name="release-builds"></a>Versions release

Une version Release utilise des optimisations. Lorsque vous utilisez des optimisations pour créer une version Release, le compilateur ne génère pas les informations de débogage symboliques. L’absence d’informations de débogage symboliques, ainsi que le fait que le code n’est pas généré pour la TRACE et ASSERT appelle, signifie que la taille de votre fichier exécutable est réduite et n’est donc plus rapidement.

Cette section présente des informations sur quand et pourquoi vous souhaiteriez modifier à partir d’une version debug à une version Release. Il aborde également certains des problèmes que vous pouvez rencontrer lors de la modification à partir d’un débogage à une version Release :

- [Création d’une version Release](../../build/reference/how-to-create-a-release-build.md)

- [Problèmes courants lors de la création d’une version Release](../../build/reference/common-problems-when-creating-a-release-build.md)

- [Résolution de problèmes liés à la version Release](../../build/reference/fixing-release-build-problems.md)

   - [Examen des instructions ASSERT](../../build/reference/using-verify-instead-of-assert.md)

   - [À l’aide de la version Debug pour vérifier les remplacements de mémoire de](../../build/reference/using-the-debug-build-to-check-for-memory-overwrite.md)

   - [Débogage d’une version Release](../../build/reference/how-to-debug-a-release-build.md)

   - [Vérification des remplacements de mémoire](../../build/reference/checking-for-memory-overwrites.md)

## <a name="see-also"></a>Voir aussi

[Génération de projets C++ dans Visual Studio](../../ide/building-cpp-projects-in-visual-studio.md)<br/>
[Référence de la génération C/C++](../../build/reference/c-cpp-building-reference.md)
