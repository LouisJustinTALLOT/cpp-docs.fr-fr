---
title: Impression et Aperçu avant impression | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- printing [MFC]
- previewing printing
- printing [MFC]
- print preview
- printing [MFC], print preview
ms.assetid: d15059cd-32de-4450-95f7-e73aece238f6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9aad5c69f6466ea8803cb466c5e5529f3dce1340
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46374449"
---
# <a name="printing-and-print-preview"></a>Impression et aperçu avant impression

MFC prend en charge l’impression et Aperçu avant impression pour les documents de votre programme via la classe [CView](../mfc/reference/cview-class.md). Pour l’impression de base et Aperçu avant impression, simplement remplacer votre classe d’affichage [OnDraw](../mfc/reference/cview-class.md#ondraw) fonction membre, ce que vous devez faire quand même. Cette fonction peut dessiner dans la vue à l’écran, pour un contexte de périphérique pour une imprimante physique, ou dans un contexte de périphérique qui simule votre imprimante à l’écran.

Vous pouvez également ajouter le code pour gérer l’impression des documents multipages et la version préliminaire, pour paginer vos documents imprimés et leur ajouter des en-têtes et pieds de page.

Cette série d’articles explique comment l’impression est implémentée dans les MFC Microsoft Foundation Class Library () et comment tirer parti de l’architecture d’impression déjà intégrée à l’infrastructure. Ces articles expliquent également comment MFC prend en charge l’implémentation simple de la fonctionnalité d’aperçu avant impression, et comment vous pouvez utiliser et modifier cette fonctionnalité.

## <a name="what-do-you-want-to-know-more-about"></a>Ce que vous souhaitez en savoir plus sur

- [Impression](../mfc/printing.md)

- [Architecture de l’aperçu avant impression](../mfc/print-preview-architecture.md)

- [Exemple](../visual-cpp-samples.md)

## <a name="see-also"></a>Voir aussi

[Éléments d’Interface utilisateur](../mfc/user-interface-elements-mfc.md)
