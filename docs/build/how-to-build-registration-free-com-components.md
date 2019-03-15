---
title: 'Procédure : Générer des composants COM sans inscription'
ms.date: 11/04/2016
helpviewer_keywords:
- COM components, registration-free
ms.assetid: 7e585d6a-0314-45b2-8f1b-cae9ac4df037
ms.openlocfilehash: 783677c97835acc98751fc4a19f9405af752b71a
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57809598"
---
# <a name="how-to-build-registration-free-com-components"></a>Procédure : Générer des composants COM sans inscription

Les composants COM sans inscription sont des composants COM qui ont des manifestes générés dans les DLL.

### <a name="to-build-manifests-into-com-components"></a>Pour générer des manifestes dans les composants COM

1. Ouvrez les pages de propriétés de projet pour le composant COM.

1. Développez le **propriétés de Configuration** nœud, puis développez le **outil manifeste** nœud.

1. Sélectionnez le **d’entrée et sortie** page de propriétés, puis définissez le **incorporer le manifeste** propriété égale à **Oui**.

1. Cliquez sur **OK**.

1. Générez la solution.

## <a name="see-also"></a>Voir aussi

[Guide pratique pour générer des applications isolées afin de consommer des composants COM](how-to-build-isolated-applications-to-consume-com-components.md)
