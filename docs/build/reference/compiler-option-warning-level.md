---
title: /w,/W0,/W1,/W2,/W3,/W4,/W1,/W2,/W3,/W4,/Wall,/WD,/we,/WO,/WV,/WX (niveau d’avertissement)
ms.date: 01/31/2018
f1_keywords:
- VC.Project.VCCLCompilerTool.DisableSpecificWarnings
- VC.Project.VCCLCompilerTool.WarningLevel
- VC.Project.VCCLWCECompilerTool.DisableSpecificWarnings
- VC.Project.VCCLCompilerTool.WarnAsError
- VC.Project.VCCLWCECompilerTool.WarnAsError
- /wx
- VC.Project.VCCLWCECompilerTool.WarningLevel
- /wall
- VC.Project.VCCLCompilerTool.TreatSpecificWarningsAsErrors
- /Wv
- /w0
- /w1
- /w2
- /w3
- /w4
- /wd
- /we
- /wo
helpviewer_keywords:
- /W1 compiler option [C++]
- w compiler option [C++]
- -wo compiler option [C++]
- Warning Level compiler option
- W1 compiler option [C++]
- -we compiler option [C++]
- /WX compiler option [C++]
- -wd compiler option [C++]
- WX compiler option [C++]
- wo compiler option [C++]
- Wall compiler option [C++]
- /w compiler option
- W2 compiler option [C++]
- -W2 compiler option [C++]
- wd compiler option [C++]
- /we compiler option [C++]
- we compiler option [C++]
- -W1 compiler option [C++]
- -W4 compiler option [C++]
- -Wall compiler option [C++]
- /Wall compiler option [C++]
- -W0 compiler option [C++]
- W0 compiler option [C++]
- -WX compiler option [C++]
- /wo compiler option [C++]
- W4 compiler option [C++]
- W3 compiler option [C++]
- /wd compiler option [C++]
- warnings, as errors compiler option
- /W3 compiler option [C++]
- /W0 compiler option [C++]
- /W4 compiler option [C++]
- -W3 compiler option [C++]
- -w compiler option [C++]
- /W2 compiler option [C++]
- /Wv compiler option [C++]
ms.openlocfilehash: 7d2fd21c476ef4346aa86e682047ea644183b2f3
ms.sourcegitcommit: d0504e2337bb671e78ec6dd1c7b05d89e7adf6a7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2019
ms.locfileid: "74683060"
---
# <a name="w-w0-w1-w2-w3-w4-w1-w2-w3-w4-wall-wd-we-wo-wv-wx-warning-level"></a>/w,/W0,/W1,/W2,/W3,/W4,/W1,/W2,/W3,/W4,/Wall,/WD,/we,/WO,/WV,/WX (niveau d’avertissement)

Spécifie comment le compilateur génère les avertissements pour une compilation donnée.

## <a name="syntax"></a>Syntaxe

> **/w**\
> **/W0**\
> **/W1**\
> **/W2**\
> **/W3**\
> **/W4**\
> \ **/Wall**
> **/WV**\[ **:** _version_] \
> **/Wx**\
> \ d'_Avertissement_ **/W1**
> \ d'_Avertissement_ **/W2**
> \ d'_Avertissement_ **/W3**
> \ d'_Avertissement_ **/W4**
> \ d'_Avertissement_ **/WD**
> \ d'_Avertissement_ **/We**
> _Avertissement_ /WO

## <a name="remarks"></a>Notes

Les options d’avertissement spécifient les avertissements du compilateur à afficher et le comportement d’avertissement pour l’ensemble de la compilation.

Les options d’avertissement et les arguments associés sont décrits dans le tableau suivant :

