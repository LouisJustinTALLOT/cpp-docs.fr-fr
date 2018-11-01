---
title: 'Contrôles ActiveX MFC : propriétés'
ms.date: 11/04/2016
helpviewer_keywords:
- properties [MFC], ActiveX controls
- MFC ActiveX controls [MFC], properties
- properties [MFC]
ms.assetid: b678a53c-0d9e-476f-8aa0-23b80baaba46
ms.openlocfilehash: 3b8d9f32246270a570b09f599f8b05f2a58ecfc6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50648459"
---
# <a name="mfc-activex-controls-properties"></a>Contrôles ActiveX MFC : propriétés

Un contrôle ActiveX déclenche des événements pour communiquer avec son conteneur. Le conteneur, utilise en retour, les méthodes et propriétés pour communiquer avec le contrôle. Méthodes et propriétés sont similaires dans l’utilisation et leur finalité, respectivement, aux fonctions membres et variables de membre d’une classe C++. Propriétés sont des membres de données du contrôle ActiveX qui sont exposés à n’importe quel conteneur. Propriétés fournissent une interface pour les applications qui contiennent des contrôles ActiveX, telles que les clients Automation et les conteneurs de contrôles ActiveX.

Propriétés sont également appelées attributs.

Pour plus d’informations sur les méthodes de contrôle ActiveX, consultez l’article [contrôles ActiveX MFC : méthodes](../mfc/mfc-activex-controls-methods.md).

Contrôles ActiveX peuvent implémenter des propriétés et méthodes personnalisées et les actions. Classe `COleControl` fournit une implémentation pour les propriétés stock. (Pour obtenir une liste complète des propriétés stock, consultez l’article [contrôles ActiveX MFC : ajout de propriétés Stock](../mfc/mfc-activex-controls-adding-stock-properties.md).) Propriétés personnalisées, définies par le développeur, ajoutent des fonctionnalités spécialisées à un contrôle ActiveX. Pour plus d’informations, consultez [contrôles ActiveX MFC : ajout de propriétés personnalisées](../mfc/mfc-activex-controls-adding-custom-properties.md).

Propriétés stocks et personnalisées, comme les méthodes, sont pris en charge par un mécanisme qui se compose d’une table de dispatch qui gère les propriétés et les méthodes et les fonctions membres existantes de la `COleControl` classe. En outre, ces propriétés peuvent avoir des paramètres que le développeur utilise pour passer des informations supplémentaires au contrôle.

Les articles suivants décrivent les propriétés du contrôle ActiveX plus en détail :

- [Contrôles ActiveX MFC : ajout de propriétés stock](../mfc/mfc-activex-controls-adding-stock-properties.md)

- [Contrôles ActiveX MFC : ajout de propriétés personnalisées](../mfc/mfc-activex-controls-adding-custom-properties.md)

- [Contrôles ActiveX MFC : implémentation des propriétés avancées](../mfc/mfc-activex-controls-advanced-property-implementation.md)

- [Contrôles ActiveX MFC : accès aux propriétés ambiantes](../mfc/mfc-activex-controls-accessing-ambient-properties.md)

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)

