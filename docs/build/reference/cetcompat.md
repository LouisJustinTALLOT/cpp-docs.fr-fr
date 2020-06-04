---
title: /CETCOMPAT (compatible avec la pile cachée de l’heure de l’est)
ms.date: 02/19/2019
f1_keywords:
- /CETCOMPAT
helpviewer_keywords:
- /CETCOMPAT linker option
- /CETCOMPAT
ms.openlocfilehash: 2c807d91d69b967fd62e01a077711dede5f55c44
ms.sourcegitcommit: 7e011c68ca7547469544fac87001a33a37e1792e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84421298"
---
# <a name="cetcompat-cet-shadow-stack-compatible"></a>/CETCOMPAT (compatible avec la pile cachée de l’heure de l’est)

Spécifie s’il faut marquer une image exécutable comme étant compatible avec la pile cachée de la technologie d’application du workflow de contrôle.

## <a name="syntax"></a>Syntaxe

> **/CETCOMPAT** \[ **: Non**]

## <a name="arguments"></a>Arguments

**º**<br/>
Spécifie que l’exécutable ne doit pas être marqué comme compatible avec la pile Shadow de CET.

## <a name="remarks"></a>Notes

La technologie de mise en application du workflow de contrôle (CET) est une fonctionnalité de processeur d’ordinateur qui fournit des fonctionnalités permettant de se défendre contre les attaques par programme malveillant basées sur la programmation orientée (ROP). Pour plus d’informations, consultez [Intel Control-Flow application Technology Preview](https://software.intel.com/sites/default/files/managed/4d/2a/control-flow-enforcement-technology-preview.pdf).

L’option de l’éditeur de liens **/CETCOMPAT** indique à l’éditeur de liens de marquer le binaire comme étant compatible avec la pile Shadow. **/CETCOMPAT : no** indique que le fichier binaire n’est pas compatible avec la pile Shadow de cet. Si les deux options sont spécifiées sur la ligne de commande, la dernière spécifiée est utilisée. Ce commutateur est actuellement applicable uniquement aux architectures x86 et x64.

L’option **/CETCOMPAT** est disponible à partir de l’ensemble d’outils visual studio 2019 Preview 3.

### <a name="to-set-the-cetcompat-linker-option-in-visual-studio"></a>Pour définir l’option de l’éditeur de liens/CETCOMPAT dans Visual Studio

1. Ouvrez la boîte de dialogue **pages de propriétés** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés avancé de l’éditeur de liens **Propriétés de configuration**  >  **Linker**  >  **Advanced** .

1. Sélectionnez la propriété **compatible avec la pile Shadow de cet** .

1. Dans le contrôle de liste déroulante, choisissez **Oui (/CETCOMPAT)** pour activer les métadonnées de continuation Eh ou **non (/CETCOMPAT : non)** pour le désactiver.


### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

Cette option n’a pas d’équivalent programmatique.

## <a name="see-also"></a>Voir aussi

[Options de l’éditeur de liens](linker-options.md)
