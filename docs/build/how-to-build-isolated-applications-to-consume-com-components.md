---
title: 'Comment : générer des applications isolées pour consommer des composants COM'
ms.date: 11/04/2016
helpviewer_keywords:
- isolated applications [C++]
ms.assetid: 04587547-1174-44ab-bd99-1292358fba20
ms.openlocfilehash: ba35c016996604e2b433083c2de7b9ddc807d52c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50587536"
---
# <a name="how-to-build-isolated-applications-to-consume-com-components"></a>Comment : générer des applications isolées pour consommer des composants COM

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