---
title: -O (optimiser le Code), Options | Documents Microsoft
ms.custom: ''
ms.date: 09/25/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.Optimization
- /o
- VC.Project.VCCLWCECompilerTool.Optimization
dev_langs:
- C++
helpviewer_keywords:
- performance, cle.exe compiler
- cl.exe compiler, performance
ms.assetid: 77997af9-5555-4b3d-aa57-6615b27d4d5d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 83ddebec9db7a02db40ef31c89c7ff48a66cf665
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32376798"
---
# <a name="o-options-optimize-code"></a>/O (Optimiser le code), options

Le **/O** options contrôlent différentes optimisations qui vous aident à créer du code pour la vitesse maximale ou une taille minimale.

- [/ O1](../../build/reference/o1-o2-minimize-size-maximize-speed.md) définit une combinaison d’optimisations qui génèrent du code de la taille minimale.

- [/ O2](../../build/reference/o1-o2-minimize-size-maximize-speed.md) définit une combinaison d’optimisations qui optimise le code pour une vitesse maximale.

- [/Ob](../../build/reference/ob-inline-function-expansion.md) contrôle l’expansion des fonctions inline.

- [/Od](../../build/reference/od-disable-debug.md) désactive l’optimisation, afin d’accélérer la compilation et de simplifier le débogage.

- [/Og](../../build/reference/og-global-optimizations.md) Active les optimisations globales.

- [/Oi](../../build/reference/oi-generate-intrinsic-functions.md) génère des fonctions intrinsèques pour les appels de fonction appropriée.

- [/OS](../../build/reference/os-ot-favor-small-code-favor-fast-code.md) indique au compilateur de favoriser les optimisations de taille par rapport aux optimisations de vitesse.

- [/OT](../../build/reference/os-ot-favor-small-code-favor-fast-code.md) (paramètre par défaut) indique au compilateur de favoriser les optimisations de vitesse par rapport aux optimisations de taille.

- [/Ox](../../build/reference/ox-full-optimization.md) est une option de combinaison sélectionne plusieurs optimisations en mettant l’accent sur la vitesse. Il s’agit d’un sous-ensemble strict de la **/O2** optimisations.

- [/Oy](../../build/reference/oy-frame-pointer-omission.md) supprime la création des pointeurs de frame sur la pile des appels pour les appels de fonction plus rapides.

## <a name="remarks"></a>Notes

Vous pouvez combiner plusieurs **/O** options dans une seule instruction d’option. Par exemple, **/Odi** est identique à **/Od /Oi**. Certaines options s’excluent mutuellement et provoquent une erreur du compilateur si utilisés ensemble. Consultez la personne **/O** options pour plus d’informations.

## <a name="see-also"></a>Voir aussi

[Options du compilateur](../../build/reference/compiler-options.md)   
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)