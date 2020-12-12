---
description: 'En savoir plus sur : contrôles ActiveX MFC : propriétés'
title: 'Contrôles ActiveX MFC : propriétés'
ms.date: 11/04/2016
helpviewer_keywords:
- properties [MFC], ActiveX controls
- MFC ActiveX controls [MFC], properties
- properties [MFC]
ms.assetid: b678a53c-0d9e-476f-8aa0-23b80baaba46
ms.openlocfilehash: 9331be68c2e09fe3a4ad83d21e3ed58bbdfdd61e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97206134"
---
# <a name="mfc-activex-controls-properties"></a>Contrôles ActiveX MFC : propriétés

Un contrôle ActiveX déclenche des événements pour communiquer avec son conteneur de contrôle. En retour, le conteneur utilise des méthodes et des propriétés pour communiquer avec le contrôle. Les méthodes et les propriétés sont similaires et utilisées, respectivement, aux fonctions membres et aux variables membres d’une classe C++. Les propriétés sont des données membres du contrôle ActiveX qui sont exposées à n’importe quel conteneur. Les propriétés fournissent une interface pour les applications qui contiennent des contrôles ActiveX, tels que les clients Automation et les conteneurs de contrôles ActiveX.

Les propriétés sont également appelées attributs.

Pour plus d’informations sur les méthodes de contrôle ActiveX, consultez l’article [contrôles ActiveX MFC : méthodes](mfc-activex-controls-methods.md).

Les contrôles ActiveX peuvent implémenter à la fois des méthodes et des propriétés stock et personnalisées. La classe `COleControl` fournit une implémentation pour les propriétés stock. (Pour obtenir la liste complète des propriétés stock, consultez l’article [contrôles ActiveX MFC : ajout de propriétés stock](mfc-activex-controls-adding-stock-properties.md).) Les propriétés personnalisées, définies par le développeur, ajoutent des fonctionnalités spécialisées à un contrôle ActiveX. Pour plus d’informations, consultez [contrôles ActiveX MFC : ajout de propriétés personnalisées](mfc-activex-controls-adding-custom-properties.md).

Les propriétés personnalisées et stock, comme les méthodes, sont prises en charge par un mécanisme qui se compose d’une table de dispatch qui gère les propriétés et les méthodes et les fonctions membres existantes de la `COleControl` classe. En outre, ces propriétés peuvent avoir des paramètres que le développeur utilise pour passer des informations supplémentaires au contrôle.

Les articles suivants traitent des propriétés des contrôles ActiveX plus en détail :

- [Contrôles ActiveX MFC : ajout de propriétés stock](mfc-activex-controls-adding-stock-properties.md)

- [Contrôles ActiveX MFC : ajout de propriétés personnalisées](mfc-activex-controls-adding-custom-properties.md)

- [Contrôles ActiveX MFC : implémentation avancée des propriétés](mfc-activex-controls-advanced-property-implementation.md)

- [Contrôles ActiveX MFC : accès aux propriétés ambiantes](mfc-activex-controls-accessing-ambient-properties.md)

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC](mfc-activex-controls.md)
