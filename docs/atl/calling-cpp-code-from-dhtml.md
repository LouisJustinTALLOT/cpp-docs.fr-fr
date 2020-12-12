---
description: 'En savoir plus sur : appel de code C++ à partir de DHTML'
title: Appeler du code C++ à partir de DHTML
ms.date: 11/04/2016
helpviewer_keywords:
- DHTML, calling C++ code from
ms.assetid: 37329acd-4c22-40ca-a85a-b7480748f75f
ms.openlocfilehash: d880b0e9cb2f0b9d5228df7da4fc96fceeb87943
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97148484"
---
# <a name="calling-c-code-from-dhtml"></a>Appeler du code C++ à partir de DHTML

Un contrôle DHTML peut être hébergé dans un conteneur, tel que Test Container ou Internet Explorer. Pour plus d’informations sur l’accès à un conteneur de test, consultez Test des [Propriétés et des événements avec le conteneur](../mfc/testing-properties-and-events-with-test-container.md) de test.

Le conteneur qui héberge le contrôle communique avec le contrôle à l’aide des interfaces de contrôle normales. DHTML utilise l’interface de dispatch qui se termine par « UI » pour communiquer avec votre code C++ et votre ressource HTML. Lors de [la modification du contrôle ATL DHTML](../atl/modifying-the-atl-dhtml-control.md), vous pouvez vous exercer à ajouter les méthodes à appeler par ces différentes interfaces.

Pour voir un exemple d’appel de code C++ à partir de DHTML, [créez un contrôle DHTML](../atl/creating-an-atl-dhtml-control.md) à l’aide de l’Assistant contrôle ATL, puis examinez le code dans le fichier d’en-tête et dans le fichier html.

## <a name="declaring-webbrowser-methods-in-the-header-file"></a>Déclaration des méthodes WebBrowser dans le fichier d’en-tête

Pour appeler des méthodes C++ à partir de l’interface utilisateur DHTML, vous devez ajouter des méthodes à l’interface d’interface utilisateur de votre contrôle. Par exemple, le fichier d’en-tête créé par l’Assistant contrôle ATL contient la méthode C++ `OnClick` , qui est un membre de l’interface d’interface utilisateur du contrôle généré par l’Assistant.

Examinez `OnClick` dans le fichier. h du contrôle :

[!code-cpp[NVC_ATL_COM#4](../atl/codesnippet/cpp/calling-cpp-code-from-dhtml_1.h)]

Le premier paramètre, *pdispBody*, est un pointeur vers l’interface de dispatch de l’objet de corps. Le deuxième paramètre, *varColor*, identifie la couleur à appliquer au contrôle.

## <a name="calling-c-code-in-the-html-file"></a>Appel de code C++ dans le fichier HTML

Une fois que vous avez déclaré les méthodes WebBrowser dans le fichier d’en-tête, vous pouvez appeler les méthodes à partir du fichier HTML. Notez dans le fichier HTML que l’Assistant contrôle ATL insère trois méthodes de distribution Windows : trois `OnClick` méthodes qui répartissent les messages pour modifier la couleur d’arrière-plan du contrôle.

Examinez l’une des méthodes dans le fichier HTML :

`<BUTTON onclick='window.external.OnClick(theBody, "red");'>Red</BUTTON>`

Dans le code HTML ci-dessus, la méthode externe de la fenêtre, `OnClick` , est appelée dans le cadre de la balise du bouton. La méthode a deux paramètres : `theBody` , qui fait référence au corps du document HTML, et `"red"` , qui indique que la couleur d’arrière-plan du contrôle sera remplacée par la couleur rouge lorsque l’utilisateur clique sur le bouton. La `Red` balise suivante est l’étiquette du bouton.

Pour plus d’informations sur la façon de fournir vos propres méthodes, consultez [modification du contrôle ATL DHTML](../atl/modifying-the-atl-dhtml-control.md) . Pour plus d’informations sur le fichier HTML, consultez [identification des éléments du projet de contrôle DHTML](../atl/identifying-the-elements-of-the-dhtml-control-project.md) .

## <a name="see-also"></a>Voir aussi

[Prise en charge pour un contrôle DHTML](../atl/atl-support-for-dhtml-controls.md)
