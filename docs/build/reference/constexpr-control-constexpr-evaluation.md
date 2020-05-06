---
title: /constexpr (Contrôler l’évaluation de constexpr)
ms.date: 08/15/2017
f1_keywords:
- /constexpr
- -constexpr
helpviewer_keywords:
- /constexpr control constexpr evaluation [C++]
- -constexpr control constexpr evaluation [C++]
- constexpr control constexpr evaluation [C++]
ms.assetid: 76d56784-f5ad-401d-841d-09d1059e8b8c
ms.openlocfilehash: 4d3f33a64dcebfc40778f81354cb5067a5239ace
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825589"
---
# <a name="constexpr-control-constexpr-evaluation"></a>/constexpr (Contrôler l’évaluation de constexpr)

Utilisez les options du compilateur **/constexpr** pour contrôler les paramètres de l’évaluation de **constexpr** au moment de la compilation.

## <a name="syntax"></a>Syntaxe

> **/constexpr : profondeur**<em>N</em>\
> **/constexpr : trace**<em>N</em>\
> **/constexpr : étapes**<em>N</em>

## <a name="arguments"></a>Arguments

**profondeur**<em>n</em> limitez la profondeur de l’appel de fonction **constexpr** récursive à *n* niveaux. La valeur par défaut est 512.

le **suivi des traces**<em>n</em> affiche jusqu’à *n* évaluations **constexpr** dans les Diagnostics. La valeur par défaut est de 10.

les **étapes**<em>n</em> terminent l’évaluation de **constexpr** après *N* étapes. La valeur par défaut est 100 000.

## <a name="remarks"></a>Notes 

Les options du compilateur **/constexpr** contrôlent l’évaluation au moment de la compilation des expressions **constexpr** . Les étapes d’évaluation, les niveaux de récurrence et la profondeur de suivi des traces sont contrôlés pour empêcher le compilateur de consacrer trop de temps à l’évaluation de **constexpr** . Pour plus d’informations sur l’élément de langage **constexpr** , consultez [constexpr (C++)](../../cpp/constexpr-cpp.md).

Les options **/constexpr** sont disponibles à partir de Visual Studio 2015.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **pages de propriétés** de votre projet.

2. Sous **Propriétés de configuration**, développez le dossier **C/C++** , puis choisissez la page de propriétés **ligne de commande** .

3. Entrez les options du compilateur **/constexpr** dans la zone **options supplémentaires** . Cliquez sur **OK** ou sur **appliquer** pour enregistrer vos modifications.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
