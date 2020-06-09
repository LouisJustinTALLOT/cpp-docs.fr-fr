---
title: Impression et aperçu avant impression
ms.date: 11/04/2016
helpviewer_keywords:
- printing [MFC]
- previewing printing
- printing [MFC]
- print preview
- printing [MFC], print preview
ms.assetid: d15059cd-32de-4450-95f7-e73aece238f6
ms.openlocfilehash: 26ced8172a36d34883d6b65997bb3a81fdc3c319
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625276"
---
# <a name="printing-and-print-preview"></a>Impression et aperçu avant impression

MFC prend en charge l’impression et l’aperçu avant impression pour les documents de votre programme par le biais de la classe [CView](reference/cview-class.md). Pour l’impression et l’aperçu avant impression de base, il vous suffit de remplacer la fonction membre [OnDraw](reference/cview-class.md#ondraw) de votre classe d’affichage, ce que vous devez faire quand même. Cette fonction peut dessiner sur la vue à l’écran, sur un contexte de périphérique d’impression pour une imprimante réelle ou sur un contexte de périphérique qui simule votre imprimante à l’écran.

Vous pouvez également ajouter du code pour gérer l’impression et l’aperçu des documents multipages, paginer vos documents imprimés et y ajouter des en-têtes et des pieds de page.

Cette famille d’articles explique comment l’impression est implémentée dans le bibliothèque MFC (Microsoft Foundation Class) (MFC) et comment tirer parti de l’architecture d’impression déjà intégrée à l’infrastructure. Les articles expliquent également comment MFC prend en charge l’implémentation simple de la fonctionnalité d’aperçu avant impression et comment vous pouvez utiliser et modifier cette fonctionnalité.

## <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus sur

- [Impression](printing.md)

- [Architecture de l’aperçu avant impression](print-preview-architecture.md)

- [Exemple](../overview/visual-cpp-samples.md)

## <a name="see-also"></a>Voir aussi

[Éléments de l’interface utilisateur](user-interface-elements-mfc.md)
