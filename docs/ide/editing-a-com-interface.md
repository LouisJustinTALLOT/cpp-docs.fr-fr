---
title: Modification d'une interface COM
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.com.editing.interfaces
helpviewer_keywords:
- methods [C++], adding to COM interfaces
- COM interfaces, editing
- properties [C++], adding to COM interfaces
ms.assetid: 6c2909e0-af2d-4a37-bb39-ed372e6129cf
ms.openlocfilehash: 338782cbf7cc302c285e8e778389ae28e20f2b14
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50657364"
---
# <a name="editing-a-com-interface"></a>Modification d'une interface COM

À l’aide des commandes du menu Affichage de classes, vous pouvez définir de nouvelles méthodes et propriétés pour les interfaces COM dans vos projets Visual C++. Par ailleurs, dans la boîte à outils, vous pouvez définir des événements pour les contrôles ActiveX.

Pour les classes d’objets COM basées sur ATL et MFC, vous pouvez modifier l’implémentation de classe en même temps que vous modifiez l’interface.

> [!NOTE]
>  Pour les interfaces que vous avez définies en dehors de la boîte de dialogue **Ajouter une classe**, Visual C++ ajoute les méthodes ou propriétés au fichier .idl, puis des stubs aux classes qui implémentent les méthodes, même si les interfaces sont ajoutées manuellement.

Les trois Assistants suivants vous aident à personnaliser les interfaces existantes. Ils sont disponibles sous Affichage de classes :

|Assistant|Type de projet|
|------------|------------------|
|[Assistant Ajout de propriété](../ide/names-add-property-wizard.md)|Projets ATL ou MFC prenant en charge ATL. Cliquez avec le bouton droit sur l’interface à laquelle vous voulez ajouter la propriété.<br /><br />Visual C++ détecte le type de projet et modifie en conséquence les options de l’Assistant Ajout de propriété :<br /><br />- Pour les dispinterfaces de projets créés à l’aide de [l’Assistant Application MFC](../mfc/reference/mfc-application-wizard.md), l’appel de l’Assistant Ajout de propriété fournit des options propres à MFC.<br />- Pour les interfaces de contrôle ActiveX MFC, l’Assistant Ajout de propriété fournit la liste des méthodes et propriétés stock que vous pouvez utiliser telles quelles ou personnaliser pour votre contrôle.<br />- Pour toutes les autres interfaces, l’Assistant Ajout de propriété fournit des options utiles dans la plupart des situations.|
|[Assistant Ajout de méthode](../ide/add-method-wizard.md)|Projets ATL ou MFC prenant en charge ATL. Cliquez avec le bouton droit sur l’interface à laquelle vous voulez ajouter la méthode.<br /><br />Visual C++ détecte le type de projet et modifie en conséquence les options de l’Assistant Ajout de méthode :<br /><br />- Pour les dispinterfaces de projets créés à l’aide de [l’Assistant Application MFC](../mfc/reference/mfc-application-wizard.md), l’appel de l’Assistant Ajout de méthode fournit des options spécifiques de MFC.<br />- Pour les interfaces de contrôle ActiveX MFC, l’Assistant Ajout de méthode fournit la liste des méthodes et propriétés stock que vous pouvez utiliser telles quelles ou personnaliser pour votre contrôle.<br />- Pour toutes les autres interfaces, l’Assistant **Ajout de méthode** fournit des options utiles dans la plupart des situations.|

Vous pouvez également implémenter de nouvelles interfaces sur votre contrôle COM en cliquant avec le bouton droit sur la classe de contrôle de l’objet dans l’affichage de classes et en cliquant sur [Implémenter l’interface](../ide/implement-interface-wizard.md).

## <a name="see-also"></a>Voir aussi

[Utilisation des fichiers de ressources](../windows/working-with-resource-files.md)<br>
[Ajout de fonctionnalités à l’aide des Assistants Code](../ide/adding-functionality-with-code-wizards-cpp.md)<br>
[Types de projets Visual C++](../ide/visual-cpp-project-types.md)