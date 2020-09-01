---
title: /CETCOMPAT (compatible avec la pile cachée de l’heure de l’est)
ms.date: 09/01/2020
f1_keywords:
- /CETCOMPAT
helpviewer_keywords:
- /CETCOMPAT linker option
- /CETCOMPAT
ms.openlocfilehash: 7de7c2007c29769cb3ac8f89d07de8b00bf44c26
ms.sourcegitcommit: e58918c45316d799c1952ca7797a85adbcd0c472
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/01/2020
ms.locfileid: "89281823"
---
# <a name="cetcompat-cet-shadow-stack-compatible"></a>/CETCOMPAT (compatible avec la pile cachée de l’heure de l’est)

Spécifie s’il faut marquer une image exécutable comme étant compatible avec la pile cachée de la technologie d’application du workflow de contrôle.

## <a name="syntax"></a>Syntaxe

> **`/CETCOMPAT`**\
> **`/CETCOMPAT:NO`**

## <a name="arguments"></a>Arguments

**`NO`**<br/>
Spécifie que le fichier exécutable ne doit pas être marqué comme compatible avec la pile Shadow de CET.

## <a name="remarks"></a>Notes

La technologie de mise en application du workflow de contrôle (CET) est une fonctionnalité de processeur d’ordinateur qui fournit des fonctionnalités permettant de se défendre contre les attaques par programme malveillant basées sur la programmation orientée retour (ROP). Pour plus d’informations, consultez [Intel Control-Flow application Technology Preview](https://software.intel.com/sites/default/files/managed/4d/2a/control-flow-enforcement-technology-preview.pdf).

L' **`/CETCOMPAT`** option de l’éditeur de liens indique à l’éditeur de liens de marquer le binaire comme étant compatible avec la pile Shadow. **`/CETCOMPAT:NO`** marque le fichier binaire comme non compatible avec la pile cachée de CET. Si les deux options sont spécifiées sur la ligne de commande, la dernière spécifiée est utilisée. Ce commutateur est actuellement applicable uniquement aux architectures x86 et x64.

L' **`/CETCOMPAT`** option est disponible à partir de Visual Studio 2019.

### <a name="to-set-the-cetcompat-linker-option-in-visual-studio"></a>Pour définir l' `/CETCOMPAT` option de l’éditeur de liens dans Visual Studio

À compter de Visual Studio 2019 version 16,7 :

1. Ouvrez la boîte de dialogue **pages de propriétés** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés avancé de l’éditeur de liens **Propriétés de configuration**  >  **Linker**  >  **Advanced** .

1. Sélectionnez la propriété **compatible avec la pile Shadow de cet** .

1. Dans le contrôle de liste déroulante, choisissez **`Yes (/CETCOMPAT)`** de marquer le binaire comme étant compatible avec la pile Shadow, ou **`No (/CETCOMPAT:NO)`** de le marquer comme non compatible.

Dans les versions précédentes de Visual Studio 2019 :

1. Ouvrez la boîte de dialogue **pages de propriétés** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés ligne de commande de l’éditeur de liens **Propriétés de configuration**  >  **Linker**  >  **Command Line** .

1. Dans le contrôle d’édition **options supplémentaires** , ajoutez *`/CETCOMPAT`* pour marquer le binaire comme étant compatible avec la pile Shadowy, ou *`/CETCOMPAT:NO`* pour le marquer explicitement comme non compatible.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

Cette option n’a pas d’équivalent programmatique.

## <a name="see-also"></a>Voir aussi

[Options de l’éditeur de liens](linker-options.md)
