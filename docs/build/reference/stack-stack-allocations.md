---
description: En savoir plus sur:/STACK (allocations de la pile)
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
ms.openlocfilehash: 6e74b508d8cdb2340c73360bf35272d9113a0f75
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97224464"
---
# <a name="stack-stack-allocations"></a>/STACK, allocations de la pile

```
/STACK:reserve[,commit]
```

## <a name="remarks"></a>Notes

L’option/STACK définit la taille de la pile en octets. Utilisez cette option uniquement lorsque vous générez un fichier. exe.

La `reserve` valeur spécifie le nombre total d’allocations de piles dans la mémoire virtuelle. Pour les machines ARM, x86 et x64, la taille de la pile par défaut est de 1 Mo.

`commit` fait l’objet d’une interprétation par le système d’exploitation. Dans Windows Windows RT, il spécifie la quantité de mémoire physique à allouer à la fois. La mémoire virtuelle validée entraîne la réservation de l’espace dans le fichier d’échange. Une valeur plus élevée permet de `commit` gagner du temps lorsque l’application a besoin de davantage d’espace de pile, mais augmente les besoins en mémoire et éventuellement le temps de démarrage. Pour les machines ARM, x86 et x64, la valeur de validation par défaut est de 4 Ko.

Spécifiez `reserve` les `commit` valeurs et en notation décimale ou de langage C.

Une autre façon de définir la taille de la pile consiste à utiliser l’instruction [STACKSIZE](stacksize.md) dans un fichier de définition de module (. def). **STACKSIZE** remplace l’option allocations de la pile (/Stack) si les deux sont spécifiées. Vous pouvez modifier la taille de la pile après la génération du fichier. exe à l’aide de l’outil [EDITBIN](editbin-reference.md) .

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez le dossier de l' **éditeur de liens** .

1. Sélectionnez la page de propriétés **système** .

1. Modifiez l’une des propriétés suivantes :

   - **Taille de la validation de pile**

   - **Taille de réserve de pile**

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

1. Consultez les propriétés <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.StackCommitSize%2A> et <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.StackReserveSize%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
