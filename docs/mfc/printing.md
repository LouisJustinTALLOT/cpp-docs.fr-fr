---
description: 'En savoir plus sur : impression'
title: Impression
ms.date: 11/04/2016
helpviewer_keywords:
- view classes [MFC], print operations
- documents [MFC], printing
- printing [MFC], from framework
- printing [MFC]
ms.assetid: be465e8d-b0c9-4fc5-9fa8-d10486064f76
ms.openlocfilehash: 0cb4455b2de27d7b609226099b00a37dc8175db6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97154862"
---
# <a name="printing"></a>Impression

Microsoft Windows implémente l’affichage indépendant du périphérique. Dans MFC, cela signifie que les mêmes appels de dessin, dans la `OnDraw` fonction membre de votre classe d’affichage, sont responsables du dessin sur l’affichage et sur d’autres périphériques, tels que les imprimantes. Pour l’aperçu avant impression, l’appareil cible est une sortie d’imprimante simulée à l’écran.

## <a name="your-role-in-printing-vs-the-frameworks-role"></a><a name="_core_your_role_in_printing_vs.._the_framework.92.s_role"></a> Votre rôle dans l’impression et le rôle de l’infrastructure

Votre classe d’affichage a les responsabilités suivantes :

- Indiquez au Framework le nombre de pages dans le document.

- Lorsque vous êtes invité à imprimer une page spécifiée, dessinez cette partie du document.

- Allouez et Désallouez les polices ou autres ressources GDI (Graphics Device Interface) nécessaires à l’impression.

- Si nécessaire, envoyez les codes d’échappement nécessaires pour modifier le mode d’impression avant d’imprimer une page donnée, par exemple pour modifier l’orientation de l’impression pour chaque page.

Les responsabilités du Framework sont les suivantes :

- Affiche la boîte de dialogue **Imprimer** .

- Créez un objet [CDC](reference/cdc-class.md) pour l’imprimante.

- Appelez les fonctions membres [StartDoc](reference/cdc-class.md#startdoc) et [EndDoc](reference/cdc-class.md#enddoc) de l' `CDC` objet.

- Appelez à plusieurs reprises la fonction membre [StartPage](reference/cdc-class.md#startpage) de l' `CDC` objet, informez la classe d’affichage de la page à imprimer et appelez la fonction membre [EndPage](reference/cdc-class.md#endpage) de l' `CDC` objet.

- Appelez les fonctions substituables dans la vue aux moments appropriés.

Les articles suivants expliquent comment le Framework prend en charge l’impression et l’aperçu avant impression :

### <a name="what-do-you-want-to-know-more-about"></a>Que voulez-vous en savoir plus sur

- [Comment exécuter l’impression par défaut](how-default-printing-is-done.md)

- [Documents multipages](multipage-documents.md)

- [En-têtes et pieds de page](headers-and-footers.md)

- [Allocation de ressources GDI pour l'impression](allocating-gdi-resources.md)

- [Aperçu avant impression](print-preview-architecture.md)

## <a name="see-also"></a>Voir aussi

[Impression et aperçu avant impression](printing-and-print-preview.md)
