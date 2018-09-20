---
title: L’impression | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- view classes [MFC], print operations
- documents [MFC], printing
- printing [MFC], from framework
- printing [MFC]
ms.assetid: be465e8d-b0c9-4fc5-9fa8-d10486064f76
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e03e750941be02385ac4d5b7463d5b6f32997b6a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46373946"
---
# <a name="printing"></a>Impression

Microsoft Windows implémente un affichage est indépendant du périphérique. Dans MFC, cela signifie que les mêmes appels de dessins, dans le `OnDraw` fonction membre de votre classe d’affichage sont responsables de dessin sur l’affichage et sur d’autres appareils, tels que les imprimantes. Pour l’aperçu avant impression, le périphérique cible est une sortie d’imprimante simulé à l’affichage.

##  <a name="_core_your_role_in_printing_vs.._the_framework.92.s_role"></a> Votre rôle dans l’impression et celui de l’infrastructure

Votre classe d’affichage responsabilités est les suivantes :

- Informer l’infrastructure combien de pages est dans le document.

- Lorsque vous êtes invité à imprimer une page spécifiée, dessinez la partie du document.

- Allouer et libérer toutes les polices ou autres ressources d’interface (GDI) de périphérique graphique nécessaires pour l’impression.

- Si nécessaire, envoyer les codes d’échappement nécessaires pour modifier le mode d’impression avant d’imprimer une page donnée, par exemple, pour modifier l’orientation de l’impression sur une base par page.

Les responsabilités de l’infrastructure sont les suivantes :

- Afficher le **impression** boîte de dialogue.

- Créer un [CDC](../mfc/reference/cdc-class.md) objet pour l’imprimante.

- Appelez le [StartDoc](../mfc/reference/cdc-class.md#startdoc) et [EndDoc](../mfc/reference/cdc-class.md#enddoc) fonctions membres de la `CDC` objet.

- Appeler à plusieurs reprises la [StartPage](../mfc/reference/cdc-class.md#startpage) fonction membre de la `CDC` de l’objet, informer de la classe d’affichage quelle page doit être imprimée et appeler le [EndPage](../mfc/reference/cdc-class.md#endpage) fonction membre de la `CDC` objet.

- Appeler des fonctions substituables dans la vue aux moments appropriés.

Les articles suivants expliquent comment le framework prend en charge l’impression et Aperçu avant impression :

### <a name="what-do-you-want-to-know-more-about"></a>Ce que vous souhaitez en savoir plus sur

- [Procédure d’impression par défaut](../mfc/how-default-printing-is-done.md)

- [Documents multipages](../mfc/multipage-documents.md)

- [En-têtes et pieds de page](../mfc/headers-and-footers.md)

- [Allocation de ressources GDI pour l’impression](../mfc/allocating-gdi-resources.md)

- [Aperçu avant impression](../mfc/print-preview-architecture.md)

## <a name="see-also"></a>Voir aussi

[Impression et aperçu avant impression](../mfc/printing-and-print-preview.md)

