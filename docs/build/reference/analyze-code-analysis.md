---
title: /analyze (analyse de code)
ms.date: 10/01/2019
f1_keywords:
- VC.Project.VCCLCompilerTool.EnablePREfast
- /analyze
- VC.Project.VCCLCompilerTool.PREfastAdditionalOptions
- VC.Project.VCCLCompilerTool.PREfastAdditionalPlugins
helpviewer_keywords:
- /analyze compiler option [C++]
- -analyze compiler option [C++]
- analyze compiler option [C++]
ms.assetid: 81da536a-e030-4bd4-be18-383927597d08
ms.openlocfilehash: d647045d76dc32544f8146424b220547890b0943
ms.sourcegitcommit: 4517932a67bbf2db16cfb122d3bef57a43696242
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71816335"
---
# <a name="analyze-code-analysis"></a>/analyze (analyse de code)

Active l'analyse du code et les options de contrôle.

## <a name="syntax"></a>Syntaxe

```cmd
/analyze[-][:WX-][:log filename][:quiet][:stacksize number][:max_paths number][:only][:ruleset]
```

## <a name="arguments"></a>Arguments

/Analyze active l’analyse en mode par défaut. La sortie de l’analyse accède à la fenêtre **sortie** comme d’autres messages d’erreur. Utilisez **/analyze-** pour désactiver l’analyse de manière explicite.

/Analyze : WX-spécification de **/analyze : WX-** signifie que les avertissements d’analyse du code ne sont pas traités comme des erreurs lors de la compilation à l’aide de **/WX**. Pour plus d’informations, consultez [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (Niveau d’avertissement)](compiler-option-warning-level.md).

/Analyze : les résultats de l’analyseur détaillé `filename` sont écrits au format XML dans le fichier spécifié par `filename`.

/Analyze : Quiet désactive la sortie de l’analyseur dans la fenêtre **sortie** .

/Analyze : STACKSIZE `number` le paramètre `number` utilisé avec cette option spécifie la taille, en octets, du frame de pile pour lequel l’avertissement [C6262](/visualstudio/code-quality/c6262) est généré. L’espace avant `number` est facultatif. Si ce paramètre n'est pas spécifié, la taille du frame de pile est de 16 Ko par défaut.

/Analyze : max_paths `number` le paramètre `number` utilisé avec cette option spécifie le nombre maximal de chemins de code à analyser. Si ce paramètre n'est pas spécifié, ce nombre est égal à 256 par défaut. Des valeurs supérieures permettent d'effectuer une vérification plus approfondie, mais l'analyse risque de prendre plus de temps.

/Analyze : uniquement en général, le compilateur génère du code et effectue davantage de vérifications de syntaxe après l’exécution de l’analyseur. L’option **/analyze : only** désactive cette étape de génération de code. l’analyse est ainsi plus rapide, mais les erreurs de compilation et les avertissements qui peuvent avoir été découverts par l’étape de génération de code du compilateur ne sont pas émis. Si le programme n'est pas exempt d'erreurs au moment de la génération du code, les résultats de l'analyse risquent de ne pas être fiables. Par conséquent, nous vous recommandons d'utiliser cette option uniquement si le code réussit l'étape de vérification de la syntaxe de génération du code sans erreurs.

/Analyze : RuleSet `<file_path>.ruleset` vous permet de spécifier les ensembles de règles à analyser, y compris les ensembles de règles personnalisés que vous pouvez créer vous-même. Lorsque ce commutateur est défini, le moteur de règles est plus efficace, car il exclut les non-membres de l’ensemble de règles spécifié avant de l’exécuter. Lorsque le commutateur n’est pas défini, le moteur vérifie toutes les règles.

Les ensembles de règles fournis avec Visual Studio se trouvent dans **%VSInstallDir%\Team Tools\Static Analysis Tools\Rule sets.**

L’exemple d’ensemble de règles personnalisé suivant indique au moteur de règles de vérifier C6001 et C26494. Vous pouvez placer ce fichier n’importe où, à condition qu’il ait une extension `.ruleset` et que vous fournissiez le chemin d’accès complet dans l’argument.

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="New Rule Set" Description=" " ToolsVersion="15.0">
  <Rules AnalyzerId="Microsoft.Analyzers.NativeCodeAnalysis" RuleNamespace="Microsoft.Rules.Native">
    <Rule Id="C6001" Action="Warning" />
    <Rule Id="C26494" Action="Warning" />
  </Rules>
</RuleSet>
```

/Analyze : le plug-in active le plug-in PREfast spécifié dans le cadre des exécutions de l’analyse du code.
LocalEspC. dll est le plug-in qui implémente les contrôles d’analyse du code liés à l’accès concurrentiel dans la plage d’avertissements C261XX. Par exemple, [C26100](/visualstudio/code-quality/c26100), [C26101](/visualstudio/code-quality/c26101),..., [C26167](/visualstudio/code-quality/c26167).

Pour exécuter LocalEspC. dll, utilisez l’option de compilateur suivante : **/analyze : plugin LocalEspC. dll**

Pour exécuter CppCoreCheck. dll, exécutez d’abord cette commande à partir d’une invite de commandes développeur :

```cmd
set Esp.Extensions=CppCoreCheck.dll
```

Utilisez ensuite cette option du compilateur : **/analyze : plugin EspXEngine. dll**.

## <a name="remarks"></a>Notes

Pour plus d’informations, consultez [analyse du code pourC++ c/Overview](/visualstudio/code-quality/code-analysis-for-c-cpp-overview) et [analyse du codeC++ pour c/Warnings](/visualstudio/code-quality/code-analysis-for-c-cpp-warnings).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Développez le nœud **Propriétés de configuration**.

1. Développez le nœud **analyse du code** .

1. Sélectionnez la page de propriétés **Général** .

1. Modifiez une ou plusieurs des propriétés de l' **analyse du code** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

1. Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnablePREfast%2A>.

## <a name="see-also"></a>Voir aussi

- [Options du compilateur MSVC](compiler-options.md)
- [Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