|Option|Description|
------------|-----------------|
|**/w**|Supprime tous les avertissements du compilateur.|
|**/W0**<br /><br /> **/W1**<br /><br /> **/W2**<br /><br /> **/W3**<br /><br /> **/W4**|Spécifie le niveau des avertissements que le compilateur doit générer. Les niveaux d’avertissement valides sont compris entre 0 et 4 :<br />**/W0** supprime tous les avertissements. Cela équivaut à **/w**.<br />**/W1** affiche les avertissements de niveau 1 (grave). **/W1** est le paramètre par défaut dans le compilateur de ligne de commande.<br />**/W2** affiche les avertissements de niveau 1 et de niveau 2 (significatif).<br />**/W3** affiche les avertissements de niveau 1, de niveau 2 et de niveau 3 (qualité de production). **/W3** est le paramètre par défaut dans l’IDE.<br />**/W4** affiche les avertissements de niveau 1, de niveau 2 et de niveau 3, ainsi que tous les avertissements de niveau 4 (informatif) qui ne sont pas désactivés par défaut. Nous vous recommandons d’utiliser cette option pour fournir des avertissements de type Lint. Pour un nouveau projet, il peut être préférable d’utiliser **/W4** dans toutes les compilations. Cela permet de garantir le moins possible d’erreurs de code difficiles à trouver.|
|**/Wall**|Affiche tous les avertissements affichés par **/W4** et tous les autres avertissements que **/W4** n’inclut pas, par exemple, les avertissements qui sont désactivés par défaut. Pour plus d’informations, consultez [avertissements du compilateur désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md).|
|**/WV**\[ **:** _version_]|Affiche uniquement les avertissements introduits dans la *version* du compilateur et les versions antérieures. Vous pouvez utiliser cette option pour supprimer les nouveaux avertissements dans le code lorsque vous migrez vers une version plus récente du compilateur et pour maintenir votre processus de génération existant pendant que vous les corrigez. La *version* de paramètre facultative prend la forme *nn*[. *mm*[. *bbbbb*]] où *nn* est le numéro de version principale, *mm* est le numéro de version mineure facultatif et *bbbbb* est le numéro de build facultatif du compilateur. Par exemple, utilisez */WV : 17* pour afficher les avertissements introduits dans Visual Studio 2012 (autrement dit, toute version du compilateur ayant un numéro de version majeure 17) ou antérieur, mais supprimez les avertissements introduits dans Visual Studio 2013 (version majeure 18) et versions ultérieures. Par défaut, **/WV** utilise le numéro de version du compilateur actuel, et aucun avertissement n’est supprimé. Pour plus d’informations sur les avertissements qui sont supprimés par la version du compilateur, consultez [avertissements du compilateur par version du compilateur](../../error-messages/compiler-warnings/compiler-warnings-by-compiler-version.md).|
|**/WX**|Considère tous les avertissements du compilateur comme des erreurs. Pour un nouveau projet, il peut être préférable d’utiliser **/WX** dans toutes les compilations. la résolution de tous les avertissements garantit le moins possible les erreurs de code difficiles à trouver.<br /><br /> L’éditeur de liens a également une option **/WX** . Pour plus d’informations, consultez l’article [/WX (Traiter les avertissements de l’Éditeur de liens comme des erreurs)](wx-treat-linker-warnings-as-errors.md).|
|**/W1**_nnnn_<br /><br /> **/W2**_nnnn_<br /><br /> **/W3**_nnnn_<br /><br /> **/W4**_nnnn_|Définit le niveau d’avertissement pour le numéro d’avertissement spécifié par _nnnn_. Cela vous permet de modifier le comportement du compilateur pour cet avertissement lorsqu’un niveau d’avertissement spécifique est défini. Vous pouvez utiliser ces options en combinaison avec d’autres options d’avertissement pour appliquer vos propres normes de codage pour les avertissements, plutôt que les paramètres par défaut fournis par Visual Studio.<br /><br /> Par exemple, **/w34326** provoque la génération de C4326 sous la forme d’un avertissement de niveau 3 au lieu du niveau 1. Si vous compilez à l’aide de l’option **/w34326** et de l’option **/W2** , l’avertissement C4326 n’est pas généré.|
|**/WD**_nnnn_|Supprime l’avertissement du compilateur spécifié par _nnnn_.<br /><br /> Par exemple, **/wd4326** supprime l’avertissement du compilateur C4326.|
|**/We**_nnnn_|Traite l’avertissement du compilateur spécifié par _nnnn_ comme une erreur.<br /><br /> Par exemple, **/we4326** fait en sorte que le nombre d’avertissements C4326 soit traité comme une erreur par le compilateur.|
|**/WO**_nnnn_|Signale l’avertissement du compilateur spécifié par _nnnn_ une seule fois.<br /><br /> Par exemple, **/wo4326** fait en sorte que l’avertissement C4326 soit signalé une seule fois, la première fois qu’il est rencontré par le compilateur.|

