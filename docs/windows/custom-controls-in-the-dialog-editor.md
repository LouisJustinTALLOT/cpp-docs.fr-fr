---
title: Contrôles personnalisés dans l’éditeur de boîtes de dialogue (C++)
ms.date: 11/04/2016
f1_keywords:
- Custom Control
helpviewer_keywords:
- controls [C++], templates
- custom controls [C++], dialog boxes
- custom controls [C++]
- dialog box controls [C++], custom (user) controls
- Dialog Editor [C++], custom controls
ms.assetid: f494b314-4000-4bbe-bbd0-4b18fb71ede1
ms.openlocfilehash: c48ad87948037fa843fdc16a016ae23bf139feb1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50677095"
---
# <a name="custom-controls-in-the-dialog-editor-c"></a>Contrôles personnalisés dans l’éditeur de boîtes de dialogue (C++)

L’éditeur de boîtes de dialogue vous permet d’utiliser l’existant « custom » ou des contrôles dans un modèle de boîte de dialogue « utilisateur ».

> [!NOTE]
> Contrôles personnalisés dans ce sens doivent ne pas être confondus avec les contrôles ActiveX. Contrôles ActiveX étaient parfois appelés contrôles personnalisés OLE. En outre, ne confondez pas ces contrôles avec les contrôles owner-drawn dans Windows.

Cette fonctionnalité vise à vous permettent d’utiliser des contrôles autres que ceux fournis par Windows. Au moment de l’exécution, le contrôle est associé à une classe de fenêtre (pas identique à une classe C++). Une façon plus courante pour accomplir la même tâche consiste à installer n’importe quel contrôle, tel qu’un contrôle statique, dans votre boîte de dialogue. Puis au moment de l’exécution, dans le [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) fonctionner, supprimez ce contrôle et remplacez-le par votre propre contrôle personnalisé.

Il s’agit d’une vieille méthode. Aujourd'hui, il est conseillé dans la plupart des cas d’écrire un contrôle ActiveX ou une sous-classe un contrôle commun de Windows.

Pour ces contrôles personnalisés, vous êtes limité à :

- Définition de l’emplacement dans la boîte de dialogue.

- Taper une légende.

- Identifiant le nom de la classe du contrôle Windows (code de votre application doit inscrire le contrôle par son nom).

- Taper une valeur hexadécimale 32 bits qui définit le style du contrôle.

- Définir le style étendu.

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Contrôles dans les boîtes de dialogue](../windows/controls-in-dialog-boxes.md)<br/>
[Contrôles](../mfc/controls-mfc.md)