---
description: 'En savoir plus sur : désactivation de l’option Activer quand elle est visible'
title: Désactivation de l'option Actif quand il est visible
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], activate options
- Activate When Visible option [MFC]
ms.assetid: 8f7ddc5a-a7a6-4da8-bcb9-1b569f0ecb48
ms.openlocfilehash: fcb5f7ef0518cbf257ef9ee7a659c9617092b7d8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97263866"
---
# <a name="turning-off-the-activate-when-visible-option"></a>Désactivation de l'option Actif quand il est visible

Un contrôle a deux États de base : actif et inactif. Traditionnellement, ces États étaient distingués par le fait que le contrôle avait une fenêtre. Un contrôle actif avait une fenêtre ; un contrôle inactif ne l’a pas fait. Avec l’introduction de l’activation sans fenêtre, cette distinction n’est plus universelle, mais s’applique toujours à de nombreux contrôles.

En comparaison avec le reste de l’initialisation généralement effectuée par un contrôle ActiveX, la création d’une fenêtre est une opération extrêmement coûteuse. Dans l’idéal, un contrôle différerait la création de sa fenêtre jusqu’à ce qu’il soit absolument nécessaire.

De nombreux contrôles n’ont pas besoin d’être actifs pendant toute la durée de leur affichage dans un conteneur. Souvent, un contrôle peut rester dans l’état inactif jusqu’à ce que l’utilisateur effectue une opération qui l’oblige à devenir actif (par exemple, en cliquant avec la souris ou en appuyant sur la touche TAB). Pour faire en sorte qu’un contrôle reste inactif jusqu’à ce que le conteneur ait besoin de l’activer, supprimez l’indicateur **OLEMISC_ACTIVATEWHENVISIBLE** des indicateurs divers du contrôle :

[!code-cpp[NVC_MFC_AxOpt#9](../mfc/codesnippet/cpp/turning-off-the-activate-when-visible-option_1.cpp)]

L’indicateur **OLEMISC_ACTIVATEWHENVISIBLE** est automatiquement omis si vous désactivez l’option **activer quand** il est visible dans la page [paramètres du contrôle](../mfc/reference/control-settings-mfc-activex-control-wizard.md) de l’Assistant contrôle ActiveX MFC lorsque vous créez votre contrôle.

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC : optimisation](../mfc/mfc-activex-controls-optimization.md)
