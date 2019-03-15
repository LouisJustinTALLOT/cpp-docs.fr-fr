---
title: /Homeparams (Copier les paramètres des registres vers la pile)
ms.date: 12/17/2018
f1_keywords:
- /homeparams
helpviewer_keywords:
- /homeparams compiler option [C++]
- -homeparams compiler option [C++]
ms.assetid: 51067de4-24f7-436b-b8d9-bc867a7d53aa
ms.openlocfilehash: a1f9269c7deae6c9ae2e4f198006ad09dd37abc3
ms.sourcegitcommit: faa42c8a051e746d99dcebe70fd4bbaf3b023ace
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2019
ms.locfileid: "57820661"
---
# <a name="homeparams-copy-register-parameters-to-stack"></a>/Homeparams (Copier les paramètres des registres vers la pile)

Paramètres de force passés dans les registres également d’être écrites dans leurs emplacements sur la pile lors de l’entrée de fonction.

## <a name="syntax"></a>Syntaxe

> **/homeparams**

## <a name="remarks"></a>Notes

Cette option du compilateur est uniquement disponible dans les compilateurs croisés qui ciblent x64 natif.

La convention d’appel de x64 nécessite de l’espace de pile doit être allouée pour tous les paramètres, même pour les paramètres passés dans les registres. Pour plus d’informations, consultez [passage de paramètres](../../build/x64-calling-convention.md#parameter-passing). Par défaut, les paramètres de Registre ne sont pas copiés dans l’espace de pile alloué pour eux dans les versions release. Cela rend difficile à déboguer une version Release optimisée de votre programme.

Pour les versions release, vous pouvez utiliser la **/homeparams** option pour forcer le compilateur pour copier les paramètres à la pile, pour vous assurer que vous pouvez déboguer votre application de Registre. **/Homeparams** implique un inconvénient de performances, car elle requiert un cycle supplémentaire pour charger les paramètres de Registre dans la pile.

Dans les versions debug, la pile est toujours remplie avec les paramètres passés dans les registres.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Ouvrez le **propriétés de Configuration** > **C/C++** > **ligne de commande** page de propriétés.

1. Entrez l’option du compilateur dans le **des Options supplémentaires** boîte.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
