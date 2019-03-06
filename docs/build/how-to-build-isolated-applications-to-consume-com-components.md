---
title: 'Procédure : Générer des Applications isolées pour consommer des composants COM'
ms.date: 11/04/2016
helpviewer_keywords:
- isolated applications [C++]
ms.assetid: 04587547-1174-44ab-bd99-1292358fba20
ms.openlocfilehash: 01b5c7056bd10a7c1f88df74b5c6b4aa78ff3fde
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57417877"
---
# <a name="how-to-build-isolated-applications-to-consume-com-components"></a>Procédure : Générer des Applications isolées pour consommer des composants COM

Applications isolées sont des applications qui ont des manifestes générés dans le programme. Vous pouvez créer des applications isolées pour consommer des composants COM.

### <a name="to-add-com-references-to-manifests-of-isolated-applications"></a>Pour ajouter des références COM aux manifestes d’applications isolées

1. Ouvrez les pages de propriétés de projet de l’application isolée.

1. Développez le **propriétés de Configuration** nœud, puis développez le **outil manifeste** nœud.

1. Sélectionnez le **COM isolé** page de propriétés, puis définissez le **nom de fichier de composant** propriété le nom du composant COM que vous souhaitez l’application isolée à consommer.

1. Cliquez sur **OK**.

### <a name="to-build-manifests-into-isolated-applications"></a>Pour générer des manifestes dans les applications isolées

1. Ouvrez les pages de propriétés de projet de l’application isolée.

1. Développez le **propriétés de Configuration** nœud, puis développez le **outil manifeste** nœud.

1. Sélectionnez le **d’entrée et sortie** page de propriétés, puis définissez le **incorporer le manifeste** propriété égale à **Oui**.

1. Cliquez sur **OK**.

1. Générez la solution.

## <a name="see-also"></a>Voir aussi

[Applications isolées](/windows/desktop/SbsCs/isolated-applications)<br/>
[Sur les assemblys côte à côte](/windows/desktop/SbsCs/about-side-by-side-assemblies-)
