---
description: En savoir plus sur:/QIfist (Supprimer _ftol)
title: /QIfist (Supprimer _ftol)
ms.date: 11/04/2016
f1_keywords:
- /qifist
helpviewer_keywords:
- QIfist compiler option [C++]
- -QIfist compiler option [C++]
- /QIfist compiler option [C++]
ms.assetid: 1afd32a5-f658-4b66-85f4-e0ce4cb955bd
ms.openlocfilehash: 79e9242d66b532f558307d05b222b2fd8cfd43ab
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97225646"
---
# <a name="qifist-suppress-_ftol"></a>/QIfist (Supprimer _ftol)

Action déconseillée. Supprime l'appel de la fonction d'assistance `_ftol` quand la conversion d'un type à virgule flottante vers un type intégral est requise.

## <a name="syntax"></a>Syntaxe

```
/QIfist
```

## <a name="remarks"></a>Notes

> [!NOTE]
> **/QIfist** est uniquement disponible dans le compilateur ciblant x86 ; Cette option du compilateur n’est pas disponible dans les compilateurs ciblant x64 orARM.

En plus de la conversion d’un type à virgule flottante en type intégral, la `_ftol` fonction garantit que le mode d’arrondi de l’unité à virgule flottante (FPU) est vers zéro (tronquer), en définissant les bits 10 et 11 du mot de contrôle. Cela garantit que la conversion d’un type à virgule flottante en type intégral se produit comme décrit par la norme C ANSI (la partie fractionnaire du nombre est ignorée). Lorsque vous utilisez **/QIfist**, cette garantie ne s’applique plus. Le mode d’arrondi sera l’un des quatre éléments décrits dans les guides de référence Intel :

- Arrondi vers le plus proche (nombre pair si équidistants)

- Arrondi vers l’infini négatif

- Arrondi vers l’infini positif

- Arrondi vers zéro

Vous pouvez utiliser la fonction [_control87, _controlfp \_ _control87_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md) C Run-Time pour modifier le comportement d’arrondi du FPU. Le mode d’arrondi par défaut du FPU est « arrondi vers le plus proche ». L’utilisation de **/QIfist** peut améliorer les performances de votre application, mais pas sans risque. Vous devez tester minutieusement les parties de votre code qui sont sensibles aux modes d’arrondi avant de vous appuyer sur le code généré avec **/QIfist** dans les environnements de production.

[/Arch (x86)](arch-x86.md) et **/QIfist** ne peuvent pas être utilisés sur le même compiland.

> [!NOTE]
> **/QIfist** n’est pas activé par défaut, car les bits d’arrondi affectent également la virgule flottante à l’arrondi à virgule flottante (qui se produit après chaque calcul). par conséquent, lorsque vous définissez les indicateurs pour l’arrondi de style C (vers zéro), vos calculs à virgule flottante peuvent être différents. **/QIfist** ne doit pas être utilisé si votre code dépend du comportement attendu de la troncation de la partie fractionnaire du nombre à virgule flottante. Si vous n’êtes pas sûr, n’utilisez pas **/QIfist**.

L’option **/QIfist** est déconseillée à partir de Visual Studio 2005. Le compilateur a apporté des améliorations significatives en matière de vitesse de conversion des valeurs float en int. Pour obtenir la liste des options du compilateur déconseillées, consultez **Options du compilateur déconseillées et supprimées** dans [Options du compilateur classées par catégorie](compiler-options-listed-by-category.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur la page de propriétés **Ligne de commande** .

1. Tapez l'option de compilateur dans la zone **Options supplémentaires** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[/Q options (opérations de bas niveau)](q-options-low-level-operations.md)<br/>
[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)
