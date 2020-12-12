---
description: 'En savoir plus sur : personnalisation pour MFC'
title: Personnalisation pour MFC
ms.date: 11/04/2016
helpviewer_keywords:
- customizations, MFC Extensions
ms.assetid: 3b1b7532-8cc9-48dc-9bbe-7fd4060530b5
ms.openlocfilehash: 50df32d4743381e1212eae53b695e2355bc8d0e1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97309405"
---
# <a name="customization-for-mfc"></a>Personnalisation pour MFC

Cette rubrique fournit des conseils pour la personnalisation d’une application MFC.

## <a name="general-customizations"></a>Personnalisations générales

Vous pouvez enregistrer et charger l’état de votre application dans le registre. Lorsque vous activez cette option, votre application charge son état initial à partir du Registre. Si vous modifiez la disposition d’ancrage initiale de votre application, vous devez effacer les données du Registre pour votre application. Dans le cas contraire, les données du Registre remplacent toutes les modifications que vous avez apportées à la disposition initiale.

## <a name="class-specific-customizations"></a>Personnalisations de l' Class-Specific

Vous trouverez des conseils supplémentaires sur la personnalisation dans les rubriques suivantes :

- [CBasePane, classe](reference/cbasepane-class.md)

- [CDockablePane, classe](reference/cdockablepane-class.md)

- [CDockingManager, classe](reference/cdockingmanager-class.md)

- [CMFCBaseTabCtrl, classe](reference/cmfcbasetabctrl-class.md)

## <a name="additional-customization-tips"></a>Conseils supplémentaires pour la personnalisation

[Personnalisation du clavier et de la souris](keyboard-and-mouse-customization.md)

[Outils définis par l’utilisateur](user-defined-tools.md)

## <a name="see-also"></a>Voir aussi

[Applications de bureau MFC](mfc-desktop-applications.md)<br/>
[Implications en matière de sécurité de la personnalisation](security-implications-of-customization.md)
