---
title: /O (Optimiser le code), options
ms.date: 09/25/2017
f1_keywords:
- VC.Project.VCCLCompilerTool.Optimization
- /o
- VC.Project.VCCLWCECompilerTool.Optimization
helpviewer_keywords:
- performance, cle.exe compiler
- cl.exe compiler, performance
ms.assetid: 77997af9-5555-4b3d-aa57-6615b27d4d5d
ms.openlocfilehash: f4e2bf8b848654f7b87c59e7a54994448ee62d51
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50481326"
---
# <a name="o-options-optimize-code"></a>/O (Optimiser le code), options

Le **/O** options contrôlent différentes optimisations qui vous aident à créer du code pour la vitesse maximale ou une taille minimale.

- [/ O1](../../build/reference/o1-o2-minimize-size-maximize-speed.md) définit une combinaison d’optimisations qui génèrent du code de la taille minimale.

- [/ O2](../../build/reference/o1-o2-minimize-size-maximize-speed.md) définit une combinaison d’optimisations qui optimise le code pour une vitesse maximale.

- [/Ob](../../build/reference/ob-inline-function-expansion.md) contrôle l’expansion des fonctions inline.

- [/Od](../../build/reference/od-disable-debug.md) désactive l’optimisation, pour accélérer la compilation et de simplifier le débogage.

- [/Og](../../build/reference/og-global-optimizations.md) Active les optimisations globales.

- [/Oi](../../build/reference/oi-generate-intrinsic-functions.md) génère des fonctions intrinsèques pour les appels de fonction appropriée.

- [/OS](../../build/reference/os-ot-favor-small-code-favor-fast-code.md) indique au compilateur de favoriser les optimisations de taille par rapport aux optimisations de vitesse.

- [/OT](../../build/reference/os-ot-favor-small-code-favor-fast-code.md) (paramètre par défaut) indique au compilateur de favoriser les optimisations de vitesse par rapport aux optimisations de taille.

- [/Ox](../../build/reference/ox-full-optimization.md) est une option de combinaison qui sélectionne plusieurs optimisations en mettant l’accent sur la vitesse. Il est un sous-ensemble strict de la **/O2** optimisations.

- [/Oy](../../build/reference/oy-frame-pointer-omission.md) supprime la création des pointeurs de frame sur la pile des appels pour les appels de fonction plus rapides.

## <a name="remarks"></a>Notes

Vous pouvez combiner plusieurs **/O** options dans une seule instruction d’option. Par exemple, **/Odi** est identique à **/Od /Oi**. Certaines options s’excluent mutuellement et provoquent une erreur du compilateur si utilisés ensemble. Consultez la personne **/O** options pour plus d’informations.

## <a name="see-also"></a>Voir aussi

[Options du compilateur](../../build/reference/compiler-options.md)<br/>
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)