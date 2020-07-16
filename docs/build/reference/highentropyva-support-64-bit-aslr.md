---
title: /HIGHENTROPYVA (Prendre en charge l'ASLR 64 bits)
ms.date: 06/12/2018
ms.assetid: fe35f9f7-d28e-4694-9aeb-a79db06168e0
ms.openlocfilehash: 929d6aa71010c1f303bf7a1ce64109a01b8792e4
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2020
ms.locfileid: "86404123"
---
# <a name="highentropyva-support-64-bit-aslr"></a>/HIGHENTROPYVA (Prendre en charge l'ASLR 64 bits)

Spécifie si l'image exécutable prend en charge la randomisation du format d'espace d'adresse (ASLR) 64 bits de forte entropie.

## <a name="syntax"></a>Syntaxe

> **`/HIGHENTROPYVA`**[**`:NO`**]

## <a name="remarks"></a>Notes

**`/HIGHENTROPYVA`** modifie l’en-tête d’un fichier *image exécutable* (par exemple, un *`.dll`* *`.exe`* fichier ou), pour indiquer si ASLR peut utiliser la totalité de l’espace d’adressage 64 bits.  Pour avoir un effet, définissez l’option sur le fichier exécutable et tous les modules dont il dépend. Un système d’exploitation qui prend en charge l’ASLR 64 bits peut rebaser les segments de l’image exécutable au moment du chargement en utilisant des adresses virtuelles aléatoires de 64 bits. Devant ce grand espace d'adressage, il est plus difficile pour une personne malveillante de deviner l'emplacement d'une région de mémoire particulière.

Par défaut, **`/HIGHENTROPYVA`** est activé pour les images exécutables 64 bits. Cette option nécessite [`/LARGEADDRESSAWARE`](largeaddressaware-handle-large-addresses.md) , qui est également activée par défaut pour les images 64 bits. **`/HIGHENTROPYVA`** n’est pas applicable aux images exécutables 32 bits, où l’éditeur de liens ignore l’option. Pour désactiver explicitement cette option, utilisez **`/HIGHENTROPYVA:NO`** .

Pour **`/HIGHENTROPYVA`** que ait un effet au moment du chargement, [`/DYNAMICBASE`](dynamicbase-use-address-space-layout-randomization.md) doit également être activé. **`/DYNAMICBASE`** est activé par défaut et est requis pour activer ASLR dans Windows Vista et les systèmes d’exploitation ultérieurs. Les versions antérieures de Windows ignorent cet indicateur.

### <a name="to-set-this-linker-option-in-visual-studio"></a>Pour définir cette option d'éditeur de liens dans Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriétés** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés ligne de commande de l’éditeur de liens **Propriétés de configuration**  >  **Linker**  >  **Command Line** .

1. Dans **options supplémentaires**, entrez `/HIGHENTROPYVA` ou `/HIGHENTROPYVA:NO` .

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur l’éditeur de liens MSVC](linking.md)
- [Options de l’éditeur de liens MSVC](linker-options.md)
- [`/DYNAMICBASE`](dynamicbase-use-address-space-layout-randomization.md)
- [`/LARGEADDRESSAWARE`](largeaddressaware-handle-large-addresses.md)
- [Défenses de la sécurité logicielle ISV Windows](https://docs.microsoft.com/previous-versions/bb430720(v=msdn.10))
