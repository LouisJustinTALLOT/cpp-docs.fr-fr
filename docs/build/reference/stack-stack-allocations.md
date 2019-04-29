---
title: /STACK, allocations de la pile
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.StackReserveSize
- VC.Project.VCLinkerTool.StackCommitSize
- /stack
helpviewer_keywords:
- STACK linker option
- -STACK linker option
- memory allocation, stack
- /STACK linker option
- stack, setting size
ms.assetid: 73283660-e4bd-47cc-b5ca-04c5d739034c
ms.openlocfilehash: 27de554e1933b2753f641be358461c8d7ff4fffa
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62317924"
---
# <a name="stack-stack-allocations"></a>/STACK, allocations de la pile

```
/STACK:reserve[,commit]
```

## <a name="remarks"></a>Notes

L’option /STACK définit la taille de la pile en octets. Utilisez cette option uniquement lorsque vous générez un fichier .exe.

Le `reserve` valeur spécifie l’allocation de pile total dans la mémoire virtuelle. Pour ARM, x86 et x64 machines, la taille de pile par défaut est de 1 Mo.

`commit` est soumis à l’interprétation par le système d’exploitation. Dans Windows RT de Windows, il spécifie la quantité de mémoire physique à allouer à la fois. Mémoire virtuelle dédiée, espace à réserver dans le fichier d’échange. Un degré plus élevé `commit` valeur fait gagner du temps quand l’application requiert davantage d’espace pile, mais augmente les besoins en mémoire et peut allonger le temps de démarrage. Pour ARM, x86 et x64 machines, la valeur de validation par défaut est de 4 Ko.

Spécifiez le `reserve` et `commit` valeurs dans la notation décimale ou en langage C.

Une autre consiste à définir la taille de la pile avec le [STACKSIZE](stacksize.md) instruction dans un fichier de définition de module (.def). **STACKSIZE** remplace les Allocations de la pile (/Stack) option si les deux sont spécifiés. Vous pouvez modifier la taille de la pile une fois que le fichier .exe est généré à l’aide de la [EDITBIN](editbin-reference.md) outil.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez le **l’éditeur de liens** dossier.

1. Sélectionnez le **système** page de propriétés.

1. Modifier l’une des propriétés suivantes :

   - **Taille de validation de pile**

   - **Taille de réserve de pile**

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

1. Consultez les propriétés <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.StackCommitSize%2A> et <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.StackReserveSize%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
