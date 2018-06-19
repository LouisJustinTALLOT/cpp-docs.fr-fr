---
title: Conseils de programmation général MBCS | Documents Microsoft
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
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ab2b67c82a04a0c355761ec6572a9718d03c4666
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33855797"
---
# <a name="general-mbcs-programming-advice"></a>Conseils généraux sur la programmation MBCS
Utilisez les conseils suivants :  
  
-   Pour une flexibilité, utiliser des macros d’exécution telles que `_tcschr` et `_tcscpy` lorsque cela est possible. Pour plus d’informations, consultez [des mappages de texte générique dans Tchar.h](../text/generic-text-mappings-in-tchar-h.md).  
  
-   Utilisez la durée d’exécution C `_getmbcp` fonction pour obtenir plus d’informations sur la page de codes actuelle.  
  
-   Ne réutilisez pas de ressources de type chaîne. Selon le langage cible, une chaîne donnée peut avoir une signification différente lors de la traduction. Par exemple, menu principal de « Fichier » sur l’application peut être traduit différemment de la chaîne « Fichier » dans une boîte de dialogue. Si vous devez utiliser plusieurs chaînes avec le même nom, utiliser les ID de chaîne différents pour chacun.  
  
-   Vous souhaiterez peut-être savoir si votre application s’exécute sur un système d’exploitation compatible MBCS. Pour ce faire, définissez un indicateur au démarrage du programme ; ne comptez pas sur les appels d’API.  
  
-   Lors de la conception des boîtes de dialogue, prévoyez environ 30 % espace supplémentaire à la fin des contrôles de texte statique pour la traduction de MBCS.  
  
-   Soyez prudent lors de la sélection de polices pour votre application, car certaines polices ne sont pas disponibles sur tous les systèmes.  
  
-   Lorsque vous sélectionnez la police des boîtes de dialogue, utilisez [MS Shell Dlg](http://msdn.microsoft.com/library/windows/desktop/dd374112) au lieu de MS Sans Serif et Helvetica. MS Shell Dlg est remplacée par la police appropriée par le système avant de créer la boîte de dialogue. À l’aide de MS Shell Dlg permet de s’assurer que toutes les modifications dans le système d’exploitation pour agir sur cette police seront automatiquement disponibles. (MFC remplace MS Shell Dlg par DEFAULT_GUI_FONT ou la police système sur Windows 95, Windows 98 et Windows NT 4 car ces systèmes ne gèrent pas correctement MS Shell Dlg.)  
  
-   Lorsque vous concevez votre application, décidez des chaînes qui peuvent être localisés. En cas de doute, supposent que toutes les chaînes destinés à être localisés. Par conséquent, ne mélangez pas les chaînes qui peuvent être localisés avec ceux qui ne peuvent pas.  
  
## <a name="see-also"></a>Voir aussi  
 [Conseils de programmation MBCS](../text/mbcs-programming-tips.md)   
 [Incrémentation et décrémentation de pointeurs](../text/incrementing-and-decrementing-pointers.md)