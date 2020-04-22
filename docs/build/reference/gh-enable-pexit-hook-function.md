---
title: /GH (Activer la fonction de raccordement _pexit)
ms.date: 11/04/2016
f1_keywords:
- _pexit
helpviewer_keywords:
- /Gh compiler option [C++]
- Gh compiler option [C++]
- _pexit function
- -Gh compiler option [C++]
ms.assetid: 93181453-2676-42e5-bf63-3b19e07299b6
ms.openlocfilehash: 5382ba90f490aaa12e9e55767fdf15170a69ced5
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749230"
---
# <a name="gh-enable-_pexit-hook-function"></a>/GH (Activer la fonction de raccordement _pexit)

Appelle `_pexit` la fonction à la fin de chaque méthode ou fonction.

## <a name="syntax"></a>Syntaxe

```
/GH
```

## <a name="remarks"></a>Notes

La `_pexit` fonction ne fait partie d’aucune bibliothèque et c’est à vous de fournir une définition pour `_pexit`.

Sauf si vous `_pexit`avez l’intention d’appeler explicitement , vous n’avez pas besoin de fournir un prototype. La fonction doit apparaître comme si elle avait le prototype suivant, et il doit pousser le contenu de tous les registres à l’entrée et pop le contenu inchangé à la sortie:

```cpp
void __declspec(naked) __cdecl _pexit( void );
```

`_pexit`est similaire `_penter`à ; voir [/Gh (Enable _penter Hook Function)](gh-enable-penter-hook-function.md) par exemple de `_pexit` la façon d’écrire une fonction.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur la page de propriétés **Ligne de commande** .

1. Tapez l'option de compilateur dans la zone **Options supplémentaires** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
