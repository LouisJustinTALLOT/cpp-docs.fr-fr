---
title: Utilisation des champs de rappel dans un contrôle de sélecteur de date et heure
ms.date: 11/04/2016
f1_keywords:
- DTN_FORMATQUERY
- DTN_FORMAT
helpviewer_keywords:
- DateTimePicker control [MFC], callback fields
- callback fields in CDateTimeCtrl class [MFC]
- CDateTimeCtrl class [MFC], callback fields
- CDateTimeCtrl class [MFC], handling DTN_FORMAT and DTN_FORMATQ
- DTN_FORMATQUERY notification [MFC]
- DTN_FORMAT notification [MFC]
- DateTimePicker control [MFC]
ms.assetid: 404f4ba9-cba7-4718-9faa-bc6b274a723f
ms.openlocfilehash: 874f73df3dda3a720d4346ae3fb0136c662221db
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403579"
---
# <a name="using-callback-fields-in-a-date-and-time-picker-control"></a>Utilisation des champs de rappel dans un contrôle de sélecteur de date et heure

Outre les caractères de format standard qui définissent les champs de sélecteur de date et d'heure, vous pouvez personnaliser la sortie en spécifiant certaines parties d'une chaîne de format personnalisée comme champs de rappel. Pour déclarer un champ de rappel, incluez un ou plusieurs caractères "X" (code ASCII 88) n'importe où dans le corps de la chaîne de format. Par exemple, la chaîne suivante "Aujourd'hui, nous sommes le : "aa"/"MM"/"jj" (jour "X") '"fait que le contrôle de date et d'heure affiche la valeur actuelle comme année suivie du mois, de la date, et enfin du jour.

> [!NOTE]
>  Le nombre "X" dans un champ de rappel ne correspond pas au nombre de caractères affichés.

Vous pouvez distinguer plusieurs champs de rappel dans une chaîne personnalisée en répétant le caractère "X". Par conséquent, la chaîne de format "XXddddMMMdd, 'yyyXXX" contient deux champs de rappel uniques, "XX" et "XXX".

> [!NOTE]
>  Champs de rappel sont traités en tant que champs valides, votre application doit être préparée à traiter les messages de notification DTN_WMKEYDOWN.

Implémenter les champs de rappel du contrôle Date Time Picker se fait en trois parties :

- Initialisation de la chaîne de format personnalisée

- Gestion de la notification DTN_FORMATQUERY

- Gestion de la notification DTN_FORMAT

## <a name="initializing-the-custom-format-string"></a>Initialisation de la chaîne de format personnalisée

Initialisez la chaîne personnalisée par un appel à `CDateTimeCtrl::SetFormat`. Pour plus d’informations, consultez [à l’aide des chaînes de Format personnalisées dans une Date et d’un contrôle de sélecteur de temps](../mfc/using-custom-format-strings-in-a-date-and-time-picker-control.md). Un emplacement commun pour définir la chaîne de format personnalisé dans la fonction `OnInitDialog` de votre classe de boîte de dialogue contenante ou dans la fonction `OnInitialUpdate` de la classe d'affichage contenante.

## <a name="handling-the-dtnformatquery-notification"></a>Gestion de la notification DTN_FORMATQUERY

Lorsque le contrôle analyse la chaîne de format et rencontre un champ de rappel, l’application envoie des messages de notification DTN_FORMAT et DTN_FORMATQUERY. La chaîne de rappel du champ est incluse avec les notifications pour vous permettre de déterminer quel champ de rappel est interrogé.

La notification DTN_FORMATQUERY est envoyée pour récupérer la taille maximale autorisée en pixels de la chaîne qui s’affichera dans le champ de rappel en cours.

Pour calculer correctement cette valeur, vous devez calculer la hauteur et la largeur de la chaîne, à remplacer pour le champ, en utilisant la police d'affichage du contrôle. Le calcul réel de la chaîne est facilement effectué par un appel à la [GetTextExtentPoint32](/windows/desktop/api/wingdi/nf-wingdi-gettextextentpoint32a) fonction Win32. Une fois la taille déterminée, passez la valeur vers l'application et terminez la fonction gestionnaire.

L'exemple suivant est une méthode pour fournir la taille de la chaîne de rappel :

[!code-cpp[NVC_MFCControlLadenDialog#8](../mfc/codesnippet/cpp/using-callback-fields-in-a-date-and-time-picker-control_1.cpp)]

Une fois la taille du champ de rappel actuel calculée, vous devez fournir une valeur pour le champ. Pour cela, utilisez le gestionnaire pour la notification DTN_FORMAT.

## <a name="handling-the-dtnformat-notification"></a>Gestion de la notification DTN_FORMAT

La notification DTN_FORMAT est utilisée par l’application pour demander la chaîne de caractères qui sera remplacée. L'exemple de code suivant illustre une méthode possible :

[!code-cpp[NVC_MFCControlLadenDialog#9](../mfc/codesnippet/cpp/using-callback-fields-in-a-date-and-time-picker-control_2.cpp)]

> [!NOTE]
>  Le pointeur vers le **NMDATETIMEFORMAT** structure se trouve en convertissant le premier paramètre du Gestionnaire de notification dans le type approprié.

## <a name="see-also"></a>Voir aussi

[Utilisation de CDateTimeCtrl](../mfc/using-cdatetimectrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
