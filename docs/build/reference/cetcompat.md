---
title: / CETCOMPAT (compatible avec la pile cachée d’Europe centrale)
ms.date: 02/19/2019
f1_keywords:
- /CETCOMPAT
helpviewer_keywords:
- /CETCOMPAT linker option
- /CETCOMPAT
ms.openlocfilehash: 0ed5d9d4f9f4f4dc5cd4fc19df4179e86e430187
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273246"
---
# <a name="cetcompat-cet-shadow-stack-compatible"></a>/ CETCOMPAT (compatible avec la pile cachée d’Europe centrale)

Spécifie s’il faut marquer une image exécutable comme étant compatible avec la pile cachée de technologie de mise en œuvre (CET) flux de contrôle.

## <a name="syntax"></a>Syntaxe

> **/CETCOMPAT**\[**:NO**]

## <a name="arguments"></a>Arguments

**NO**<br/>
Spécifie que le fichier exécutable ne doit pas être marqué compatible avec la pile cachée d’Europe centrale.

## <a name="remarks"></a>Notes

Pile cachée de technologie de mise en œuvre (CET) flux de contrôle est une fonctionnalité de processeur d’ordinateur qui fournit des fonctionnalités pour se défendre de programmation orientée retournée (ROP) en fonction des attaques de programmes malveillants. Pour plus d’informations, consultez [la présentation de la technologie de mise en œuvre du flux de contrôle Intel](https://software.intel.com/sites/default/files/managed/4d/2a/control-flow-enforcement-technology-preview.pdf).

Le **/CETCOMPAT** option de l’éditeur de liens indique à l’éditeur de liens pour marquer le fichier binaire comme pile de clichés instantanés Europe centrale-compatible. **/CETCOMPAT:no** marque le binaire comme non compatible avec la pile cachée d’Europe centrale. Si les deux options sont spécifiées sur la ligne de commande, la dernière spécifiée est utilisée. Ce commutateur est actuellement uniquement applicable aux architectures x86 et x64.

Le **/CETCOMPAT** option est disponible à compter de l’ensemble d’outils Visual Studio 2019 Preview 3.

### <a name="to-set-the-cetcompat-linker-option-in-visual-studio"></a>Pour définir l’option de l’éditeur de liens /CETCOMPAT dans Visual Studio

1. Ouvrez le **Pages de propriétés** boîte de dialogue pour le projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration** > **l’éditeur de liens** > **ligne de commande** page de propriétés.

1. Dans le **des options supplémentaires** zone, ajoutez **/CETCOMPAT** ou **/CETCOMPAT:NO** , puis **OK** ou **appliquer**pour enregistrer vos modifications.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

Cette option n’a pas un équivalent de programmation.

## <a name="see-also"></a>Voir aussi

[Options de l’éditeur de liens](linker-options.md)
