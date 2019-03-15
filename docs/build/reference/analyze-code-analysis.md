---
title: /analyze (analyse de code)
ms.date: 04/26/2018
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
ms.openlocfilehash: 63cfd2bd206a361301c75110a684e1d2c642a1f2
ms.sourcegitcommit: faa42c8a051e746d99dcebe70fd4bbaf3b023ace
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2019
ms.locfileid: "57819504"
---
# <a name="analyze-code-analysis"></a>/analyze (analyse de code)

Active l'analyse du code et les options de contrôle.

## <a name="syntax"></a>Syntaxe

```cmd
/analyze[-][:WX-][:log filename][:quiet][:stacksize number][:max_paths number][:only][:ruleset]
```

## <a name="arguments"></a>Arguments

/Analyze active sur l’analyse dans le mode par défaut. Sortie de l’analyse passe à la **sortie** fenêtre similaire à d’autres messages d’erreur. Utilisez **/ analyze-** pour désactiver explicitement l’analyse.

/ analyze : WX-spécification **/ analyze : WX -** signifie que les avertissements d’analyse du code n’est pas traités comme des erreurs lorsque vous compilez à l’aide de **/WX**. Pour plus d’informations, consultez [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (Niveau d’avertissement)](compiler-option-warning-level.md).

/ analyze : log `filename` les résultats détaillés de l’analyseur sont écrits au format XML dans le fichier spécifié par `filename`.

/ analyze : quiet désactive la sortie d’analyseur pour le **sortie** fenêtre.

/ analyze : stacksize `number` le `number` paramètre qui est utilisé avec cette option spécifie la taille, en octets, du frame de pile pour lequel l’avertissement [C6262](/visualstudio/code-quality/c6262) est généré. Si ce paramètre n'est pas spécifié, la taille du frame de pile est de 16 Ko par défaut.

/ analyze : max_paths `number` le `number` paramètre qui est utilisé avec cette option spécifie le nombre maximal de chemins d’accès du code à analyser. Si ce paramètre n'est pas spécifié, ce nombre est égal à 256 par défaut. Des valeurs supérieures permettent d'effectuer une vérification plus approfondie, mais l'analyse risque de prendre plus de temps.

/ analyze : uniquement en règle générale, le compilateur génère du code et qu’il effectue la vérification après avoir exécuté l’Analyseur de syntaxe plus. Le **/ analyze : uniquement** option désactive la génération de code ; Ceci analyse plus rapide mais des erreurs de compilation et les avertissements qui peuvent avoir été détectées par la génération de code du compilateur ne sont pas émis. Si le programme n'est pas exempt d'erreurs au moment de la génération du code, les résultats de l'analyse risquent de ne pas être fiables. Par conséquent, nous vous recommandons d'utiliser cette option uniquement si le code réussit l'étape de vérification de la syntaxe de génération du code sans erreurs.

/ analyze : ruleset `<file_path>.ruleset` vous permet de spécifier la règle qui définit à analyser, y compris les ensembles de règles personnalisés que vous pouvez créer vous-même. Lorsque ce commutateur est défini, le moteur de règles est plus efficace car elle exclut les membres non de la règle spécifiée définie avant l’exécution. Lorsque le commutateur n’est pas défini, le moteur vérifie toutes les règles.

Les ensembles de règles fournis avec Visual Studio sont trouvent dans **%VSINSTALLDIR%\Team Tools\Static Analysis Tools\Rule jeux.**

L’exemple de jeu de règles personnalisé suivant indique au moteur de règles pour vérifier C6001 et C26494. Vous pouvez placer ce fichier n’importe où tant que qu’il a un `.ruleset` extension et que vous indiquez le chemin complet dans l’argument.

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="New Rule Set" Description=" " ToolsVersion="15.0">
  <Rules AnalyzerId="Microsoft.Analyzers.NativeCodeAnalysis" RuleNamespace="Microsoft.Rules.Native">
    <Rule Id="C6001" Action="Warning" />
    <Rule Id="C26494" Action="Warning" />
  </Rules>
</RuleSet>
```

/ analyze : plug-in permet le plug-in PREfast spécifié comme partie de l’analyse du code est exécutée.
LocalEspC.dll est le plug-in qui implémente l’analyse du code dépendant de l’accès concurrentiel vérifie les avertissements de la plage de C261XX. Par exemple, [C26100](/visualstudio/code-quality/c26100), [C26101](/visualstudio/code-quality/c26101),..., [C26167](/visualstudio/code-quality/c26167).

Pour exécuter LocalEspC.dll, utilisez cette option du compilateur : **/ analyze : plug-in LocalEspC.dll**

Pour exécuter CppCoreCheck.dll, exécutez d’abord cette commande à partir d’une invite de commandes développeur :

```cmd
set Esp.Extensions=CppCoreCheck.dll
```

Puis utilisez cette option du compilateur : **/ analyze : plug-in EspXEngine.dll**.

## <a name="remarks"></a>Notes

Pour plus d’informations, consultez [analyse du Code pour C/C++ Overview](/visualstudio/code-quality/code-analysis-for-c-cpp-overview) et [analyse du Code pour les avertissements C/C++](/visualstudio/code-quality/code-analysis-for-c-cpp-warnings).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Développez le nœud **Propriétés de configuration**.

1. Développez le **analyse du Code** nœud.

1. Sélectionnez la page de propriétés **Général** .

1. Modifier une ou plusieurs de la **analyse du Code** propriétés.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

1. Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnablePREfast%2A>.

## <a name="see-also"></a>Voir aussi

- [Options du compilateur MSVC](compiler-options.md)
- [Syntaxe de ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
