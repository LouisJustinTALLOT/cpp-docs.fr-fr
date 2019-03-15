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
ms.openlocfilehash: 077096cc296f2aa2128127493a84a91da9a067c5
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57822169"
---
# <a name="gh-enable-pexit-hook-function"></a>/GH (Activer la fonction de raccordement _pexit)

Appelle le `_pexit` fonction à la fin de chaque méthode ou fonction.

## <a name="syntax"></a>Syntaxe

```
/GH
```

## <a name="remarks"></a>Notes

Le `_pexit` fonction ne fait pas partie d’une bibliothèque quelconque, et il vous incombe de fournir une définition pour `_pexit`.

Sauf si vous envisagez d’appeler explicitement `_pexit`, vous n’avez pas besoin de fournir un prototype. La fonction doit apparaître comme si elle avait le prototype suivant, et il doit transférer le contenu de tous les registres sur entrée et affiche le contenu non modifié à la sortie :

```
void __declspec(naked) __cdecl _pexit( void );
```

`_pexit` est similaire à `_penter`; consultez [/Gh (activer _penter la fonction de raccordement)](gh-enable-penter-hook-function.md) pour obtenir un exemple montrant comment écrire un `_pexit` (fonction).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur la page de propriétés **Ligne de commande** .

1. Tapez l'option de compilateur dans la zone **Options supplémentaires** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
