---
title: /constexpr (contrôler l’évaluation de constexpr)
ms.date: 08/15/2017
f1_keywords:
- /constexpr
- -constexpr
helpviewer_keywords:
- /constexpr control constexpr evaluation [C++]
- -constexpr control constexpr evaluation [C++]
- constexpr control constexpr evaluation [C++]
ms.assetid: 76d56784-f5ad-401d-841d-09d1059e8b8c
ms.openlocfilehash: ea55a2686c2cdd7f4e0a6b558d3cd456fe87cb9d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50544246"
---
# <a name="constexpr-control-constexpr-evaluation"></a>/constexpr (contrôler l’évaluation de constexpr)

Utilisez le **/constexpr** options du compilateur pour les paramètres de contrôle pour **constexpr** évaluation au moment de la compilation.

## <a name="syntax"></a>Syntaxe

> **/ constexpr : Depth**<em>N</em>
>  **/constexpr:backtrace**<em>N</em>
>  ** /constexpr : Steps** <em>N</em>

## <a name="arguments"></a>Arguments

**profondeur**<em>N</em> limiter la profondeur des récursive **constexpr** l’appel de fonction *N* niveaux. La valeur par défaut est 512.

**backtrace**<em>N</em> afficher jusqu'à *N* **constexpr** évaluations dans les diagnostics. La valeur par défaut est 10.

**étapes**<em>N</em> Terminate **constexpr** évaluation après *N* étapes. La valeur par défaut est 100 000.

## <a name="remarks"></a>Notes

Le **/constexpr** évaluation au moment de la compilation de contrôlent les options du compilateur **constexpr** expressions. Procédure d’évaluation, les niveaux de récursivité et la profondeur de suivi sont contrôlés pour empêcher le compilateur de passer beaucoup trop de temps sur **constexpr** évaluation. Pour plus d’informations sur la **constexpr** l’élément de langage, consultez [constexpr (C++)](../../cpp/constexpr-cpp.md).

Le **/constexpr** options sont disponibles depuis dans Visual Studio 2015.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez votre projet **Pages de propriétés** boîte de dialogue.

2. Sous **propriétés de Configuration**, développez le **C/C++** dossier et choisissez le **ligne de commande** page de propriétés.

3. Entrer une **/constexpr** options du compilateur dans le **des Options supplémentaires** boîte. Choisissez **OK** ou **appliquer** pour enregistrer vos modifications.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur](../../build/reference/compiler-options.md)<br/>
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)