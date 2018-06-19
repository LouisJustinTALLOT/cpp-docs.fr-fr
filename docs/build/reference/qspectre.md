---
title: / Qspectre | Documents Microsoft
ms.custom: ''
ms.date: 1/23/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
f1_keywords:
- /Qspectre
helpviewer_keywords:
- /Qspectre
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3d87850ae5413ccf876eb4d4b44b34e34527ef9a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379417"
---
# <a name="qspectre"></a>/ Qspectre

Spécifie la génération du compilateur des instructions pour atténuer certaines vulnérabilités de sécurité de type variant 1 Spectre.

## <a name="syntax"></a>Syntaxe

> **/Qspectre**

## <a name="remarks"></a>Notes

Le **/Qspectre** option indique au compilateur d’insérer des instructions pour atténuer certaines [des failles de sécurité Spectre](https://spectreattack.com/spectre.pdf). Ces vulnérabilités, appelées *attaques côté canal de l’exécution spéculatif*, affecter de nombreux systèmes d’exploitation et les processeurs modernes, y compris les processeurs Intel, AMD et ARM.

Le **/Qspectre** option est désactivée par défaut.

Dans sa version initiale, le **/Qspectre** option fonctionne uniquement sur le code optimisé. Vous devez vous assurer que compilez votre code avec une des options d’optimisation (par exemple, [/O2 ou/O1](o1-o2-minimize-size-maximize-speed.md) mais pas [/Od](od-disable-debug.md)) pour vous assurer de l’atténuation est appliquée. De même, vérifiez que tout code qui utilise [#pragma optimize (« stg », off)](../../preprocessor/optimize.md).

### <a name="applicability"></a>Mise en application

Si votre code fonctionne sur les données qui rencontrent une limite de confiance, nous vous recommandons d’utiliser le **/Qspectre** permet de régénérer et redéployer votre code pour résoudre ce problème dès que possible. Code qui charge une entrée non fiable qui peut affecter l’exécution des exemples de code qui fonctionne sur les données qui dépasse une limite d’approbation, par exemple, le code qui permet de créer une procédure à distance appelle, analyse entrée non fiable ou des fichiers ou utilise d’autres processus entre local interfaces de communication (IPC). Techniques de sandboxing standard peuvent ne pas suffire. Vous devez examiner votre sandbox avec soin avant de décider que votre code ne dépasse pas une limite d’approbation.

### <a name="availability"></a>Disponibilité

Le **/Qspectre** option est disponible dans la version de Visual Studio 2017 15.5.5 et toutes les mises à jour aux compilateurs de Microsoft Visual C++ (MSVC) effectuées sur ou après le 23 janvier 2018.

Toutes les versions de la version de Visual Studio 2017 15,5 et toutes les versions préliminaires de Visual Studio version 15,6 inclure une option non documentée, **/d2guardspecload**, qui est équivalent au comportement initial de **/Qspectre**. Vous pouvez utiliser **/d2guardspecload** pour appliquer les mêmes fonctionnalités de prévention à votre code dans ces versions du compilateur. Mettez à jour votre build à utiliser **/Qspectre** dans les compilateurs qui prennent en charge l’option ; la **/Qspectre** option peut également prendre en charge les nouvelles solutions d’atténuation dans les versions ultérieures du compilateur.

### <a name="effect"></a>Effet

Le **/Qspectre** option génère le code pour atténuer le spectre de type variant 1, contournement de vérification des limites, [CVE-2017-5753](https://nvd.nist.gov/vuln/detail/CVE-2017-5753). Il fonctionne par insertion d’instructions qui agissent comme une barrière de l’exécution de code spéculatif. Les instructions spécifiques permet d’atténuer spéculation sur les processeurs varient en fonction du processeur et de son architecture de micro et peuvent changer dans les futures versions du compilateur.

Lorsque le **/Qspectre** est activée, le compilateur tente d’identifier les instances dans lesquelles l’exécution spéculative peut-être ignorer les contrôles de limites et insère les instructions de cloisonnement. Il est important de noter qu’il existe des limites à l’analyse un compilateur peut effectuer pour identifier les instances de type variant 1. Par conséquent, il n’existe aucune garantie que toutes les instances possibles de la variante 1 sont instrumentés sous **/Qspectre**.

### <a name="performance-impact"></a>Impact sur les performances

L’impact sur les performances de **/Qspectre** a été constaté négligeable dans plusieurs bases de code très volumineuses, mais il n’existe aucune garantie que les performances de votre code sous **/Qspectre** continuent. Vous devez banc d’essai de votre code pour déterminer l’effet de l’option sur les performances. Si vous savez que la prévention n’est pas requis dans une boucle ou un bloc critique pour les performances, la limitation des risques peuvent être désactivée à l’aide de sélectivement une [__declspec(spectre(nomitigation))](../../cpp/spectre.md) la directive. Cette directive n’est pas disponible dans les compilateurs qui prennent en charge uniquement la **/d2guardspecload** option.

### <a name="additional-information"></a>Informations supplémentaires

Pour plus d’informations, consultez officielle [ADV180002 avis de sécurité de Microsoft, des conseils pour limiter les vulnérabilités de canal latéral exécution spéculative](https://portal.msrc.microsoft.com/en-US/security-guidance/advisory/ADV180002). Guide est également disponible dans Intel, [spéculatif d’exécution côté canal atténuation](https://software.intel.com/sites/default/files/managed/c5/63/336996-Speculative-Execution-Side-Channel-Mitigations.pdf)et ARM, [canaux du côté de Cache spéculation](https://developer.arm.com/-/media/Files/pdf/Cache_Speculation_Side-channels.pdf). Pour obtenir une présentation spécifiques à Windows de solutions d’atténuation Spectre et Meltdown, consultez [comprendre l’impact des performances de solutions d’atténuation Spectre et Meltdown sur les systèmes Windows](https://cloudblogs.microsoft.com/microsoftsecure/2018/01/09/understanding-the-performance-impact-of-spectre-and-meltdown-mitigations-on-windows-systems/) sur le blog Microsoft Secure. Pour une vue d’ensemble de la vulnérabilité Spectre traitée par les solutions d’atténuation MSVC, consultez [atténuation Spectre en MSVC](https://blogs.msdn.microsoft.com/vcblog/2018/01/15/spectre-mitigations-in-msvc./) sur le Blog d’équipe Visual C++.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration** > **C/C++** > **ligne de commande** page de propriétés.

1. Entrez le **/Qspectre** option du compilateur dans le **des Options supplémentaires** boîte. Choisissez **OK** pour appliquer la modification.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[/Q, options (Opérations de bas niveau)](../../build/reference/q-options-low-level-operations.md)  
[Options du compilateur](../../build/reference/compiler-options.md)  
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)  
