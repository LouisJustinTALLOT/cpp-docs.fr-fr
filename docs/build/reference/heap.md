---
title: /HEAP
description: L’option MSVC Linker ou EDITBIN/HEAP définit la taille totale du tas et, éventuellement, la taille des blocs de tas supplémentaires.
ms.date: 07/07/2020
f1_keywords:
- /heap
helpviewer_keywords:
- heap allocation, setting heap size
- HEAP editbin option
- -HEAP editbin option
- /HEAP editbin option
ms.assetid: 6ce759b5-75b7-44ff-a5fd-3a83a0ba9a48
ms.openlocfilehash: 7976ae2927ca731c83fa42e87da182fee4df3d7c
ms.sourcegitcommit: e17cc8a478b51739d67304d7d82422967b35f716
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/08/2020
ms.locfileid: "86127827"
---
# `/HEAP`

Définit la taille du tas en octets. Cette option s’applique uniquement aux fichiers exécutables.

## <a name="syntax"></a>Syntaxe

> **`/HEAP:`**_`reserve`_\[**`,`**_`commit`_]

## <a name="remarks"></a>Notes

L' *`reserve`* argument spécifie l’allocation de tas initiale totale dans la mémoire virtuelle. L' **`/HEAP`** éditeur de liens ou l’option [EDITBIN](editbin-reference.md) arrondit la valeur spécifiée au multiple le plus proche de 4 octets. Par défaut, la taille du tas est de 1 Mo.

L' *`commit`* argument facultatif est soumis à une interprétation par le système d’exploitation. Sur un système d’exploitation Windows, il spécifie la quantité initiale de mémoire physique à allouer. Il spécifie également la quantité de mémoire supplémentaire à allouer lorsque le tas est développé. La mémoire virtuelle validée entraîne la réservation de l’espace dans le fichier d’échange. Une valeur plus élevée *`commit`* permet au système d’allouer la mémoire moins souvent lorsque l’application a besoin de davantage d’espace de tas, mais augmente les besoins en mémoire et éventuellement la durée de démarrage de l’application. La *`commit`* valeur doit être inférieure ou égale à la *`reserve`* valeur. La valeur par défaut est 4 Ko.

Spécifiez *`reserve`* les *`commit`* valeurs et en notation décimale, hexadécimale en langage C ou octal. Par exemple, une valeur de 1 Mo peut être spécifiée en tant que 1048576 en décimal, ou en tant que valeur de 1 à 1 dans hexadécimal, ou en tant que 04000000 en octal. Les valeurs par défaut sont équivalentes à l’option **`/HEAP:1048576,4096`** .

### <a name="example"></a>Exemple

Cet exemple de commande de liaison crée un *main.exe* exécutable dont la réserve de tas est de 2 Mo. Le tas initial et les expansions de tas ultérieurs sont placés dans des blocs de 64 Ko :

**`link /heap:0x200000,0x10000 main.obj`**

### <a name="to-set-this-linker-option-in-visual-studio"></a>Pour définir cette option d'éditeur de liens dans Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriétés** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés système de l’éditeur de liens **Propriétés de configuration**  >  **Linker**  >  **System** .

1. Définissez les propriétés taille de la **réserve de tas** et taille de la validation du **tas** , puis cliquez sur **OK** ou sur **appliquer** pour enregistrer vos modifications.

## <a name="see-also"></a>Voir aussi

[Options EDITBIN](editbin-options.md)\
[Options de l’éditeur de liens MSVC](linker-options.md)
