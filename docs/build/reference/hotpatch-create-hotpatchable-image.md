---
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
ms.openlocfilehash: 8830b26b8fdfc3db2aa5fe31a52e6226fd554946
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62291650"
---
# <a name="hotpatch-create-hotpatchable-image"></a>/hotpatch (Créer une image corrigeable en mémoire)

Prépare une image corrigeable en mémoire.

## <a name="syntax"></a>Syntaxe

```
/hotpatch
```

## <a name="remarks"></a>Notes

Lorsque **/hotpatch** est utilisé dans une compilation, le compilateur garantit que la première instruction de chaque fonction est d’au moins deux octets, ce qui est requis pour la création d’images corrigeables.

Pour terminer la préparation de création d’une image corrigeable en mémoire, une fois que vous utilisez **/hotpatch** pour compiler, vous devez utiliser [/FUNCTIONPADMIN (créer une Image corrigeable en mémoire)](functionpadmin-create-hotpatchable-image.md) à lier. Lorsque vous compilez et liez une image à l’aide d’un appel de cl.exe, **/hotpatch** implique **/functionpadmin**.

Étant donné que les instructions sont toujours deux octets ou plus sur l’architecture ARM et parce que x64 compilation est toujours traitée comme si **/hotpatch** a été spécifié, vous n’êtes pas obligé de spécifier **/hotpatch** lorsque vous compilez pour ces cibles ; Toutefois, vous devez toujours lier à l’aide de **/functionpadmin** pour créer des images corrigeables en mémoire pour eux. Le **/hotpatch** du compilateur option seule affecte x86 compilation.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez le **C/C++** dossier.

1. Sélectionnez le **ligne de commande** page de propriétés.

1. Ajoutez l’option du compilateur pour le **des Options supplémentaires** boîte.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
