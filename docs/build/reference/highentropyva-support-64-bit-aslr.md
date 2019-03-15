---
title: /HIGHENTROPYVA (Prendre en charge l'ASLR 64 bits)
ms.date: 06/12/2018
ms.assetid: fe35f9f7-d28e-4694-9aeb-a79db06168e0
ms.openlocfilehash: 5ecbbf8bbd8e74f80f2f5b2d7df0d2ef544112fc
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57822000"
---
# <a name="highentropyva-support-64-bit-aslr"></a>/HIGHENTROPYVA (Prendre en charge l'ASLR 64 bits)

Spécifie si l'image exécutable prend en charge la randomisation du format d'espace d'adresse (ASLR) 64 bits de forte entropie.

## <a name="syntax"></a>Syntaxe

> **/HIGHENTROPYVA**[**:NO**]

## <a name="remarks"></a>Notes

**/ HIGHENTROPYVA** modifie l’en-tête d’un *image exécutable*, un fichier .dll ou .exe, pour indiquer si ASLR peut utiliser l’espace d’adresse entière de 64 bits. Quand cette option est définie au niveau d’un fichier exécutable et de tous les modules dont il dépend, un système d’exploitation qui prend en charge l’ASLR 64 bits peut redéfinir les segments de l’image exécutable au moment du chargement en utilisant des adresses aléatoires tirées d’un espace d’adressage virtuel de 64 bits. Devant ce grand espace d'adressage, il est plus difficile pour une personne malveillante de deviner l'emplacement d'une région de mémoire particulière.

Par défaut, **/HIGHENTROPYVA** est activé pour les images exécutables 64 bits. Cette option nécessite [/LARGEADDRESSAWARE](largeaddressaware-handle-large-addresses.md), qui est également activé par défaut pour les images de 64 bits. **/ HIGHENTROPYVA** n’est pas applicable aux images exécutables 32 bits, où l’éditeur de liens ignore l’option. Pour désactiver explicitement cette option, utilisez **/highentropyva : no**.

Pour **/HIGHENTROPYVA** pour avoir un effet au moment du chargement, [/DYNAMICBASE](dynamicbase-use-address-space-layout-randomization.md) doit également être activée. **/ DYNAMICBASE** est activée par défaut et est obligatoire pour activer l’ASLR dans Windows Vista et les systèmes d’exploitation ultérieurs. Les versions antérieures de Windows ignorent cet indicateur.

### <a name="to-set-this-linker-option-in-visual-studio"></a>Pour définir cette option d'éditeur de liens dans Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriétés** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration** > **l’éditeur de liens** > **ligne de commande** page de propriétés.

1. Dans **des Options supplémentaires**, entrez `/HIGHENTROPYVA` ou `/HIGHENTROPYVA:NO`.

## <a name="see-also"></a>Voir aussi

- [Référence de l’éditeur de liens MSVC](linking.md)
- [Options de l’éditeur de liens MSVC](linker-options.md)
- [/DYNAMICBASE](dynamicbase-use-address-space-layout-randomization.md)
- [/LARGEADDRESSAWARE](largeaddressaware-handle-large-addresses.md)
- [Défenses de sécurité d’éditeurs de logiciels Windows](https://msdn.microsoft.com/library/bb430720.aspx)
