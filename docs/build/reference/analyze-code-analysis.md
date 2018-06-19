---
title: -analyser (analyse du Code) | Documents Microsoft
ms.custom: ''
ms.date: 04/26/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.EnablePREfast
- /analyze
- VC.Project.VCCLCompilerTool.PREfastAdditionalOptions
- VC.Project.VCCLCompilerTool.PREfastAdditionalPlugins
dev_langs:
- C++
helpviewer_keywords:
- /analyze compiler option [C++]
- -analyze compiler option [C++]
- analyze compiler option [C++]
ms.assetid: 81da536a-e030-4bd4-be18-383927597d08
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4893f30bae3b29538c8bead637cb4d083087a57b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32376583"
---
# <a name="analyze-code-analysis"></a>/analyze (analyse de code)

Active l'analyse du code et les options de contrôle.

## <a name="syntax"></a>Syntaxe

```cmd
/analyze[-][:WX-][:log filename][:quiet][:stacksize number][:max_paths number][:only][:ruleset]
```

## <a name="arguments"></a>Arguments

 /analyze  
 Active l'analyse en mode par défaut. Sortie de l’analyse passe à la **sortie** fenêtre comme d’autres messages d’erreur. Utilisez **/ analyze-** pour désactiver explicitement l’analyse.

 /analyze:WX-  
 Spécification de **/ analyze : WX -** signifie que les avertissements d’analyse du code n’est pas traités comme des erreurs lorsque vous compilez à l’aide de **/WX**. Pour plus d’informations, consultez [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (Niveau d’avertissement)](../../build/reference/compiler-option-warning-level.md).

 /analyze:log `filename`  
 Les résultats détaillés de l'analyseur sont écrits au format XML dans le fichier spécifié par `filename`.

 /analyze:quiet  
 Désactive la sortie de l’analyseur pour le **sortie** fenêtre.

 /analyze:stacksize `number`  
 Le `number` paramètre qui est utilisé avec cette option spécifie la taille, en octets, du frame de pile pour lequel l’avertissement [C6262](/visualstudio/code-quality/c6262) est généré. Si ce paramètre n'est pas spécifié, la taille du frame de pile est de 16 Ko par défaut.

 /analyze:max_paths `number`  
 Le paramètre `number` utilisé avec cette option spécifie le nombre maximal de chemins de code à analyser. Si ce paramètre n'est pas spécifié, ce nombre est égal à 256 par défaut. Des valeurs supérieures permettent d'effectuer une vérification plus approfondie, mais l'analyse risque de prendre plus de temps.

 /analyze:only  
 En règle générale, le compilateur génère du code et effectue plutôt une vérification de la syntaxe après avoir exécuté l'analyseur. Le **/ analyze : uniquement** option désactive cette étape de génération de code ; cela rend l’analyse plus rapide, mais les erreurs de compilation et les avertissements qui peuvent avoir été détectées par le test de génération de code du compilateur ne sont pas émis. Si le programme n'est pas exempt d'erreurs au moment de la génération du code, les résultats de l'analyse risquent de ne pas être fiables. Par conséquent, nous vous recommandons d'utiliser cette option uniquement si le code réussit l'étape de vérification de la syntaxe de génération du code sans erreurs.

 / analyze : groupe de règles `<file_path>.ruleset`  
Permet de spécifier la règle définit à analyser, y compris les ensembles de règles personnalisés que vous pouvez créer vous-même. Lorsque ce commutateur est défini, le moteur de règles est plus efficace car elle exclut les membres non de la règle spécifiée est définie avant l’exécution. Lorsque le commutateur n’est pas défini, le moteur vérifie toutes les règles.

Les ensembles de règles qui sont fournis avec Visual Studio sont trouvent dans **%VSINSTALLDIR%\Team Tools\Static Analysis Tools\Rule jeux.**

L’exemple de jeu de règles personnalisé suivant indique au moteur de règles pour vérifier les C6001 et C26494. Vous pouvez placer ce fichier tant n’importe où il a un `.ruleset` extension et que vous indiquez le chemin complet de l’argument.

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="New Rule Set" Description=" " ToolsVersion="15.0">
  <Rules AnalyzerId="Microsoft.Analyzers.NativeCodeAnalysis" RuleNamespace="Microsoft.Rules.Native">
    <Rule Id="C6001" Action="Warning" />
    <Rule Id="C26494" Action="Warning" />
  </Rules>
</RuleSet>
```

/ analyze : plug-in  
Active le plug-in PREfast spécifié comme partie de l’analyse du code s’exécute. LocalEspC.dll est le plug-in qui implémente l’analyse du code lié à la concurrence vérifie les avertissements de la plage de C261XX. Par exemple, [C26100](/visualstudio/code-quality/c26100), [C26101](/visualstudio/code-quality/c26101),..., [C26167](/visualstudio/code-quality/c26167).

Pour exécuter LocalEspC.dll, utilisez cette option du compilateur : **/ analyze : plugin LocalEspC.dll**

Pour exécuter CppCoreCheck.dll, vous devez tout d’abord exécuter cette commande à partir d’une invite de commandes développeur :

```cmd
set Esp.Extensions=CppCoreCheck.dll
```

Utilisez ensuite cette option du compilateur : **/ analyze : plugin EspXEngine.dll**.

## <a name="remarks"></a>Notes

Pour plus d’informations, consultez [analyse du Code pour C/C++ Overview](/visualstudio/code-quality/code-analysis-for-c-cpp-overview) et [l’analyse du Code pour les avertissements C/C++](/visualstudio/code-quality/code-analysis-for-c-cpp-warnings).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Développez le **propriétés de Configuration** nœud.

1. Développez le **l’analyse du Code** nœud.

1. Sélectionnez la page de propriétés **Général** .

1. Modifier une ou plusieurs de la **l’analyse du Code** propriétés.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

1. Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnablePREfast%2A>.

## <a name="see-also"></a>Voir aussi

- [Options du compilateur](../../build/reference/compiler-options.md)
- [Définition des options du compilateur](../../build/reference/setting-compiler-options.md)