---
description: 'En savoir plus sur : utilisation de chaînes de format personnalisées dans un contrôle de sélecteur de date et d’heure'
title: Utilisation de chaînes de format personnalisées dans un contrôle de sélecteur de date et heure
ms.date: 11/04/2016
helpviewer_keywords:
- CDateTimeCtrl class [MFC], display styles
- DateTimePicker control [MFC], display styles
- DateTimePicker control [MFC]
ms.assetid: 7d577f03-6ca0-4597-9093-50b78f304719
ms.openlocfilehash: 91add199ffd852a107588617d47a2fd51136596d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97154550"
---
# <a name="using-custom-format-strings-in-a-date-and-time-picker-control"></a>Utilisation de chaînes de format personnalisées dans un contrôle de sélecteur de date et heure

Par défaut, les contrôles de sélecteur de date et d’heure fournissent trois types de format (chaque format correspondant à un style unique) pour afficher la date ou l’heure actuelle :

- **DTS_LONGDATEFORMAT** Affiche la date au format long, produisant une sortie telle que « mercredi 3 janvier 2000 ».

- **DTS_SHORTDATEFORMAT** Affiche la date au format abrégé, produisant une sortie comme « 1/3/00 ».

- **DTS_TIMEFORMAT** Affiche l’heure au format long, produisant une sortie comme « 5:31:42 PM ».

Toutefois, vous pouvez personnaliser l’apparence de la date ou de l’heure à l’aide d’une chaîne de format personnalisée. Cette chaîne personnalisée est constituée de caractères de format existants, de caractères non formatés ou d’une combinaison des deux. Une fois la chaîne personnalisée générée, effectuez un appel à [CDateTimeCtrl :: SetFormat](../mfc/reference/cdatetimectrl-class.md#setformat) en passant dans votre chaîne personnalisée. Le contrôle de sélecteur de date et d’heure affichera ensuite la valeur actuelle à l’aide de votre chaîne de format personnalisée.

L’exemple de code suivant (où *m_dtPicker* est l' `CDateTimeCtrl` objet) illustre une solution possible :

[!code-cpp[NVC_MFCControlLadenDialog#7](../mfc/codesnippet/cpp/using-custom-format-strings-in-a-date-and-time-picker-control_1.cpp)]

Outre les chaînes de format personnalisées, les contrôles de sélecteur de date et d’heure prennent également en charge les [champs de rappel](../mfc/using-callback-fields-in-a-date-and-time-picker-control.md).

## <a name="see-also"></a>Voir aussi

[Utilisation de CDateTimeCtrl](../mfc/using-cdatetimectrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
