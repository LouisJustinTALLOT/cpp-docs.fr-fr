---
title: -w,-W0,-W1, - W2,-W3, - W4,-w1,-w2,-w3,-w4,-Wall, -wd,-nous, -wo, -Wv, - WX (niveau d’avertissement) | Documents Microsoft
ms.custom: ''
ms.date: 01/31/2018
ms.technology:
- cpp-tools
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 60fc8072a95787f9e6f50e7e5c50408ef66e3261
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379248"
---
# <a name="w-w0-w1-w2-w3-w4-w1-w2-w3-w4-wall-wd-we-wo-wv-wx-warning-level"></a>Wn, / W0, /W1, /W2, /W3, / W4, /w1, /w2, /w3, / W4, Wall, /wd, / nous, /wo, /WV., /Won (niveau d’avertissement)

Spécifie comment le compilateur génère les avertissements pour une compilation donnée.

## <a name="syntax"></a>Syntaxe

> **/w**  
> **/W0**  
> **/W1**  
> **/W2**  
> **/W3**  
> **/W4**  
> **/Wall**  
> **/WV.**\[**:**_version_]  
> **/WX**  
> **/W1**_avertissement_  
> **/W2**_avertissement_  
> **/w3**_avertissement_  
> **/ W4**_avertissement_  
> **/WD**_avertissement_  
> **/We**_avertissement_  
> **/wo**_avertissement_  

## <a name="remarks"></a>Notes

Les options de l’avertissement spécifient les avertissements du compilateur à afficher et le comportement d’avertissement pour la compilation entier.

Les options d’avertissement et les arguments associés sont décrites dans le tableau suivant :

|Option|Description|
------------|-----------------|
|**/w**|Supprime tous les avertissements du compilateur.|
|**/W0**<br /><br /> **/W1**<br /><br /> **/W2**<br /><br /> **/W3**<br /><br /> **/W4**|Spécifie le niveau d’avertissements générés par le compilateur. Les niveaux d’avertissement valide comprise entre 0 et 4 :<br />**/ W0** supprime tous les avertissements. Cela est équivalent à **Wn**.<br />**/ W1** affiche les avertissements de niveau 1 (critique). **/ W1** est le paramètre par défaut dans le compilateur de ligne de commande.<br />**/ W2** présente le niveau 1 et les avertissements de niveau 2 (importantes).<br />**/ W3** affiche au niveau 1, niveau 2 et les avertissements de niveau 3 (qualité de production). **/ W3** est le paramètre par défaut dans l’IDE.<br />**/ W4** présente le niveau 1, niveau 2 et les avertissements de niveau 3 et tous les de niveau 4 avertissements (informations) qui ne sont pas désactivées par défaut. Nous vous recommandons d’utiliser cette option pour fournir des avertissements de type "lint"-like. Pour un nouveau projet, il peut être préférable d’utiliser **/W4** dans toutes les compilations ; ainsi, le minimum d’erreurs difficiles à trouver les erreurs de code.|
|**/Wall**|Affiche tous les avertissements sont affichés par **/W4** et tous les autres avertissements qui **/W4** n’inclut pas, par exemple, les avertissements qui sont désactivés par défaut. Pour plus d’informations, consultez [du compilateur avertissements qu’est désactivé par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md).|
|**/WV.**\[**:**_version_]|Affiche uniquement les avertissements introduits dans la version du compilateur *version* et les versions antérieures. Vous pouvez utiliser cette option pour supprimer les nouveaux avertissements dans le code lorsque vous migrez vers une version plus récente du compilateur et mettre à jour votre processus de génération existant pendant que vous les résoudre. Le paramètre facultatif *version* prend la forme *nn*[. *mm*[. *bbbbb*]] où *nn* est le numéro de version principale, *mm* est le numéro de version secondaire facultative, et *bbbbb* est le numéro de version facultatif le compilateur. Par exemple, utilisez */Wv:17* pour afficher les avertissements introduits dans Visual Studio 2012 (autrement dit, n’importe quelle version du compilateur qui a un numéro de version principale de 17) ou une version antérieure, sans supprimer les avertissements introduits dans Visual Studio 2013 (version principale 18) et versions ultérieures. Par défaut, **/WV.** utilise le numéro de version du compilateur actuel et aucun avertissement n’est supprimés. Pour plus d’informations sur les avertissements sont supprimés par la version du compilateur, consultez [avertissements du compilateur par la version du compilateur](../../error-messages/compiler-warnings/compiler-warnings-by-compiler-version.md).|
|**/WX**|Considère tous les avertissements du compilateur comme des erreurs. Pour un nouveau projet, il peut être préférable d’utiliser **/WX** dans toutes les compilations ; résoudre tous les avertissements garantit le minimum d’erreurs difficiles à trouver les erreurs de code.<br /><br /> L’éditeur de liens a également un **/WX** option. Pour plus d’informations, consultez l’article [/WX (Traiter les avertissements de l’Éditeur de liens comme des erreurs)](../../build/reference/wx-treat-linker-warnings-as-errors.md).|
|**/W1**_nnnn_<br /><br /> **/W2**_nnnn_<br /><br /> **/w3**_nnnn_<br /><br /> **/ W4**_nnnn_|Définit le niveau d’avertissement pour le numéro d’avertissement spécifié par _nnnn_. Cela vous permet de modifier le comportement du compilateur pour cet avertissement lorsque la valeur d’un niveau d’avertissement spécifiques. Vous pouvez utiliser ces options en combinaison avec d’autres options d’avertissement pour appliquer des normes de votre propre code pour les avertissements, plutôt que la valeur par défaut de ceux fournis par Visual Studio.<br /><br /> Par exemple, **/w34326** fait être C4326 comme un avertissement de niveau 3 au lieu de niveau 1. Si vous compilez à l’aide du **/w34326** option et la **/W2** option, l’avertissement C4326 n’est pas générée.|
|**/WD**_nnnn_|Supprime l’avertissement du compilateur spécifié par _nnnn_.<br /><br /> Par exemple, **/wd4326** supprime l’avertissement du compilateur C4326.|
|**/We**_nnnn_|Considère l’avertissement du compilateur spécifié par _nnnn_ comme une erreur.<br /><br /> Par exemple, **/we4326** provoque l’avertissement C4326 est traitée comme une erreur par le compilateur.|
|**/wo**_nnnn_|L’avertissement du compilateur qui est spécifié par les rapports _nnnn_ qu’une seule fois.<br /><br /> Par exemple, **/wo4326** causes avertissement C4326 seulement une seule fois, la première fois qu’il est rencontré par le compilateur.|

