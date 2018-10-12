---
title: -GH (activer la fonction de raccordement _pexit) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _pexit
dev_langs:
- C++
helpviewer_keywords:
- /Gh compiler option [C++]
- Gh compiler option [C++]
- _pexit function
- -Gh compiler option [C++]
ms.assetid: 93181453-2676-42e5-bf63-3b19e07299b6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e9b8ee4c80310c4d94ed432d48ee9702c41f80bf
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49161786"
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

`_pexit` est similaire à `_penter`; consultez [/Gh (activer _penter la fonction de raccordement)](../../build/reference/gh-enable-penter-hook-function.md) pour obtenir un exemple montrant comment écrire un `_pexit` (fonction).

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