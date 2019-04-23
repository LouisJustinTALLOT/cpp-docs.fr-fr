---
title: wln, / W0, W1, W2, / w3, / W4, W1, W2, / w3, / W4, Wall, WD, / we, Wo, / WV, /WX (niveau d’avertissement)
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
ms.openlocfilehash: 7b5c19c95cff3058bb3dcc6640f8ab07cf01edd6
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59040067"
---
# <a name="w-w0-w1-w2-w3-w4-w1-w2-w3-w4-wall-wd-we-wo-wv-wx-warning-level"></a>wln, / W0, W1, W2, / w3, / W4, W1, W2, / w3, / W4, Wall, WD, / we, Wo, / WV, /WX (niveau d’avertissement)

Spécifie comment le compilateur génère les avertissements pour une compilation donnée.

## <a name="syntax"></a>Syntaxe

> **/w**
>  **/W0**
> **W1**
> **W2**
> **w3** 
>  **/W4**
>  **/Wall**
>  **/WV**\[**:**_version _] **/WX**
> **W1**_avertissement_
> **W2** _ avertissement_
> **w3**_avertissement_
>  **/W4**_avertissement_ 
>  **WD**_avertissement_
>  **/we**_avertissement_ 
>  **wo**_avertissement_

## <a name="remarks"></a>Notes

Les options de l’avertissement spécifient que les avertissements du compilateur à afficher et le comportement d’avertissement pour la compilation entière.

Les options de l’avertissement et les arguments associés sont décrites dans le tableau suivant :

|Option|Description|
------------|-----------------|
|**/w**|Supprime tous les avertissements du compilateur.|
|**/W0**<br /><br /> **/W1**<br /><br /> **/W2**<br /><br /> **/W3**<br /><br /> **/W4**|Spécifie le niveau d’avertissements générés par le compilateur. Les niveaux d’avertissement valide comprise entre 0 et 4 :<br />**/ W0** supprime tous les avertissements. Cela équivaut à **/w**.<br />**/ W1** affiche les avertissements de niveau 1 (critique). **/ W1** est le paramètre par défaut dans le compilateur de ligne de commande.<br />**/ W2** présente au niveau 1 et les avertissements de niveau 2 (importantes).<br />**/ W3** affiche au niveau 1, niveau 2 et les avertissements de niveau 3 (qualité de production). **/ W3** est le paramètre par défaut dans l’IDE.<br />**/ W4** présente le niveau 1, niveau 2 et les avertissements de niveau 3, et tous les niveau 4 avertissements (informations) qui ne sont pas désactivées par défaut. Nous vous recommandons d’utiliser cette option pour fournir des avertissements de type lint. Pour un nouveau projet, il peut être préférable d’utiliser **/W4** dans toutes les compilations ; Cela garantit les erreurs de code difficiles à trouver détectables.|
|**/Wall**|Affiche tous les avertissements affichés par **/W4** et tous les autres avertissements qui **/W4** n’inclut pas, par exemple, les avertissements qui sont désactivés par défaut. Pour plus d’informations, consultez [du compilateur avertissements que sont désactivé par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md).|
|**/ WV**\[**:**_version_]|Affiche uniquement les avertissements introduits dans la version du compilateur *version* et versions antérieures. Vous pouvez utiliser cette option pour supprimer les avertissements de nouveau dans le code lorsque vous migrez vers une version plus récente du compilateur et de maintenir votre processus de génération existante tandis que les corriger. Le paramètre facultatif *version* prend la forme *nn*[. *mm*[. *bbbbb*]] où *nn* est le numéro de version principale, *mm* est le numéro de version mineure facultatif et *bbbbb* est le numéro de build facultatif de le compilateur. Par exemple, utilisez */Wv:17* pour afficher les avertissements introduits dans Visual Studio 2012 (autrement dit, n’importe quelle version du compilateur qui a un numéro de version principale de 17) ou une version antérieure, sans supprimer les avertissements introduits dans Visual Studio 2013 (version principale 18) et versions ultérieures. Par défaut, **/WV** utilise le numéro de version du compilateur actuel et aucun avertissement n’est pas supprimés. Pour plus d’informations sur les avertissements sont supprimés par la version du compilateur, consultez [avertissements du compilateur par version du compilateur](../../error-messages/compiler-warnings/compiler-warnings-by-compiler-version.md).|
|**/WX**|Considère tous les avertissements du compilateur comme des erreurs. Pour un nouveau projet, il peut être préférable d’utiliser **/WX** dans toutes les compilations ; résolution de tous les avertissements garantit que les erreurs de code difficiles à trouver détectables.<br /><br /> L’éditeur de liens a également un **/WX** option. Pour plus d’informations, consultez l’article [/WX (Traiter les avertissements de l’Éditeur de liens comme des erreurs)](wx-treat-linker-warnings-as-errors.md).|
|**/w1**_nnnn_<br /><br /> **/w2**_nnnn_<br /><br /> **/w3**_nnnn_<br /><br /> **/w4**_nnnn_|Définit le niveau d’avertissement pour le numéro d’avertissement spécifié par _nnnn_. Cela vous permet de modifier le comportement du compilateur pour cet avertissement si la valeur d’un niveau d’avertissement spécifique. Vous pouvez utiliser ces options en combinaison avec d’autres options d’avertissement pour appliquer votre propre codage normes pour les avertissements, plutôt que les valeurs par défaut fournies par Visual Studio.<br /><br /> Par exemple, **/w34326** fait être C4326 comme un avertissement de niveau 3 au lieu de niveau 1. Si vous compilez à l’aide à la fois le **/w34326** option et la **W2** option, l’avertissement C4326 n’est pas générée.|
|**/wd**_nnnn_|Supprime l’avertissement du compilateur spécifié par _nnnn_.<br /><br /> Par exemple, **/wd4326** supprime l’avertissement du compilateur C4326.|
|**/we**_nnnn_|Traite l’avertissement du compilateur spécifié par _nnnn_ comme une erreur.<br /><br /> Par exemple, **/we4326** provoque l’avertissement C4326 est traitée comme une erreur par le compilateur.|
|**/wo**_nnnn_|L’avertissement du compilateur qui est spécifié par les rapports _nnnn_ qu’une seule fois.<br /><br /> Par exemple, **/wo4326** causes possibles de l’avertissement C4326 seulement une seule fois, la première fois qu’il est rencontré par le compilateur.|

