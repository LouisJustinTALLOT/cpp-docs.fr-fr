---
title: 'Comment : générer des Applications isolées pour consommer des composants COM | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- isolated applications [C++]
ms.assetid: 04587547-1174-44ab-bd99-1292358fba20
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6d2acabb6a5e9c35029b346097a66eaf1311826c
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45704026"
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