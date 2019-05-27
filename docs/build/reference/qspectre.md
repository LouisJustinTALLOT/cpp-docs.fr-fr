---
title: /Qspectre
ms.date: 10/12/2018
f1_keywords:
- /Qspectre
helpviewer_keywords:
- /Qspectre
ms.openlocfilehash: e44416a44a9f772c17bc734d26c62ff87be775c8
ms.sourcegitcommit: a10c9390413978d36b8096b684d5ed4cf1553bc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65837421"
---
# <a name="qspectre"></a>/Qspectre

Spécifie la génération par le compilateur d’instructions pour atténuer certaines failles de sécurité Spectre Variant 1.

## <a name="syntax"></a>Syntaxe

> **/Qspectre**

## <a name="remarks"></a>Remarques

L’option **/Qspectre** est disponible dans Visual Studio 2017 version 15.5.5 et ultérieure ainsi que dans Visual Studio 2015 Update 3 par le biais de l’[article 4338871 de la base de connaissances](https://support.microsoft.com/help/4338871/visual-studio-2015-update-3-spectre-variant-1-toolset-qspectre). Elle entraîne l’insertion, par le compilateur, d’instructions destinées à atténuer certaines [failles de sécurité Spectre](https://spectreattack.com/spectre.pdf). Ces failles, appelées *attaques par canal auxiliaire d’exécution spéculative*, affectent de nombreux systèmes d’exploitation et processeurs modernes, notamment les processeurs Intel, AMD et ARM.

L’option **/Qspectre** est désactivée par défaut.

Dans sa version initiale, l’option **/Qspectre** fonctionnait uniquement sur du code optimisé. Dans Visual Studio 2017 version 15.7 et ultérieure, l’option **/Qspectre** est prise en charge à tous les niveaux d’optimisation.

Les bibliothèques Microsoft Visual C++ sont également disponibles dans les versions disposant de l’atténuation de Spectre. Les bibliothèques avec atténuation de Spectre pour Visual Studio 2017 et ultérieur peuvent être téléchargées dans Visual Studio Installer. Elles se trouvent sous l’onglet **Composants individuels** sous **Compilateurs, outils de build et runtime**, et leur nom contient « Libs for Spectre ». Les bibliothèques runtime statiques et DLL pour lesquelles l’atténuation est activée sont disponibles pour un sous-ensemble de runtimes Visual C++ : code de démarrage VC++, vcruntime140, msvcp140, concrt140 et vcamp140. Les DLL sont prises en charge uniquement pour un déploiement local d’application ; le contenu du package redistribuable de bibliothèques runtime Visual C++ 2017 et ultérieur n’a pas été modifié. Vous pouvez également installer les bibliothèques avec atténuations de Spectre pour MFC et ATL se trouvant sous l’onglet **Composants individuels** sous **SDK, bibliothèques et frameworks**.

### <a name="applicability"></a>Applicabilité

Si votre code fonctionne sur des données qui franchissent une limite d’approbation, nous vous recommandons d’utiliser dès que possible l’option **/Qspectre** pour régénérer et redéployer votre code afin d’atténuer ce problème. Les exemples de code fonctionnant sur des données qui franchissent une limite d’approbation incluent le code qui charge une entrée non approuvée pouvant affecter l’exécution, par exemple le code qui effectue des appels de procédure distante, qui analyse une entrée ou des fichiers non approuvés ou qui utilise d’autres interfaces de communication entre processus (IPC) locales. Les techniques de sandboxing standard peuvent ne pas suffire. Vous devez examiner soigneusement vos bacs à sable (sandbox) avant de décider que votre code ne franchit pas une limite d’approbation.

### <a name="availability"></a>Disponibilité

L’option **/Qspectre** est disponible dans Visual Studio 2017 version 15.5.5 et dans toutes les mises à jour des compilateurs Microsoft MSVC (MSVC) effectuées le 23 janvier 2018 ou après cette date. Utilisez Visual Studio Installer pour mettre à jour le compilateur et installer les bibliothèques avec atténuation de Spectre en tant que composants individuels. L’option **/Qspectre** est également disponible dans Visual Studio 2015 Update 3 par le biais d’un correctif. Pour plus d’informations, consultez l’[article 4338871 de la Base de connaissances](https://support.microsoft.com/help/4338871).

Toutes les versions de Visual Studio 2017 version 15.5 et toutes les préversions de Visual Studio 2017 version 15.6 incluent une option non documentée, **/d2guardspecload**, dont le comportement est équivalent au comportement initial de **/Qspectre**. Vous pouvez utiliser **/d2guardspecload** pour appliquer les mêmes atténuations à votre code dans ces versions du compilateur. Mettez à jour votre build pour utiliser l’option **/Qspectre** dans les compilateurs qui la prennent en charge ; l’option **/Qspectre** peut également prendre en charge de nouvelles atténuations dans les versions ultérieures du compilateur.

### <a name="effect"></a>Effet

L’option **/Qspectre** génère du code pour atténuer Spectre Variant 1, Bounds Check Bypass, [CVE-2017-5753](https://nvd.nist.gov/vuln/detail/CVE-2017-5753). Elle fonctionne par insertion d’instructions qui agissent comme un cloisonnement de l’exécution spéculative du code. Les instructions spécifiques utilisées pour atténuer la spéculation du processeur varient en fonction du processeur et de sa micro-architecture ; elles peuvent changer dans les futures versions du compilateur.

Quand l’option **/Qspectre** est activée, le compilateur tente d’identifier les instances où l’exécution spéculative peut ignorer les vérifications des limites et insère les instructions de cloisonnement. Il est important de noter qu’il existe des limites à l’analyse qu’un compilateur peut effectuer pour identifier des instances de Variant 1. Par conséquent, rien ne garantit que toutes les instances possibles de Variant 1 sont instrumentées sous **/Qspectre**.

### <a name="performance-impact"></a>Impact sur les performances

L’impact sur les performances de **/Qspectre** a été jugé négligeable dans plusieurs bases de code très grandes, mais il n’existe aucune garantie que les performances de votre code sous **/Qspectre** restent inchangées. Vous devez effectuer un test d’évaluation de votre code pour déterminer l’effet de l’option sur les performances. Si vous savez que l’atténuation n’est pas nécessaire dans une boucle ou un bloc critiques pour les performances, l’atténuation peut être désactivée de manière sélective à l’aide d’une directive [__declspec(spectre(nomitigation))](../../cpp/spectre.md). Cette directive n’est pas disponible dans les compilateurs qui prennent uniquement en charge l’option **/d2guardspecload**.

### <a name="required-libraries"></a>Bibliothèques nécessaires

L’option de compilateur **/Qspectre** génère du code liant implicitement des versions des bibliothèques runtime qui ont été générées pour fournir des atténuations de Spectre. Ces bibliothèques sont des composants facultatifs qui doivent être installés à l’aide de Visual Studio Installer :

- MSVC version *numéros_version* Libs for Spectre \[(x86 et x64) | (ARM) | (ARM64)]
- Visual C++ ATL pour \[(x86/x64) | ARM | ARM64] avec atténuations de Spectre
- Visual C++ MFC pour \[x86/x64 | ARM | ARM64] avec atténuations de Spectre

Si vous générez votre code à l’aide de **/Qspectre** et que ces bibliothèques ne sont pas installées, le système de build signale l’**avertissement MSB8038 : l’atténuation de Spectre est activée mais les bibliothèques atténuées contre Spectre sont introuvables**. Si la génération de votre code MFC ou ATL échoue et que l’éditeur de liens signale une erreur comme **Erreur irrécupérable LNK1104 : Impossible d’ouvrir le fichier 'oldnames.lib'** , ces bibliothèques manquantes peuvent en être la cause.

### <a name="additional-information"></a>Informations supplémentaires

Pour plus d’informations, consultez le document officiel [Microsoft Security Advisory ADV180002, Guidance to mitigate speculative execution side-channel vulnerabilities](https://portal.msrc.microsoft.com/en-US/security-guidance/advisory/ADV180002) (Conseil de sécurité Microsoft ADV180002 : Conseils pour atténuer les failles par canal auxiliaire d’exécution spéculative). Des conseils sont également disponibles auprès d’Intel, [Speculative Execution Side Channel Mitigations](https://software.intel.com/sites/default/files/managed/c5/63/336996-Speculative-Execution-Side-Channel-Mitigations.pdf) (Atténuations par canal auxiliaire d’exécution spéculative), et d’ARM, [Cache Speculation Side-channels](https://developer.arm.com/-/media/Files/pdf/Cache_Speculation_Side-channels.pdf) (Mettre en cache les canaux auxiliaires de spéculation). Pour obtenir une vue d’ensemble spécifique à Windows des atténuations de Spectre et Meltdown, consultez [Understanding the performance impact of Spectre and Meltdown mitigations on Windows Systems](https://cloudblogs.microsoft.com/microsoftsecure/2018/01/09/understanding-the-performance-impact-of-spectre-and-meltdown-mitigations-on-windows-systems/) (Présentation de l’impact sur les performances des atténuations de Spectre et Meltdown sur les systèmes Windows) sur le blog Microsoft Secure. Pour obtenir une vue d’ensemble de la vulnérabilité de Spectre traitée par les atténuations MSVC, consultez [Spectre mitigations in MSVC](https://blogs.msdn.microsoft.com/vcblog/2018/01/15/spectre-mitigations-in-msvc./) (Atténuations de Spectre dans MSVC) sur le blog de l’équipe Visual C++.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés **Propriétés de configuration** > **C/C++** > **Ligne de commande**.

1. Entrez l’option de compilateur **/Qspectre** dans la zone **Options supplémentaires**. Choisissez **OK** pour appliquer le changement.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[/Q, options (Opérations de bas niveau)](q-options-low-level-operations.md)<br/>
[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
