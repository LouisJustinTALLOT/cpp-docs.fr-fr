---
description: En savoir plus sur:/Qspectre
title: /Qspectre
ms.date: 09/06/2019
f1_keywords:
- VC.Project.VCCLCompilerTool.SpectreMitigation
helpviewer_keywords:
- /Qspectre
ms.openlocfilehash: 576052a9db8a4ce63c82afaf644f41fa847ad9a9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97225490"
---
# <a name="qspectre"></a>/Qspectre

Spécifie la génération par le compilateur d’instructions pour atténuer certaines failles de sécurité Spectre Variant 1.

## <a name="syntax"></a>Syntaxe

> **/Qspectre**

## <a name="remarks"></a>Notes

L’option **/Qspectre** est disponible dans Visual Studio 2017 version 15.5.5 et ultérieure ainsi que dans Visual Studio 2015 Update 3 par le biais de l’[article 4338871 de la base de connaissances](https://support.microsoft.com/help/4338871/visual-studio-2015-update-3-spectre-variant-1-toolset-qspectre). Elle entraîne l’insertion, par le compilateur, d’instructions destinées à atténuer certaines [failles de sécurité Spectre](https://spectreattack.com/spectre.pdf). Ces vulnérabilités sont appelées *attaques par canal côté exécution spéculative*. Elles affectent un grand nombre de systèmes d’exploitation et de processeurs modernes, y compris les processeurs Intel, AMD et ARM.

L’option **/Qspectre** est désactivée par défaut.

Dans sa version initiale, l’option **/Qspectre** fonctionnait uniquement sur du code optimisé. Dans Visual Studio 2017 version 15.7 et ultérieure, l’option **/Qspectre** est prise en charge à tous les niveaux d’optimisation.

Les bibliothèques Microsoft Visual C++ sont également disponibles dans les versions disposant de l’atténuation de Spectre. Les bibliothèques avec atténuation de Spectre pour Visual Studio 2017 et ultérieur peuvent être téléchargées dans Visual Studio Installer. Ils se trouvent sous l’onglet **composants individuels** sous **compilateurs, outils de génération et runtimes**, et contiennent « libs pour spectre » dans le nom. Les bibliothèques DLL et Runtime statiques avec atténuation activée sont disponibles pour un sous-ensemble des runtimes Visual C++ : code de démarrage VC + +, vcruntime140, msvcp140, concrt140 et vcamp140. Les dll sont uniquement prises en charge pour le déploiement local de l’application. Le contenu du Visual C++ 2017 et les bibliothèques d’exécution ultérieures redistribuables n’ont pas été modifiés.

Vous pouvez également installer les bibliothèques atténuées par spectre pour MFC et ATL. Ils se trouvent sous l’onglet **composants individuels** sous **Kits de développement logiciel (SDK), bibliothèques et frameworks**.

> [!NOTE]
> Il n’existe aucune version des bibliothèques atténuées par spectre pour les applications ou les composants Windows universels. Le déploiement local des applications de ces bibliothèques n’est pas possible.

### <a name="applicability"></a>Applicabilité

Si votre code s’exécute sur des données qui franchissent une limite d’approbation, nous vous recommandons d’utiliser l’option **/Qspectre** pour régénérer et redéployer votre code afin d’atténuer ce problème le plus rapidement possible. Un exemple de code de ce type est le code qui charge des entrées non fiables qui peuvent affecter l’exécution. Par exemple, le code qui effectue des appels de procédure distante, analyse des fichiers ou des entrées non fiables, ou utilise d’autres interfaces IPC (inter-process communication) locales. Les techniques de sandboxing standard peuvent ne pas suffire. Examinez attentivement vos bacs à sable avant de décider que votre code ne franchit pas une limite d’approbation.

### <a name="availability"></a>Disponibilité

L’option **/Qspectre** est disponible dans Visual Studio 2017 version 15.5.5, ainsi que dans toutes les mises à jour des compilateurs Microsoft C++ (MSVC) effectuées à partir du 23 janvier 2018. Utilisez Visual Studio Installer pour mettre à jour le compilateur et installer les bibliothèques avec atténuation de Spectre en tant que composants individuels. L’option **/Qspectre** est également disponible dans Visual Studio 2015 Update 3 par le biais d’un correctif. Pour plus d’informations, consultez l’[article 4338871 de la Base de connaissances](https://support.microsoft.com/help/4338871).

Toutes les versions de Visual Studio 2017 version 15,5, ainsi que tous les aperçus de Visual Studio 2017 version 15,6. incluez une option non documentée, **/d2guardspecload**. Elle est équivalente au comportement initial de **/Qspectre**. Vous pouvez utiliser **/d2guardspecload** pour appliquer les mêmes atténuations à votre code dans ces versions du compilateur. Nous vous recommandons de mettre à jour votre build pour utiliser **/Qspectre** dans les compilateurs qui prennent en charge l’option. L’option **/Qspectre** peut également prendre en charge de nouvelles atténuations dans les versions ultérieures du compilateur.

### <a name="effect"></a>Résultat

L’option **/Qspectre** génère du code pour atténuer Spectre Variant 1, Bounds Check Bypass, [CVE-2017-5753](https://nvd.nist.gov/vuln/detail/CVE-2017-5753). Elle fonctionne par insertion d’instructions qui agissent comme un cloisonnement de l’exécution spéculative du code. Les instructions spécifiques utilisées pour atténuer la spéculation du processeur varient en fonction du processeur et de sa micro-architecture ; elles peuvent changer dans les futures versions du compilateur.

Lorsque vous activez l’option **/Qspectre** , le compilateur tente d’identifier les instances où l’exécution spéculative peut contourner les contrôles de limites. C’est là qu’il insère les instructions de cloisonnement. Il est important de connaître les limites de l’analyse qu’un compilateur peut effectuer pour identifier les instances de la variante 1. Par conséquent, il n’y a aucune garantie que toutes les instances possibles de la variante 1 sont instrumentées sous **/Qspectre**.

### <a name="performance-impact"></a>Impact sur les performances

L’impact sur les performances de **/Qspectre** s’est avéré négligeable dans plusieurs bases de code redimensionnables. Toutefois, il n’y a aucune garantie que les performances de votre code sous **/Qspectre** restent inchangées. Vous devez effectuer un test d’évaluation de votre code pour déterminer l’effet de l’option sur les performances. Si vous savez que l’atténuation n’est pas requise dans un bloc ou une boucle critique pour les performances, vous pouvez désactiver de manière sélective l’atténuation à l’aide d’une directive [__declspec (spectre (nomitigation))](../../cpp/spectre.md) . Cette directive n’est pas disponible dans les compilateurs qui prennent uniquement en charge l’option **/d2guardspecload** .

### <a name="required-libraries"></a>Bibliothèques requises

L’option de compilateur **/Qspectre** génère du code qui lie implicitement les versions des bibliothèques Runtime générées pour fournir des atténuations spectre. Ces bibliothèques sont des composants facultatifs qui doivent être installés à l’aide de Visual Studio Installer :

- MSVC version *numéros_version* Libs for Spectre \[(x86 et x64) | (ARM) | (ARM64)]
- Visual C++ ATL pour \[(x86/x64) | ARM | ARM64] avec atténuations de Spectre
- Visual C++ MFC pour \[x86/x64 | ARM | ARM64] avec atténuations de Spectre

Si vous générez votre code à l’aide de **/Qspectre** et que ces bibliothèques ne sont pas installées, le système de génération signale un **Avertissement MSB8038 : l’atténuation de spectre est activée, mais les bibliothèques atténuées de spectre sont introuvables**. Si la génération de votre code MFC ou ATL échoue, et que l’éditeur de liens signale une erreur telle que **Erreur irrécupérable LNK1104 : impossible d’ouvrir le fichier’oldnames. lib'**; ces bibliothèques manquantes peuvent en être la cause.

### <a name="additional-information"></a>Informations supplémentaires

Pour plus d’informations, consultez l' [avis de sécurité Microsoft officiel ADV180002, conseils pour atténuer les vulnérabilités de canal latéral d’exécution spéculative](https://portal.msrc.microsoft.com/en-US/security-guidance/advisory/ADV180002). Des conseils sont également disponibles auprès d’Intel, [Speculative Execution Side Channel Mitigations](https://software.intel.com/sites/default/files/managed/c5/63/336996-Speculative-Execution-Side-Channel-Mitigations.pdf) (Atténuations par canal auxiliaire d’exécution spéculative), et d’ARM, [Cache Speculation Side-channels](https://developer.arm.com/-/media/Files/pdf/Cache_Speculation_Side-channels.pdf) (Mettre en cache les canaux auxiliaires de spéculation). Pour obtenir une vue d’ensemble spécifique à Windows des atténuations de spectre et de Meltdown, consultez [Présentation de l’impact sur les performances des atténuations de spectre et de Meltdown sur les systèmes Windows](https://www.microsoft.com/security/blog/2018/01/09/understanding-the-performance-impact-of-spectre-and-meltdown-mitigations-on-windows-systems/). Pour obtenir une vue d’ensemble des vulnérabilités de spectre adressées par les atténuations MSVC, consultez [atténuations de spectre dans MSVC](https://devblogs.microsoft.com/cppblog/spectre-mitigations-in-msvc./) sur le blog de l’équipe C++.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

::: moniker range="msvc-160"

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés **Propriétés de configuration** > **C/C++** > **génération de code** .

1. Sélectionnez une nouvelle valeur pour la propriété d' **atténuation spectre** . Choisissez **OK** pour appliquer le changement.

::: moniker-end

::: moniker range="<=msvc-150"

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés **Propriétés de configuration** > **C/C++** > **Ligne de commande**.

1. Entrez l’option de compilateur **/Qspectre** dans la zone **Options supplémentaires**. Choisissez **OK** pour appliquer le changement.

::: moniker-end

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[/Q options (opérations de bas niveau)](q-options-low-level-operations.md)<br/>
[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)
