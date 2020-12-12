---
description: En savoir plus sur:/homeparams (copier les paramètres du Registre dans la pile)
title: /Homeparams (Copier les paramètres des registres vers la pile)
ms.date: 12/17/2018
f1_keywords:
- /homeparams
helpviewer_keywords:
- /homeparams compiler option [C++]
- -homeparams compiler option [C++]
ms.assetid: 51067de4-24f7-436b-b8d9-bc867a7d53aa
ms.openlocfilehash: 52145534121831be256c3db2a6ccacdffb30b2c2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97191470"
---
# <a name="homeparams-copy-register-parameters-to-stack"></a>/Homeparams (Copier les paramètres des registres vers la pile)

Force les paramètres passés dans les registres à être également écrits dans leurs emplacements sur la pile lors de l’entrée de la fonction.

## <a name="syntax"></a>Syntaxe

> **/homeparams**

## <a name="remarks"></a>Notes

Cette option du compilateur est uniquement disponible dans les compilateurs natifs et croisés qui ciblent x64.

La Convention d’appel x64 requiert que l’espace de la pile soit alloué pour tous les paramètres, même pour les paramètres passés dans les registres. Pour plus d’informations, consultez [passage de paramètres](../../build/x64-calling-convention.md#parameter-passing). Par défaut, les paramètres de registre ne sont pas copiés dans l’espace de pile qui leur est alloué dans les versions release. Cela complique le débogage d’une version de mise en sortie optimisée de votre programme.

Pour les versions release, vous pouvez utiliser l’option **/homeparams** pour forcer le compilateur à copier les paramètres du Registre dans la pile, afin de vous assurer que vous pouvez déboguer votre application. **/homeparams** implique un inconvénient en matière de performances, car il nécessite un cycle supplémentaire pour charger les paramètres de Registre sur la pile.

Dans les versions Debug, la pile est toujours remplie avec les paramètres passés dans les registres.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Ouvrez la page de propriétés ligne de commande des **Propriétés de configuration**  >  **C/C++**  >   .

1. Entrez l’option de compilateur dans la zone **options supplémentaires** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)
