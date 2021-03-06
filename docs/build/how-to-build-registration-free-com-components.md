---
description: 'En savoir plus sur : Comment : générer des composants COM Registration-Free'
title: 'Comment : générer des composants COM sans inscription'
ms.date: 11/04/2016
helpviewer_keywords:
- COM components, registration-free
ms.assetid: 7e585d6a-0314-45b2-8f1b-cae9ac4df037
ms.openlocfilehash: ddcb378989878749d170705b4808d8302523a73a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97162714"
---
# <a name="how-to-build-registration-free-com-components"></a>Comment : générer des composants COM sans inscription

Les composants COM sans inscription sont des composants COM qui ont des manifestes intégrés aux dll.

### <a name="to-build-manifests-into-com-components"></a>Pour générer des manifestes dans des composants COM

1. Ouvrez les pages de propriétés du projet pour le composant COM.

1. Développez le nœud **Propriétés de configuration** , puis développez le nœud **outil manifeste** .

1. Sélectionnez la page de propriétés **entrée et sortie** , puis affectez à la propriété **incorporer le manifeste** la valeur **Oui**.

1. Cliquez sur **OK**.

1. Générez la solution.

## <a name="see-also"></a>Voir aussi

[Comment : générer des applications isolées pour consommer des composants COM](how-to-build-isolated-applications-to-consume-com-components.md)
