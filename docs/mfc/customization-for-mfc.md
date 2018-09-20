---
title: Personnalisation pour MFC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- customizations, MFC Extensions
ms.assetid: 3b1b7532-8cc9-48dc-9bbe-7fd4060530b5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 640d6726623e8fb6d563153823f449f7caefcf30
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46384999"
---
# <a name="customization-for-mfc"></a>Personnalisation pour MFC

Cette rubrique fournit des conseils pour la personnalisation d’une application MFC.

## <a name="general-customizations"></a>Personnalisations générales

Vous pouvez enregistrer et charger l’état de votre application dans le Registre. Lorsque vous activez cette option, votre application chargera ainsi son état initial à partir du Registre. Si vous modifiez la disposition d’ancrage initiale pour votre application, vous devrez effacer les données de Registre pour votre application. Sinon, les données dans le Registre remplacera toutes les modifications que vous avez apportées à la disposition initiale.

## <a name="class-specific-customizations"></a>Personnalisations spécifiques à la classe

Vous trouverez des conseils de personnalisation supplémentaires dans les rubriques suivantes :

- [CBasePane, classe](../mfc/reference/cbasepane-class.md)

- [CDockablePane, classe](../mfc/reference/cdockablepane-class.md)

- [CDockingManager, classe](../mfc/reference/cdockingmanager-class.md)

- [CMFCBaseTabCtrl, classe](../mfc/reference/cmfcbasetabctrl-class.md)

## <a name="additional-customization-tips"></a>Conseils de personnalisation supplémentaires

[Personnalisation du clavier et de la souris](../mfc/keyboard-and-mouse-customization.md)

[Outils définis par l’utilisateur](../mfc/user-defined-tools.md)

## <a name="see-also"></a>Voir aussi

[MFC, applications de bureau](../mfc/mfc-desktop-applications.md)<br/>
[Implications en matière de sécurité de la personnalisation](../mfc/security-implications-of-customization.md)

