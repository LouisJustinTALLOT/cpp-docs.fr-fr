---
title: À l’aide des champs de rappel dans une Date Time Picker contrôle | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- DTN_FORMATQUERY
- DTN_FORMAT
dev_langs:
- C++
helpviewer_keywords:
- DateTimePicker control [MFC], callback fields
- callback fields in CDateTimeCtrl class [MFC]
- CDateTimeCtrl class [MFC], callback fields
- CDateTimeCtrl class [MFC], handling DTN_FORMAT and DTN_FORMATQ
- DTN_FORMATQUERY notification [MFC]
- DTN_FORMAT notification [MFC]
- DateTimePicker control [MFC]
ms.assetid: 404f4ba9-cba7-4718-9faa-bc6b274a723f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9b0d59aa8c30e9308448467bb198e898106e61f0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33383784"
---
# <a name="using-callback-fields-in-a-date-and-time-picker-control"></a>Utilisation des champs de rappel dans un contrôle de sélecteur de date et heure
Outre les caractères de format standard qui définissent les champs de sélecteur de date et d'heure, vous pouvez personnaliser la sortie en spécifiant certaines parties d'une chaîne de format personnalisée comme champs de rappel. Pour déclarer un champ de rappel, incluez un ou plusieurs caractères "X" (code ASCII 88) n'importe où dans le corps de la chaîne de format. Par exemple, la chaîne suivante "Aujourd'hui, nous sommes le : "aa"/"MM"/"jj" (jour "X") '"fait que le contrôle de date et d'heure affiche la valeur actuelle comme année suivie du mois, de la date, et enfin du jour.  
  
> [!NOTE]
>  Le nombre "X" dans un champ de rappel ne correspond pas au nombre de caractères affichés.  
  
 Vous pouvez distinguer plusieurs champs de rappel dans une chaîne personnalisée en répétant le caractère "X". Par conséquent, la chaîne de format "XXddddMMMdd, 'yyyXXX" contient deux champs de rappel uniques, "XX" et "XXX".  
  
> [!NOTE]
>  Champs de rappel sont traités comme des champs valides, afin de votre application doit être prête à gérer **DTN_WMKEYDOWN** messages de notification.  
  
 Implémenter les champs de rappel du contrôle Date Time Picker se fait en trois parties :  
  
-   Initialisation de la chaîne de format personnalisée  
  
-   Gère la **DTN_FORMATQUERY** notification  
  
-   Gère la **DTN_FORMAT** notification  
  
## <a name="initializing-the-custom-format-string"></a>Initialisation de la chaîne de format personnalisée  
 Initialisez la chaîne personnalisée par un appel à `CDateTimeCtrl::SetFormat`. Pour plus d’informations, consultez [à l’aide des chaînes de Format personnalisées dans une Date et d’un contrôle sélecteur d’heure](../mfc/using-custom-format-strings-in-a-date-and-time-picker-control.md). Un emplacement commun pour définir la chaîne de format personnalisé dans la fonction `OnInitDialog` de votre classe de boîte de dialogue contenante ou dans la fonction `OnInitialUpdate` de la classe d'affichage contenante.  
  
## <a name="handling-the-dtnformatquery-notification"></a>Gestion de la notification DTN_FORMATQUERY  
 Lorsque le contrôle analyse la chaîne de format et rencontre un champ de rappel, l’application envoie **DTN_FORMAT** et **DTN_FORMATQUERY** messages de notification. La chaîne de rappel du champ est incluse avec les notifications pour vous permettre de déterminer quel champ de rappel est interrogé.  
  
 Le **DTN_FORMATQUERY** notification est envoyée pour récupérer la taille maximale autorisée en pixels de la chaîne qui sera affiché dans le champ de rappel actuel.  
  
 Pour calculer correctement cette valeur, vous devez calculer la hauteur et la largeur de la chaîne, à remplacer pour le champ, en utilisant la police d'affichage du contrôle. Le calcul réel de la chaîne est facilement effectué par un appel à la [GetTextExtentPoint32](http://msdn.microsoft.com/library/windows/desktop/dd144938) fonction Win32. Une fois la taille déterminée, passez la valeur vers l'application et terminez la fonction gestionnaire.  
  
 L'exemple suivant est une méthode pour fournir la taille de la chaîne de rappel :  
  
 [!code-cpp[NVC_MFCControlLadenDialog#8](../mfc/codesnippet/cpp/using-callback-fields-in-a-date-and-time-picker-control_1.cpp)]  
  
 Une fois la taille du champ de rappel actuel calculée, vous devez fournir une valeur pour le champ. Cette opération est effectuée dans le gestionnaire pour le **DTN_FORMAT** notification.  
  
## <a name="handling-the-dtnformat-notification"></a>Gestion de la notification DTN_FORMAT  
 Le **DTN_FORMAT** notification est utilisée par l’application pour demander la chaîne de caractères qui sera remplacée. L'exemple de code suivant illustre une méthode possible :  
  
 [!code-cpp[NVC_MFCControlLadenDialog#9](../mfc/codesnippet/cpp/using-callback-fields-in-a-date-and-time-picker-control_2.cpp)]  
  
> [!NOTE]
>  Le pointeur vers le **NMDATETIMEFORMAT** structure se trouve en effectuant un cast du premier paramètre du Gestionnaire de notification dans le type approprié.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CDateTimeCtrl](../mfc/using-cdatetimectrl.md)   
 [Contrôles](../mfc/controls-mfc.md)

