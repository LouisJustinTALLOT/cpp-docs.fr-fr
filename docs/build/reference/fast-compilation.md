---
title: Compilation de rapides | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- performance, cle.exe compiler
- compilation, performance
- cl.exe compiler, performance
- fast compiling
ms.assetid: 5fead136-ba69-40c8-8e25-236f89d5990a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 926c63d3d556d1aa9b85a7ce97e93b60e7c2ea23
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45722265"
---
# <a name="fast-compilation"></a>Compilation rapide

Pour augmenter la vitesse des compilations :

- Utilisez [régénération minimale](../../build/reference/gm-enable-minimal-rebuild.md), dans laquelle le compilateur C++ recompile un fichier source uniquement si elle est dépendante des modifications apportées à une classe dans un fichier d’en-tête.

- [Créer des fichiers d’en-tête précompilé](../../build/reference/creating-precompiled-header-files.md) et utiliser le [précompilé options d’en-tête](../../build/reference/yc-create-precompiled-header-file.md).

## <a name="see-also"></a>Voir aussi

[Options du compilateur](../../build/reference/compiler-options.md)<br/>
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)