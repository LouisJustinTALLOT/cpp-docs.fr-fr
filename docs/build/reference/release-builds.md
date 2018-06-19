---
title: Versions Release | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- debugging [C++], release builds
- release builds
- debug builds, converting to release build
ms.assetid: fa9a78fa-f4b5-4722-baf4-aec655c4ff0f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f3ae18c5e2dcdb735880509fd158dac4ccaa1462
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32376648"
---
# <a name="release-builds"></a>Versions release
Une version Release utilise des optimisations. Lorsque vous utilisez des optimisations pour créer une version Release, le compilateur ne produira pas les informations de débogage symboliques. L’absence d’informations de débogage symboliques, ainsi que le fait que le code n’est pas généré pour la TRACE et ASSERT appelle, signifie que la taille de votre fichier exécutable est réduite, il est donc plus rapidement.  
  
 Cette section présente des informations sur quand et pourquoi vous souhaiterez modifier à partir d’une version debug à une version Release. Elle décrit également les problèmes que vous pouvez rencontrer lors de la modification à partir d’un débogage à une version Release :  
  
-   [Création d’une version Release](../../build/reference/how-to-create-a-release-build.md)  
  
-   [Problèmes courants lors de la création d’une version Release](../../build/reference/common-problems-when-creating-a-release-build.md)  
  
-   [Résolution de problèmes liés à la version Release](../../build/reference/fixing-release-build-problems.md)  
  
    -   [Examen des instructions ASSERT](../../build/reference/using-verify-instead-of-assert.md)  
  
    -   [À l’aide de la version Debug pour vérifier les remplacements de mémoire de](../../build/reference/using-the-debug-build-to-check-for-memory-overwrite.md)  
  
    -   [Débogage d’une version Release](../../build/reference/how-to-debug-a-release-build.md)  
  
    -   [Vérification des remplacements de mémoire](../../build/reference/checking-for-memory-overwrites.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Génération de projets C++ dans Visual Studio](../../ide/building-cpp-projects-in-visual-studio.md)   
 [Référence de la génération C/C++](../../build/reference/c-cpp-building-reference.md)