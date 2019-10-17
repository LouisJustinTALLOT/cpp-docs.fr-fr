---
title: /analyze (Analyse de code)
ms.date: 10/15/2019
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
ms.openlocfilehash: f537fdea2703805c7ab1c57ba0d4429f6b683ae4
ms.sourcegitcommit: 9aab425662a66825772f091112986952f341f7c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72444886"
---
# <a name="analyze-code-analysis"></a>/analyze (Analyse de code)

Active l'analyse du code et les options de contrôle.

## <a name="syntax"></a>Syntaxe

> **/analyze**[-] [ **: WX-** ] [ **:** *nom du fichier*journal] [ **: Quiet**] [ **: STACKSIZE** *nombre*] [ **: max_paths** *numéro*] [ **: uniquement**] [ **: RuleSet** *RuleSet*] [ **:p Lugin**  *plugin-dll*]

## <a name="arguments"></a>Arguments

**/analyze**\
Active l'analyse en mode par défaut. La sortie de l’analyse accède à la fenêtre **sortie** comme d’autres messages d’erreur. Utilisez **/analyze-** pour désactiver l’analyse de manière explicite.

**/analyze : WX-** \
Les avertissements d’analyse du code ne sont pas traités comme des erreurs quand vous compilez à l’aide de **/WX**. Pour plus d’informations, consultez [/WX (niveau d’avertissement)](compiler-option-warning-level.md).

**/analyze :** *nom de fichier*journal \
Les résultats détaillés de l’analyseur sont écrits au format XML dans le fichier spécifié par *filename*.

**/analyze : quiet**\
Désactive la sortie de l’analyseur dans la fenêtre **sortie** .

**/analyze : STACKSIZE** *nombre*\
Le paramètre *Number* utilisé avec cette option spécifie la taille, en octets, du frame de pile pour lequel l’avertissement [C6262](/visualstudio/code-quality/c6262) est généré. L’espace avant le *nombre* est facultatif. Si ce paramètre n’est pas spécifié, la taille du frame de pile est de 16 Ko par défaut.

**/analyze : max_paths** *nombre*\
Le paramètre *Number* utilisé avec cette option spécifie le nombre maximal de chemins de code à analyser. Si ce paramètre n’est pas spécifié, le nombre est 256 par défaut. Des valeurs plus élevées entraînent une vérification plus approfondie, mais l’analyse peut prendre plus de temps.

**/analyze : uniquement**\
En règle générale, le compilateur génère du code et effectue plutôt une vérification de la syntaxe après avoir exécuté l'analyseur. L’option **/analyze : only** désactive cette étape de génération de code. L’analyse est plus rapide, mais les erreurs et les avertissements de compilation que l’étape de génération de code du compilateur peut trouver ne sont pas émis. Si le programme n’est pas exempt d’erreurs de génération de code, les résultats d’analyse peuvent ne pas être fiables. Nous vous recommandons d’utiliser cette option uniquement si le code passe déjà la vérification de la syntaxe de génération de code sans erreurs.

**/analyze : RuleSet** *chemin_fichier. RuleSet*\
Vous permet de spécifier les ensembles de règles à analyser, y compris les ensembles de règles personnalisés que vous pouvez créer vous-même. Lorsque ce commutateur est défini, le moteur de règles est plus efficace, car il exclut les non-membres de l’ensemble de règles spécifié avant de l’exécuter. Dans le cas contraire, le moteur vérifie toutes les règles.

Les ensembles de règles fournis avec Visual Studio se trouvent dans *%VSInstallDir%\Team Tools\Static Analysis Tools\Rule sets.*

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

**/analyze :** *plug-in de plug-in-dll*\
Active le plug-in PREfast spécifié dans le cadre des exécutions de l’analyse du code.

::: moniker range="<=vs-2017"

LocalEspC. dll est le plug-in qui implémente les contrôles d’analyse du code liés à l’accès concurrentiel dans la plage d’avertissements C261XX. Par exemple, [C26100](/visualstudio/code-quality/c26100), [C26101](/visualstudio/code-quality/c26101),..., [C26167](/visualstudio/code-quality/c26167).

Pour exécuter LocalEspC. dll, utilisez l’option de compilateur suivante : **/analyze : plugin LocalEspC. dll**

::: moniker-end
::: moniker range=">=vs-2019"

ConcurrencyCheck. dll implémente les contrôles d’analyse du code liés à l’accès concurrentiel dans la plage d’avertissements C261XX. Par exemple, [C26100](/visualstudio/code-quality/c26100), [C26101](/visualstudio/code-quality/c26101),..., [C26167](/visualstudio/code-quality/c26167).

Pour exécuter ConcurrencyCheck. dll, exécutez d’abord cette commande à partir d’une invite de commandes développeur :

```cmd
set Esp.Extensions=ConcurrencyCheck.dll
```

Utilisez ensuite cette option du compilateur : **/analyze : plugin EspXEngine. dll**.

::: moniker-end

Pour exécuter CppCoreCheck. dll, exécutez d’abord cette commande à partir d’une invite de commandes développeur :

```cmd
set Esp.Extensions=CppCoreCheck.dll
```

Utilisez ensuite cette option du compilateur : **/analyze : plugin EspXEngine. dll**.

## <a name="remarks"></a>Notes

Pour plus d’informations, consultez [analyse du code pourC++ c/Overview](/visualstudio/code-quality/code-analysis-for-c-cpp-overview) et [analyse du codeC++ pour c/Warnings](/visualstudio/code-quality/code-analysis-for-c-cpp-warnings).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page **Propriétés de Configuration** >  analyse du**code** > **général** .

1. Modifiez une ou plusieurs des propriétés de l' **analyse du code** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

1. Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnablePREfast%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)\
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
