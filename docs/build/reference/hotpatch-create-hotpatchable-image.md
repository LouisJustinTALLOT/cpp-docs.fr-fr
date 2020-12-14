---
description: En savoir plus sur:/hotpatch (créer une image corrigeable en mémoire)
title: /hotpatch (Créer une image corrigeable en mémoire)
ms.date: 11/12/2018
f1_keywords:
- /hotpatch
- VC.Project.VCCLCompilerTool.CreateHotpatchableImage
helpviewer_keywords:
- hot patching
- -hotpatch compiler option [C++]
- /hotpatch compiler option [C++]
- hotpatching
ms.assetid: aad539b6-c053-4c78-8682-853d98327798
ms.openlocfilehash: 2fc5fe629afcb1e721943b852c6f92351900ab7e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97199868"
---
# <a name="hotpatch-create-hotpatchable-image"></a>/hotpatch (Créer une image corrigeable en mémoire)

Prépare une image corrigeable en mémoire.

## <a name="syntax"></a>Syntaxe

```
/hotpatch
```

## <a name="remarks"></a>Notes

Lorsque **/hotpatch** est utilisé dans une compilation, le compilateur s’assure que la première instruction de chaque fonction est au moins égale à deux octets, ce qui est nécessaire pour la mise à jour corrective.

Pour terminer la préparation de la création d’une image corrigeable en mémoire, après avoir utilisé **/hotpatch** pour la compilation, vous devez utiliser [/FUNCTIONPADMIN (créer une image corrigeable en mémoire)](functionpadmin-create-hotpatchable-image.md) à lier. Quand vous compilez et liez une image à l’aide d’un appel de cl.exe, **/hotpatch** implique **/FUNCTIONPADMIN**.

Étant donné que les instructions sont toujours de deux octets ou plus sur l’architecture ARM, et que la compilation x64 est toujours traitée comme si **/hotpatch** a été spécifié, vous n’avez pas besoin de spécifier **/hotpatch** lors de la compilation pour ces cibles. Toutefois, vous devez toujours établir une liaison à l’aide de **/FUNCTIONPADMIN** pour créer des images corrigeables en mémoire. L’option du compilateur **/hotpatch** affecte uniquement la compilation x86.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez le dossier **C/C++** .

1. Sélectionnez la page de propriétés **ligne de commande** .

1. Ajoutez l’option de compilateur à la zone **options supplémentaires** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)
