---
title: /analyze (Analyse de code)
description: Syntaxe et utilisation de l’option/Analyze du compilateur Microsoft C++.
ms.date: 07/27/2020
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
ms.openlocfilehash: dcf44f1d282a9dd39205aecb4e75b59a6e8481f9
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92919096"
---
# <a name="analyze-code-analysis"></a>`/analyze` (Analyse du code)

Active l'analyse du code et les options de contrôle.

## <a name="syntax"></a>Syntaxe

::: moniker range=">=msvc-150"

> **`/analyze`**\
> **`/analyze-`**\
> **`/analyze:autolog`**\
> **`/analyze:autolog-`**\
> **`/analyze:autolog:ext`***extension*\
> **`/analyze:log`***nom du fichier*\
> **`/analyze:max_paths`***nombre*\
> **`/analyze:only`**\
> **`/analyze:plugin`***plug-in-dll*\
> **`/analyze:quiet`**\
> **`/analyze:ruleset`** ensemble de *règles*\
> **`/analyze:stacksize`***nombre*\
> **`/analyze:WX-`**

::: moniker-end
::: moniker range="msvc-140"

> **`/analyze`**\
> **`/analyze-`**\
> **`/analyze:autolog`**\
> **`/analyze:autolog-`**\
> **`/analyze:autolog:ext`***extension*\
> **`/analyze:log`***nom du fichier*\
> **`/analyze:max_paths`***nombre*\
> **`/analyze:only`**\
> **`/analyze:plugin`***plug-in-dll*\
> **`/analyze:quiet`**\
> **`/analyze:stacksize`***nombre*\
> **`/analyze:WX-`**

::: moniker-end

## <a name="arguments"></a>Arguments

**`/analyze`**\
Active l'analyse en mode par défaut. La sortie de l’analyse est envoyée à la console ou à la fenêtre **sortie** de Visual Studio, comme d’autres messages d’erreur. Utilisez **`/analyze-`** pour désactiver l’analyse de manière explicite.

**`/analyze:autolog`**\
Les résultats détaillés de l’analyseur sont écrits au format XML dans un fichier avec le même nom de base que le fichier source et une extension de *`.pftlog`* . **`/analyze:autolog-`** désactive ce fichier journal.

**`/analyze:autolog:ext`***extension*\
Les résultats détaillés de l’analyseur sont écrits au format XML dans un fichier avec le même nom de base que le fichier source et une extension de l' *extension* .

**`/analyze:log`***nom du fichier*\
Les résultats détaillés de l’analyseur sont écrits au format XML dans le fichier spécifié par *filename* .

**`/analyze:max_paths`***nombre*\
Le paramètre *Number* utilisé avec cette option spécifie le nombre maximal de chemins de code à analyser. Si ce paramètre n’est pas spécifié, le nombre est 256 par défaut. Des valeurs plus élevées entraînent une vérification plus approfondie, mais l’analyse peut prendre plus de temps.

**`/analyze:only`**\
En règle générale, le compilateur génère du code et effectue plutôt une vérification de la syntaxe après avoir exécuté l'analyseur. L' **`/analyze:only`** option désactive cette étape de génération de code. Elle rend l’analyse plus rapide, mais n’émet pas d’erreurs et d’avertissements du compilateur que l’étape de génération de code du compilateur peut trouver. Si le programme n’est pas exempt d’erreurs de génération de code, les résultats d’analyse peuvent ne pas être fiables. Nous vous recommandons d’utiliser cette option uniquement si le code passe déjà la vérification de la syntaxe de génération de code sans erreurs.

**`/analyze:plugin`***plug-in-dll*\
Active le plug-in PREfast spécifié dans le cadre des exécutions de l’analyse du code.

::: moniker range="<=msvc-150"

LocalEspC.dll est le plug-in qui implémente les contrôles d’analyse du code liés à l’accès concurrentiel dans la plage d’avertissements C261XX. Par exemple, [C26100](../../code-quality/c26100.md), [C26101](../../code-quality/c26101.md),...,  [C26167](../../code-quality/c26167.md).

