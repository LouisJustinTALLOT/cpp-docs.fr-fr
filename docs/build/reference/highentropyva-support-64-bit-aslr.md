---
title: /HIGHENTROPYVA (Prendre en charge l'ASLR 64 bits)
ms.date: 06/12/2018
ms.assetid: fe35f9f7-d28e-4694-9aeb-a79db06168e0
ms.openlocfilehash: 8f8601d89e8456461aac3d91f9fd2cfda216d7f5
ms.sourcegitcommit: 31a443c9998cf5cfbaff00fcf815b133f55b2426
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86373838"
---
# <a name="highentropyva-support-64-bit-aslr"></a>/HIGHENTROPYVA (Prendre en charge l'ASLR 64 bits)

Spécifie si l'image exécutable prend en charge la randomisation du format d'espace d'adresse (ASLR) 64 bits de forte entropie.

## <a name="syntax"></a>Syntaxe

> **/HIGHENTROPYVA**[**: no**]

## <a name="remarks"></a>Notes

**/HIGHENTROPYVA** modifie l’en-tête d’une *image exécutable*, un fichier. dll ou. exe pour indiquer si ASLR peut utiliser la totalité de l’espace d’adressage 64 bits. Quand cette option est définie au niveau d’un fichier exécutable et de tous les modules dont il dépend, un système d’exploitation qui prend en charge l’ASLR 64 bits peut redéfinir les segments de l’image exécutable au moment du chargement en utilisant des adresses aléatoires tirées d’un espace d’adressage virtuel de 64 bits. Devant ce grand espace d'adressage, il est plus difficile pour une personne malveillante de deviner l'emplacement d'une région de mémoire particulière.

Par défaut, **/HIGHENTROPYVA** est activé pour les images exécutables 64 bits. Cette option requiert [/LARGEADDRESSAWARE](largeaddressaware-handle-large-addresses.md), qui est également activée par défaut pour les images 64 bits. **/HIGHENTROPYVA** n’est pas applicable aux images exécutables 32 bits, où l’éditeur de liens ignore l’option. Pour désactiver explicitement cette option, utilisez **/HIGHENTROPYVA : no**.

Pour que **/HIGHENTROPYVA** ait un effet au moment du chargement, [/DynamicBase](dynamicbase-use-address-space-layout-randomization.md) doit également être activé. **/DynamicBase** est activé par défaut et est requis pour activer ASLR dans Windows Vista et les systèmes d’exploitation ultérieurs. Les versions antérieures de Windows ignorent cet indicateur.

### <a name="to-set-this-linker-option-in-visual-studio"></a>Pour définir cette option d'éditeur de liens dans Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriétés** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés ligne de commande de l’éditeur de liens **Propriétés de configuration**  >  **Linker**  >  **Command Line** .

1. Dans **options supplémentaires**, entrez `/HIGHENTROPYVA` ou `/HIGHENTROPYVA:NO` .

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur l’éditeur de liens MSVC](linking.md)
- [Options de l’éditeur de liens MSVC](linker-options.md)
- [/DYNAMICBASE](dynamicbase-use-address-space-layout-randomization.md)
- [/LARGEADDRESSAWARE](largeaddressaware-handle-large-addresses.md)
- [Défenses de la sécurité logicielle ISV Windows](https://docs.microsoft.com/previous-versions/bb430720(v=msdn.10))
