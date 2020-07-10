---
title: /O (Optimiser le code), options
description: Les options du compilateur MSVC/O spécifient les optimisations du compilateur à utiliser.
ms.date: 07/08/2020
f1_keywords:
- VC.Project.VCCLCompilerTool.Optimization
- /o
- VC.Project.VCCLWCECompilerTool.Optimization
helpviewer_keywords:
- performance, cle.exe compiler
- cl.exe compiler, performance
ms.assetid: 77997af9-5555-4b3d-aa57-6615b27d4d5d
ms.openlocfilehash: 36ef582787a3ec2d7aee1e589c70b48712d9d552
ms.sourcegitcommit: 80c8a512b361bd84e38958beb1a1bf6db7434021
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86180875"
---
# <a name="o-options-optimize-code"></a>`/O`options (optimiser le code)

Les **`/O`** options contrôlent différentes optimisations qui vous aident à créer du code pour une vitesse maximale ou une taille minimale.

- [`/O1`](o1-o2-minimize-size-maximize-speed.md)définit une combinaison d’optimisations qui génèrent un code de taille minimale.

- [`/O2`](o1-o2-minimize-size-maximize-speed.md)définit une combinaison d’optimisations qui optimise le code pour une vitesse maximale.

- [`/Ob`](ob-inline-function-expansion.md)contrôle l’expansion des fonctions inline.

- [`/Od`](od-disable-debug.md)désactive l’optimisation, pour accélérer la compilation et simplifier le débogage.

- [`/Og`](og-global-optimizations.md)(déconseillé) permet des optimisations globales.

- [`/Oi`](oi-generate-intrinsic-functions.md)génère des fonctions intrinsèques pour les appels de fonction appropriés.

- [`/Os`](os-ot-favor-small-code-favor-fast-code.md)indique au compilateur de privilégier les optimisations de la taille par rapport aux optimisations de vitesse.

- [`/Ot`](os-ot-favor-small-code-favor-fast-code.md)(paramètre par défaut) indique au compilateur de privilégier les optimisations de vitesse par rapport aux optimisations de taille.

- [`/Ox`](ox-full-optimization.md)est une option de combinaison qui sélectionne plusieurs des optimisations, en mettant l’accent sur la vitesse. **`/Ox`** est un sous-ensemble strict des **`/O2`** optimisations.

- [`/Oy`](oy-frame-pointer-omission.md)supprime la création de pointeurs de frame sur la pile des appels pour des appels de fonction plus rapides.

## <a name="remarks"></a>Notes

Vous pouvez combiner plusieurs **`/O`** options en une seule instruction d’option. Par exemple, **`/Odi`** est identique à **`/Od /Oi`** . Certaines options s’excluent mutuellement et provoquent une erreur du compilateur si elles sont utilisées ensemble. Pour plus d’informations, consultez les différentes **`/O`** options.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
