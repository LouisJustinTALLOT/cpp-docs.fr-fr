---
title: /DYNAMICBASE (Utiliser la randomisation du format d'espace d'adresse)
ms.date: 06/12/2018
f1_keywords:
- VC.Project.VCLinkerTool.RandomizedBaseAddress
helpviewer_keywords:
- -DYNAMICBASE linker option
- /DYNAMICBASE linker option
- DYNAMICBASE linker option
ms.assetid: 6c0ced8e-fe9c-4b63-b956-eb8a55fbceb2
ms.openlocfilehash: 66d6232ed43f9c842ebbb0e22b57c509cf610afa
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170057"
---
# <a name="dynamicbase-use-address-space-layout-randomization"></a>/DYNAMICBASE (Utiliser la randomisation du format d'espace d'adresse)

Spécifie s’il faut générer une image exécutable qui peut être redéfinie de façon aléatoire au moment du chargement à l’aide de la fonctionnalité de randomisation du format d’espace d’adresse (ASLR) de Windows qui était d’abord disponible dans Windows Vista.

## <a name="syntax"></a>Syntaxe

> **/DynamicBase**[ **: no**]

## <a name="remarks"></a>Notes

L’option **/DynamicBase** modifie l’en-tête d’une *image exécutable*, un fichier. dll ou. exe pour indiquer si l’application doit être redéfinie de façon aléatoire au moment du chargement, et active la randomisation de l’allocation d’adresses virtuelles, ce qui affecte l’emplacement de la mémoire virtuelle des tas, des piles et d’autres allocations du système d’exploitation. L’option **/DynamicBase** s’applique aux images 32 bits et 64 bits. ASLR est pris en charge sur Windows Vista et les systèmes d’exploitation ultérieurs. L’option est ignorée par les systèmes d’exploitation antérieurs.

Par défaut, **/DynamicBase** est activé. Pour désactiver cette option, utilisez **/DynamicBase : no**. L’option **/DynamicBase** est nécessaire pour que l’option [/HIGHENTROPYVA](highentropyva-support-64-bit-aslr.md) ait un effet.

### <a name="to-set-this-linker-option-in-visual-studio"></a>Pour définir cette option d'éditeur de liens dans Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriétés** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez **Propriétés de Configuration** > **éditeur de liens** > page de propriétés **avancé** .

1. Modifiez la propriété **adresse de base aléatoire** .

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.RandomizedBaseAddress%2A>.

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur l’éditeur de liens MSVC](linking.md)
- [Options de l’éditeur de liens MSVC](linker-options.md)
- [/HIGHENTROPYVA](highentropyva-support-64-bit-aslr.md)
- [Défenses de la sécurité logicielle ISV Windows](https://msdn.microsoft.com/library/bb430720.aspx)
