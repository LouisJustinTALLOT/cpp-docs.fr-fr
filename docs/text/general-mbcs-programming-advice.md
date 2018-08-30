---
title: Conseils sur la programmation MBCS de général | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- _mbcs
dev_langs:
- C++
helpviewer_keywords:
- MBCS [C++], dialog box fonts
- MS Shell Dlg
- MBCS [C++], programming
- dialog boxes [C++], fonts
ms.assetid: 7b541235-f3e5-4af0-b2c2-a0112cd5fbfb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 532f1e060398b20d4714f461c2d687031756c910
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43201120"
---
# <a name="general-mbcs-programming-advice"></a>Conseils généraux sur la programmation MBCS
Utilisez les conseils suivants :  
  
-   Pour une flexibilité, utiliser les macros d’exécution telles que `_tcschr` et `_tcscpy` lorsque cela est possible. Pour plus d’informations, consultez [des mappages de texte générique dans Tchar.h](../text/generic-text-mappings-in-tchar-h.md).  
  
-   Utilisez la durée d’exécution C `_getmbcp` (fonction) pour obtenir des informations sur la page de codes actuelle.  
  
-   Ne réutilisez pas les ressources de type chaîne. Selon le langage cible, une chaîne donnée peut avoir une signification différente lors de la traduction. Par exemple, menu principal de « Fichier » sur l’application peut être traduit différemment de la chaîne « Fichier » dans une boîte de dialogue. Si vous devez utiliser plusieurs chaînes avec le même nom, utiliser les ID de chaîne différentes pour chacun.  
  
-   Vous souhaiterez peut-être savoir si votre application est en cours d’exécution sur un système d’exploitation prenant en charge MBCS. Pour ce faire, définissez un indicateur au démarrage du programme ; ne comptez pas sur les appels d’API.  
  
-   Lorsque vous concevez des boîtes de dialogue, prévoyez environ 30 % espace supplémentaire à la fin des contrôles de texte statique pour la traduction de MBCS.  
  
-   Soyez prudent lors de la sélection de polices pour votre application, car certaines polices ne sont pas disponibles sur tous les systèmes.  
  
-   Lorsque vous sélectionnez la police des boîtes de dialogue, utilisez [MS Shell Dlg](/windows/desktop/Intl/using-ms-shell-dlg-and-ms-shell-dlg-2) au lieu de MS Sans Serif et Helvetica. MS Shell Dlg est remplacée par la police appropriée par le système avant de créer la boîte de dialogue. À l’aide de MS Shell Dlg permet de s’assurer que toutes les modifications dans le système d’exploitation pour agir sur cette police seront automatiquement disponibles. (MFC remplace MS Shell Dlg DEFAULT_GUI_FONT ou la police système sur Windows 95, Windows 98 et Windows NT 4, car ces systèmes ne gèrent pas correctement MS Shell Dlg.)  
  
-   Lorsque vous concevez votre application, décidez des chaînes qui peuvent être localisés. En cas de doute, supposons que n’importe quelle chaîne donnée sera localisée. Par conséquent, ne mélangez pas les chaînes qui peuvent être localisés avec ceux qui ne peuvent pas.  
  
## <a name="see-also"></a>Voir aussi  
 [Conseils de programmation MBCS](../text/mbcs-programming-tips.md)   
 [Incrémentation et décrémentation de pointeurs](../text/incrementing-and-decrementing-pointers.md)