Si vous utilisez les options d’avertissement lorsque vous créez un en-tête précompilé à l’aide de la [/Yc](../../build/reference/yc-create-precompiled-header-file.md) option, toute utilisation de l’en-tête précompilé à l’aide de la [/Yu](../../build/reference/yu-use-precompiled-header-file.md) l’option, ces mêmes options d’avertissement en vigueur à nouveau. Vous pouvez remplacer les options d’avertissement définies dans l’en-tête précompilé à l’aide d’une autre option d’avertissement sur la ligne de commande.

Vous pouvez utiliser un [#pragma warning](../../preprocessor/warning.md) directive pour contrôler le niveau d’avertissement signalé au moment de la compilation dans les fichiers sources spécifiques.

Directives de pragma avertissement dans le code source ne sont pas affectés par la **Wn** option.

Le [documentation sur les erreurs de build](../../error-messages/compiler-errors-1/c-cpp-build-errors.md) décrit les avertissements et les niveaux d’avertissement et indique pourquoi certaines instructions ne peuvent pas compiler comme vous le souhaitez.

### <a name="to-set-the-compiler-options-in-the-visual-studio-development-environment"></a>Pour définir les options du compilateur dans l’environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Pour définir le **/W0**, **/W1**, **/W2**, **/W3**, **/W4**, **/Wall**m **/WV.**, **/WX** ou **/WX-** options, sélectionnez le **propriétés de Configuration** > **C / C++** > **général** page de propriétés.

   - Pour définir le **/W0**, **/W1**, **/W2**, **/W3**, **/W4**, ou **/Wall** Options, modifier le **le niveau d’avertissement** propriété.

   - Pour définir le **/WX** ou **/WX-** options, modifier le **considérer les avertissements comme des erreurs** propriété.

   - Pour définir la version pour le **/WV.** option, entrez le numéro de version du compilateur dans le **avertissement Version** propriété.

1. Pour définir le **/wd** ou **/we** options, sélectionnez le **propriétés de Configuration** > **C/C++**  >   **Advanced** page de propriétés.

   - Pour définir le **/wd** option, sélectionnez le **désactivation des avertissements spécifiques** propriété de contrôle de liste déroulante, puis choisissez **modifier**. Dans la zone d’édition dans le **désactivation des avertissements spécifiques** boîte de dialogue, entrez le numéro d’avertissement. Pour entrer plus d’un avertissement, séparez les valeurs à l’aide d’un point-virgule (**;**). Par exemple, pour désactiver C4001 et C4010, entrez **4001 ; 4010**. Choisissez **OK** pour enregistrer vos modifications et revenir à la **Pages de propriétés** boîte de dialogue.

   - Pour définir le **/we** option, sélectionnez le **considérer les avertissements comme des erreurs spécifiques** propriété de contrôle de liste déroulante, puis choisissez **modifier**. Dans la zone d’édition dans le **considérer les avertissements comme des erreurs spécifiques** boîte de dialogue, entrez le numéro d’avertissement. Pour entrer plus d’un avertissement, séparez les valeurs à l’aide d’un point-virgule (**;**). Par exemple, pour traiter C4001 et C4010 en tant qu’erreurs, entrez **4001 ; 4010**. Choisissez **OK** pour enregistrer vos modifications et revenir à la **Pages de propriétés** boîte de dialogue.

1. Pour définir le **/wo** option, sélectionnez le **propriétés de Configuration** > **C/C++** > **ligne de commande** page de propriétés. Entrez l’option du compilateur dans le **des Options supplémentaires** boîte.

1. Choisissez **OK** pour enregistrer vos modifications.

### <a name="to-set-the-compiler-option-programmatically"></a>Pour définir l'option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WarningLevel%2A>, <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WarnAsError%2A>, <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DisableSpecificWarnings%2A> et <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur](../../build/reference/compiler-options.md)  
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)  
