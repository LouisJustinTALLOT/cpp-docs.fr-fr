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
ms.openlocfilehash: 13987b4ba9c25db0f5417da562ff86f4230937d7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62271825"
---
# <a name="dynamicbase"></a>/DYNAMICBASE

Spécifie s’il faut générer une image exécutable pouvant être aléatoirement redéfinie au moment du chargement à l’aide de la fonctionnalité espace d’adresse disposition randomization (ASLR) de Windows qui était auparavant disponible dans Windows Vista.

## <a name="syntax"></a>Syntaxe

> **/DYNAMICBASE**[**:NO**]

## <a name="remarks"></a>Notes

Le **/DYNAMICBASE** option modifie l’en-tête d’un *image exécutable*, un fichier .dll ou .exe pour indiquer si l’application doit être aléatoirement redéfinie au moment du chargement et permet d’adresse virtuelle randomisation d’allocation, ce qui affecte l’emplacement de mémoire virtuelle de segments de mémoire, les piles et autres allocations de système d’exploitation. Le **/DYNAMICBASE** option s’applique aux images 32 bits et 64 bits. ASLR est prise en charge sur Windows Vista et les systèmes d’exploitation ultérieurs. L’option est ignorée par les systèmes d’exploitation antérieurs.

Par défaut, **/DYNAMICBASE** est activé. Pour désactiver cette option, utilisez **/DYNAMICBASE : no**. Le **/DYNAMICBASE** option est requise pour le [/HIGHENTROPYVA](highentropyva-support-64-bit-aslr.md) option ait un effet.

## <a name="see-also"></a>Voir aussi

- [Options EDITBIN](editbin-options.md)
- [Défenses de sécurité d’éditeurs de logiciels Windows](https://msdn.microsoft.com/library/bb430720.aspx)