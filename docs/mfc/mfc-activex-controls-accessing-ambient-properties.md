---
description: 'En savoir plus sur : contrôles ActiveX MFC : accès aux propriétés ambiantes'
title: 'Contrôles ActiveX MFC : accès aux propriétés ambiantes'
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], accessing ambient properties
- properties [MFC], accessing ambient
ms.assetid: fdc9db29-e6b0-45d2-a879-8bd60e2058a7
ms.openlocfilehash: 6b553c73873a6f96cab3ab55b576a51045c06609
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97203066"
---
# <a name="mfc-activex-controls-accessing-ambient-properties"></a>Contrôles ActiveX MFC : accès aux propriétés ambiantes

Cet article explique comment un contrôle ActiveX peut accéder aux propriétés ambiantes de son conteneur de contrôle.

Un contrôle peut obtenir des informations sur son conteneur en accédant aux propriétés ambiantes du conteneur. Ces propriétés présentent des caractéristiques visuelles, telles que la couleur d'arrière-plan du conteneur, la police actuelle utilisée par le conteneur, et des caractéristiques opérationnelles, par exemple si le conteneur est actuellement en mode utilisateur ou en mode concepteur. Un contrôle peut utiliser les propriétés ambiantes pour adapter son apparence et son comportement au conteneur particulier dans lequel il est incorporé. Toutefois, un contrôle ne doit jamais supposer que son conteneur prend en charge une propriété ambiante particulière. En fait, certains conteneurs peuvent ne pas prendre en charge les propriétés ambiantes du tout. En l'absence d'une propriété ambiante, un contrôle doit utiliser une valeur par défaut raisonnable.

Pour accéder à une propriété ambiante, effectuez un appel à [COleControl :: GetAmbientProperty](reference/colecontrol-class.md#getambientproperty). Cette fonction attend l'ID de dispatch de la propriété ambiante en tant que premier paramètre (le fichier OLECTL.H définit les ID de dispatch pour l'ensemble standard de propriétés ambiantes).

Les paramètres de la fonction `GetAmbientProperty` sont l’ID de dispatch, une étiquette de variante indiquant le type de propriété attendu et un pointeur vers la mémoire dans laquelle la valeur doit être retournée. Le type de données auxquelles ce pointeur fait référence varie selon la balise de variante. La fonction retourne la **valeur true** si le conteneur prend en charge la propriété ; sinon, elle retourne **false**.

L'exemple de code suivant obtient la valeur de la propriété ambiante appelée "UserMode". Si la propriété n’est pas prise en charge par le conteneur, la valeur par défaut **true** est utilisée :

[!code-cpp[NVC_MFC_AxUI#30](codesnippet/cpp/mfc-activex-controls-accessing-ambient-properties_1.cpp)]

Pour plus de commodité, `COleControl` fournit des fonctions d'assistance qui accèdent à plusieurs des propriétés ambiantes couramment utilisées et retourne les valeurs par défaut appropriées lorsque les propriétés ne sont pas disponibles. Ces fonctions d'assistance sont les suivantes :

- [COleControl::AmbientBackColor](reference/colecontrol-class.md#ambientbackcolor)

- [AmbientDisplayName](reference/colecontrol-class.md#ambientdisplayname)

- [AmbientFont](reference/colecontrol-class.md#ambientfont)

    > [!NOTE]
    >  L’appelant doit appeler `Release( )` sur la police retournée.

- [AmbientForeColor](reference/colecontrol-class.md#ambientforecolor)

- [AmbientLocaleID](reference/colecontrol-class.md#ambientlocaleid)

- [AmbientScaleUnits](reference/colecontrol-class.md#ambientscaleunits)

- [AmbientTextAlign](reference/colecontrol-class.md#ambienttextalign)

- [AmbientUserMode](reference/colecontrol-class.md#ambientusermode)

- [AmbientUIDead](reference/colecontrol-class.md#ambientuidead)

- [AmbientShowHatching](reference/colecontrol-class.md#ambientshowhatching)

- [AmbientShowGrabHandles](reference/colecontrol-class.md#ambientshowgrabhandles)

Si la valeur d’une propriété ambiante change (par le biais d’une action du conteneur), la `OnAmbientPropertyChanged` fonction membre du contrôle est appelée. Remplacez cette fonction membre pour traiter cette notification. Le paramètre pour `OnAmbientPropertyChanged` est l’ID de dispatch de la propriété ambiante affectée. La valeur de cet ID de dispatch peut être DISPID_UNKNOWN, qui indique qu'une ou plusieurs propriétés ambiantes ont été modifiées, mais les informations sur les propriétés affectées ne sont pas disponibles.

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC](mfc-activex-controls.md)
