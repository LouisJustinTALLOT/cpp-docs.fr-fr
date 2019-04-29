---
title: /Ox (activer la plupart des optimisations de vitesse)
ms.date: 10/18/2018
f1_keywords:
- VC.Project.VCCLCompilerTool.ToolOptimization
- /Ox
- /Oxs
helpviewer_keywords:
- Ox compiler option [C++]
- fast code [C++]
- /Ox compiler option [C++]
- -Ox compiler option [C++]
ms.assetid: 3ad7c30b-c615-428c-b1d0-2e024f81c760
ms.openlocfilehash: e39905608087425fe5a445f4ef88434d73bb2ded
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320095"
---
# <a name="ox-enable-most-speed-optimizations"></a>/Ox (activer la plupart des optimisations de vitesse)

Le **/Ox** option du compilateur permet une combinaison d’optimisations qui favoriser la vitesse. Dans certaines versions de l’IDE Visual Studio et le message d’aide du compilateur, on parle de *optimisation complète*, mais la **/Ox** option du compilateur permet uniquement un sous-ensemble des options d’optimisation vitesse activé par **/O2**.

## <a name="syntax"></a>Syntaxe

> **/Ox**

## <a name="remarks"></a>Notes

Le **/Ox** permet d’option du compilateur le **/O** options de compilateur favoriser la vitesse. Le **/Ox** option du compilateur n’inclut pas les autres [/GF (supprimer les doublons)](gf-eliminate-duplicate-strings.md) et [/Gy (activer la liaison au niveau des fonctions)](gy-enable-function-level-linking.md) options activées par [/O1 ou/O2 (réduire la taille, augmenter la vitesse)](o1-o2-minimize-size-maximize-speed.md). Les options supplémentaires appliquées par **/O1** et **/O2** peut provoquer des pointeurs vers les chaînes ou aux fonctions de partager une adresse cible, ce qui peut affecter le débogage et la conformité du langage stricte. Le **/Ox** option est un moyen simple pour activer la plupart des optimisations sans inclure **/GF** et **/Gy**. Pour plus d’informations, consultez les descriptions de la [/GF](gf-eliminate-duplicate-strings.md) et [/Gy](gy-enable-function-level-linking.md) options.

Le **/Ox** option du compilateur est identique à l’aide des options suivantes dans la combinaison :

- [/OB (Expansion des fonctions Inline)](ob-inline-function-expansion.md), où le paramètre option 2 (**/Ob2**)

- [/Og (Optimisations globales)](og-global-optimizations.md)

- [/Oi (Générer des fonctions intrinsèques)](oi-generate-intrinsic-functions.md)

- [/Ot (favoriser un Code rapide)](os-ot-favor-small-code-favor-fast-code.md)

- [/Oy (Omission du pointeur frame)](oy-frame-pointer-omission.md)

**/Ox** s’excluent mutuellement :

- [/ O1 (réduire la taille)](o1-o2-minimize-size-maximize-speed.md)

- [/ O2 (augmenter la vitesse)](o1-o2-minimize-size-maximize-speed.md)

- [/Od (Désactiver (Débogage))](od-disable-debug.md)

Vous pouvez annuler le décalage par rapport à la vitesse de la **/Ox** option du compilateur si vous spécifiez **/Oxs**, qui associe le **/Ox** option du compilateur avec [/Os (favoriser petite Code)](os-ot-favor-small-code-favor-fast-code.md). Les options combinées favorisent la taille du code.  Le **/Oxs** option est exactement le même que la spécification **/Ox** **/Os** lorsque les options apparaissent dans cet ordre.

Pour appliquer toutes les optimisations au niveau des fichiers disponibles pour les versions release, nous vous recommandons de spécifier [/O2 (augmenter la vitesse)](o1-o2-minimize-size-maximize-speed.md) au lieu de **/Ox**, et [/O1 (réduire la taille)](o1-o2-minimize-size-maximize-speed.md) à la place de **/Oxs**. Pour les versions encore plus l’optimisation de mise en production, vous devez également envisager le [/GL (Whole Program Optimization)](gl-whole-program-optimization.md) option du compilateur et [/LTCG (Link-time Code Generation)](ltcg-link-time-code-generation.md) option de l’éditeur de liens.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Sous **propriétés de Configuration**, ouvrez **C/C++** , puis choisissez le **optimisation** page de propriétés.

1. Modifier le **optimisation** propriété.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Optimization%2A>.

## <a name="see-also"></a>Voir aussi

[/O, options (Optimiser le code)](o-options-optimize-code.md)<br/>
[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
