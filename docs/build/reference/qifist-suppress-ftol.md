---
title: /QIfist (Supprimer _ftol)
ms.date: 11/04/2016
f1_keywords:
- /qifist
helpviewer_keywords:
- QIfist compiler option [C++]
- -QIfist compiler option [C++]
- /QIfist compiler option [C++]
ms.assetid: 1afd32a5-f658-4b66-85f4-e0ce4cb955bd
ms.openlocfilehash: 5d6e12a1003ea125b0da4bfef580d8096e97553a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336101"
---
# <a name="qifist-suppress-_ftol"></a>/QIfist (Supprimer _ftol)

Action déconseillée. Supprime l'appel de la fonction d'assistance `_ftol` quand la conversion d'un type à virgule flottante vers un type intégral est requise.

## <a name="syntax"></a>Syntaxe

```
/QIfist
```

## <a name="remarks"></a>Notes

> [!NOTE]
> **/QIfist n’est** disponible que dans le compilateur ciblant x86; cette option de compilateur n’est pas disponible dans les compilateurs ciblant x64 ouARM.

En plus de la conversion d’un type `_ftol` de point flottant à type intégral, la fonction assure le mode d’arrondi de l’unité à point flottant (FPU) est vers zéro (tronqué), en définissant les bits 10 et 11 du mot de commande. Cela garantit que la conversion d’un type de point flottant à un type intégral se produit comme décrit par la norme ANSI C (la partie fractionnaire du nombre est jetée). Lors de l’utilisation **/QIfist**, cette garantie ne s’applique plus. Le mode d’arrondissement sera l’un des quatre tels que documentés dans les manuels de référence Intel:

- Ronde vers le plus proche (même nombre si équidistant)

- Rond vers l’infini négatif

- Tour vers l’infini positif

- Ronde vers zéro

Vous pouvez utiliser la fonction [_control87, \__controlfp, _control87_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md) C Run-Time pour modifier le comportement d’arrondissement du FPU. Le mode d’arrondissement par défaut de la FPU est "Round vers le plus proche." L’utilisation **de /QIfist** peut améliorer les performances de votre application, mais pas sans risque. Vous devez tester en profondeur les parties de votre code qui sont sensibles aux modes d’arrondissement avant de vous fier au code construit avec **/QIfist** dans les environnements de production.

[/arch (x86)](arch-x86.md) et **/QIfist** ne peut pas être utilisé sur le même compiland.

> [!NOTE]
> **/QIfist n’est** pas en vigueur par défaut parce que les bits d’arrondissement affectent également le point flottant à l’arrondissement de points flottants (qui se produit après chaque calcul), ainsi quand vous définissez les drapeaux pour L’arrondi de C-modèle (vers zéro), vos calculs de point flottant pourraient être différents. **/QIfist** ne doit pas être utilisé si votre code dépend du comportement prévu de tronquer la partie fractionnelle du nombre de points flottants. Si vous n’êtes pas sûr, ne pas utiliser **/QIfist**.

**L’option /QIfist** est dépréciée à partir de Visual Studio 2005. Le compilateur a apporté des améliorations significatives dans la vitesse de conversion de flotteur à l’int. Pour une liste d’options de compilateur dépréciés, voir **Les options de compilateur déprécié et supprimé** dans les options [compilateur énumérées par catégorie](compiler-options-listed-by-category.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur la page de propriétés **Ligne de commande** .

1. Tapez l'option de compilateur dans la zone **Options supplémentaires** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[/Q, options (Opérations de bas niveau)](q-options-low-level-operations.md)<br/>
[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
