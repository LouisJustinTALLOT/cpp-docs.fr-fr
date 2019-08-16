---
title: Conseils généraux sur la programmation MBCS
ms.date: 11/04/2016
helpviewer_keywords:
- MBCS [C++], dialog box fonts
- MS Shell Dlg
- MBCS [C++], programming
- dialog boxes [C++], fonts
ms.assetid: 7b541235-f3e5-4af0-b2c2-a0112cd5fbfb
ms.openlocfilehash: 887387220105614eb3257f008ec601a6fc0adc18
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491183"
---
# <a name="general-mbcs-programming-advice"></a>Conseils généraux sur la programmation MBCS

Utilisez les conseils suivants:

- Pour plus de flexibilité, utilisez des macros Runtime telles `_tcschr` que `_tcscpy` et lorsque cela est possible. Pour plus d’informations, consultez mappages de [texte générique dans Tchar. h](../text/generic-text-mappings-in-tchar-h.md).

- Utilisez la `_getmbcp` fonction Runtime C pour obtenir des informations sur la page de codes actuelle.

- Ne réutilisez pas les ressources de type chaîne. Selon le langage cible, une chaîne donnée peut avoir une signification différente lors de la traduction. Par exemple, «fichier» dans le menu principal de l’application peut se traduire différemment de la chaîne «fichier» dans une boîte de dialogue. Si vous devez utiliser plusieurs chaînes portant le même nom, utilisez des ID de chaîne différents pour chacun d’entre eux.

- Vous souhaiterez peut-être savoir si votre application s’exécute sur un système d’exploitation compatible MBCS. Pour ce faire, définissez un indicateur au démarrage du programme. ne vous fiez pas aux appels d’API.

- Lors de la conception de boîtes de dialogue, prévoyez environ 30% d’espace supplémentaire à la fin des contrôles de texte statiques pour la traduction MBCS.

- Soyez prudent lorsque vous sélectionnez des polices pour votre application, car certaines polices ne sont pas disponibles sur tous les systèmes.

- Lorsque vous sélectionnez la police des boîtes de dialogue, utilisez [MS Shell Dlg](/windows/win32/Intl/using-ms-shell-dlg-and-ms-shell-dlg-2) au lieu de MS sans serif ou Helvetica. MS Shell Dlg est remplacé par la police correcte par le système avant la création de la boîte de dialogue. L’utilisation de MS Shell Dlg garantit que toutes les modifications apportées au système d’exploitation pour gérer cette police seront automatiquement disponibles. (MFC remplace MS Shell Dlg par DEFAULT_GUI_FONT ou la police système sur Windows 95, Windows 98 et Windows NT 4, car ces systèmes ne gèrent pas correctement MS Shell Dlg.)

- Lorsque vous concevez votre application, choisissez les chaînes qui peuvent être localisées. En cas de doute, supposez qu’une chaîne donnée sera localisée. Par conséquent, ne mélangez pas les chaînes qui peuvent être localisées avec celles qui ne le peuvent pas.

## <a name="see-also"></a>Voir aussi

[Conseils de programmation MBCS](../text/mbcs-programming-tips.md)<br/>
[Incrémentation et décrémentation de pointeurs](../text/incrementing-and-decrementing-pointers.md)