Pour exécuter LocalEspC.dll, utilisez cette option du compilateur : **`/analyze:plugin LocalEspC.dll`**

::: moniker-end
::: moniker range=">=msvc-160"

ConcurrencyCheck.dll implémente les contrôles d’analyse du code liés à l’accès concurrentiel dans la plage d’avertissements C261XX. Par exemple, [C26100](../../code-quality/c26100.md), [C26101](../../code-quality/c26101.md),...,  [C26167](../../code-quality/c26167.md).

Pour exécuter ConcurrencyCheck.dll, exécutez d’abord cette commande à partir d’une invite de commandes développeur :

```cmd
set Esp.Extensions=ConcurrencyCheck.dll
```

Utilisez ensuite cette option du compilateur : **`/analyze:plugin EspXEngine.dll`** .

Pour exécuter CppCoreCheck.dll, exécutez d’abord cette commande à partir d’une invite de commandes développeur :

```cmd
set Esp.Extensions=CppCoreCheck.dll
```

Utilisez ensuite cette option du compilateur : **`/analyze:plugin EspXEngine.dll`** .

::: moniker-end

**`/analyze:quiet`**\
Désactive la sortie de l’analyseur dans la fenêtre de **sortie** de la console ou de Visual Studio.

::: moniker range=">=msvc-150"

**`/analyze:ruleset`***FILE_PATH. RuleSet*\
Vous permet de spécifier les ensembles de règles à analyser, y compris les ensembles de règles personnalisés que vous pouvez créer vous-même. Lorsque ce commutateur est défini, le moteur de règles est plus efficace, car il exclut les non-membres de l’ensemble de règles spécifié avant de l’exécuter. Dans le cas contraire, le moteur vérifie toutes les règles.

Les ensembles de règles fournis avec Visual Studio se trouvent dans *`%VSINSTALLDIR%\Team Tools\Static Analysis Tools\Rule Sets`* .

L’exemple d’ensemble de règles personnalisé suivant indique au moteur de règles de vérifier C6001 et C26494. Vous pouvez placer ce fichier n’importe où, à condition qu’il ait une *`.ruleset`* extension et que vous fournissiez le chemin d’accès complet dans l’argument.

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="New Rule Set" Description="New rules to apply." ToolsVersion="15.0">
  <Rules AnalyzerId="Microsoft.Analyzers.NativeCodeAnalysis" RuleNamespace="Microsoft.Rules.Native">
    <Rule Id="C6001" Action="Warning" />
    <Rule Id="C26494" Action="Warning" />
  </Rules>
</RuleSet>
```

::: moniker-end

**`/analyze:stacksize`***nombre*\
Le paramètre *Number* utilisé avec cette option spécifie la taille, en octets, du frame de pile pour lequel l’avertissement [C6262](../../code-quality/c6262.md) est généré. L’espace avant le *nombre* est facultatif. Si ce paramètre n’est pas spécifié, la taille du frame de pile est de 16 Ko par défaut.

**`/analyze:WX-`**\
Les avertissements d’analyse du code ne sont pas traités comme des erreurs quand vous compilez à l’aide de **`/WX`** . Pour plus d’informations, consultez [ `/WX` (niveau d’avertissement)](compiler-option-warning-level.md).

## <a name="remarks"></a>Notes

Pour plus d’informations, consultez [vue d’ensemble de l’analyse du code pour c/c++](../../code-quality/code-analysis-for-c-cpp-overview.md) et [analyse du code pour les avertissements c/c++](../../code-quality/code-analysis-for-c-cpp-warnings.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page **Propriétés de configuration** général de l'  >  **analyse du code**  >  **General** .

1. Modifiez une ou plusieurs des propriétés de l' **analyse du code** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

1. Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnablePREfast%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)\
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)
