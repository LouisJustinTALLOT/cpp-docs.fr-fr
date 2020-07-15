---
title: /DYNAMICBASE
ms.date: 06/12/2018
f1_keywords:
- /dynamicbase
helpviewer_keywords:
- -DYNAMICBASE editbin option
- DYNAMICBASE editbin option
- /DYNAMICBASE editbin option
ms.assetid: edb3df90-7b07-42fb-a94a-f5a4c1d325d6
ms.openlocfilehash: 54644d9df546299be3b688f9745a121592938df6
ms.sourcegitcommit: 31a443c9998cf5cfbaff00fcf815b133f55b2426
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86373617"
---
# <a name="dynamicbase"></a>/DYNAMICBASE

Spécifie s’il faut générer une image exécutable qui peut être redéfinie de façon aléatoire au moment du chargement à l’aide de la fonctionnalité de randomisation du format d’espace d’adresse (ASLR) de Windows qui était d’abord disponible dans Windows Vista.

## <a name="syntax"></a>Syntaxe

> **/DynamicBase**[**: no**]

## <a name="remarks"></a>Notes

L’option **/DynamicBase** modifie l’en-tête d’une *image exécutable*, un fichier. dll ou. exe pour indiquer si l’application doit être redéfinie de façon aléatoire au moment du chargement, et active la randomisation de l’allocation d’adresses virtuelles, ce qui affecte l’emplacement de la mémoire virtuelle des tas, des piles et d’autres allocations du système d’exploitation. L’option **/DynamicBase** s’applique aux images 32 bits et 64 bits. ASLR est pris en charge sur Windows Vista et les systèmes d’exploitation ultérieurs. L’option est ignorée par les systèmes d’exploitation antérieurs.

Par défaut, **/DynamicBase** est activé. Pour désactiver cette option, utilisez **/DynamicBase : no**. L’option **/DynamicBase** est nécessaire pour que l’option [/HIGHENTROPYVA](highentropyva-support-64-bit-aslr.md) ait un effet.

## <a name="see-also"></a>Voir aussi

- [Options EDITBIN](editbin-options.md)
- [Défenses de la sécurité logicielle ISV Windows](https://docs.microsoft.com/previous-versions/bb430720(v=msdn.10))
