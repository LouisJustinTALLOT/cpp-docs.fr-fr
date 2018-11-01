---
title: Compilation rapide
ms.date: 11/04/2016
helpviewer_keywords:
- performance, cle.exe compiler
- compilation, performance
- cl.exe compiler, performance
- fast compiling
ms.assetid: 5fead136-ba69-40c8-8e25-236f89d5990a
ms.openlocfilehash: ab3171d7bb6d85cbe010e0efce39eda14b166527
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50667650"
---
# <a name="fast-compilation"></a>Compilation rapide

Pour augmenter la vitesse des compilations :

- Utilisez [régénération minimale](../../build/reference/gm-enable-minimal-rebuild.md), dans laquelle le compilateur C++ recompile un fichier source uniquement si elle est dépendante des modifications apportées à une classe dans un fichier d’en-tête.

- [Créer des fichiers d’en-tête précompilé](../../build/reference/creating-precompiled-header-files.md) et utiliser le [précompilé options d’en-tête](../../build/reference/yc-create-precompiled-header-file.md).

## <a name="see-also"></a>Voir aussi

[Options du compilateur](../../build/reference/compiler-options.md)<br/>
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)