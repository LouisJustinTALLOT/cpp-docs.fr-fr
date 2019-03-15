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
ms.openlocfilehash: ffd3023120f1d930a24ccef6fa297594062322df
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57816124"
---
# <a name="o-options-optimize-code"></a>/O (Optimiser le code), options

Le **/O** options contrôlent différentes optimisations qui vous aident à créer du code pour la vitesse maximale ou une taille minimale.

- [/ O1](o1-o2-minimize-size-maximize-speed.md) définit une combinaison d’optimisations qui génèrent du code de la taille minimale.

- [/ O2](o1-o2-minimize-size-maximize-speed.md) définit une combinaison d’optimisations qui optimise le code pour une vitesse maximale.

- [/Ob](ob-inline-function-expansion.md) contrôle l’expansion des fonctions inline.

- [/Od](od-disable-debug.md) désactive l’optimisation, pour accélérer la compilation et de simplifier le débogage.

- [/Og](og-global-optimizations.md) Active les optimisations globales.

- [/Oi](oi-generate-intrinsic-functions.md) génère des fonctions intrinsèques pour les appels de fonction appropriée.

- [/OS](os-ot-favor-small-code-favor-fast-code.md) indique au compilateur de favoriser les optimisations de taille par rapport aux optimisations de vitesse.

- [/OT](os-ot-favor-small-code-favor-fast-code.md) (paramètre par défaut) indique au compilateur de favoriser les optimisations de vitesse par rapport aux optimisations de taille.

- [/Ox](ox-full-optimization.md) est une option de combinaison qui sélectionne plusieurs optimisations en mettant l’accent sur la vitesse. Il est un sous-ensemble strict de la **/O2** optimisations.

- [/Oy](oy-frame-pointer-omission.md) supprime la création des pointeurs de frame sur la pile des appels pour les appels de fonction plus rapides.

## <a name="remarks"></a>Notes

Vous pouvez combiner plusieurs **/O** options dans une seule instruction d’option. Par exemple, **/Odi** est identique à **/Od /Oi**. Certaines options s’excluent mutuellement et provoquent une erreur du compilateur si utilisés ensemble. Consultez la personne **/O** options pour plus d’informations.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
