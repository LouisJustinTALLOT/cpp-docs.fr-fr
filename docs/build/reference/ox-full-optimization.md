---
title: -Ox (activer la plupart des optimisations de vitesse) | Documents Microsoft
ms.custom: ''
ms.date: 09/25/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.ToolOptimization
- /ox
dev_langs:
- C++
helpviewer_keywords:
- Ox compiler option [C++]
- fast code [C++]
- /Ox compiler option [C++]
- -Ox compiler option [C++]
ms.assetid: 3ad7c30b-c615-428c-b1d0-2e024f81c760
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 569563bff030904988e93db749438eaeb58ce9db
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32378380"
---
# <a name="ox-enable-most-speed-optimizations"></a>/Ox (activer la plupart des optimisations de vitesse)

Le **/Ox** option du compilateur permet une combinaison d’optimisations qui favorise la vitesse. Dans certaines versions de l’IDE de Visual Studio et le message d’aide du compilateur, il s’agit *optimisation complète*, mais la **/Ox** option du compilateur permet uniquement un sous-ensemble des options d’optimisation vitesse activé par **/O2**.

## <a name="syntax"></a>Syntaxe

> /Ox

## <a name="remarks"></a>Notes

Le **/Ox** permet d’option du compilateur le **/O** cette vitesse de favoriser des options de compilateur. Le **/Ox** option du compilateur n’inclut pas les autres [/GF (éliminer les doublons)](../../build/reference/gf-eliminate-duplicate-strings.md) et [/Gy (activer la liaison au niveau des fonctions)](../../build/reference/gy-enable-function-level-linking.md) options activées par [/O1 ou/O2 (réduire la taille, augmenter la vitesse)](../../build/reference/o1-o2-minimize-size-maximize-speed.md). Les options supplémentaires appliquées par **/O1** et **/O2** peut entraîner des pointeurs vers les chaînes ou les fonctions de partager une adresse cible, ce qui peut affecter le débogage et la conformité de la syntaxe de langue stricte. Le **/Ox** option est un moyen simple pour activer la plupart des optimisations sans inclure **/GF** et **/Gy**. Pour plus d’informations, consultez les descriptions de la [/GF](../../build/reference/gf-eliminate-duplicate-strings.md) et [/Gy](../../build/reference/gy-enable-function-level-linking.md) options.

Le **/Ox** option du compilateur est identique à l’aide des options suivantes en combinaison :

- [/OB (Expansion des fonctions Inline)](../../build/reference/ob-inline-function-expansion.md), où le paramètre option 2 (**/Ob2**)

- [/Og (Optimisations globales)](../../build/reference/og-global-optimizations.md)

- [/Oi (Générer des fonctions intrinsèques)](../../build/reference/oi-generate-intrinsic-functions.md)

- [/Ot (favoriser la vitesse du Code rapide)](../../build/reference/os-ot-favor-small-code-favor-fast-code.md)

- [/Oy (Omission du pointeur frame)](../../build/reference/oy-frame-pointer-omission.md)

**/Ox** s’excluent mutuellement :

- [/ O1 (réduire la taille)](../../build/reference/o1-o2-minimize-size-maximize-speed.md)

- [/ O2 (augmenter la vitesse)](../../build/reference/o1-o2-minimize-size-maximize-speed.md)

- [/Od (Désactiver (Débogage))](../../build/reference/od-disable-debug.md)

Vous pouvez annuler le décalage par rapport à la vitesse de la **/Ox** option du compilateur si vous spécifiez **/Oxs**, qui associe le **/Ox** option du compilateur avec [/Os (favoriser la vitesse petite Code)](../../build/reference/os-ot-favor-small-code-favor-fast-code.md). Les options combinées favorisent la taille du code.

Pour appliquer toutes les optimisations au niveau des fichiers disponibles pour les versions release, nous vous recommandons de vous spécifiez [/O2 (augmenter la vitesse)](../../build/reference/o1-o2-minimize-size-maximize-speed.md) au lieu de **/Ox**, et [/O1 (réduire la taille)](../../build/reference/o1-o2-minimize-size-maximize-speed.md) à la place de **/Oxs**. Pour les versions davantage d’optimisation de mise en production, vous devez également envisager le [/GL (optimisation de l’ensemble du programme)](../../build/reference/gl-whole-program-optimization.md) option du compilateur et [/LTCG (génération de Code d’édition de liens)](../../build/reference/ltcg-link-time-code-generation.md) option de l’éditeur de liens.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Sous **propriétés de Configuration**, ouvrez **C/C++** , puis choisissez le **optimisation** page de propriétés.

1. Modifier la **optimisation** propriété.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Optimization%2A>.

## <a name="see-also"></a>Voir aussi

[/O, options (Optimiser le code)](../../build/reference/o-options-optimize-code.md)  
[Options du compilateur](../../build/reference/compiler-options.md)  
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)