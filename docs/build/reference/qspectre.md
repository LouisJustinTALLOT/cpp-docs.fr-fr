---
title: /Qspectre
ms.date: 10/12/2018
f1_keywords:
- /Qspectre
helpviewer_keywords:
- /Qspectre
ms.openlocfilehash: e0d3af50015b77af297cbee22f439cd17d803de9
ms.sourcegitcommit: 6cf0c67acce633b07ff31b56cebd5de3218fd733
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/24/2019
ms.locfileid: "67344160"
---
# <a name="qspectre"></a>/Qspectre

Spécifie la génération par le compilateur d’instructions pour atténuer certaines failles de sécurité Spectre Variant 1.

## <a name="syntax"></a>Syntaxe

> **/Qspectre**

## <a name="remarks"></a>Notes

L’option **/Qspectre** est disponible dans Visual Studio 2017 version 15.5.5 et ultérieure ainsi que dans Visual Studio 2015 Update 3 par le biais de l’[article 4338871 de la base de connaissances](https://support.microsoft.com/help/4338871/visual-studio-2015-update-3-spectre-variant-1-toolset-qspectre). Elle entraîne l’insertion, par le compilateur, d’instructions destinées à atténuer certaines [failles de sécurité Spectre](https://spectreattack.com/spectre.pdf). Ces vulnérabilités sont appelées *attaques par canal latéral de l’exécution spéculative*. Ils affectent de nombreux systèmes d’exploitation et les processeurs modernes, y compris les processeurs Intel, AMD et ARM.

L’option **/Qspectre** est désactivée par défaut.

Dans sa version initiale, l’option **/Qspectre** fonctionnait uniquement sur du code optimisé. Dans Visual Studio 2017 version 15.7 et ultérieure, l’option **/Qspectre** est prise en charge à tous les niveaux d’optimisation.

Les bibliothèques Microsoft Visual C++ sont également disponibles dans les versions disposant de l’atténuation de Spectre. Les bibliothèques avec atténuation de Spectre pour Visual Studio 2017 et ultérieur peuvent être téléchargées dans Visual Studio Installer. Elles sont trouvées dans le **composants individuels** onglet sous **compilateurs, outils de génération et runtimes**, et le nom contient « Libs pour Spectre ». Les bibliothèques runtime statiques et DLL pour lesquelles l’atténuation est activée sont disponibles pour un sous-ensemble de runtimes Visual C++ : code de démarrage VC++, vcruntime140, msvcp140, concrt140 et vcamp140. Les DLL sont pris en charge pour le déploiement local de l’application uniquement. Le contenu de l’élément visuel C++ 2017 et versions ultérieures Runtime bibliothèques redistribuables n’ont pas été modifié.

Vous pouvez également installer les bibliothèques d’atténuation de Spectre pour MFC et ATL. Elles sont trouvées dans le **composants individuels** onglet sous **SDK, bibliothèques et infrastructures**.

### <a name="applicability"></a>Applicabilité

Si votre code fonctionne sur les données qui transitent par une limite d’approbation, nous vous recommandons d’utiliser le **/qspectre** option pour régénérer et redéployer votre code pour résoudre ce problème dès que possible. Un exemple de ce code est le code qui charge des entrées non approuvées qui peuvent affecter l’exécution. Par exemple, codes facilitant la procédure distante appelle, analyse les entrées non approuvées ou des fichiers ou utilise d’autres interfaces de communication entre processus local (IPC). Les techniques de sandboxing standard peuvent ne pas suffire. Examinez soigneusement votre bacs à sable avant de décider de que votre code ne franchit une limite d’approbation.

### <a name="availability"></a>Disponibilité

Le **/qspectre** option est disponible dans Visual Studio 2017 version 15.5.5 et dans toutes les mises à jour Microsoft C++ compilateurs (MSVC) effectuées sur ou après le 23 janvier 2018. Utilisez Visual Studio Installer pour mettre à jour le compilateur et installer les bibliothèques avec atténuation de Spectre en tant que composants individuels. L’option **/Qspectre** est également disponible dans Visual Studio 2015 Update 3 par le biais d’un correctif. Pour plus d’informations, consultez l’[article 4338871 de la Base de connaissances](https://support.microsoft.com/help/4338871).

Toutes les versions de Visual Studio 2017 version 15.5 et toutes les versions préliminaires de Visual Studio 2017 version 15.6. inclure une option non documentée, **/d2guardspecload**. Il est équivalent au comportement initial de **/qspectre**. Vous pouvez utiliser **/d2guardspecload** pour appliquer les mêmes atténuations à votre code dans ces versions du compilateur. Nous vous recommandons de vous mettre à jour votre build pour utiliser **/qspectre** dans les compilateurs qui prennent en charge l’option. Le **/qspectre** option peut également en charge les atténuations de nouveau dans les versions ultérieures du compilateur.

### <a name="effect"></a>Effet

L’option **/Qspectre** génère du code pour atténuer Spectre Variant 1, Bounds Check Bypass, [CVE-2017-5753](https://nvd.nist.gov/vuln/detail/CVE-2017-5753). Elle fonctionne par insertion d’instructions qui agissent comme un cloisonnement de l’exécution spéculative du code. Les instructions spécifiques utilisées pour atténuer la spéculation du processeur varient en fonction du processeur et de sa micro-architecture ; elles peuvent changer dans les futures versions du compilateur.

Lorsque vous activez le **/qspectre** option, le compilateur tente d’identifier les instances où l’exécution spéculative peut-être contourner les vérifications des limites. Voilà où il insère les instructions de cloisonnement. Il est important d’être conscient des limites à l’analyse un compilateur peut faire pour identifier les instances du type variant 1. Par conséquent, il n’existe aucune garantie que toutes les instances possibles de la variante 1 sont instrumentés sous **/qspectre**.

### <a name="performance-impact"></a>Impact sur les performances

L’impact sur les performances de **/qspectre** semblait être négligeable dans plusieurs bases de code dimensionnable. Toutefois, il n’existe aucune garantie ayant les performances de votre code sous **/qspectre** reste inchangé. Vous devez effectuer un test d’évaluation de votre code pour déterminer l’effet de l’option sur les performances. Si vous savez que l’atténuation n’est pas requis dans une boucle ou un bloc de performances critiques, vous pouvez désactiver de manière sélective l’atténuation à l’aide d’un [__declspec(spectre(nomitigation))](../../cpp/spectre.md) directive. Cette directive n’est pas disponible dans les compilateurs qui prennent en charge uniquement le **/d2guardspecload** option.

### <a name="required-libraries"></a>Bibliothèques nécessaires

Le **/qspectre** option du compilateur génère du code qui lie implicitement des versions des bibliothèques runtime conçus pour fournir des atténuations de Spectre. Ces bibliothèques sont des composants facultatifs qui doivent être installés à l’aide de Visual Studio Installer :

- MSVC version *numéros_version* Libs for Spectre \[(x86 et x64) | (ARM) | (ARM64)]
- Visual C++ ATL pour \[(x86/x64) | ARM | ARM64] avec atténuations de Spectre
- Visual C++ MFC pour \[x86/x64 | ARM | ARM64] avec atténuations de Spectre

Si vous générez votre code à l’aide de **/qspectre** et ces bibliothèques ne sont pas installés, les rapports de système de génération **avertissement MSB8038 : l’atténuation de Spectre est activée mais les bibliothèques atténuées contre Spectre sont introuvables**. Si votre code MFC ou ATL ne parvient pas à générer, et l’éditeur de liens signale une erreur comme **erreur irrécupérable LNK1104 : Impossible d’ouvrir le fichier 'oldnames.lib'** , ces bibliothèques manquantes peuvent être la cause.

### <a name="additional-information"></a>Informations supplémentaires

Pour plus d’informations, consultez le [ADV180002 avis de sécurité Microsoft, des conseils pour atténuer les vulnérabilités par canal latéral l’exécution spéculative](https://portal.msrc.microsoft.com/en-US/security-guidance/advisory/ADV180002). Des conseils sont également disponibles auprès d’Intel, [Speculative Execution Side Channel Mitigations](https://software.intel.com/sites/default/files/managed/c5/63/336996-Speculative-Execution-Side-Channel-Mitigations.pdf) (Atténuations par canal auxiliaire d’exécution spéculative), et d’ARM, [Cache Speculation Side-channels](https://developer.arm.com/-/media/Files/pdf/Cache_Speculation_Side-channels.pdf) (Mettre en cache les canaux auxiliaires de spéculation). Pour une vue d’ensemble de Windows spécifiques des atténuations de Spectre et Meltdown, consultez [comprendre l’impact sur les performances de solutions d’atténuation de Spectre et Meltdown sur les systèmes Windows](https://www.microsoft.com/security/blog/2018/01/09/understanding-the-performance-impact-of-spectre-and-meltdown-mitigations-on-windows-systems/). Pour une vue d’ensemble des vulnérabilités de Spectre visées par les atténuations de MSVC, consultez [atténuations de Spectre dans MSVC](https://devblogs.microsoft.com/cppblog/spectre-mitigations-in-msvc./) sur le C++ Blog de l’équipe.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés **Propriétés de configuration** > **C/C++**  > **Ligne de commande**.

1. Entrez l’option de compilateur **/Qspectre** dans la zone **Options supplémentaires**. Choisissez **OK** pour appliquer le changement.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[/Q, options (Opérations de bas niveau)](q-options-low-level-operations.md)<br/>
[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
