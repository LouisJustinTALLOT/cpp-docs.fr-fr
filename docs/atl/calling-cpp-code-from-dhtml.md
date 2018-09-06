---
title: Appeler le Code C++ à partir de DHTML | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DHTML, calling C++ code from
ms.assetid: 37329acd-4c22-40ca-a85a-b7480748f75f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dd28c36127edf75478874867a3a14ad52391ae76
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43767450"
---
# <a name="calling-c-code-from-dhtml"></a>Appel du Code C++ à partir de DHTML

Un contrôle DHTML Edit peut être hébergé dans un conteneur, tel que le conteneur de Test ou d’Internet Explorer. Consultez [test des propriétés et des événements avec le conteneur de Test](../mfc/testing-properties-and-events-with-test-container.md) pour plus d’informations sur l’accès du conteneur de Test.

Le conteneur qui héberge le contrôle communique avec le contrôle à l’aide des interfaces de contrôle normal. DHTML utilise l’interface de dispatch qui se termine par « UI » pour communiquer avec votre code C++ et votre ressource HTML. Dans [modification du contrôle ATL DHTML](../atl/modifying-the-atl-dhtml-control.md), vous pouvez vous exercer à ajouter les méthodes à appeler par ces différentes interfaces.

Pour voir un exemple de l’appel de code C++ à partir de DHTML, [créer un contrôle DHTML Edit](../atl/creating-an-atl-dhtml-control.md) à l’aide de l’Assistant contrôle ATL et examinez le code dans le fichier d’en-tête et dans le fichier HTML.

## <a name="declaring-webbrowser-methods-in-the-header-file"></a>Déclaration des méthodes WebBrowser dans le fichier d’en-tête

Pour appeler les méthodes C++ depuis l’UI DHTML, vous devez ajouter des méthodes à l’interface de l’interface utilisateur de votre contrôle. Par exemple, le fichier d’en-tête créé par l’Assistant contrôle ATL contient la méthode C++ `OnClick`, qui est un membre de l’interface de l’interface utilisateur du contrôle généré par l’Assistant.

Examinez `OnClick` dans le fichier .h du contrôle :

[!code-cpp[NVC_ATL_COM#4](../atl/codesnippet/cpp/calling-cpp-code-from-dhtml_1.h)]

Le premier paramètre, *pdispBody*, est un pointeur vers l’interface de dispatch de l’objet corps. Le deuxième paramètre, *varColor*, identifie la couleur à appliquer au contrôle.

## <a name="calling-c-code-in-the-html-file"></a>Appel du Code C++ dans le fichier HTML

Une fois que vous avez déclaré les méthodes WebBrowser dans le fichier d’en-tête, vous pouvez appeler les méthodes à partir du fichier HTML. Notez que, dans le fichier HTML que l’Assistant contrôle ATL insère trois méthodes de dispatch Windows : trois `OnClick` méthodes qui distribuent des messages pour modifier la couleur d’arrière-plan du contrôle.

Examinez une des méthodes dans le fichier HTML :

`<BUTTON onclick='window.external.OnClick(theBody, "red");'>Red</BUTTON>`

Dans le code HTML ci-dessus, la méthode externe de fenêtre, `OnClick`, est appelé dans le cadre de la balise de bouton. La méthode a deux paramètres : `theBody`, qui fait référence le corps du document HTML, et `"red"`, ce qui indique que couleur d’arrière-plan du contrôle devient rouge lorsque le bouton est activé. Le `Red` après la balise est l’étiquette du bouton.

Consultez [modification du contrôle ATL DHTML](../atl/modifying-the-atl-dhtml-control.md) pour plus d’informations sur la fourniture de vos propres méthodes. Consultez [identification des éléments du projet de contrôle DHTML Edit](../atl/identifying-the-elements-of-the-dhtml-control-project.md) pour plus d’informations sur le fichier HTML.

## <a name="see-also"></a>Voir aussi

[Prise en charge pour le contrôle DHTML](../atl/atl-support-for-dhtml-controls.md)