Si vous utilisez les options d’avertissement lorsque vous créez un en-tête précompilé à l’aide de la [/Yc](yc-create-precompiled-header-file.md) option, toute utilisation de l’en-tête précompilé à l’aide de la [/Yu](yu-use-precompiled-header-file.md) option entraîne en vigueur ces mêmes options avertissement à nouveau. Vous pouvez remplacer les options d’avertissement définies dans l’en-tête précompilé à l’aide d’une autre option d’avertissement sur la ligne de commande.

Vous pouvez utiliser un [#pragma warning](../../preprocessor/warning.md) directive pour contrôler le niveau d’avertissement signalé au moment de la compilation dans les fichiers sources spécifiques.

Directives de pragma warning dans le code source ne sont pas affectés par la **/w** option.

Le [documentation sur les erreurs de build](../../error-messages/compiler-errors-1/c-cpp-build-errors.md) décrit les avertissements et les niveaux d’avertissement et indique pourquoi certaines instructions ne peuvent pas compiler comme vous le souhaitez.

### <a name="to-set-the-compiler-options-in-the-visual-studio-development-environment"></a>Pour définir les options du compilateur dans l’environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Pour définir le **/W0**, **W1**, **W2**, **w3**, **/W4**, **/Wall**, **/WV**, **/WX** ou **/WX-** options, sélectionnez le **propriétés de Configuration** > **C / C++**   >  **Général** page de propriétés.

   - Pour définir le **/W0**, **W1**, **W2**, **w3**, **/W4**, ou **/Wall** Options, modifier le **niveau d’avertissement** propriété.

   - Pour définir le **/WX** ou **/WX-** options, modifier le **considérer les avertissements comme des erreurs** propriété.

   - Pour définir la version pour le **/WV** option, entrez le numéro de version du compilateur dans le **avertissement Version** propriété.

1. Pour définir le **WD** ou **/we** options, sélectionnez le **propriétés de Configuration** > **C/C++**  >   **Advanced** page de propriétés.

   - Pour définir le **WD** option, sélectionnez le **désactivation des avertissements spécifiques** propriété contrôle drop down, puis choisissez **modifier**. Dans la zone d’édition dans le **désactivation des avertissements spécifiques** boîte de dialogue, entrez le numéro d’avertissement. Pour entrer plusieurs avertissements, séparez les valeurs à l’aide d’un point-virgule (**;**). Par exemple, pour désactiver C4001 et C4010, entrez **4001 ; 4010**. Choisissez **OK** pour enregistrer vos modifications et revenir à la **Pages de propriétés** boîte de dialogue.

   - Pour définir le **/we** option, sélectionnez le **considérer les avertissements spécifiques en tant qu’erreurs** propriété contrôle drop down, puis choisissez **modifier**. Dans la zone d’édition dans le **considérer les avertissements spécifiques en tant qu’erreurs** boîte de dialogue, entrez le numéro d’avertissement. Pour entrer plusieurs avertissements, séparez les valeurs à l’aide d’un point-virgule (**;**). Par exemple, pour traiter C4001 et C4010 comme des erreurs, entrez **4001 ; 4010**. Choisissez **OK** pour enregistrer vos modifications et revenir à la **Pages de propriétés** boîte de dialogue.

1. Pour définir le **wo** option, sélectionnez le **propriétés de Configuration** > **C/C++** > **ligne de commande** page de propriétés. Entrez l’option du compilateur dans le **des Options supplémentaires** boîte.

1. Choisissez **OK** pour enregistrer vos modifications.

### <a name="to-set-the-compiler-option-programmatically"></a>Pour définir l'option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WarningLevel%2A>, <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WarnAsError%2A>, <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DisableSpecificWarnings%2A> et <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
