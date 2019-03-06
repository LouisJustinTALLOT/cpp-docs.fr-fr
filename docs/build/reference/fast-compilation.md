---
title: Compilation rapide
ms.date: 11/04/2016
helpviewer_keywords:
- performance, cle.exe compiler
- compilation, performance
- cl.exe compiler, performance
- fast compiling
ms.assetid: 5fead136-ba69-40c8-8e25-236f89d5990a
ms.openlocfilehash: e613e12eb9089348ea3f82bc5fac43d569a89f35
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57426158"
---
# <a name="fast-compilation"></a>Compilation rapide

Pour augmenter la vitesse des compilations :

- Utilisez [régénération minimale](../../build/reference/gm-enable-minimal-rebuild.md), dans laquelle le compilateur C++ recompile un fichier source uniquement si elle est dépendante des modifications apportées à une classe dans un fichier d’en-tête.

- [Créer des fichiers d’en-tête précompilé](../../build/reference/creating-precompiled-header-files.md) et utiliser le [précompilé options d’en-tête](../../build/reference/yc-create-precompiled-header-file.md).

## <a name="see-also"></a>Voir aussi

[Options du compilateur](../../build/reference/compiler-options.md)<br/>
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)
