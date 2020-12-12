---
description: En savoir plus sur:/HEAP (définir la taille du tas)
title: /HEAP (Définir la taille des tas)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.HeapCommitSize
- VC.Project.VCLinkerTool.HeapReserveSize
helpviewer_keywords:
- -HEAP linker option
- heap allocation, setting heap size
- /HEAP linker option
- HEAP linker option
ms.assetid: a3f71927-7f1d-492c-9fdb-dfccb1a043da
ms.openlocfilehash: 9831180925d5d669c799982d021d75ea31a2dae5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97191665"
---
# <a name="heap-set-heap-size"></a>/HEAP (Définir la taille des tas)

```
/HEAP:reserve[,commit]
```

## <a name="remarks"></a>Notes

L’option/HEAP définit la taille du segment de mémoire en octets. Cette option est réservée à une utilisation lors de la génération d’un fichier. exe.

L’argument *Reserve* spécifie l’allocation totale du tas dans la mémoire virtuelle. La taille du tas par défaut est de 1 Mo. L’éditeur de liens arrondit la valeur spécifiée aux 4 octets les plus proches.

L' `commit` argument facultatif spécifie la quantité de mémoire physique à allouer à la fois. La mémoire virtuelle validée entraîne la réservation de l’espace dans le fichier d’échange. Une valeur plus élevée permet de `commit` gagner du temps lorsque l’application a besoin de davantage d’espace de tas, mais augmente les besoins en mémoire et éventuellement le temps de démarrage.

Spécifiez la *réserve* et les `commit` valeurs en notation décimale ou de langage C.

Cette fonctionnalité est également disponible via un fichier de définition de module avec [HEAPSIZE](heapsize.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **Éditeur de liens**.

1. Cliquez sur la page de propriétés **système** .

1. Modifiez la propriété taille de la **validation du tas** .

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Localisez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.HeapReserveSize%2A> et <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.HeapCommitSize%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
