---
title: /Qspectre
ms.date: 10/12/2018
f1_keywords:
- /Qspectre
helpviewer_keywords:
- /Qspectre
ms.openlocfilehash: 42adff6564dc1c2ef47abffe9f9e6e630279ea7d
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57812458"
---
# <a name="qspectre"></a>/Qspectre

Spécifie la génération du compilateur des instructions pour atténuer certaines vulnérabilités de sécurité de Spectre variante 1.

## <a name="syntax"></a>Syntaxe

> **/Qspectre**

## <a name="remarks"></a>Notes

Le **/qspectre** option est disponible dans Visual Studio 2017 version 15.5.5 et versions ultérieures et dans Visual Studio 2015 Update 3 via [Ko 4338871](https://support.microsoft.com/help/4338871/visual-studio-2015-update-3-spectre-variant-1-toolset-qspectre). Il indique au compilateur d’insérer des instructions pour atténuer certaines [des failles de sécurité de Spectre](https://spectreattack.com/spectre.pdf). Ces vulnérabilités, appelées *attaques par canal latéral de l’exécution spéculative*, affecter de nombreux systèmes d’exploitation et les processeurs modernes, y compris les processeurs Intel, AMD et ARM.

Le **/qspectre** option est désactivée par défaut.

Dans sa version initiale, le **/qspectre** option travaillée uniquement sur le code optimisé. Dans Visual Studio 2017 version 15.7 et ultérieure, le **/qspectre** option est prise en charge à tous les niveaux d’optimisation.

Bibliothèques Visual C++ de Microsoft sont également disponibles dans les versions avec atténuation de Spectre. Les bibliothèques d’atténuation de Spectre pour Visual Studio 2017 peuvent être téléchargés dans le programme d’installation Visual Studio. Ils sont trouvent dans le **composants individuels** onglet sous **compilateurs, outils de génération et runtimes**, et le nom contient « Libs pour Spectre ». DLL et bibliothèques runtime statique avec atténuation est activée sont disponibles pour un sous-ensemble des runtimes Visual C++ : Code de démarrage VC ++, vcruntime140, msvcp140, concrt140 et vcamp140. Les DLL sont pris en charge pour le déploiement local de l’application uniquement ; le contenu de Redistributable Visual C++ 2017 Runtime bibliothèques n’ont pas été modifié. Vous pouvez également installer les bibliothèques d’atténuation de Spectre pour MFC et ATL, trouvé dans le **composants individuels** onglet sous **SDK, bibliothèques et infrastructures**.

### <a name="applicability"></a>Mise en application

Si votre code fonctionne sur les données qui transitent par une limite d’approbation, nous vous recommandons d’utiliser le **/qspectre** option pour régénérer et redéployer votre code pour résoudre ce problème dès que possible. Code qui charge des entrées non approuvées qui peuvent affecter l’exécution des exemples de code qui fonctionne sur les données qui transitent par une limite d’approbation, par exemple, les codes facilitant la procédure distante appelle, analyse les entrées non approuvées ou des fichiers ou utilise d’autres processus entre local interfaces de communication (IPC). Techniques de sandboxing standard peut ne pas suffire. Vous devez examiner soigneusement votre bacs à sable avant de décider que votre code ne franchit pas une limite d’approbation.

### <a name="availability"></a>Disponibilité

Le **/qspectre** option est disponible dans Visual Studio 2017 version 15.5.5 et dans toutes les mises à jour pour les compilateurs Microsoft MSVC (MSVC) effectuées sur ou après le 23 janvier 2018. Utilisez Visual Studio Installer pour mettre à jour le compilateur et pour installer les bibliothèques d’atténuation de Spectre en tant que composants individuels. Le **/qspectre** option est également disponible dans Visual Studio 2015 Update 3 via un correctif. Pour plus d’informations, consultez [Ko 4338871](https://support.microsoft.com/help/4338871).

Toutes les versions de Visual Studio 2017 version 15.5 et toutes les versions préliminaires de Visual Studio 2017 version 15.6 incluent une option non documentée, **/d2guardspecload**, qui équivaut au comportement initial de   **/qspectre**. Vous pouvez utiliser **/d2guardspecload** à appliquer les atténuations mêmes à votre code dans ces versions du compilateur. Mettez à jour votre build pour utiliser **/qspectre** dans les compilateurs qui prennent en charge l’option ; la **/qspectre** option peut également en charge les atténuations de nouveau dans les versions ultérieures du compilateur.

### <a name="effect"></a>Effet

Le **/qspectre** option génère le code pour atténuer la variante spectre 1, contournement de vérification des limites, [CVE-2017-5753](https://nvd.nist.gov/vuln/detail/CVE-2017-5753). Il fonctionne par insertion d’instructions qui agissent comme une barrière de l’exécution de code spéculative. Les instructions spécifiques qui permettent de réduire les spéculations processeur varient en fonction du processeur et de son architecture de micro et peuvent changer dans les futures versions du compilateur.

Lorsque le **/qspectre** option est activée, le compilateur tente d’identifier les instances où l’exécution spéculative peut-être contourner les vérifications des limites et insère les instructions de cloisonnement. Il est important de noter qu’il existe des limites à l’analyse un compilateur peut effectuer pour identifier les instances du type variant 1. Par conséquent, il n’existe aucune garantie que toutes les instances possibles de la variante 1 sont instrumentés sous **/qspectre**.

### <a name="performance-impact"></a>Impact sur les performances

L’impact sur les performances de **/qspectre** a été vu négligeable dans plusieurs bases de code très volumineuses, mais il n’existe aucune garantie que les performances de votre code sous **/qspectre** reste inchangé. Vous devez évaluer votre code pour déterminer l’effet de l’option sur les performances. Si vous savez que l’atténuation n’est pas requise dans une boucle ou un bloc critiques pour les performances, l’atténuation peut être désactivée à l’aide de manière sélective un [__declspec(spectre(nomitigation))](../../cpp/spectre.md) directive. Cette directive n’est pas disponible dans les compilateurs qui prennent en charge uniquement le **/d2guardspecload** option.

### <a name="required-libraries"></a>Bibliothèques nécessaires

Le **/qspectre** option du compilateur génère du code qui lie implicitement des versions des bibliothèques runtime qui ont été conçus pour fournir des atténuations de Spectre. Ces bibliothèques sont des composants facultatifs qui doivent être installés à l’aide de Visual Studio Installer :

- VC ++ 2017 version *version_numbers* Libs pour Spectre \[(x86 et x64) | (ARM) | (ARM64)]
- Visual C++ ATL pour \[(x86/x64) | ARM | ARM64] avec atténuations Spectre
- Visual C++ MFC pour \[x86/x64 | ARM | ARM64] avec atténuations Spectre

Si vous générez votre code à l’aide de **/qspectre** et ces bibliothèques ne sont pas installés, les rapports de système de génération **avertissement MSB8038 : Atténuation de spectre est activée, mais les bibliothèques atténuée de Spectre sont introuvables**. Si votre code MFC ou ATL ne parvient pas à générer et de l’éditeur de liens signale une erreur comme **erreur irrécupérable LNK1104 : Impossible d’ouvrir le fichier 'oldnames.lib'**, ces bibliothèques manquantes peuvent être la cause.

### <a name="additional-information"></a>Informations supplémentaires

Pour plus d’informations, consultez le fonctionnaire [ADV180002 avis de sécurité Microsoft, des conseils pour atténuer les vulnérabilités par canal latéral l’exécution spéculative](https://portal.msrc.microsoft.com/en-US/security-guidance/advisory/ADV180002). Conseils est également disponible à partir d’Intel, [atténuations de canal de côté l’exécution spéculative](https://software.intel.com/sites/default/files/managed/c5/63/336996-Speculative-Execution-Side-Channel-Mitigations.pdf)et ARM, [canaux du côté de Cache spéculation](https://developer.arm.com/-/media/Files/pdf/Cache_Speculation_Side-channels.pdf). Pour une vue d’ensemble de Windows spécifiques des atténuations de Spectre et Meltdown, consultez [comprendre l’impact sur les performances de solutions d’atténuation de Spectre et Meltdown sur les systèmes Windows](https://cloudblogs.microsoft.com/microsoftsecure/2018/01/09/understanding-the-performance-impact-of-spectre-and-meltdown-mitigations-on-windows-systems/) sur le blog Microsoft Secure. Pour une vue d’ensemble de la vulnérabilité Spectre traitée par les atténuations de MSVC, consultez [atténuations de Spectre dans MSVC](https://blogs.msdn.microsoft.com/vcblog/2018/01/15/spectre-mitigations-in-msvc./) sur le Blog d’équipe Visual C++.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration** > **C/C++** > **ligne de commande** page de propriétés.

1. Entrez le **/qspectre** option du compilateur dans le **des Options supplémentaires** boîte. Choisissez **OK** pour appliquer la modification.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[/Q, options (Opérations de bas niveau)](q-options-low-level-operations.md)<br/>
[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
