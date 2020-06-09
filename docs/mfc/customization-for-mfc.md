---
title: Personnalisation pour MFC
ms.date: 11/04/2016
helpviewer_keywords:
- customizations, MFC Extensions
ms.assetid: 3b1b7532-8cc9-48dc-9bbe-7fd4060530b5
ms.openlocfilehash: 3b7597c3709ed700e82af94c78450ee5aff2d99b
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622964"
---
# <a name="customization-for-mfc"></a>Personnalisation pour MFC

Cette rubrique fournit des conseils pour la personnalisation d’une application MFC.

## <a name="general-customizations"></a>Personnalisations générales

Vous pouvez enregistrer et charger l’état de votre application dans le registre. Lorsque vous activez cette option, votre application charge son état initial à partir du Registre. Si vous modifiez la disposition d’ancrage initiale de votre application, vous devez effacer les données du Registre pour votre application. Dans le cas contraire, les données du Registre remplacent toutes les modifications que vous avez apportées à la disposition initiale.

## <a name="class-specific-customizations"></a>Personnalisations spécifiques à la classe

Vous trouverez des conseils supplémentaires sur la personnalisation dans les rubriques suivantes :

- [CBasePane, classe](reference/cbasepane-class.md)

- [CDockablePane, classe](reference/cdockablepane-class.md)

- [CDockingManager, classe](reference/cdockingmanager-class.md)

- [CMFCBaseTabCtrl, classe](reference/cmfcbasetabctrl-class.md)

## <a name="additional-customization-tips"></a>Conseils supplémentaires pour la personnalisation

[Personnalisation du clavier et de la souris](keyboard-and-mouse-customization.md)

[Outils définis par l’utilisateur](user-defined-tools.md)

## <a name="see-also"></a>Voir aussi

[MFC, applications de bureau](mfc-desktop-applications.md)<br/>
[Implications en matière de sécurité de la personnalisation](security-implications-of-customization.md)
