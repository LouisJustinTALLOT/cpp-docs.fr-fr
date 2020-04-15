---
title: Impression
ms.date: 11/04/2016
helpviewer_keywords:
- view classes [MFC], print operations
- documents [MFC], printing
- printing [MFC], from framework
- printing [MFC]
ms.assetid: be465e8d-b0c9-4fc5-9fa8-d10486064f76
ms.openlocfilehash: a46096592c9983d04d2122bfabb56ece9346c4bc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371206"
---
# <a name="printing"></a>Impression

Microsoft Windows implémente un écran indépendant de l’appareil. Dans MFC, cela signifie que les `OnDraw` mêmes appels de dessin, dans la fonction membre de votre classe de vue, sont responsables du dessin sur l’écran et sur d’autres appareils, tels que les imprimantes. Pour l’aperçu d’impression, l’appareil cible est une sortie d’imprimante simulée à l’écran.

## <a name="your-role-in-printing-vs-the-frameworks-role"></a><a name="_core_your_role_in_printing_vs.._the_framework.92.s_role"></a>Votre rôle dans l’impression par rapport au rôle du Cadre

Votre classe de vue a les responsabilités suivantes :

- Informez le cadre du nombre de pages dans le document.

- Lorsqu’on lui demande d’imprimer une page spécifiée, dessinez cette partie du document.

- Répartir et traiter les polices ou autres ressources d’interface graphique (GDI) nécessaires à l’impression.

- Si nécessaire, envoyez les codes d’évacuation nécessaires pour modifier le mode d’imprimante avant d’imprimer une page donnée, par exemple, pour modifier l’orientation d’impression par page.

Les responsabilités du cadre sont les suivantes :

- Affichez la boîte de dialogue **d’impression.**

- Créez un objet [CDC](../mfc/reference/cdc-class.md) pour l’imprimante.

- Appelez les fonctions des membres [StartDoc](../mfc/reference/cdc-class.md#startdoc) et [EndDoc](../mfc/reference/cdc-class.md#enddoc) de l’objet. `CDC`

- Appelez à plusieurs reprises la `CDC` fonction membre [StartPage](../mfc/reference/cdc-class.md#startpage) de l’objet, informez la classe `CDC` de vue quelle page doit être imprimée et appelez la fonction membre [EndPage](../mfc/reference/cdc-class.md#endpage) de l’objet.

- Appelez des fonctions primordiales dans la vue aux moments appropriés.

Les articles suivants discutent de la façon dont le cadre prend en charge l’impression et l’impression aperçu:

### <a name="what-do-you-want-to-know-more-about"></a>Qu’est-ce que vous voulez savoir plus sur

- [Comment l’impression par défaut est effectuée](../mfc/how-default-printing-is-done.md)

- [Documents multipages](../mfc/multipage-documents.md)

- [En-têtes et pieds](../mfc/headers-and-footers.md)

- [Allocation de ressources GDI pour l'impression](../mfc/allocating-gdi-resources.md)

- [Aperçu d’impression](../mfc/print-preview-architecture.md)

## <a name="see-also"></a>Voir aussi

[Impression et aperçu avant impression](../mfc/printing-and-print-preview.md)
