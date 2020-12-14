---
description: 'En savoir plus sur : utilisation des champs de rappel dans un contrôle de sélecteur de date et d’heure'
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
ms.openlocfilehash: 3ff0ae2af8e71a53cceff4d5d8df652f701b1ef1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97202624"
---
# <a name="using-callback-fields-in-a-date-and-time-picker-control"></a>Utilisation des champs de rappel dans un contrôle de sélecteur de date et heure

Outre les caractères de format standard qui définissent les champs de sélecteur de date et d'heure, vous pouvez personnaliser la sortie en spécifiant certaines parties d'une chaîne de format personnalisée comme champs de rappel. Pour déclarer un champ de rappel, incluez un ou plusieurs caractères "X" (code ASCII 88) n'importe où dans le corps de la chaîne de format. Par exemple, la chaîne suivante "Aujourd'hui, nous sommes le : "aa"/"MM"/"jj" (jour "X") '"fait que le contrôle de date et d'heure affiche la valeur actuelle comme année suivie du mois, de la date, et enfin du jour.

> [!NOTE]
> Le nombre "X" dans un champ de rappel ne correspond pas au nombre de caractères affichés.

Vous pouvez distinguer plusieurs champs de rappel dans une chaîne personnalisée en répétant le caractère "X". Par conséquent, la chaîne de format "XXddddMMMdd, 'yyyXXX" contient deux champs de rappel uniques, "XX" et "XXX".

> [!NOTE]
> Les champs de rappel étant traités comme des champs valides, votre application doit être préparée à gérer les messages de notification DTN_WMKEYDOWN.

Implémenter les champs de rappel du contrôle Date Time Picker se fait en trois parties :

- Initialisation de la chaîne de format personnalisée

- Gérer la notification DTN_FORMATQUERY

- Gérer la notification DTN_FORMAT

## <a name="initializing-the-custom-format-string"></a>Initialisation de la chaîne de format personnalisée

Initialisez la chaîne personnalisée par un appel à `CDateTimeCtrl::SetFormat`. Pour plus d’informations, consultez [utilisation de chaînes de format personnalisées dans un contrôle de sélecteur de date et heure](../mfc/using-custom-format-strings-in-a-date-and-time-picker-control.md). Un emplacement commun pour définir la chaîne de format personnalisé dans la fonction `OnInitDialog` de votre classe de boîte de dialogue contenante ou dans la fonction `OnInitialUpdate` de la classe d'affichage contenante.

## <a name="handling-the-dtn_formatquery-notification"></a>Gestion de la notification DTN_FORMATQUERY

Lorsque le contrôle analyse la chaîne de format et rencontre un champ de rappel, l'application envoie des messages de notification DTN_FORMAT et DTN_FORMATQUERY. La chaîne de rappel du champ est incluse avec les notifications pour vous permettre de déterminer quel champ de rappel est interrogé.

La notification DTN_FORMATQUERY est envoyée pour récupérer la taille maximale autorisée en pixels de la chaîne qui sera affichée dans le champ de rappel actuel.

Pour calculer correctement cette valeur, vous devez calculer la hauteur et la largeur de la chaîne, à remplacer pour le champ, en utilisant la police d'affichage du contrôle. Le calcul réel de la chaîne est facilement effectué avec un appel à la fonction Win32 [GetTextExtentPoint32](/windows/win32/api/wingdi/nf-wingdi-gettextextentpoint32w) . Une fois la taille déterminée, passez la valeur vers l'application et terminez la fonction gestionnaire.

L'exemple suivant est une méthode pour fournir la taille de la chaîne de rappel :

[!code-cpp[NVC_MFCControlLadenDialog#8](../mfc/codesnippet/cpp/using-callback-fields-in-a-date-and-time-picker-control_1.cpp)]

Une fois la taille du champ de rappel actuel calculée, vous devez fournir une valeur pour le champ. Cette opération s’effectue dans le gestionnaire de la notification de DTN_FORMAT.

## <a name="handling-the-dtn_format-notification"></a>Gestion de la notification DTN_FORMAT

La notification DTN_FORMAT est utilisée par l'application pour demander la chaîne de caractères qui sera remplacée. L'exemple de code suivant illustre une méthode possible :

[!code-cpp[NVC_MFCControlLadenDialog#9](../mfc/codesnippet/cpp/using-callback-fields-in-a-date-and-time-picker-control_2.cpp)]

> [!NOTE]
> Le pointeur vers la structure **NMDATETIMEFORMAT** est trouvé en effectuant un cast du premier paramètre du gestionnaire de notification vers le type approprié.

## <a name="see-also"></a>Voir aussi

[Utilisation de CDateTimeCtrl](../mfc/using-cdatetimectrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
