---
title: /HEAP (Définir la taille des tas)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.HeapCommitSize
- /heap
- VC.Project.VCLinkerTool.HeapReserveSize
helpviewer_keywords:
- -HEAP linker option
- heap allocation, setting heap size
- /HEAP linker option
- HEAP linker option
ms.assetid: a3f71927-7f1d-492c-9fdb-dfccb1a043da
ms.openlocfilehash: 715eaa358d052d4ae646f38f2e784f0235dffccb
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57813291"
---
# <a name="heap-set-heap-size"></a>/HEAP (Définir la taille des tas)

```
/HEAP:reserve[,commit]
```

## <a name="remarks"></a>Notes

L’option /HEAP définit la taille du segment de mémoire en octets. Cette option est uniquement pour une utilisation lors de la création d’un fichier .exe.

Le *réserver* argument spécifie l’allocation totale des tas dans la mémoire virtuelle. La taille de segment de mémoire par défaut est 1 Mo. L’éditeur de liens arrondit la valeur spécifiée aux 4 octets plus proches.

Le paramètre facultatif `commit` argument spécifie la quantité de mémoire physique à allouer à la fois. Mémoire virtuelle dédiée, espace à réserver dans le fichier d’échange. Un degré plus élevé `commit` valeur fait gagner du temps quand l’application requiert davantage d’espace du tas, mais augmente les besoins en mémoire et peut allonger le temps de démarrage.

Spécifiez le *réserver* et `commit` valeurs dans la notation décimale ou en langage C.

Cette fonctionnalité est également disponible via un fichier de définition de module avec [HEAPSIZE](heapsize.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le **l’éditeur de liens** dossier.

1. Cliquez sur le **système** page de propriétés.

1. Modifier le **taille de la validation du tas** propriété.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.HeapReserveSize%2A> et <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.HeapCommitSize%2A>.

## <a name="see-also"></a>Voir aussi

[Référence de l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
