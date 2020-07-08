---
title: /GH (Activer la fonction de raccordement _pexit)
description: Décrit l’option du compilateur/GH pour définir une fonction de raccordement de _pexit local.
ms.date: 07/06/2020
f1_keywords:
- _pexit
helpviewer_keywords:
- /Gh compiler option [C++]
- Gh compiler option [C++]
- _pexit function
- -Gh compiler option [C++]
ms.assetid: 93181453-2676-42e5-bf63-3b19e07299b6
ms.openlocfilehash: b8fc355503055af8b928874ced39cb8224901d3e
ms.sourcegitcommit: 85d96eeb1ce41d9e1dea947f65ded672e146238b
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86058605"
---
# <a name="gh-enable-_pexit-hook-function"></a>/GH (Activer la fonction de raccordement _pexit)

Appelle la `_pexit` fonction à la fin de chaque méthode ou fonction.

## <a name="syntax"></a>Syntaxe

> **`/GH`**

## <a name="remarks"></a>Notes

La `_pexit` fonction ne fait partie d’aucune bibliothèque. C’est à vous de fournir une définition pour `_pexit` .

À moins que vous n’envisagez d’appeler explicitement `_pexit` , vous n’avez pas besoin de fournir un prototype. La fonction doit transmettre le contenu de tous les registres sur l’entrée et dépiler le contenu non modifié à la sortie. Il doit apparaître comme s’il avait le prototype suivant :

```cpp
void __declspec(naked) __cdecl _pexit( void );
```

Cette déclaration n’est pas disponible pour les projets 64 bits.

`_pexit`est semblable à `_penter` ; consultez [ `/Gh` (activer la fonction de raccordement _penter)](gh-enable-penter-hook-function.md) pour obtenir un exemple d’écriture d’une `_penter` fonction.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Ouvrez la page de propriétés ligne de commande des **Propriétés de configuration**  >  **C/C++**  >  **Command Line** .

1. Entrez l’option de compilateur dans la zone **options supplémentaires** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)<br/>
[`/Gh`(Activer la fonction de raccordement _penter)](gh-enable-penter-hook-function.md)
