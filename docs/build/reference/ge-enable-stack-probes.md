---
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
ms.openlocfilehash: 34799529517e0263f71ce4f6f29537bf4b59056f
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57415420"
---
# <a name="ge-enable-stack-probes"></a>/Ge (Activer les tests de pile)

Active les tests de pile pour chaque appel de fonction qui requiert un stockage pour les variables locales.

## <a name="syntax"></a>Syntaxe

```
/Ge
```

## <a name="remarks"></a>Notes

Ce mécanisme est utile si vous réécrivez la fonctionnalité de la sonde de pile. Il est recommandé d’utiliser [/Gh (activer _penter la fonction de raccordement)](../../build/reference/gh-enable-penter-hook-function.md) au lieu de la réécriture de la sonde de pile.

[/GS (contrôle pile des appels vérification)](../../build/reference/gs-control-stack-checking-calls.md) a le même effet.

**/GE** est déconseillé ; à compter de Visual Studio 2005, le compilateur génère automatiquement le contrôle de pile. Pour obtenir la liste des options du compilateur déconseillées, consultez **Options déconseillées et supprimées du compilateur** dans [Options du compilateur classées par catégorie](../../build/reference/compiler-options-listed-by-category.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur la page de propriétés **Ligne de commande** .

1. Tapez l'option de compilateur dans la zone **Options supplémentaires** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur](../../build/reference/compiler-options.md)<br/>
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)
