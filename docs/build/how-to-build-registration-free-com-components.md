---
title: 'Comment : générer des composants COM sans inscription | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- COM components, registration-free
ms.assetid: 7e585d6a-0314-45b2-8f1b-cae9ac4df037
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e0a9e1769ff0ba9a0589f9d59c3d1f1ed2fc5bcb
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45699853"
---
# <a name="how-to-build-registration-free-com-components"></a>Comment : générer des composants COM sans inscription

Les composants COM sans inscription sont des composants COM qui ont des manifestes générés dans les DLL.

### <a name="to-build-manifests-into-com-components"></a>Pour générer des manifestes dans les composants COM

1. Ouvrez les pages de propriétés de projet pour le composant COM.

1. Développez le **propriétés de Configuration** nœud, puis développez le **outil manifeste** nœud.

1. Sélectionnez le **d’entrée et sortie** page de propriétés, puis définissez le **incorporer le manifeste** propriété égale à **Oui**.

1. Cliquez sur **OK**.

1. Générez la solution.

## <a name="see-also"></a>Voir aussi

[Applications isolées](/windows/desktop/SbsCs/isolated-applications)<br/>
[Sur les assemblys côte à côte](/windows/desktop/SbsCs/about-side-by-side-assemblies-)<br/>
[Guide pratique pour générer des applications isolées pour consommer des composants COM](../build/how-to-build-isolated-applications-to-consume-com-components.md)