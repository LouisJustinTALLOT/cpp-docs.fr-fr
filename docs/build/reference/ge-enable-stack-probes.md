---
description: En savoir plus sur:/GE (activer les tests de pile)
title: /Ge (Activer les tests de pile)
ms.date: 11/04/2016
f1_keywords:
- /ge
helpviewer_keywords:
- -Ge compiler option [C++]
- enable stack probes
- /Ge compiler option [C++]
- stack, stack probes
- stack probes
- stack checking calls
- Ge compiler option [C++]
ms.assetid: 4b54deae-4e3c-4bfa-95f3-ba23590f7258
ms.openlocfilehash: db996deb1c5b964661e5465fe72cfb0fab93df56
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97192016"
---
# <a name="ge-enable-stack-probes"></a>/Ge (Activer les tests de pile)

Active les tests de pile pour chaque appel de fonction qui requiert le stockage pour les variables locales.

## <a name="syntax"></a>Syntaxe

```
/Ge
```

## <a name="remarks"></a>Notes

Ce mécanisme est utile si vous réécrivez les fonctionnalités de la sonde de pile. Il est recommandé d’utiliser [/GH (activer la fonction de raccordement _penter)](gh-enable-penter-hook-function.md) au lieu de réécrire la sonde de pile.

[/GS (contrôler les appels de contrôle de pile)](gs-control-stack-checking-calls.md) a le même effet.

**/GE** est déconseillé ; à compter de Visual Studio 2005, le compilateur génère automatiquement le contrôle de pile. Pour obtenir la liste des options du compilateur déconseillées, consultez **Options du compilateur déconseillées et supprimées** dans [Options du compilateur classées par catégorie](compiler-options-listed-by-category.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur la page de propriétés **Ligne de commande** .

1. Tapez l'option de compilateur dans la zone **Options supplémentaires** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)
