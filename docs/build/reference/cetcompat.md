---
title: / CETCOMPAT (compatible avec la technologie de mise en œuvre de flux de contrôle)
ms.date: 02/19/2019
f1_keywords:
- /CETCOMPAT
helpviewer_keywords:
- /CETCOMPAT linker option
- /CETCOMPAT
ms.openlocfilehash: 1a01dd45667f64dbcbe11acaf1180835bd0d6e31
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57809845"
---
# <a name="cetcompat-control-flow-enforcement-technology-compatible"></a>/ CETCOMPAT (compatible avec la technologie de mise en œuvre de flux de contrôle)

Spécifie s’il faut marquer une image exécutable comme étant compatible avec la technologie de mise en œuvre flux de contrôle (CET).

## <a name="syntax"></a>Syntaxe

> **/CETCOMPAT**\[**:NO**]

## <a name="arguments"></a>Arguments

**NO**<br/>
Spécifie que le fichier exécutable ne doit pas être marqué compatible avec Europe centrale.

## <a name="remarks"></a>Notes

Technologie de mise en œuvre de flux de contrôle (CET) est une fonctionnalité de processeur d’ordinateur qui fournit des fonctionnalités pour vous défendre contre certains types d’attaques de programmes malveillants. Pour plus d’informations, consultez [la présentation de la technologie de mise en œuvre du flux de contrôle Intel](https://software.intel.com/sites/default/files/managed/4d/2a/control-flow-enforcement-technology-preview.pdf).

Le **/CETCOMPAT** option de l’éditeur de liens indique à l’éditeur de liens pour marquer le fichier binaire comme Europe centrale-compatible. **/CETCOMPAT:no** marque le binaire comme non compatible avec Europe centrale. Si les deux options sont spécifiées sur la ligne de commande, la dernière spécifiée est utilisée. Ce commutateur est actuellement uniquement applicable aux architectures x86 et x64.

Le **/CETCOMPAT** option est disponible à compter de l’ensemble d’outils Visual Studio 2019 Preview 3.

### <a name="to-set-the-cetcompat-linker-option-in-visual-studio"></a>Pour définir l’option de l’éditeur de liens /CETCOMPAT dans Visual Studio

1. Ouvrez le **Pages de propriétés** boîte de dialogue pour le projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration** > **l’éditeur de liens** > **ligne de commande** page de propriétés.

1. Dans le **des options supplémentaires** zone, ajoutez **/CETCOMPAT** ou **/CETCOMPAT:NO** , puis **OK** ou **appliquer**pour enregistrer vos modifications.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

Cette option n’a pas un équivalent de programmation.

## <a name="see-also"></a>Voir aussi

[Options de l’éditeur de liens](linker-options.md)