Si vous utilisez l’une des options d’avertissement lorsque vous créez un en-tête précompilé à l’aide de l’option [/Yc](yc-create-precompiled-header-file.md) , toute utilisation de l’en-tête précompilé à l’aide de l’option [/Yu](yu-use-precompiled-header-file.md) fait en sorte que ces mêmes options d’avertissement soient à nouveau en vigueur. Vous pouvez remplacer les options d’avertissement définies dans l’en-tête précompilé à l’aide d’une autre option d’avertissement sur la ligne de commande.

Vous pouvez utiliser une directive [#pragma warning](../../preprocessor/warning.md) pour contrôler le niveau d’avertissement signalé au moment de la compilation dans des fichiers sources spécifiques.

Les directives pragma d’avertissement dans le code source ne sont pas affectées par l’option **/w** .

La [documentation](../../error-messages/compiler-errors-1/c-cpp-build-errors.md) sur les erreurs de build décrit les avertissements et les niveaux d’avertissement, et indique pourquoi certaines instructions peuvent ne pas se compiler comme vous le souhaitez.

### <a name="to-set-the-compiler-options-in-the-visual-studio-development-environment"></a>Pour définir les options du compilateur dans l’environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Pour définir les options **/W0**, **/W1**, **/W2**, **/W3**, **/W4**, **/Wall**, **/WV**, **/WX** ou **/WX-** , sélectionnez la page **Propriétés de configuration** > la page de propriétés **général** **C/C++**  > .

   - Pour définir les options **/W0**, **/W1**, **/W2**, **/W3**, **/W4**ou **/Wall** , modifiez la propriété **niveau d’avertissement** .

   - Pour définir les options **/WX** ou **/WX-** , modifiez la propriété **Treat Warnings As Errors** .

   - Pour définir la version de l’option **/WV** , entrez le numéro de version du compilateur dans la propriété **version d’avertissement** .

1. Pour définir les options **/WD** ou **/We** , sélectionnez la page **Propriétés de configuration** > la page de propriétés **avancé** **C/C++**  > .

   - Pour définir l’option **/WD** , sélectionnez le contrôle de liste déroulante **Désactiver les avertissements spécifiques** , puis choisissez **modifier**. Dans la zone d’édition de la boîte de dialogue **désactiver des avertissements spécifiques** , entrez le numéro d’avertissement. Pour entrer plusieurs avertissements, séparez les valeurs à l’aide d’un point-virgule ( **;** ). Par exemple, pour désactiver C4001 et C4010, entrez **4001 ; 4010**. Choisissez **OK** pour enregistrer vos modifications et revenir à la boîte de dialogue **pages de propriétés** .

   - Pour définir l’option **/We** , sélectionnez le contrôle de liste déroulante **traiter les avertissements spécifiques en tant qu’erreurs** , puis choisissez **modifier**. Dans la zone d’édition de la boîte de dialogue **traiter des avertissements spécifiques en tant qu’erreurs** , entrez le numéro d’avertissement. Pour entrer plusieurs avertissements, séparez les valeurs à l’aide d’un point-virgule ( **;** ). Par exemple, pour traiter à la fois C4001 et C4010 comme des erreurs, entrez **4001 ; 4010**. Choisissez **OK** pour enregistrer vos modifications et revenir à la boîte de dialogue **pages de propriétés** .

1. Pour définir l’option **/WO** , sélectionnez les **Propriétés de configuration** > page de propriétés de ligne de **commande** **C/C++**  > . Entrez l’option de compilateur dans la zone **options supplémentaires** .

1. Choisissez **OK** pour enregistrer vos modifications.

### <a name="to-set-the-compiler-option-programmatically"></a>Pour définir l'option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WarningLevel%2A>, <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WarnAsError%2A>, <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DisableSpecificWarnings%2A> et <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)\
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
