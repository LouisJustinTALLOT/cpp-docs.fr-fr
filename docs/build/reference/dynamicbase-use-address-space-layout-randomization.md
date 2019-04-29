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
ms.openlocfilehash: a3495de3ec72bcac78cdee2f5f3265864e7a2932
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62293067"
---
# <a name="dynamicbase-use-address-space-layout-randomization"></a>/DYNAMICBASE (Utiliser la randomisation du format d'espace d'adresse)

Spécifie s’il faut générer une image exécutable pouvant être aléatoirement redéfinie au moment du chargement à l’aide de la fonctionnalité espace d’adresse disposition randomization (ASLR) de Windows qui était auparavant disponible dans Windows Vista.

## <a name="syntax"></a>Syntaxe

> **/DYNAMICBASE**[**:NO**]

## <a name="remarks"></a>Notes

Le **/DYNAMICBASE** option modifie l’en-tête d’un *image exécutable*, un fichier .dll ou .exe pour indiquer si l’application doit être aléatoirement redéfinie au moment du chargement et permet d’adresse virtuelle randomisation d’allocation, ce qui affecte l’emplacement de mémoire virtuelle de segments de mémoire, les piles et autres allocations de système d’exploitation. Le **/DYNAMICBASE** option s’applique aux images 32 bits et 64 bits. ASLR est prise en charge sur Windows Vista et les systèmes d’exploitation ultérieurs. L’option est ignorée par les systèmes d’exploitation antérieurs.

Par défaut, **/DYNAMICBASE** est activé. Pour désactiver cette option, utilisez **/DYNAMICBASE : no**. Le **/DYNAMICBASE** option est requise pour le [/HIGHENTROPYVA](highentropyva-support-64-bit-aslr.md) option ait un effet.

### <a name="to-set-this-linker-option-in-visual-studio"></a>Pour définir cette option d'éditeur de liens dans Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriétés** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration** > **l’éditeur de liens** > **avancé** page de propriétés.

1. Modifier le **adresse de Base aléatoire** propriété.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.RandomizedBaseAddress%2A>.

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur l’éditeur de liens MSVC](linking.md)
- [Options de l’éditeur de liens MSVC](linker-options.md)
- [/HIGHENTROPYVA](highentropyva-support-64-bit-aslr.md)
- [Défenses de sécurité d’éditeurs de logiciels Windows](https://msdn.microsoft.com/library/bb430720.aspx)